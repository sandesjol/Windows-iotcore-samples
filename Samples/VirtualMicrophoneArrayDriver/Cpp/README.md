# Create A Virtual Audio Microphone Array For Your Windows 10 IoT Core Device

If you are not very familiar with Windows universal drivers yet, we strongly encourage you to start by reading the following materials:

* [Building Universal Drivers - Channel9 Video](https://channel9.msdn.com/Blogs/WinHEC/Building-a-Universal-Driver)

* [Getting Started with Universal Windows Drivers - MSDN](https://msdn.microsoft.com/en-us/library/windows/hardware/dn941241(v=vs.85).aspx)

<br/>

## Did you set up your development environment yet?

* Instructions on how to set up your development environment with Visual Studio 2017 can be found [here]({{site.baseurl}}/{{page.lang}}/GetStarted)

* Additionally, you will need to install the Windows Driver Kit (WDK) which you can download from [here](https://developer.microsoft.com/en-us/windows/hardware/windows-driver-kit) 

<br/>

## Overview
We will now be walking you through the process of creating and installing a device driver that will run on any Windows 10 IoT Core device.  This driver will be specifically built to be a universal driver.

<br/>

## Description
The name of the driver in this sample is `virtualaudiomicarray`.  

<br/>

## Source Code And Binaries
You can find the source code for this sample by downloading a zip of all of our samples [here](https://github.com/Microsoft/Windows-iotcore-samples/archive/master.zip) and navigating to the `samples\VirtualMicrophoneArrayDriver`.  Make a copy of the folder on your disk and open the solution file from Visual Studio.

<br/>

 Originally derived from the SYSVAD driver sample (https://github.com/Microsoft/Windows-driver-samples/tree/master/audio/sysvad),
 this sample illustrates how to construct a virtual microphone array at runtime using monoaural audio devices present on the system.

 Before running the sample, the INF must be updated to setup registry keys under the 
 drivers 'Parameters' subkey to identify which audio endpoints should be used as inputs and the
 format (NumChannels - for the entire array, SamplesPerSecond, BitsPerSample) of each input stream.

 Limitations in the sample:

 All input streams must use the same format - this sample performs no format conversion.

 There is no mechanism to control the gain of the input streams.

 The metadata for the microphone array geometry is hardcoded and CMicArrayMiniportTopology::PropertyHandlerMicArrayGeometry should be
 updated in micarraytopo.cpp should be updated to reflect the actual physical characteristics of the microphone array.
