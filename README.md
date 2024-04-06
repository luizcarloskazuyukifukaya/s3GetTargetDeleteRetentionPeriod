# s3GetTargetDeleteRetentionPeriod
Identify and calculate the amount volume of the objects violating the Wasabi Delete Retention period.

## Execute
You need to install python environment, so please refer to the following repository for details on how to setup.
[How to setup your environment](https://github.com/luizcarloskazuyukifukaya/s3pythonsamples/blob/main/README.md)

Once the environment setup is completed, you can execute the Python code like the following:

```
python3 ./s3GetTargetDeleteRetentionPeriod.py
```

## Output sample
The output will show the information about the bucket names, regions and objects details before the total amount of data violating the delete retention policy based on the current date and time.

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

## Customization Tips
### Define the date point
You can modify the Python code so the delete retention violation is analyzed based on a specific date and time.
For instance, the current code takes the current time to be the date point to analyze the objects that are subject to the delete retention period. The objects will be picked by comparing the object's Last Modified Date and Time against the current date and time.

Please modify the python code following the example bellow:
```
    # Define Date Point for the detection of objects violating the delete retention policy
    # Date point: April 30th, 2024 at 9:30 AM
    from zoneinfo import ZoneInfo
    tzinfo=ZoneInfo('Asia/Tokyo')
    current_time = datetime.datetime(year=2024, month=4, day=30, hour=9, minute=30, second=0, tzinfo=tzinfo)
    # Get the current time
    # Against this time the delta time will be calculated to determine the delete retention violation
    # current_time = datetime.datetime.now(JST)
    current_time_str = current_time.strftime('%A, %B %d, %Y %I:%M %p')
    print(f"[Current date and time] : {current_time_str}")
```
(Note) For the above case, the date point is April 30th, 2024 at 9:30.00 AM.

### Define the delete retention period
You can modify the Python code so the delete retention period is defined as 90 days instead of 30 days, which is the current value.
If you want to change the delete retention period to 90 days, modify the Python code like the following example:
```
        # Delete retention: 30 days (RCS, used this time)
        # Delete retention: 90 days (PayGO)
        # retention_days = 30
        retention_days = 90
```
(Note) Change comment "retention_days = 90" from "retention = 30". 