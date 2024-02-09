# Note for daily use of ubuntu
Record all the important things when using ubuntu22.04. 
I should take a look to all the `man` page of all the commands I used to know what I'm doing.

## Install the ubuntu

Install ubuntu with whatever medium. Make a partition for `/home`, `/` and `/mnt/timeshift`
which should not be used by ubuntu and is aiming to backing up the system with `timeshift`. Choose the whatever filesystem you
like such as `ext4`.

## Basic set up

### Back up with `timeshift`

The most important thing is the backup of the system. Install `timeshift` with `apt`.
Then I need to mount that unused partition to `mnt/timeshft`.

First, make a directory by `sudo mkdir /mnt/timeshift`. Then check the UUID of that unused
partition by `sudo blkid`. The output should be
```
...
/dev/<partition_name> PARTUUID=<PARTUUID> ...
...
```
Set the filesystem of that partition with
```
sudo mkfs -t ext4 /dev/<partition_name>
```
Modity the `/etc/fstab` to let the system mount that partition by adding
```
PARTUUID=<PARTUUID> /mnt/timeshift ext4 defaults 0 0
```
To test without rebooting, run `sudo mount -a`, otherwise you will need to enter the recovery mode if there's problem 
when checking all your filesystems.
