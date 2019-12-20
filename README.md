# SdrGult
SdrGlut is a simple software defined radio player. Using glut for drawing and glui for its dialogs makes it tiny compared to programs that use QT5 or wxWidgets. SdrGlut uses liquid-sdr and SoapySDR to preform the SDR calculations. The audio is handled by OpenAL.

The second release is now avaliable - It fixes a number of problems with the audio. It has a prebuild exe for the macOS. It has serveral of modules build in. If it has the module that you what - download, install and you are ready to go. It also has zip file for Windows. Unpack and go to the bin folder and click on SdrGlut.exe to run.


https://github.com/righthalfplane/SdrGlut/releases/tag/v1.1


# Movies

Cobra 38 WXST testing an inverted T antenna using SdrGlut
https://www.youtube.com/watch?v=s-Rg2XC7bUY

SdrGlut a Software Defined Radio player test drive #1
https://www.youtube.com/watch?v=zxgcRjTahcA

SDRPlay RSP2 vs a HackRF One using SdrGlut at FRS frequencies
https://www.youtube.com/watch?v=42uEKTncpbQ

Corbra 38WXST vs Radio Shack TRC-236
https://www.youtube.com/watch?v=O9MQbf1ArQk

Corbra 38WXST using three different antennas
https://www.youtube.com/watch?v=JDmxGQFwX-Y

SdrGlut Simultaneously Running Five SDRs
https://www.youtube.com/watch?v=BmUNrAn1Llk

Raspberry PI 4 using SdrGlut to control the NetSDR
https://www.youtube.com/watch?v=jV-LxQS_acY

SdrGlut vs CubicSDR on the Raspberry pi 4 with a Lime Mini SDR
https://www.youtube.com/watch?v=C18bGxbXNsA

SdrPlay RSP2 vs NetSDR+ using SdrGlut Part 1. 
https://youtu.be/LdIaFVuAICw

SdrPlay RSP2 vs NetSDR+ using SdrGlut Part 2. 
https://youtu.be/1QJromJ76Lo

SdrPlay RSP2 vs NetSDR+ using SdrGlut Part 3. 
https://youtu.be/NXLYYvLQN_k

SdrPlay RSP2 vs a simple RTL stick using SdrGlut at FRS frequencies
https://www.youtube.com/watch?v=eiuTO5yIR7w

SdrPlay RSP2 vs a LimeSDR Mini using SdrGlut at FRS frequencies
https://www.youtube.com/watch?v=PEfrJ4ZuN9g

Lime Mini vs a RTL stick using SdrGlut at FRS frequencies
https://www.youtube.com/watch?v=pDqNCe6GxnA

# Installation of libliquid

There are several recent versions of libliquid. The call to ampmodem_create differs. If a complier error happens,  switch the line that is commented out. It occurs in two places.

      f->demodAM = ampmodem_create(0.5, mode, iflag);
    
  //  f->demodAM = ampmodem_create(0.5, 0.0, mode, iflag);
  
# Install on Ubuntu 18.04


This is what I did to get SdrGlut running on a fresh install of Ubuntu 18.04.3

sudo apt-get update

sudo apt-get upgrade

sudo apt-get install build-essential

sudo apt-get install libsoapysdr0.6

sudo apt-get install libsoapysdr-dev

sudo apt-get install libopenal-dev

sudo apt-get install libliquid-dev

sudo apt-get install freeglut3

sudo apt-get install freeglut3-dev

sudo apt-get install libalut0

sudo apt-get install libalut-dev

sudo apt-get install git

cd ~/Desktop

git clone https://github.com/righthalfplane/SdrGlut.git

cd SdrGlut

make -f makefileUbunta

./sdrglut.x

# Install on Raspberry pi

SdrGlut runs nicely on the Raspberry pi 4 -  Do not know if slower version have enough horsepower for it

To do the normal edition of Raspbian - follow the uBuntu instructions with -

make -f makefileRaspbian

instead of

make -f makefileUbunta

## The SDRPlay Edition


This is what I did to get SdrGlut running on the SDRPlay verison of Raspbian.

The SDRPlay verison Raspbian has the SDRPlay libraries already installed.


sudo apt-get update

sudo apt-get upgrade

sudo apt-get install build-essential

sudo apt-get install libopenal-dev

sudo apt-get install libliquid-dev

sudo apt-get install freeglut3

sudo apt-get install freeglut3-dev

sudo apt-get install libalut0

sudo apt-get install libalut-dev

sudo apt-get install git

cd ~/Desktop

git clone https://github.com/righthalfplane/SdrGlut.git

cd SdrGlut

make -f makefileRaspbian

./sdrglut.x


## added support for NetSDR -

cd ~/Desktop

git clone https://github.com/pothosware/SoapyNetSDR.git

cd SoapyNetSDR

mkidr build

cd build

cmake ../

make -j 4

sudo make install

## added support for LimeSDR  -

cd ~/Desktop

git clone https://github.com/myriadrf/LimeSuite.git

cd LimeSuite

mkidr build

cd build

cmake ../

make -j 4

sudo make install

# Install on MacOS 10.4 with brew

This is a copy of some of the instruction from -

https://github.com/pothosware/homebrew-pothos/wiki


brew tap pothosware/homebrew-pothos

brew tap dholm/homebrew-sdr #other sdr apps

brew update


brew install soapyremote

brew install soapyaudio

brew install soapyrtlsdr

brew install soapyhackrf

brew install soapybladerf

brew install soapyairspy

brew install soapyairspyhf

brew install soapyosmo

brew install soapyredpitaya

brew install soapyiris

brew install limesuite

brew install cubicsdr

cd ~/Desktop

git clone https://github.com/righthalfplane/SdrGlut.git

cd SdrGlut

make -f makefileMACINTOSH

./sdrglut.x

Do not do the "brew install soapyuhd" suggested by the wiki as it generates an exception error when it is used.

The install of cubicsdr fails, but it installs the needed liquid-sdr.

To compile with the GUI envoke - SdrGlut.xcodeproj

## added support for NetSDR -

cd ~/Desktop

git clone https://github.com/pothosware/SoapyNetSDR.git

cd SoapyNetSDR

mkidr build

cd build

cmake ../

make -j 4

sudo make install

## added support for SDRPlay -

Get the sdrplay driver installer and install it -

https://www.sdrplay.com/macdl.php

SDRplay_RSP_API-MacOSX-2.13.2.pkg




# Install SdrGlut on Windows 7

## Install OpenAL -

OpenAL must be loaded on to window. Get the two packages -

OpenAL1.1.CoreSDK

OpenAL 1.1 windows install

from "https://www.openal.org/downloads"

and install them.

## Install PothosSDR and SdrGlut -

The easiest way to install SdrGlut is to install the PothosSDR package first -

https://downloads.myriadrf.org/builds/PothosSDR/

Run PothosSDR-2019.06.09-vc14-x64.exe and select

add PothosSDR to system path for all users

full install

There is a problem with the "Device.h" the following section needs to be commented out -

///@cond INTERNAL
//! Old setupStream invoked by compatibility macro

//static inline int SoapySDRDevice_setupStream_(SoapySDRDevice *device,

//    SoapySDRStream **stream,

//    const int direction,

//    const char *format,

//    const size_t *channels,

//    const size_t numChans,

//    const SoapySDRKwargs *args)

//{////

//    *stream = SoapySDRDevice_setupStream(device, direction, format, channels, numChans, args);

//    return (*stream == NULL)?-1:0;

//}


//#define SoapySDR_getMacro(_1,_2,_3,_4,_5,_6,_7,NAME,...) NAME

//#define SoapySDRDevice_setupStream(...) SoapySDR_getMacro(__VA_ARGS__, SoapySDRDevice_setupStream_, SoapySDRDevice_setupStream)(__VA_ARGS__)

///@endcond


git clone https://github.com/righthalfplane/SdrGlut.git

Then use the GUI and go to the directory SdrGlut/Sdrglut-windows and click the project SdrGlut.sln.

Select "Release" and "X64" and then find and switch the comments on the lines -

           // SoapySDRDevice_setupStream(rx->device,&rx->rxStream,SOAPY_SDR_RX, SOAPY_SDR_CF32, NULL,0,NULL);
            
           rx->rxStream=SoapySDRDevice_setupStream(rx->device,SOAPY_SDR_RX, SOAPY_SDR_CF32, NULL,0,NULL);


Then select "Start without Debugging", SdrGlut should compile and start running.













