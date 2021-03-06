
This Python script simply takes the compressed MySQL dumps and then upload it to AMAZON S3 Bucket using boto module. The script will also automatically delete the backup that are older than the days (mentioned in the script).

Requirements
------------

This script requires boto. Install boto using pip:

```
sudo pip install boto
```
Configuration
-------------

The script requires the following configuration parameters

###### AWS Details
```
AWS_ACCESS_KEY_ID = 'You-AWS-ACCESS-KEY-ID'

AWS_SECRET_ACCESS_KEY = 'You-AWS-SECRET-ACCESS-KEY'

S3_BUCKET = 'Your-S3-Bucket'
```

###### MySQL Details 
```
DB_HOST = 'DB-HOST-ADDRESS' # Can be RDS/localhost

DB_USER = 'USERNAME'

DB_USER_PASSWD = 'PASSWORD'

BACKUP_PATH = '/tmp/dbbackup' # location on local host to save dump before upload it to S3

DeleteOlderThan = 10 # Delete the dumps older then mentioned days
```

######  To use this script

You can use it manually or using as cronjob.
```
python mysqldumptos3.py
```
or

Make it executable first:
```
chmod +x mysqldumptos3.py 
```
and then run it:
```
./mysqldumptos3.py
```
Or add this line to run the script at midnight every day: 
```
0 0 * * * /usr/bin/python /path/to/script/mysqldumptos3.py
```
