---
title: KVM clone existing VM with new ip and mac
date: 2022-10-27 22:48:58
tags:
---

you need a existing VM and the status of the vm should be shutdown/offline.

```
virsh list
```
####info: the output from this command may not show the VM what you want to clone

#### cloning VM with virt-clone
```
	NEWVM=new-vm-unchanged-name
    IMAGEPATH=/mnt/lvmvg01storageraid1 
  PATHTOIMAGE=$IMAGEPATH/${VMNAME}.qcow2
   VMTEMPLATE=debian10-tmpl

virt-clone --original $VMTEMPLATE --name $NEWVM --file $PATHTOIMAGE
```
##### info: with command `file` you can check the  type of the new create container file 
