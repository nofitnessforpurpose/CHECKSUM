# CHKSUM
Calculate the check sum of used space on a data pack that matches ORG-LINK pack .OPK images.

This <a href="https://en.wikipedia.org/wiki/Psion_Organiser"> Organiser II</a> <a href="https://en.wikipedia.org/wiki/Open_Programming_Language">OPL progam</a> reads the used space of a datapack and calculates a simple check sum for the pack. This checksum value will match a <a href="https://en.wikipedia.org/wiki/Checksum">Checksum 32</a> value.  

<div align="center">
  <div style="display: flex; align-items: flex-start;">
    <img src="https://github.com/nofitnessforpurpose/CHECKSUM/blob/main/images/CHECKSUM-01.jpg?raw=true" width="400px" alt="NotFitForPurpose Image copyright (c) 01 July 2025 nofitnessforpurpose All Rights Reserved">
  </div>
</div>
<BR>

[![Organiser](https://img.shields.io/badge/gadget-Organiser_II-blueviolet.svg?%3D&style=flat-square)](https://en.wikipedia.org/wiki/Psion_Organiser)
[![GitHub License](https://img.shields.io/github/license/nofitnessforpurpose/LOGMETER?style=flat-square)](https://github.com/nofitnessforpurpose/CHECKSUM/blob/main/LICENSE)
[![Maintenance](https://img.shields.io/badge/maintained%3F-yes-green.svg?style=flat-square)](https://github.com/nofitnessforpurpose/CHECKSUM/graphs/commit-activity)
![GitHub repo size](https://img.shields.io/github/repo-size/nofitnessforpurpose/LOGMETER?style=flat-square)

<br>  

## Use Case
Check sum values are frequently used where it's helpful to independently determine if data has changed either due to degradation, purposeful or accidental modification.  

Changes may arise for example due to corruption (e.g. for EPROMS inadequate label, erase time or positioning in the 'formatter'), physical read / write errors or overwriting of data.  

The CHKSUM program contained in the repository is configured to calculate a check sum for data packs B, C or D as selected by the user on a Psion Organiser 2 device.  

The CHKSUM program calculates the used space on the data pack and calculates a check sum for the selected pack content. The <strong>Normal</strong> option excludes the data pack header as this is variable for user created packs. The <strong>All</strong> option includes a .OPK and the data pack header to allow comparison with a standard <a href="https://www.jaapsch.net/psion/fileform.htm#opkfile">.OPK</a> file header.  

The <strong>All</strong> option therefore allows immediate comparison with data packs uploaded / downloaded using tools such as <a href="https://www.jaapsch.net/psion/connect.htm#software">CL.EXE</a> or <a href="https://www.lostgallifreyan.net/Software/ORG-Link/ORG-Link.htm">ORG-LINK</a> (see note below on pack delimiters).
Calculation comprises the used areas of the pack, including items marked deleted, which limits the calculation duration whilst retaining compatability with .OPK file checksums.

<div align="center">
  <div style="display: flex; align-items: flex-start;">
    <img src="https://github.com/nofitnessforpurpose/CHECKSUM/blob/main/images/2025-07-22%2012-37-59.gif?raw=true" width="200px" alt="NotFitForPurpose Image copyright (c) 22 July 2025 nofitnessforpurpose All Rights Reserved">
  </div>
</div>

The demonstration above shows verification of CHCKSUM02 against its self on Pack B: and verification of its own checksum against the Personal Finance Pack in Pack C:, together with a test against the held check sum of CHCKSUM02 against the Personal Finance packs check sum. The Personal Finance Pack in Pack C: is ~32k bytes, the checksum calculation takes ~8 seconds.

<BR>

## Check Sum
The available algorithm in revision 0.2 is a sum of bytes approach. This has limitations, such as lack of sensitivity to complementary errors. 
Revision 0.2 implements a machine code algorithim for sum of bytes. More sophisticated algorithms will be added.  

Checksums are represented in Hexadecimal values.
Two Checksum values can be calculated:  
|  Type    | Description                                                    |
| -------- | ---------------------------------------------------------------|
|  <strong>Normal</strong>  | The principal pack content which excludes the header which can vary by creation date and pack type |
|  <strong>All</strong>     | All the pack data which includs the header |  

The sum of bytes checksums for revision 2 .OPK included in the distribution are:  
| Type     | Value                                                          |
| -------- | ---------------------------------------------------------------|
| Normal   | 000616E5 |
| All      | 00061B30 |


At the time of publishing it is believed this is the first such use of a check sum for the purposes of verifying downloaded pack integrity on the Psion Organiser 2 device.  

Many programs are capable of calculating check sums, the author uses a number though finds <a href="https://mh-nexus.de/en/hxd/">this<a> tool convenient when verifying .OPK files on Microsoft Windows Computers.  

Version 0.3 will include verification of the pack header checksum for all packs.

<br>  

## Installation
<img src="https://github.com/nofitnessforpurpose/CHECKSUM/blob/main/images/OPK.jpg">  

A PSION Organiser 2 .OPK file is <a href="https://github.com/nofitnessforpurpose/CHECKSUM/blob/main/code/chksum02/CHKSUM02.OPL">available</a> which contains both source and object code. This file can be downloaded onto a data pack using a COMMS link and tools such as <a href="https://www.lostgallifreyan.net/Software/ORG-Link/ORG-Link.htm">ORG-LINK</a> or <a href="https://www.jaapsch.net/psion/connect.htm">similar</a>.

When down loaded and programmed onto a data pack, run the CHKSUMxx progam from the data pack. The program will allow selection of the Drive of the target data pack e.g. B: 
The tool should then determine the size of the used data space on the data pack and calculate the check sum for the target data pack. 
When the data pack containing the utility is selected, the cacluated value should match the value shown for the current release of the software.
When the values match there is a limited liklihood of issue with the data pack, source data or data transfer process.  

<br>  

## Additional Uses
In the case of data storage reliability such as on a RAM PACK or long term storage on an EPROM or other memory device. 
The tool allows validation of the data storage content, without needing to interpret data (files, programs or other information) on the storage device.
An example use case has been validating a new U.V. erase system. To ensure that data once written, remains constant for all the used space of the data pack. 
Note used space includes all data including deleted files or data.  

<br>  

## Programs
The programs in the distribution are as detailed in the table below:

| Name         | Description                                 |
| ------------ |---------------------------------------------| 
| CHKSUMxx.OPL | Main program                                |
| HX$.OPL      | Converts a number to hexadecimal string     |
| CONV$.OPL    | Convert a Hexadecimal string to byte values |
|              |                                             |
| CHKSUMxx.OPK | .OPK Pack image with sources & Rev 3.3 LA Object code |


<br>  

Note  
Some versions of .OPK program packs have been found to use different length byte referencing which can lead to checksums which do not include all the data in the .OPK file. 
The issue is associated with inclusion or not of the terminating 0xFFFF bytes of the .OPK file record structure.
Part of the modification ensures that the terminating 0xFFFF is included in the size of the data as expressed in the 4th, 5th & 6th bytes of the .OPK file structure. 
This approach has the benefit of third party check sum calculations matching those obtained using the tool.  

Some, typically older .OPK program packs may indicate a differing check sum value i.e. 2 for the sum of bytes technique, which is accounted for data block length value applied in the 6th length byte location of the .OPK file.

e.g.
As shown for a blank 32k byte data pack in the image below, at byte location 5 the value 0x17 (23d) includes the last two bytes. In some .OPK pack image files it has been observed that byte 5 was set so as not to include the terminating 0xFFFF byte sequence in the block length.

<div align="center">
  <div style="display: flex; align-items: flex-start;">
  <img src="https://github.com/nofitnessforpurpose/CHECKSUM/blob/main/images/2025-07-14%20-%2032K-EMPTY-PACK.jpg?raw=true" width="400px" alt="NotFitForPurpose Image copyright (c) 01 July 2025 nofitnessforpurpose All Rights Reserved">
  </div>
</div>
<BR>

A <strong>Normal</strong> checksum calculation commences at absolute pack address 0x000A, in the .OPK file shown in the image above the equivalent location is 0x0010 due to the addition of the 6 byte .OPK header.  

<BR>

## Attribution
The original pack read code is drawn from the <a href="https://www.jaapsch.net/psion/software/opl/sendpack.zip">SENDPACK</a> program by Jaap Scherphuis, psion@jaapsch.net. 
The code was modified and adapted to generate values as would be obtained using <a href="https://www.lostgallifreyan.net/Software/ORG-Link/ORG-Link.htm">ORG-LINK</a> pack upload feature generating a .OPK file.  

<BR>

## Questions / Discussion
See <a target="_blank" rel="noopener noreferrer" href="https://www.organiser2.com/"> Organiser 2 Software </a> forum, though see note below first.

<BR>

## Please note:  
All information is For Indication only.
No association, affiliation, recommendation, suitability, fitness for purpose should be assumed or is implied.
Registered trademarks are owned by their respective registrants.

