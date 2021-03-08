 

## **EC Firmware Flash Utility** 
it provides to update the EC firmware on x86-64 platforms. It uses eSPI to communicate with the EC chip. This document will help to understand the Flash Firmware Utility supported features and how user can use it.



## How to Install  

1. Install required dependencies on your target device


| Supported Hardware | **Architecture**        |
| ------------------ | ----------------------- |
| cExpress-EL        | Ubuntu 20.04 LTS 64 bit |
| cExpress-TL        | Ubuntu 20.04 LTS 64 bit |
| cExpress-AR        | Ubuntu 20.04 LTS 64 bit |

2. Git clone the binary & driver from https://github.com/adlink/ec-fwupd.git on your target device

3. Install the drive using below command.

   ```
   $ cd ec-fwupd
   $ insmod ad-ec-fwupd.ko 
   ```

4. change the access permissions

   ```
   chmod 777 ad-ec-fwupd
   ```



<br>



## How to Use 

The command **ad-ec-fwupd** is used in Linux to flash EC firmware on your target device.

**Usage**  

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
  
  <br>


* Display the BMC version of .bin binary:

  ```
  $ ad-ec-fwupd -d -f your_file.bin
  ```

  **Note:**

  * it will give the below output with the valid .bin file:
  
    > **Output format: EC [MODULE_NAME](#_Module_Details_:) [VERSION](#_Module_Details_:) [DATE](#_Module_Details_:) © ADLINK Technology Inc.**

<br> 

* Display the BMC version on your target device

  ```
  $ ad-litbmc-fwupd -d -t
  ```

  **Note:**

  * it will give the below output when the firmware is in your target,

    > **Output format: EC [MODULE_NAME](#_Module_Details_:) [VERSION](#_Module_Details_:) [DATE](#_Module_Details_:) © ADLINK Technology Inc.**

  * it will give the below output when the firmware is NOT in your target

    > **Output format: Firmware is corrupted, please update the firmware in recovery mode.**
    


<br>
 
 * Please feel free to send us (email: ryanzj.huang@adlinktech.com) patches for this layer and report bugs of this layer.
For hardware support, please contact your local representative.
 
 * Internal gitlab commit id:682c503c1dfffa38239a34cf7ab8ce746ddf5dcd



 

 
