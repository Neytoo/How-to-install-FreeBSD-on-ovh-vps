# How to install FreeBSD on OVH VPS

OVH does not natively support the installation of **FreeBSD** on their **VPS**. As such, a manual approach is necessary.

You can find all currently available versions of **FreeBSD** on the official site:
https://download.freebsd.org

## Prepare VPS on panel side
To begin the **FreeBSD** installation, first install **Ubuntu** on your **VPS**.
Once **Ubuntu** is installed, activate the **Rescue mode** for your **VPS**.
After the **Rescue mode** is active, connect to the server via **KVM** or **SSH**.

## Identifying the Target Disk for FreeBSD Installation
Once connected, identify the disk where **FreeBSD** will be installed. Note that the rescue system's disk has limited space.
To identify the correct disk, use the following command:
```
lsblk
```
Generally, you'll identify two disks: one corresponding to the entirety of your VPS's space and a smaller one (~3GB). Select the larger disk.
Mount the chosen disk using:

```
mkdir /mnt/frebsd
mount /dev/sda /mnt/freebsd
```

## Download FreeBSD
Navigate to the mounted directory and download **FreeBSD**:
```
cd /mnt/freebsd
wget https://download.freebsd.org/ftp/snapshots/VM-IMAGES/13.2-STABLE/amd64/Latest/FreeBSD-13.2-STABLE-amd64.raw.xz
```
> [!IMPORTANT]
> This guide uses version FreeBSD-13.2. Regardless of the version you opt for, ensure that you download the raw image of the system. Note that in this example, the image is compressed with .xz.

If the **FreeBSD** raw image is compressed as ```.xz```, decompress it:
```
xz -d FreeBSD-13.2-STABLE-amd64.raw.xz
```

## Creating a Bootable Disk
> [!WARNING]
> This step will erase all data on the selected disk. Ensure you've backed up any critical data before proceeding.

To create bootable disk you need to use ```dd``` command:
```
dd if=FreeBSD-13.2-STABLE-amd64.raw of=/dev/sda bs=1M
```

# Booting FreeBSD
Congratulations! You can now restart your VPS into its default mode and begin using **FreeBSD**. If the system does not automatically boot into **FreeBSD**, revisit the steps to ensure all procedures were followed correctly.
