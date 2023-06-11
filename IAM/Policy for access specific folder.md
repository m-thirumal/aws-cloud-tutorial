`IAM policy` to access(Read/Write) specific folder in `S3`

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "AllowStatement1",
            "Action": [
                "s3:ListAllMyBuckets",
                "s3:GetBucketLocation"
            ],
            "Effect": "Allow",
            "Resource": [
                "arn:aws:s3:::*"
            ]
        },
        {
            "Sid": "AllowStatement2B",
            "Action": [
                "s3:ListBucket"
            ],
            "Effect": "Allow",
            "Resource": [
                "arn:aws:s3:::BUCKET-NAME"
            ],
            "Condition": {
                "StringEquals": {
                    "s3:prefix": [
                        "",
                        "sub-1"
                    ],
                    "s3:delimiter": [
                        "/"
                    ]
                }
            }
        },
        {
            "Sid": "AllowStatement3",
            "Action": [
                "s3:ListBucket"
            ],
            "Effect": "Allow",
            "Resource": [
                "arn:aws:s3:::BUCKET-NAME"
            ],
            "Condition": {
                "StringLike": {
                    "s3:prefix": [
                        "FOLDER-NAME/*"
                    ]
                }
            }
        },
        {
            "Sid": "AllowStatement4B",
            "Effect": "Allow",
            "Action": [
                "s3:GetObject",
                "s3:PutObject"
            ],
            "Resource": [
                "arn:aws:s3:::BUCKET-NAME/FOLDER-NAME/*"
            ]
        }
    ]
}
```
