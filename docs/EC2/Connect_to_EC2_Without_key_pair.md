## Connect to EC2 Instance without key pair

### Prerequisite

* root login (OR) sudo login
 
### Login

Login using `key pair`, then follow the below steps


#### Create new login user [Optional]

```bash
# Add user with home directory & bash shell
sudo useradd -s /bin/bash -d /home/{home directory} -m {user name}
# Add bash shell
sudo chsh -s /bin/bash {userName}
# Make sudo user
sudo usermod -aG sudo {username}
# Change pass
sudo passwd {userName}
```

#### Enable password & SSH authentication

* Open `sudo vi /etc/ssh/sshd_config` and modify the following

** To enable password authentication, uncomment

```bash
#PasswordAuthentication yes
```

** To enable root login, uncomment

```bash
#PermitRootLogin yes
```

** To enable ssh key login, uncomment

```bash
#PubkeyAuthentication yes
#AuthorizedKeysFile .ssh/authorized_keys
```

** Add user name in

```bash
AllowUsers thirumal ubuntu
```

** After modification, restart ssh:

```bash
sudo service ssh restart
```