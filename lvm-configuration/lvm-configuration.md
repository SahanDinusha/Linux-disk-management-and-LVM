# Lab 03, 04 & 05 – LVM Configuration

## 1. Objective

Configure Linux Logical Volume Management by creating
Physical Volumes, a Volume Group and Logical Volumes.

## 2. Physical Volume Creation

Initialized the first disk partition as an LVM Physical Volume.

Device: /dev/sdb1

Command:

    sudo pvcreate /dev/sdb1

Verification:

    sudo pvs
    sudo pvdisplay

## 3. Volume Group Creation

Created a Volume Group named vg_data using the
Physical Volume /dev/sdb1.

Command:

    sudo vgcreate vg_data /dev/sdb1

Verification:

    sudo vgs
    sudo vgdisplay vg_data

## 4. Logical Volume Creation

Created two Logical Volumes inside vg_data.

| Logical Volume | Allocated Size | Purpose |
|---|---:|---|
| lv_data | 4 GB | Application data |
| lv_backup | 3 GB | Backup storage |

Commands:

    sudo lvcreate -L 4G -n lv_data vg_data
    sudo lvcreate -L 3G -n lv_backup vg_data

Verification:

    sudo lvs
    sudo lvdisplay
    lsblk

## 5. Result

Successfully configured LVM storage with one
Volume Group and two Logical Volumes.

The remaining unallocated capacity was retained
for future storage expansion.
