# Buckets

## Points
435

## Description
easy

Checkout my s3 bucket website!
http://tamuctf.s3-website-us-west-2.amazonaws.com/

Difficulty: easy

## Solution
Look at http://tamuctf.s3.amazonaws.com/. Listing access is enabled for everyone.

```xml
<Contents>
<Key>
Dogs/CC2B70BD238F48BE29D8F0D42B170127/CBD2DD691D3DB1EBF96B283BDC8FD9A1/flag.txt
</Key>
<LastModified>2019-02-19T17:06:51.000Z</LastModified>
<ETag>"0a2a337eda703cf59b4bc491dbc73621"</ETag>
<Size>28</Size>
<StorageClass>STANDARD</StorageClass>
</Contents>
```
http://tamuctf.s3.amazonaws.com/Dogs/CC2B70BD238F48BE29D8F0D42B170127/CBD2DD691D3DB1EBF96B283BDC8FD9A1/flag.txt

## Flag
`flag{W0W_S3_BAD_PERMISSIONS}`