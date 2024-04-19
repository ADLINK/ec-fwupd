 

## **EC Firmware Flash Utility** 
It provides a feasibility to update the EC firmware on ADLINK x86-64 computing platforms. It uses eSPI to communicate with the EC chip. This document will help to understand the Flash Firmware Utility supported features and how user can use it.

## Supported Hardware

- cExpress-EL
- cExpress-TL
- cExpress-AR

## How to Install  

1. Git clone the binary & driver from https://github.com/adlink/ec-fwupd.git on your target device

   ```sh
   $ git clone https://github.com/ADLINK/ec-fwupd
   ```

2. Navigate to the cloned directory  and install the driver based on the Ubuntu version that you've installed. There is a driver support for Ubuntu 20.04 and Ubuntu 22.04

   ```sh
   $ cd ec-fwupd
   $ sudo insmod bin/Ubuntu-22.04LTS/ad-ec-fwupd.ko
   ```

3. change the access permissions

   ```sh
   $ chmod 777 ad-ec-fwupd
   ```
   ```sh
   $ export PATH=$PATH:/${PWD}
   ```



## How to Use 

The command **ad-ec-fwupd** is used in Linux to flash EC firmware on your target device.

**Usage**

* Display about the utility tool

  ```sh
  $ cd ec-fwupd
  $ ad-ec-fwupd
  ```
  
   Function : EC Firmware Flash Utility on ADLINK [ARCH](#_Module_Details_:) platform
  
   Version : 1.01
  
   Usage :
  
  1. Update Firmware: ad-ec-fwupd -u filename.bin
  2. Firmware version on Target device :  ad-ec-fwupd -d -t
  3. Display Firmware version in bin file : ad-ec-fwupd -d -f filename.bin
  
  ​                 Options :
  
  ​                         -u start to update the firmware in normal mode
  
  ​                         -d -t Display the firmware version on your target device or module
  
  ​                         -d -f Display the firmware version on your bin file
  
  ​                         -h|? Display command line help information
  
* Display the help:

  ```sh
  $ ad-ec-fwupd -h
  ```
  
  Usage:

  `-h` Display this screen

  ​      	  -u                            update EC firmware in normal mode

  ​         	-u <filename>
  
  ​              	<filename>   full path of firmware image file
  
  `-d` Display firmware version
  
  ​          	-d <-t/-f> <filename>
  
  ​                	-t         target device             
  
  ​                	-f          firmware file                 

  ​               <filename>   full path of firmware image file
  
* Firmware Update:

  The utility will validate your file is valid or not. Once done, it will start to flash this firmware. 

  ```
  $ ad-ec-fwupd -u your_file.bin
  ```

    **Note**: 

  * it will give the below output with **the valid .bin file**:

    > Firmware file validation is in progress
    > Firmware file validation done successfully
    > Firmware updating in normal mode.
    > Firmware flashing in progress, please don't abort the application
    > Updating ….100%
    > Flashing done!
    > Firmware version on target device: cExpress-AR ADLINK  007
    > Firmware version on your bin file EC cExpress-AR ADLINK 01.004.007 Dec 14 2020
    > Updated successfully and please reboot the system.
    
  * it will give the below output with **the invalid .bin file**:

    > Validating the bin file is in progress...
    > Firmware file is not valid. please provide valid firmware file to update EC.
    
  * it will give the below output with **the incompatible .bin file**:
  
    > Validating the bin file is in progress... 
    > Firmware file is not suitable for current EC, Tool expecting cExpress-AR. But user provided firmware file is for cExpress-EL
  


* Display the EC version of .bin binary:

  ```
  $ ad-ec-fwupd -d -f your_file.bin
  ```

  **Note:**

  * it will give the below output with the valid .bin file:
  
    > **Output format: EC MODULE_NAME ADLINK VERSION DATE**

* Display the EC version on your target device

  ```
  $ ad-ec-fwupd -d -t
  ```

  **Note:**

  * it will give the below output when the firmware is in your target,

    > **Output format: MODULE_NAME ADLINK VERSION**



