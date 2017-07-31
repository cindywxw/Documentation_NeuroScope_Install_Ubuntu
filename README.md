## Installing Neuroscope(using source code) on Ubuntu 16.04:


1. Make sure g++, cmake, Qt4 and QtWebKit are installed. To install, in terminal: 
```bash
sudo apt-get install g++ cmake libqt4-dev libqtwebkit-dev
```
g++, cmake and Qt version guaranteed suitable for neuroscope installation:  
g++(5.4.0), cmake(3.9.0), Qt(4.8.7)  
  
2. To install neuroscope, LibKlustersShared is needed. Download codes of "LibKlustersShared" from [sourceforge](http://neurosuite.sourceforge.net/GNULinux.html). Then unpack the downloaded source tarball: 
```bash
tar xvzf libklustersshared-2.0.0.tar.gz
```
  
3. After unpacking and before installing LibKlustersShared-2.0.0, change src/gui/qhelpviewer.cpp:
```cpp
#include <QWebView>
#include <QWebPage>
```
to:
```cpp
#include <QtWebKit/QWebView>
#include <QtWebKit/QWebPage>
```
  
4. In terminal, under the directory of libklustersshared, build and install libklustersshared:
```bash
cd libklustersshared-2.0.0/  (the directory where you download libklustersshared)
mkdir build && cd build
cmake -DCMAKE_INSTALL_PREFIX=$HOME .. 
make install
```
  
5. Add symbolic links:
```bash
sudo ln -s /home/[user name]/lib/libklustersshared.so /usr/lib/libklustersshared.so
sudo ln -s /home/[user name]/lib/libklustersshared.so.2 /usr/lib/libklustersshared.so.2
sudo ln -s /home/[user name]/lib/libklustersshared.so.2.0.0 /usr/lib/libklustersshared.so.2.0.0
```
  
6. Download codes of "neuroscope" from [sourceforge](http://neurosuite.sourceforge.net/GNULinux.html) (modified neuroscope from github in the future).  
For the pack from sourceforge, unpack the downloaded source tarball:
```bash
tar xvzf neuroscope-2.0.0.tar.gz
```
  
7. Build and install neuroscope as libklustersshared in step 4.
```bash
cd neuroscope-2.0.0/  (the directory where you download neuroscope)
mkdir build && cd build
cmake -DCMAKE_INSTALL_PREFIX=$HOME .. 
make install
```
  
TaDa, Neuroscope is ready to use, and you can start the program from terminal by typing in
```bash
neuroscope
```
