# USBPcap - USB Packet capture for Windows

End-user installer is available at: https://desowin.org/usbpcap
Following informations are intended for developers and power users only.

Directory overview:
  USBPcapCMD - sample user space application
  USBPcapDriver - filter driver used to capture data

Build instructions:
  Download and install Windows Driver Kit 7.1.0 from Microsoft
    https://www.microsoft.com/en-us/download/details.aspx?id=11800

  Adjust driver_build_win7_64bit.bat (first line of that file):
    * To change to checked build: replace 'fre' with 'chk'
    * To build for x86: replace 'x64' with 'x86'
    * To build for Windows XP: replace 'WIN7' with 'WXP'

  Windows 8 Build instructions:
  In order to compile for Windows 8, you need to have Visual Studio 2013
  Community and install Windows Driver Kit 8.1 Update.
  To create solution file use the following command from Visual Studio 2013
  Command Prompt (while being chdired into usbpcap sources directory):
  > Nmake2MsBuild dirs

  This will create solution dirs.sln. You can build the driver from the
  Visual Studio 2013 Command Prompt:
  > MSBuild dirs.sln /p:Configuration="Win8 Debug"

Installation:
  TESTSIGNING must be enabled in order to install this driver on 64 bit
  Windows. To do so, issue following command (as administrator):
    Bcdedit.exe -set TESTSIGNING ON
  and reboot.

  Right click on the USBPcap.inf file and select Install.

  After installing, reboot.

Usage:
  Currently there is no capture engine dll.
  You can use the USBPcapCMD.exe to select the filter instance (there is one
  instance per root hub) and specify the output pcap file name.

Licensing:
  USBPcapDriver is licensed under GPLv2 license.
  USBPcapCMD is licensed under BSD 2-Clause license.

