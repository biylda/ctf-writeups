# Local News

## Points
495

## Description
Be sure to check your local news broadcast for the latest updates!

Difficulty: medium-hard

[app.apk](https://tamuctf.com/files/ff1dc83797ccb54f513a23b2a6d87648/app.apk)

## Solution
Looking at `strings.xml` resource as in [Secrets](../secrets/readme.md) won't help here. The string is hidden somewhere inside the code.

Decompile `app.apk` using [dex2jar](https://github.com/pxb1988/dex2jar).
```sh
λ d2j-dex2jar.bat app.apk
dex2jar app.apk -> .\app-dex2jar.jar
```

Open the `app-dex2jar.jar` using [jd-gui](https://github.com/java-decompiler/jd-gui). Look at `com.tamu.ctf.hidden/MainActivity`.
```java
package com.tamu.ctf.hidden;

import android.content.BroadcastReceiver;
import android.content.Context;
import android.content.Intent;
import android.content.IntentFilter;
import android.os.Bundle;
import android.support.v4.content.LocalBroadcastManager;
import android.support.v7.app.AppCompatActivity;
import android.util.Log;
import io.michaelrocks.paranoid.Deobfuscator.app.Debug;

public class MainActivity
  extends AppCompatActivity
{
  protected void onCreate(Bundle paramBundle)
  {
    super.onCreate(paramBundle);
    setContentView(2131296282);
    paramBundle = new BroadcastReceiver()
    {
      public void onReceive(Context paramAnonymousContext, Intent paramAnonymousIntent)
      {
        Log.d(MainActivity.this.getString(2131427360), Deobfuscator.app.Debug.getString(0));
      }
    };
    IntentFilter localIntentFilter = new IntentFilter();
    localIntentFilter.addAction(getString(2131427361));
    LocalBroadcastManager.getInstance(this).registerReceiver(paramBundle, localIntentFilter);
  }
}
```
You can see that the app is able to receive broadcasts with action `getString(2131427361) = "hidden_action"` and whenever such broadcast is received, it logs the flag `MainActivity.this.getString(2131427360) = "flag", Deobfuscator.app.Debug.getString(0)`.

There are two ways to solve this:
- Create your own app which broadcasts `"hidden_action"`, and read the flag from log. (too much work, haven't tried it :-)
- Look at what `Deobfuscator.app.Debug.getString(0)` returns.

Let's look at `io.michaelrocks.paranoid.Deobfuscator.app.Debug`. But where is it?

Extract `app.apk` as a regular zip, e.g. using `7zip`. Decompile `app\classes2.dex` using [dex2jar](https://github.com/pxb1988/dex2jar).
```sh
λ 7z x -oapp app.apk
λ d2j-dex2jar.bat app\classes2.dex
dex2jar app\classes2.dex -> .\classes2-dex2jar.jar
```

Open the `classes2-dex2jar.jar` using [jd-gui](https://github.com/java-decompiler/jd-gui). Look at `io.michaelrocks.paranoid/Deobfuscator$app$Debug`.
```java
package io.michaelrocks.paranoid;

public class Deobfuscator$app$Debug
{
  private static final String[] charChunks = { "}18m_hanbed3i{0g" };
  private static final String[] indexChunks = { "\017\f\017\t\003\r\005\f\n\n\t\007\004\002\001\006\t\b\016\001\013\b\t\006\000" };
  private static final String[] locationChunks = { "\000\000\031\000" };
  
  public static String getString(int paramInt)
  {
    int j = paramInt / 4096;
    int i = paramInt % 4096;
    int k = (paramInt + 1) / 4096;
    paramInt = (paramInt + 1) % 4096;
    Object localObject = locationChunks[j];
    String str = locationChunks[k];
    j = ((String)localObject).charAt(i * 2);
    i = (((String)localObject).charAt(i * 2 + 1) & 0xFFFF) << '\020' | j & 0xFFFF;
    j = str.charAt(paramInt * 2);
    j = (str.charAt(paramInt * 2 + 1) << '\020' | j) - i;
    localObject = new char[j];
    paramInt = 0;
    while (paramInt < j)
    {
      k = i + paramInt;
      int m = k / 8192;
      k = indexChunks[m].charAt(k % 8192) & 0xFFFF;
      m = k / 8192;
      localObject[paramInt] = charChunks[m].charAt(k % 8192);
      paramInt += 1;
    }
    return new String((char[])localObject);
  }
}
```

Let's make a few adjustments so that it prints the flag and just run the [code](Flag.java) in java.

```java
public class Flag
{
  private static final String[] charChunks = { "}18m_hanbed3i{0g" };
  private static final String[] indexChunks = { "\017\f\017\t\003\r\005\f\n\n\t\007\004\002\001\006\t\b\016\001\013\b\t\006\000" };
  private static final String[] locationChunks = { "\000\000\031\000" };
  
  public static String getString(int paramInt)
  {
    int j = paramInt / 4096;
    int i = paramInt % 4096;
    int k = (paramInt + 1) / 4096;
    paramInt = (paramInt + 1) % 4096;
    Object localObject = locationChunks[j];
    String str = locationChunks[k];
    j = ((String)localObject).charAt(i * 2);
    i = (((String)localObject).charAt(i * 2 + 1) & 0xFFFF) << '\020' | j & 0xFFFF;
    j = str.charAt(paramInt * 2);
    j = (str.charAt(paramInt * 2 + 1) << '\020' | j) - i;
    localObject = new char[j];
    paramInt = 0;
    while (paramInt < j)
    {
      k = i + paramInt;
      int m = k / 8192;
      k = indexChunks[m].charAt(k % 8192) & 0xFFFF;
      m = k / 8192;
      ((char[])localObject)[paramInt] = charChunks[m].charAt(k % 8192);
      paramInt += 1;
    }
    return new String((char[])localObject);
  }
  
  public static void main(String[] args)
  {
    System.out.println(getString(0));
  }
}
```

```sh
λ javac Flag.java
λ java Flag
gigem{hidden_81aeb013bea}
```

## Flag
`gigem{hidden_81aeb013bea}`