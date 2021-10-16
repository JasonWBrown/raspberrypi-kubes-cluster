# Create Swap space with MicroSD cards

# Helpful links
https://itectec.com/ubuntu/ubuntu-how-to-make-a-usb-stick-swap-disk/

# Delete everything on the MicroSD card

1. sudo dd if=/dev/zero of=/dev/mmcblk0 bs=4096 status=progress

#  Make the SD card swap  

1. sudo mkswap /dev/mmcblk0

# Edit fstab to set up swap 

1. sudo blkid
1. Get UUID of sd card
1. sudo nano /etc/fstab
1. use UUID of sd card to create this line in fstab `UUID=1f06e362-989a-4045-9ddb-a4657104e4e4 none swap sw,pri=5 0 0`

# Turn swap on

1. sudo swapon -a

# TBD 
Change swapiness?
Change caching?

```
  111  cat /proc/sys/vm/swappiness
  112  sudo sysctl vm.swappiness=90
  610  cat /proc/sys/vm/swappiness
  615  sudo sysctl vm.vfs_cache_pressure=50
```