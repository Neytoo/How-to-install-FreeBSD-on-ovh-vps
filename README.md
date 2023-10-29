# How-to-install-FreeBSD-on-ovh

Ovh doesn't support installing **FreeBSD** on their **VPS**, and we need to do it manually.

There are all actually available versions of the **FreeBSD** system available on the official site:
https://download.freebsd.org

## Prepare VPS on panel side
To install **FreeBSD** first I propose to install the **Ubuntu** system on your **VPS**
When you already have **Ubuntu installed** we can go through the next steps.

Run **Rescue mode** on your **VPS** and when it is ready connect to the server over **KVM or SSH**.

## Choose disc where FreeBSD will be installed
When you are connected to the server we can mount the disc where FreeBSD should be installed, because you don't have that much space on your disc where the rescue system is running.
To mount disc first you need to know which to choose so use this command:
```
lsblk
```
Probably you will see one disc where there is that much space you have in your whole VPS and a second disc where is around 3GB of space,
you need to mount this bigger disc i propose doing it like this:

```
mkdir /mnt/frebsd
mount /dev/sda /mnt/freebsd
```

## Download FreeBSD
To download FreeBSD you need to use these commands:
```
cd /mnt/freebsd
wget https://download.freebsd.org/ftp/snapshots/VM-IMAGES/13.2-STABLE/amd64/Latest/FreeBSD-13.2-STABLE-amd64.raw.xz
```
> [!IMPORTANT]
> In my case this is FreeBSD-13.2 but it doesn't matter which version you choose, the only 1 important thing is to choose a raw image of the system, in my case this image is compressed to .xz

If your FreeBSD raw image is packed like there to ```.xz``` format you need to unpack it like this:
```
xz -d FreeBSD-13.2-STABLE-amd64.raw.xz
```

## Create a bootable disc from your main disc
> [!WARNING]
> In this step you will lose all data on the selected disc, make sure you want to do this.

To create bootable disc you need to use ```dd``` command:
```
dd if=FreeBSD-13.2-STABLE-amd64.raw of=/dev/sda bs=1M
```
