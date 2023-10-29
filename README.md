# How-to-install-FreeBSD-on-ovh

Ovh doesn't support installing FreeBSD on their VPS, and we need to do it manually.

There are all actual available versions of the FreeBSD system available on the official site:
https://download.freebsd.org

To install FreeBSD first I propose to install the Ubuntu system on your VPS
When you already have Ubuntu installed we can go through the next steps.

Run Rescue mode on your VPS and when it is ready connect to the server over KVM or SSH.

When you are connected to the server we can go with downloading FreeBSD and for this, you need to use this command:
```
wget https://download.freebsd.org/ftp/snapshots/VM-IMAGES/13.2-STABLE/amd64/Latest/FreeBSD-13.2-STABLE-amd64.raw.xz
```
> [!IMPORTANT]
> In my case this is FreeBSD-13.2 but it doesn't matter which version you choose, the only 1 important thing is to choose a raw image of the system, in my case this image is compressed to .xz

