**S3-Objects-Rename-Utility**


A Python Script to rename objects in an AWS S3 bucket by replacing colons (:) with hyphens (-) in object keys.

**Features**
 
- Rename S3 objects by replacing : with - in their keys.
- Supports filtering objects by a prefix (folder path).
- Uses AWS profiles for authentication.
- Includes a dry-run mode to preview changes without modifying the bucket.
- Built with boto3 for AWS S3 interaction and click for the command-line interface.

## Requirements

- Python 3.6+
- [boto3](https://boto3.amazonaws.com/v1/documentation/api/latest/index.html)
- [click](https://click.palletsprojects.com/)


 


**Clone the repository:**

```bash
git clone https://github.com/yourusername/S3-Objects-Rename-Utility.git
cd S3-Objects-Rename-Utility
 ```


**Install dependencies:**

```bash
pip install boto3 click
```

Ensure your AWS credentials are configured:

Run aws configure to set up your AWS profile, or ensure ~/.aws/credentials contains the necessary credentials.

### Options

- `--bucket` (required): Name of the S3 bucket.
- `--prefix`: Prefix (folder path) in the bucket to filter objects (default: `''`).
- `--profile`: AWS CLI profile name to use (default: `'default'`).
- `--dry-run`: If set, shows what would be renamed without making changes.

### Example

Dry run (no changes, just output):
```bash
python s3_rename.py --bucket my-bucket --prefix my/folder/ --profile myprofile --dry-run
```

Perform actual renaming:
```bash
python s3_rename.py --bucket my-bucket --prefix my/folder/ --profile myprofile
```

## How it works

- The script currently copies objects to new keys but does not delete the original objects (the delete_object call is commented out). 
- Uncomment the s3.delete_object line in the script to enable deletion after copying.
- This means you'll have both the old and new versions after running the script.
- Errors during processing (e.g., permission issues) are logged to the console.

Example 1: Rename all objects in a bucket
```bash
C:\temp\ABC_LOGS\est>python s3_rename.py --bucket icm-pe-prd-us-east-1-audit --prefix redshift_audit_log/AWSLogs/123456789/redshift/us-east-1/testlogs-2025/2025/ --profile ABCPRD

Output:
Would rename: logs/2024-01-01:12:30:45.log -> logs/2024-01-01-12-30-45.log
Would rename: data/export:final.csv -> data/export-final.csv

