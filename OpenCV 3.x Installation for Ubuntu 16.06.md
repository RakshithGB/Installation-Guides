# OpenCV 3.x Installation for Ubuntu 16.06

[OpenCV](https://opencv.org) is an open source library for image processing thats supported in multiple languages. This guide explains installation steps for **Python** only. 

#### Prerequisites:
**1.1 Python** : Install python from [miniconda](https://conda.io/miniconda.html). Avoid anaconda since it comes with too many redundant packages.

**1.1.1 Steps to install python:**
1. Download the required python from the above link. (Python 3.6 Recommended)
2. In terminal run:
    
```
$ bash <yourpythonfile.sh>
```
###### Note: Everytime it asks about updating path and where to install leave it at its default. (Just press enter.)
**1.2 Changing the system python (in order to use sudo with miniconda python):**

1. First add all the pythons in a list like this:

    ```
$ sudo update-alternatives --install /usr/bin/python python /usr/bin/python2.7 1
$ sudo update-alternatives --install /usr/bin/python python /usr/bin/python3.5 2
$ sudo update-alternatives --install /usr/bin/python python /home/rakshith/miniconda3/bin/python3.6 3
```
(Enter your corresponding miniconda python path, the last number in each command is basically a priority)

2. Everytime you want to give sudo permission to minconda python you can do so by:

    ```
$ sudo update-alternatives --config python
```
3. Then type the corresponding index number of the python you want to give sudo permission to and press enter.
4. Make sure to change the permission back to system python2.7 once your done. Since Ubuntu needs this for installing system packages.

**1.3 Assigning root permissions to conda environment: [ Warning: Be very careful while doing this. One mistake can destroy your system. ]**
Conda sometimes throws permission error in order to fix this. Run this in terminal:

```
$ sudo chown -R USERNAME /home/USERNAME/miniconda3
```
Here replace **USERNAME** with your username and the path with the path of your miniconda.

###### **BE VERY CAREFULL WITH THE PATH. YOU WILL HAVE TO REINSTALL OS IF SOMETHING GOES WRONG.**

**1.4 Installing OpenCV prerequisite packages:**
Make sure invoking `$ sudo python` shows system python 2.7, if not then follow step **1.2** to change it to system python 2.7.

Update Packages:

```
$ sudo apt-get update
$ sudo apt-get upgrade
```
Install OS Packages:

```$ sudo apt-get remove x264 libx264-dev
$ sudo apt-get install build-essential checkinstall cmake pkg-config yasm
$ sudo apt-get install git gfortran
$ sudo apt-get install libjpeg8-dev libjasper-dev libpng12-dev
$ sudo apt-get install libtiff5-dev
$ sudo apt-get install libavcodec-dev libavformat-dev libswscale-dev libdc1394-22-dev
$ sudo apt-get install libxine2-dev libv4l-dev
$ sudo apt-get install libgstreamer0.10-dev libgstreamer-plugins-base0.10-dev
$ sudo apt-get install qt5-default libgtk2.0-dev libtbb-dev
$ sudo apt-get install libatlas-base-dev
$ sudo apt-get install libfaac-dev libmp3lame-dev libtheora-dev
$ sudo apt-get install libvorbis-dev libxvidcore-dev
$ sudo apt-get install libopencore-amrnb-dev libopencore-amrwb-dev
$ sudo apt-get -qq install libopencv-dev libqt4-dev
$ sudo apt-get install x264 v4l-utils ffmpeg
$ sudo apt-get install libprotobuf-dev protobuf-compiler
$ sudo apt-get install libgoogle-glog-dev libgflags-dev
$ sudo apt-get install libgphoto2-dev libeigen3-dev libhdf5-dev doxygen
```
 
  




