# Linux Disk Management & Logical Volume Management (LVM)

A practical Linux System Administration project demonstrating
disk management, partitioning, Logical Volume Management,
filesystem configuration and storage expansion using
Red Hat Enterprise Linux.

## Project Overview

This project simulates a real-world Linux server storage
administration scenario using Oracle VirtualBox.

Two additional virtual disks were introduced to configure
LVM storage, create filesystems, establish persistent
mount points and demonstrate dynamic storage expansion.

## Environment

| Component | Configuration |
|---|---|
| Operating System | Red Hat Enterprise Linux 10.2 |
| Virtualization | Oracle VirtualBox |
| Virtual Disks | 2 x 10 GB |
| Partition Table | GPT |
| Volume Manager | LVM2 |
| Filesystem | XFS |
| Administration | Linux CLI |

## Storage Architecture

The project implements the following storage architecture:

    Disk 1 (/dev/sdb)
        |
        └── Partition (/dev/sdb1)
                  |
                  └── Physical Volume (PV)
                            |
                            ┐
                            |
                       Volume Group
                         (vg_data)
                            |
                            ┘
                  |
                  ├── Logical Volume (lv_data)
                  |       └── XFS
                  |            └── /data
                  |
                  └── Logical Volume (lv_backup)
                          └── XFS
                               └── /backup

    Disk 2 (/dev/sdc)
        |
        └── Partition (/dev/sdc1)
                  |
                  └── Physical Volume (PV)
                            |
                            └── Added to vg_data

The existing lv_data Logical Volume was extended
using the additional storage capacity.

## Project Tasks

### 01. Disk Management

- Identified available block devices.
- Inspected disk and partition information.
- Created GPT disk partitions.
- Used fdisk for disk partition management.

### 02. LVM Configuration

- Created Physical Volumes.
- Created a Volume Group.
- Created multiple Logical Volumes.
- Inspected LVM storage allocation.

### 03. Filesystem Management

- Created XFS filesystems.
- Created filesystem mount points.
- Mounted Logical Volumes.
- Configured persistent mounting using /etc/fstab.
- Tested filesystem accessibility.

### 04. Storage Expansion

- Added a second virtual disk.
- Created another Physical Volume.
- Extended the existing Volume Group.
- Extended an existing Logical Volume.
- Expanded the XFS filesystem using xfs_growfs.

## Technologies and Commands

| Area | Commands |
|---|---|
| Disk inspection | lsblk, fdisk, blkid |
| Partitioning | fdisk |
| Physical Volumes | pvcreate, pvs, pvdisplay |
| Volume Groups | vgcreate, vgextend, vgs, vgdisplay |
| Logical Volumes | lvcreate, lvextend, lvs, lvdisplay |
| Filesystems | mkfs.xfs, xfs_info, xfs_growfs |
| Mount management | mount, umount, findmnt |
| Storage verification | df, du |
| Configuration | /etc/fstab |

## Repository Structure

    linux-disk-management-and-lvm/
    |
    ├── README.md
    |
    ├── disk-management/
    │   ├── disk-management.md
    │   └── screenshots/
    |
    ├── lvm-configuration/
    │   ├── lvm-configuration.md
    │   └── screenshots/
    |
    ├── filesystem-management/
    │   ├── filesystem-management.md
    │   └── screenshots/
    |
    └── storage-extension/
        ├── storage-extension.md
        └── screenshots/

## Learning Outcomes

Through this project, I gained practical experience in:

- Linux block device management.
- Disk partitioning using GPT and fdisk.
- LVM Physical Volume, Volume Group and Logical
  Volume administration.
- XFS filesystem creation and management.
- Linux filesystem mounting and persistent configuration.
- LVM storage expansion.
- Growing XFS filesystems without recreating them.
- Linux storage inspection and troubleshooting.

## Project Environment

This project was implemented in a local Red Hat
Enterprise Linux virtual machine using Oracle VirtualBox.

## Author

Sahan Dinusha

GitHub: https://github.com/YOUR_GITHUB_USERNAME

---

This project was developed for practical learning
and professional portfolio development in Linux
System Administration and Cloud/DevOps.
