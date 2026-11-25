# Lab 09 – LVM Storage Expansion

## 1. Objective

Demonstrate how to expand an existing LVM storage
pool and increase Logical Volume capacity by adding
an additional virtual disk.

## 2. Additional Disk Preparation

Identified the second 10 GB virtual disk (/dev/sdc).

Created a GPT partition using fdisk.

Partition:

    /dev/sdc1

Configured the partition type as Linux LVM.

## 3. Physical Volume Creation

Initialized the new partition as an LVM Physical Volume.

    sudo pvcreate /dev/sdc1

Verified:

    sudo pvs

## 4. Volume Group Extension

Added the new Physical Volume to the existing
Volume Group vg_data.

    sudo vgextend vg_data /dev/sdc1

Verified:

    sudo vgs

## 5. Logical Volume Extension

Extended the existing lv_data Logical Volume
by an additional 5 GB.

    sudo lvextend -L +5G /dev/vg_data/lv_data

Verified:

    sudo lvs

## 6. XFS Filesystem Expansion

Expanded the existing XFS filesystem mounted
at /data to utilize the additional Logical
Volume capacity.

    sudo xfs_growfs /data

Verified:

    df -hT /data

## 7. Final Verification

Verified the updated storage configuration using:

- lsblk
- pvs
- vgs
- lvs
- df -hT

## 8. Result

Successfully added a second Physical Volume to
the existing Volume Group and extended the
lv_data Logical Volume.

The XFS filesystem was expanded without
recreating the filesystem.
