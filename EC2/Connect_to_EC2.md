## Connect to EC2 Instance

### Prerequisite

* Download `.pem` file

### Login

* Give permission for `.pem` file

```bash
chmod 600
```

* `Login` to `EC2`

```bash
ssh -i {.pem} ubuntu@{ip-dns}
```

### Switch to root without password

```bash
sudo su -
```

* Copy files from local system to `ec2`

```bash
scp -i {.pem} /user/thirumal/file_to_copy.pdf ubuntu@{ip}:/home/ubuntu
```
