# s3GetTargetDeleteRetentionPeriod
Identify and calculate the amount volume of the objects violating the Wasabi Delete Retention period.

## Execute
You need to install python environment, so please refer to the following repository for details on how to setup.
[How to setup your environment](https://github.com/luizcarloskazuyukifukaya/s3pythonsamples/blob/main/README.md)

```
python3 ./s3GetTargetDeleteRetentionPeriod.py
```

## Output sample
```
Object Key name: DummyFile-Root-L1.txt
Object Last Modified Time: Tuesday, March 19, 2024 05:13 AM [violating 30 days]
Object Size: 113282
... Accumulated Total Size: 11681253
Bucket name: sca-primary-wcn-bucket-wcn-sync
Bucket location: ap-southeast-2
Object Key name: .tt_rt/sync/.clients/CLAT7-5Z9PD-MM989-74215-R9VR9
Object Last Modified Time: Tuesday, March 19, 2024 05:21 AM [violating 30 days]
Object Size: 0
... Accumulated Total Size: 11681253
Bucket name: sca-secondry-wcn-bucket
Bucket location: ap-southeast-2
Bucket name: test-versioning-with-suspend-status
Bucket location: ap-northeast-1
No object found... the target bucket is empty!!!
Bucket name: wasabi-lucidlink
Bucket location: ap-northeast-1
No object found... the target bucket is empty!!!
Bucket name: wasabi-lucidlink-2
Bucket location: ap-northeast-1
Bucket name: wasabi-wcn-backup-bucket
Bucket location: ap-northeast-1
No object found... the target bucket is empty!!!
Bucket name: wasabijfs
Bucket location: ap-northeast-1
******** Calculated based on Date: Friday, April 05, 2024 11:56 PM
******** Delete Retention Total Size: 11.1401 MB
******** Delete Retention Total Size: 11681253 bytes
Delete Retention check completed.
```

