# AWS S3 Sync

AWS S3 sync will have a capability of resume upload and download.

To upload Local to S3:

```bash
nohup aws s3 sync  /opt/thirumal/ s3://thirumal-bucket/ > /home/ubuntu/thirumal.log 2>&1 &
```

with sudo,

Export credentials

```bash
export AWS_ACCESS_KEY_ID=XXXXXXX
export AWS_SECRET_ACCESS_KEY=XXXX
```
Run command with sudo

```bash
nohup sudo  -E aws s3 sync  /opt/thirumal/ s3://thirumal-bucket/ > /home/ubuntu/thirumal.log 2>&1 &
```

To Download S3 to Local:

```bash
nohup aws s3 sync s3://full-backup/ /opt/thirumal/ > /home/ubuntu/thirumal.log 2>&1 &
```

## Monitor

Check the running jobs by typing 

```bash
jobs
```