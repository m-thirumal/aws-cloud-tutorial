## Step 1. Set up your default identity

1. Open Terminal (Ctrl + Alt + T) and enter the following command to set up your default identity

```
ssh-keygen
```
 
Eg:

```
thirumal@thirumal:~/git$ ssh-keygen
Generating public/private rsa key pair.
Enter file in which to save the key (/home/thirumal/.ssh/id_rsa): 
Press enter to accept the default key and path, `/c/Users/<username>/.ssh/id_rsa`.
 Enter and re-enter a passphrase when prompted.The command creates your default identity with its public and private keys. The whole interaction looks similar to this:

Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
Your identification has been saved in /home/thirumal/.ssh/id_rsa
Your public key has been saved in /home/thirumal/.ssh/id_rsa.pub
The key fingerprint is:
SHA256:h4xKiyvxzOWkeXcwxmkAYSZ9AsDOikB14+vgzpTnjPs thirumal@thirumal
The keys randomart image is:
+---[RSA 3072]----+
|*o=o o           |
| *+ + .          |
|+  + .           |
|.o  . .o .       |
|+  ..+..S .      |
|+ .o*oB  .       |
| =.Xo= o         |
|. X.B . .        |
| ..*oE .         |
+----[SHA256]-----+
```

## Step 2 Add the public key to your Account settings

* Copy your public key using the following command 

```
cat ~/.ssh/id_rsa.pub
```

* Add/Upload it to your `IAM` -> `security credentials`

* Add the generated AWS `SSH key ID` to `~.ssh/config`

```
  Host git-codecommit.*.amazonaws.com
    User {SSHKEYID}
    IdentityFile ~/.ssh/id_rsa
```

or 

```
  Host git-codecommit.*.amazonaws.com
    User {SSHKEYID}
    IdentityFile ~/.ssh/id_rsa
    PubkeyAcceptedAlgorithms +ssh-rsa
    HostkeyAlgorithms +ssh-rsa
```

* Return to your terminal and clone the repository using

```
git clone {SSH_URL}
```

