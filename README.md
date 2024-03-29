# Note for daily use of Ubuntu
Record all the important things when using ubuntu22.04. 
I should take a look at all the `man` pages of all the commands I used to know what I'm doing.

## Install the Ubuntu

Install Ubuntu with whatever medium. Make a partition for `/home`, `/` and `/mnt/timeshift`
which should not be used by Ubuntu and is aiming to back up the system with `timeshift`. Choose whatever filesystem you
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
Modify the `/etc/fstab` to let the system mount that partition by adding
```
PARTUUID=<PARTUUID> /mnt/timeshift ext4 defaults 0 0
```
To test without rebooting, run `sudo mount -a`, otherwise, you will need to enter the recovery mode if there's a problem 
when checking all your filesystems. Take a snapshot often.

### Chinese input

In `Settings`, make sure that there is `汉语` in the language. You don't need to set it as the language
for your system. In the `keyboard`, choose `Chinese(Intelligent Pinyin)` as your input source.
You can modify some configurations in the preference such as `Cloud Input` and `Fuzzy syllable`.
啊！中文！

### Proxy server core

`v2raya` with `snap`. Very important but quite simple. 

### Vim

First, install `vim` with `apt`. Then get `vim-plug`. And get my [configuration for vim](https://github.com/kalium222/vim-config).

Then I swapped `capslock` and `esc` under `xorg` and `wayland` by modifying the entries for `esc` and `Capslock` in `/usr/share/X11/xkb/keycodes/evdev`.

### Tmux

Get `tmux` by package manager. Then get [configurations](https://github.com/kalium222/tmux-config).
Don't forget to get `fonts-powerline` by the package manager if you want some arrow effects. This is the same for `vim` and `bash`.

## Nvidia driver

My graphics is 4070s. Good luck.

FUCK YOU, NVIDIA!
