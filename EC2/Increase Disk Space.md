
### Increase Volume/Disk space (EBS)

* Select the `Instance`, you want to modify, and select `volume` under `storage`.
* In the volume page select, select the volume and click on `Action` -> `Modify Volume` -> `Enter the volume size`

* Connect to the EC2/Cloud 9 Instance
* To verify the file system for each volume, use the `df -hT` command. 

```bash
thirumal:~/environment $ df -hT
Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  476M     0  476M   0% /dev
tmpfs          tmpfs      98M  724K   98M   1% /run
/dev/xvda1     ext4       9.7G  9.5G 128M  99% /
tmpfs          tmpfs     490M     0  490M   0% /dev/shm
tmpfs          tmpfs     5.0M     0  5.0M   0% /run/lock
tmpfs          tmpfs     490M     0  490M   0% /sys/fs/cgroup
/dev/loop0     squashfs   56M   56M     0 100% /snap/core18/1997
/dev/loop2     squashfs   13M   13M     0 100% /snap/amazon-ssm-agent/495
/dev/loop1     squashfs   34M   34M     0 100% /snap/amazon-ssm-agent/3552
/dev/loop3     squashfs   88M   88M     0 100% /snap/core/5328
/dev/loop4     squashfs  100M  100M     0 100% /snap/core/10958
tmpfs          tmpfs      98M     0   98M   0% /run/user/1000
```

* To check whether the volume has a partition that must be extended, use the lsblk command to display information 


```bash
thirumal:~/environment $ lsblk
NAME    MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
loop0     7:0    0 55.5M  1 loop /snap/core18/1997
loop1     7:1    0 33.3M  1 loop /snap/amazon-ssm-agent/3552
loop2     7:2    0 12.7M  1 loop /snap/amazon-ssm-agent/495
loop3     7:3    0 87.9M  1 loop /snap/core/5328
loop4     7:4    0 99.2M  1 loop /snap/core/10958
xvda    202:0    0   10G  0 disk 
└─xvda1 202:1    0   10G  0 part /
```
* The above output shows, `xvda` has one partition
* Extend/Grow the partition

```bash
sudo growpart /dev/xvda 1

(OR)
sudo growpart /dev/nvme0n1 1


```

or 

```bash
# resize filesystem
thirumal.mari:~/environment $ sudo resize2fs /dev/xvda1
```

* Check after resizing

```bash
thirumal.mari:~/environment $ df -hT
Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  476M     0  476M   0% /dev
tmpfs          tmpfs      98M  724K   98M   1% /run
/dev/xvda1     ext4       49G  9.5G   39G  20% /
tmpfs          tmpfs     490M     0  490M   0% /dev/shm
tmpfs          tmpfs     5.0M     0  5.0M   0% /run/lock
tmpfs          tmpfs     490M     0  490M   0% /sys/fs/cgroup
/dev/loop0     squashfs   56M   56M     0 100% /snap/core18/1997
/dev/loop2     squashfs   13M   13M     0 100% /snap/amazon-ssm-agent/495
/dev/loop1     squashfs   34M   34M     0 100% /snap/amazon-ssm-agent/3552
/dev/loop3     squashfs   88M   88M     0 100% /snap/core/5328
/dev/loop4     squashfs  100M  100M     0 100% /snap/core/10958
tmpfs          tmpfs      98M     0   98M   0% /run/user/1000
```

* Extend the file system.

```bash
df -hT

sudo xfs_growfs -d /

sudo resize2fs /dev/nvme0n1p1
```


