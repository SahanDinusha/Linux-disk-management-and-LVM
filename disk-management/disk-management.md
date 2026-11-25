# Lab 01 & 02 – Linux Disk Management and Partitioning

## 1. Objective

Identify additional storage devices in a Red Hat Enterprise Linux
environment and prepare a virtual disk partition for LVM usage.

## 2. Environment

- Operating System: Red Hat Enterprise Linux 10.2
- Virtualization: Oracle VirtualBox
- Additional Virtual Disks: 2 x 10 GB
- Partitioning Tool: fdisk
- Partition Table: GPT

## 3. Disk Identification

Inspected available block devices and existing filesystems.

Commands used:

- lsblk
- fdisk -l
- df -h
- blkid

Identified the additional virtual disks without modifying
the operating system disk.

## 4. Disk Partitioning

Selected the first additional 10 GB virtual disk (/dev/sdb).

Created a GPT partition table and allocated the available
disk space to a new partition (/dev/sdb1).

The partition was created using fdisk.

## 5. Verification

Verified the partition table and partition information using:

- lsblk
- fdisk -l /dev/sdb

## 6. Result

Successfully identified the additional virtual storage
and created a partition for LVM configuration.

The partition was successfully initialized as an LVM
Physical Volume in the subsequent LVM configuration lab.
