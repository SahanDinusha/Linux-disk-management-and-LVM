# Lab 06, 07 & 08 – Linux Filesystem Management

## 1. Objective

Create XFS filesystems on LVM Logical Volumes,
mount them to Linux directories and configure
persistent mounting using /etc/fstab.

## 2. Filesystem Creation

Created XFS filesystems on both Logical Volumes.

Commands:

    sudo mkfs.xfs /dev/vg_data/lv_data
    sudo mkfs.xfs /dev/vg_data/lv_backup

Verification:

    lsblk -f
    sudo blkid

## 3. Filesystem Mounting

Created two mount-point directories:

- /data – Application data
- /backup – Backup storage

Commands:

    sudo mkdir /data
    sudo mkdir /backup

    sudo mount /dev/vg_data/lv_data /data
    sudo mount /dev/vg_data/lv_backup /backup

Verification:

    df -hT
    findmnt /data
    findmnt /backup

Created test files to verify storage accessibility.

## 4. Persistent Mounting

Created a backup of the original fstab configuration.

    sudo cp /etc/fstab /etc/fstab.bak

Retrieved filesystem UUIDs using blkid and
added the corresponding entries to /etc/fstab.

Configured persistent mounting for:

- /data
- /backup

Unmounted both filesystems and tested the
configuration using:

    sudo umount /data
    sudo umount /backup
    sudo mount -a

Verified the mount configuration using findmnt
and df -hT.

## 5. Result

Successfully created XFS filesystems, mounted
both Logical Volumes and configured persistent
mounting through /etc/fstab.
