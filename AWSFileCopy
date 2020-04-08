import csv
import boto3
from botocore.exceptions import NoCredentialsError

ACCESS_KEY = [Enter Access Key Here]
SECRET_KEY = [Enter Secret Key Here]
#MOUNT_PREFIX = '/Volumes/home'
#AWS_PREFIX = 'originals'
#BUCKET_NAME = 'yale-image-samples'

def upload_to_aws(file_path_name):
    s3 = boto3.client('s3', aws_access_key_id=ACCESS_KEY,
                      aws_secret_access_key=SECRET_KEY)
    bucket = 'yale-image-samples'
#    local_file = '/Volumes/home'+file_path_name
#    s3_file = 'originals'+file_path_name
    local_file = '/Volumes/home' + file_path_name
    s3_file = 'originals/'+oid_number+file_extension

    try:
        s3.upload_file(local_file, bucket, s3_file)
        print("Upload Successful")
        return True
    except FileNotFoundError:
        print("The file was not found")
        return False
    except NoCredentialsError:
        print("Credentials not available")
        return False

with open('/Users/fcrodriguez/PycharmProjects/File_Copy/oidpath32320_2Test.csv', newline='') as csv_file:
    file_extension = '.tif'
    csv_reader = csv.reader(csv_file)
    for csv_row in csv_reader:
        oid_number = csv_row[0]
        file_path_name = csv_row[1]
        uploaded = upload_to_aws(file_path_name.lstrip())
