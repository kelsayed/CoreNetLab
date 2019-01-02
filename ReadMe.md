# Virtual Networks Lab using Linux and the CORE Network Emulator

## Overview

This lab was developed as part of the ECE403 Computer Networks course in [Cairo University](http://cu.edu.eg). The lab is comprised of a set experiments whose objective is to enhance the skills the ECE403 students in the area of IP networking.  It can be used for any basic or advanced Computer Networking course. I have used it in both this course and the graduate Computer Networking course and the feedback has been very good. 

Using virtualization and the [Common Open Research Emulator](https://www.nrl.navy.mil/itd/ncs/products/core) (CORE)  open source network emulators, the students will be able to build and configure a network that resembles and behaves exactly like a network of real routers and end nodes. The routers are based on [Quagga](https://www.quagga.net/) software that are fully capable of using Cisco routers configuration commands and support OSPF, RIP, BGP, etc. Students will collect results from the network traces and asked to interpret the results in order to gain good understanding of IP networking concepts.

In the experiments, students will be exposed to different techniques such as router configuration, traffic generation, TCP protocol performance, OSPF routing, network analysers and tracers. It also serves as a very nice introduction to [Software-Defined Networking](https://en.wikipedia.org/wiki/Software-defined_networking) (SDN). As a side knowledge students will be exposed to using Linux and virtualization tools.

The purpose of this github repository is two things:

1. Share the labs with a wider community to maximize the benefits.
2. Extend the labs by other contributors as in in open source project (see [How to Contribute](#how-to-contribute) below).

## Core Setup Tutorial 

1.  Install VirtualBox on your PC. You can use VMWARE as well or install virtualbox/vmware on Linux if you plan to use Linux to host the virtual lab. However, the process herein assumes virtualbox on windows environment. You are on your own if you want to try other combinations (they should work without problems).
2.  Download the core network emulator Virtualbox image from this [link](https://drive.google.com/file/d/1g5zGgwHICIvmtEQzSGVgqiyt6PaX7teA/view?usp=sharing) . This is a modified image from the original core network emulator virtual machine that has some additional tools installed such as wireshark, iperf, and the network topologies used in the labs. 
    Alternatively, [download](https://downloads.pf.itd.nrl.navy.mil/core/vmware-image/) VMWare image from official core network emulator site but you will need to add the tools manually. 
3.  The rest of the instructions assumes you got the vcore4.7.zip as shown in step 1 above. 
4.  Move the folder Vcore4.7.zip to the location of your choice. For example D:\\Vbox\Vcore4.7. Unzip the file. 
5.  Now open virtualbox software, select Machine -\> Add and browse to D:\\Vbox\Vcore4.7 and select the file vcore-4.7.vbox
    A new virtual machine will be added. You can select Machine -\> Settings -\> System and increase the virtual machine allocated RAM to 1 Gbytes or more for better performance.
6.  Start the virtual machine Vcore by selecting it and clicking start. It may ask you few questions about LAN cards, etc, choose default answers.
7.  **Important Note**: It is highly likely that the virtual machine may not start complaining about some network card does not exist. If this happens select the virtual machine on virtuabox, right click, select properties -\> network -\> and then on adapter 1 attached either choose not attached or choose bridge and then select the network adapter installed on your PC (e.g. some Ethernet or Wifi interface).

## Running VCore 

**Important Note**: Both the user name and password to the Vcore Linux installation are "core"

1. The Linux virtual machine will start and you will see on the desktop a green icon named CORE as shown below
![CORE_Desktop](./Images/vcoredesktop.png) 
2. Double click on CORE icon, the CORE emulator starts

3. You are now ready to work on the labs. It is recommended to start with the Introduction lab.

   a. [Introduction Lab](./IntroLab.md)

   b. [TCP Performance Labs](./TCPPerfLab,md)

   c. [OSPF Lab](./OSPFLab,md)

## How To Contribute
If you like these set of experiments, you can contribute by using normal [github pull](https://github.com/kelsayed/CoreNetLab/pulls) requests. 
You can either:


1. Contribute new labs 
2. Modify existing labs (correcting typos or additions of new ideas)

## Acknowledgements

Brian Linkletter [web site](http://www.brianlinkletter.com ) has great tutorials that helped me developoing this lab and exploring multiple other packages.
