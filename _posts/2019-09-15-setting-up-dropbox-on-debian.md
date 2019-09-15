---
layout: post
title: Setting up Dropbox on Debian
---

Setting up Dropbox on Debian from the offical Dropbox repository saves you from downloading dropbox binary everytime, and easies the management of the package.

Until recently Dropbox offical repository for debian only had jessie, which had now changed.

I will try to give you a guide to setting it up, and cover some problems I have faced in the past

## Intro

If you don't have Dropbox yet now is a good time to [Signup for a free account](https://db.tt/Fx5tGN3Cqr).

### Create file
Create a file in the sources directory for Dropbox 

```bash
sudo nano /etc/apt/sources.list.d/dropbox.list
```

You can choose what every file name you want.

Add the url to the offical Dropbox repository with the version as follows

```bash
#Dropbox Offical Repo
deb [arch=i386,amd64] http://linux.dropbox.com/debian buster main
```

As for the date of writing this the offical repository supported 
- Buster
- Stretch
- Jessie
- Sid

choose the version you are using.

### Add the PGP key

Dropbox offical key is at pgp.mit.edu, but occasionally it might fail to response, you can use pool.sks-keyservers.net instead.

```bash
sudo apt install dirmngr

apt-key adv --keyserver pool.sks-keyservers.net --recv-keys 1C61A2656FB57B7E4DE0F4C1FC918B335044912E
```

### Install Dropbox

Now update the package manager, and install python3-gpg if you want the signture of the binaries to be verified.

```bash
sudo apt update
sudo apt install python3-gpg dropbox
```

Now start Dropbox from programs menu or use the command

```bash
dropbox start -i
```

After download and installation, You will be asked to login to your Dropbox account and allow linking this installation to your account.

Happy dropping.
