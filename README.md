# Flash Image

Get your image file.
I am personnaly using raspbian (freshly renamed **raspios**), so all the projet is based on it.
You can download it [there](https://downloads.raspberrypi.org/raspios_lite_armhf/images/): 

Get your SD card entrypoint 

```bash 
$ lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0  91,5G  0 disk
├─sda1   8:1    0   512M  0 part /boot
├─sda2   8:2    0     8G  0 part [SWAP]
├─sda3   8:3    0   9,5G  0 part /
├─sda4   8:4    0     5G  0 part /var
└─sda5   8:5    0  81,5G  0 part /home
sdb      8:16   1   9,7G  0 disk
├─sdb1   8:17   1   256M  0 part /run/media/boot
└─sdb2   8:18   1  29,5G  0 part /run/media/rootfs
```
In this example **/dev/sdb**

The script flashsdcard can download wanted target image.
You can set this image in .env file
Default one is `raspios_lite_armhf-2021-03-25/2021-03-04-raspios-buster-armhf-lite.zip`

When you have set wanted image and you know your SDCard entrypoint, you can run the script as sudo.
`sudo` is needed to write to external device to `mount` and `umount`.

```bash 
./flashsdcard /dev/sdb
``` 

## Wifi

If you want to enable wifi and BTW not too worry about security concern (wifi password is in clear text), you can use template file at `boot` directory. Renamed if to `wpa_supplicant.conf` and set your ssid and password.
