# MongoDB Backup to AWS S3

This script provides an automated solution for backing up MongoDB databases and saving the backup archives to an AWS S3 bucket.

## Description

Upon executing the script:
1. A dump of the specified MongoDB database is performed.
2. The dump is archived into a tarball (`.tar.gz` format).
3. The tarball is uploaded to a specified S3 bucket.
4. Email notifications are sent upon success or failure of the dump and upload operations.

## Prerequisites

- AWS CLI configured with the necessary permissions to write to the specified S3 bucket.
- A mail system (like `sendmail` or `postfix`) configured to send emails from the server executing the script.
- MongoDB client tools (`mongodump` in particular) installed.

## Configuration

Before using the script, replace placeholder values in the following variables:

- `S3_BUCKET_NAME`: Name of your AWS S3 bucket.
- `EMAIL_RECIPIENT`: Email address where you wish to receive notifications.
- `MONGO_URI`: MongoDB connection URI. It should include the username, password, hostname, port, and database name.

## Usage

To execute the script, you can simply run:

```bash
./<script_name>.sh
```

Replace `<script_name>` with whatever you've named the script.

## Notifications

Upon successful completion of the MongoDB dump and its upload to S3, an email will be sent with the subject "MongoDB Dump Upload Success". In case of any failures, appropriate emails with subjects "MongoDB Dump Upload Failed" or "MongoDB Dump Failed" will be sent.

## Cleanup

After the script execution, any temporary files or directories created during the process will be removed.

## Author

- **Pubudu Dias** - *Initial work* - [Date: 2022/10/23]

## Note

Ensure you store sensitive information like `MONGO_URI` securely and avoid exposing them in your scripts. Consider using environment variables or secret management tools. Always be cautious when handling databases and backups, especially when automating tasks.