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
Check sum values are frequently used where its helpful to independently determine if data has changed either due to degradation, purposeful or accidental modification.  
Changes may arise for example due to corruption, physical read / write errors or overwriting of data.
The CHKSUM program contained in the repository is configured to calculate a check sum for data packs B, C or D of a Psion Organiser 2 device, as selected by the user.  

The CHKSUM program calculates the used space on the data pack and calculates a check sum that includes a standard <a href="https://www.jaapsch.net/psion/fileform.htm#opkfile">.OPK</a> file header. 
This is to allow immediate comparison with data packs uploaded using tools such as <a href="https://www.jaapsch.net/psion/connect.htm#software">CL.EXE</a> or <a href="https://www.lostgallifreyan.net/Software/ORG-Link/ORG-Link.htm">ORG-LINK</a>.
It also limits the calculation to the used area of the pack, including items marked deleted, which limits the calculation duration.

<br>  

## Check Sum
The available algorithm in revision 0.1 is a sum of bytes approach. This has limitations, such as lack of sensitivity to complementary errors. 
Following the initial release, more sophisticated algorithms will be added, most probably in machine code.  

Checksums are represented in Hexadecimal values.
The checksum for the demonstration pack .OPK included in the distribution is:  
<bold>003A4EE</bold>

At the time of publishing it is believed this is the first such use of a check sum for the purposes of verifying downloaded pack integrity on the Psion Organiser 2 device.  

Many programs are capable of calculating check sums, the author uses a number though finds <a href="https://mh-nexus.de/en/hxd/">this<a> tool convenient.
<br>  

## Installation
A PSION Organiser 2 .OPK file is avialble which contains both source and object code. This file can be downloaded onto a data pack using tools such as <a href="https://www.lostgallifreyan.net/Software/ORG-Link/ORG-Link.htm">ORG-LINK</a> or similar.

When down loaded and programmed onto a data pack, run the CHKSUM progam from the data pack. The program will allow selection of the Drive the data pack is located in e.g. B: 
The tool should then determine the size of the used data space on the data pack and calculate the check sum for the data pack. 
The cacluated value should match the value shown for the current release of the software.
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
| CHKSUM.OPL   | Main program                                |
| CSC.OPL      | Calculate checksum                          |
| HX$.OPL      | Converts a number to hexadecimal string     |
| CONV$.OPL    | Convert a Hexadecimal string to byte values |

<br>  

## Attribution
The original code is drawn from a program by Jaap Scherphuis, psion@jaapsch.net SENDPACK. 
The code was modified and adapted to generate values as would be obtained using <a href="https://www.lostgallifreyan.net/Software/ORG-Link/ORG-Link.htm">ORG-LINK</a>.

Note  
Some versions of .OPK program packs have been found to use different length byte referencing which can lead to checksums which are not of all the data in the .OPK file. 
The issue is associated with inclusion or not of the terminating 0xFFFF bytes of the .OPK file record structure.
Part of the modification ensures that the terminating 0xFFFF is included in the size of the data as expressed in the 4th, 5th & 6th bytes of the .OPK file structure. 
This approach has the benefit of third party check sum calculations matching those obtained using the tool.  

Some, typically older .OPK program packs may differ by a value of 2 which is accounted for data block length value applied in the 6th length byte location of the .OPK file.

<BR>

## Questions / Discussion
See <a target="_blank" rel="noopener noreferrer" href="https://www.organiser2.com/"> Organiser 2 Software </a> forum, though see note below first.

<BR>

## Please note:  
All information is For Indication only.
No association, affiliation, recommendation, suitability, fitness for purpose should be assumed or is implied.
Registered trademarks are owned by their respective registrants.

