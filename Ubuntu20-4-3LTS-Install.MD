# Install Ubuntu 20.04 LTS

## Step 0 update boot order I don't think this is even necessary. 

1. sudo EDITOR=vi rpi-eeprom-config -e
1. Change boot order to BOOT_ORDER=0xf14
1. https://www.raspberrypi.org/documentation/computers/raspberry-pi.html#boot_order-examples
1. turn off the pi

## Step 1 Install OS

1. Open Raspberry PI Imager
1. Choose SSD Drive
1. Connect PI and SSD 
1. Boot.  Let Boot complete then power down PI.  Roughly 5 minute process

## Step 2. Add SSH
1. Remove SSD and hook up to Computer used to install OS.
1. Add the and empty ssh file to the boot volume of the ssd drive. 
1. `touch /boot/firmware/ssh`

## Step 2a  If ssh fails for any reason Hook to Monitor and Keyboard

1. Login 
1. Change password
1. Check ssh status `service ssh status`
1. Add an empty ssh file in the boot folder
1. `touch /boot/firmware ssh`

## Step 3 update the OS
1. `sudo apt update`
1. `sudo apt -y upgrade && sudo systemctl reboot`

## Step 3.  Set up .ssh public key to login without keys | set up ssh/config to login quickly.

1.  Add SSH public key to servers ` ssh-copy-id -i ~/.ssh/id_rsa.pub ubuntu@ip.0.0.0`
1.  Set up ~/.ssh/config

## Step 4.  Set a static IP

1. sudo apt-get install network-manager
1. create /etc/netplan/00-installer-config.yaml
```
network:
  version: 2
  ethernets:
    eth0:
      dhcp4: false
      addresses: [change this static ip/24]
      gateway4: change this to ip of your gateway
      nameservers:
        addresses: [8.8.8.8,8.8.4.4]
```
1. Comment out or remove all other files in that directory /etc/netplan
1. create file  /etc/cloud/cloud.cfg.d/99-disable-network-config.cfg with the following:
```
network: {config: disabled}
```

1. in the /etc/netplan dir run the command `sudo netplan try`  this will verify that plan is correct
1. after no errors run `sudo netplan apply`

