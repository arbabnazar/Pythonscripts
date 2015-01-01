
This Python script takes the mysql db backup and then upload it to AMAZON S3 Bucket using boto module. The script will also automatically delete the backup that are older than the days (mentioned in the script).

In order to use this script, we must have the boto moudle installed on the host, where we need to upload the backup to S3. Install the boto using pip:

sudo pip install boto

### Mentioned your AWS Credentials here ###

AWS_ACCESS_KEY_ID = 'You-AWS-ACCESS-KEY-ID'
AWS_SECRET_ACCESS_KEY = 'You-AWS-SECRET-ACCESS-KEY'
S3_BUCKET = 'Your-S3-Bucket'


### Mentioned the MySQL database details to which backup to be done.

DB_HOST = 'DB-HOST-ADDRESS' # Can be RDS/localhost
DB_USER = 'USERNAME'
DB_USER_PASSWD = 'PASSWORD'
BACKUP_PATH = '/tmp/dbbackup' # location on local host to save dump before uploading to S3 
DeleteOlderThan = 10 # Delete the dumps older then mentioned days

### How to use this script

You can use it manually or using as cronjob.

python completedbtos3.py

or

Make it executable first:

chmod +x completedbtos3.py 

and then run it:

./completedbtos3.py

Or add this line to run the script at midnight every day: 

0 0 * * * /usr/bin/python /path/to/script/completedbtos3.py
