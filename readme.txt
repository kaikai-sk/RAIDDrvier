Copyright Adaptec Inc. 2005.  All rights reserved.

Contents:
1. Criticality
2. Title / Description
3. Compatibility / Minimum Requirements
4. Release Highlights - Fixes
5. Installation
6. Known Limitations
7. History

Criticality:
Recommended. Adaptec recommends applying this update during your
next scheduled update cycle. The update contains feature enhancements or
changes that will help keep your system software current and compatible with
other system modules (firmware and software).

Title / Description:
Adaptec AAC RAID controller device driver. Supports the following cards:
	Adaptec	2120S		Adaptec	2200S		ICP	5045BL
	Adaptec	3230S		Adaptec	3240S		ICP	5085BL
	Adaptec	2020ZCR		Adaptec	2025ZCR		ICP	5085BR
	Adaptec	2020SA		Adaptec	2025SA		ICP	5085SL
	Adaptec	2130S		Adaptec	2230S		ICP	5805BL
	Adaptec	2240S		Adaptec	2820SA		ICP	5805SL
	Adaptec	2620SA		Adaptec	2420SA		ICP	5445SL
	Adaptec	2810SA		Adaptec	2410SA		ICP	5125BR
	Adaptec	21610SA		Adaptec	2610SA		ICP	5125SL
	Adaptec	4000		Adaptec	4005		ICP	5165BR
	Adaptec	4800SAS		Adaptec	4805SAS		ICP	5165SL
	Adaptec	1800		Adaptec	5445		ICP	9014RO
	Adaptec	5085		Adaptec	3405		ICP	9024RO
	Adaptec	31205		Adaptec	31605		ICP	9047MA
	Adaptec	51205		Adaptec	51605		ICP	9087MA
	Adaptec	51245		Adaptec	51645		ICP	9085LI
	Adaptec	52445		Adaptec	5805		ICP	9067MA
	Adaptec	5400S		Adaptec	5405		Adaptec	ASR-2405
	Adaptec	3805		Adaptec	3085		Adaptec	ASR-2045
	Adaptec	ASR-2805	Adaptec	ASR-2445	Adaptec ASR-2405G
	Adaptec	ASR-2045G	Adaptec	ASR-2445G	Adaptec	ASR-2805G
	Adaptec	5405G		Adaptec	5445G		Adaptec	5805G
	Adaptec	5085G		Adaptec	51245G		Adaptec	51645G
	Adaptec	52445G		Adaptec	61205		Adaptec	61605
	Adaptec	62405		Adaptec	6405		Adaptec	6405E
	Adaptec	6445		Adaptec	6805		Adaptec	6805E
	Huawei80T HUA-6805T	Adaptec	FVB-7995	Adaptec	ASR-7805
	Adaptec	ASR-71605	Adaptec	ASR-71685	Adaptec	ASR-72405
	Adaptec	ASR-7885	Adaptec	ASR-71605E	Adaptec	ASR-72405E	
	Adaptec ASR-78165	Adaptec ASR-82405	Adaptec ASR-81605
	Adaptec ASR-8805	Adaptec ASR-8085	Adaptec ASR-8885
	Adaptec FVB-8805	Adaptec FVB-81605	Adaptec	ASR-8405
	Adaptec ASR-8885E
	IBM	ServeRAID 7t	DELL	PERC 320/DC	Legend	S220
	IBM	ServeRAID 8i 	DELL	PERC 3/DiV	Legend	S230
	IBM	ServeRAID 7t	DELL	PERC 3/DiL	DELL	CERC 2
	IBM	ServeRAID 8k-l4	DELL	PERC 3/DiF	DELL	PERC 3/Si
	IBM	ServeRAID 8k-l8	DELL	PERC 3/DiJ	DELL	PERC 2/QC
	IBM	ServeRAID 8s	DELL	PERC 3/DiD	DELL	PERC 2/Si
	HP	NetRAID-4M	DELL	PERC 3/DiB	DELL	PERC 3/Di
	SMC	AOC-USAS-S4i	SMC	AOC-USAS-S4iR	SMC	AOC-USAS-S8i
	SMC	AOC-USAS-S8iR	SMC	AOC-USAS-S8i-LP	SMC	AOC-USAS-S8iR-LP
	SUN	STK RAID REM	SUN	STK RAID INT	SUN	STK RAID EXT
	SUN	STK RAID EM

Compatibility / Minimum Requirements:
Linux Development Build Environment

Release Highlights - Features:
Initial Release

Release Highlights - Fixes:
Initial Release

Installation:
-----------------------------------

o The aacraid-dkms-1.2.1-41024.tgz package includes two packages:
	o dkms-2.2.0.3-1.noarch.rpm (or dkms-2.0.17.4-0ubuntu1_all.deb)
	o aacraid-1.2.1.41024-dkms.noarch.rpm (or foreign extraction)
o Download the package into a temporary directory (/tmp)
	o Change to /tmp directory and untar the package:
	o cd /tmp
	  tar xvzf aacraid-dkms-1.2.1-41024.tgz
o Install the packages:
	o rpm -Uvh dkms-2.2.0.3-1.noarch.rpm
	   or install the debian version.
	  rpm -Uvh aacraid-1.2.1.41024-dkms.noarch.rpm
	   rpm2cpio aacraid-1.2.1.41024-dkms.noarch.rpm | (cd / ; cpio -idmu )
	   for debian.
	o For your interest, the source rpm places driver
	  source contents in /usr/src/aacraid-1.2.1.41024
	  in case manual build intervention is required.
o Use the various dkms commands to accomplish your goals:
	o Build and install a driver:
	  dkms add -m aacraid -v 1.2.1.41024
	  dkms build -m aacraid -v 1.2.1.41024
	   products in /var/lib/dkms/aacraid/1.1.5.xxxx/<kernel>/<arch>/module/
	  dkms install -m aacraid -v 1.2.1.41024
	o Build a driver for a different system other than native:
	  dkms build -k 2.4.21-4.ELsmp -m aacraid -v 1.2.1.41024
	  dkms install -k 2.4.21-4.ELsmp -m aacraid -v 1.2.1.41024
	o Make a driver disk from a set of built drivers:
	  dkms mkdriverdisk -k 2.4.21-4.ELBOOT,2.4.21-4.ELsmp,2.4.21-4.EL \
	     -d redhat -m aacraid -v 1.2.1.41024
	  dkms mkdriverdisk -k 2.6.11.4-20a-default,2.6.11.4-20a-smp \
	     -d suse -m aacraid -v 1.2.1.41024
	o Check current status of dkms:
	  dkms status

Note: o The driver RPM is in DKMS format and requires user to install dkms
        rpm (dkms-2.2.0.3-1.noarch.rpm) first.
      o Additional support documentation:
	      o man dkms
	      o download http://linux.dell.com/dkms/dkms-ols2004.pdf for
	        theory and practice

------------------------------------
Additonal Information regarding how to use the .img files for a fresh Linux
OS installation:

Create the driver disk using the dd command (on a Linux machine).

- Using a UNIX/Linux system mount the drive containing the .img file,
- Insert a blank floppy disk in your disk drive
- Use the dd command to copy the image to the floppy by issueing the
  following the command:

  dd if=aacraid-driverdisk-1.2.1-41024-<arch>.img of=/dev/fd0 bs=1440k

Where <arch> is a combination name of operating system(s) release and
destination CPU architecture(s).



Known Limitations:
1. aacraid-driverdisk-1.2.1-41024-<arch>.img won't work with the
   "linux noprobe dd" option during a fresh Linux installation. Please use
   "linux dd" instead.

2. A logical drive/array has to be configured before installing the linux
   driver using aacraid-driverdisk-1.2.1-41024-<arch>.img file during a fresh
   Linux installation. If there are no logical disks configured on the card.
   The following message appears:
	No devices of the appropriate type were found on the driver disk.






History:
Initial Release.













