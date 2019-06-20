# PWM Analyzer for Saleae Logic

This plugin for [Saleae Logic][logic] allows you to analyze a PWM
stream as commonly found in RC.

![logic analyzer](https://github.com/dustin/logic-pwm/raw/master/docs/pwm-logic.png)

## Exporting

The analyzer exports to a simple csv format with a timestamp and the
value read at that timestamp.

```csv
Time [s],High,Low,Duty,Frequency
0.000000000000000,1497,20000,6.964123,46.5
0.042996833333333,1494,20000,6.954384,46.5
0.085988500000000,1501,20000,6.981431,46.5
0.107489583333333,1437,20000,6.706990,46.6
0.128927416666667,1506,20000,7.004859,46.5
0.150433916666667,1577,20000,7.309066,46.3
0.172011000000000,1574,20000,7.299042,46.4
0.193585750000000,1606,20000,7.437048,46.3
0.236799666666667,1656,20000,7.648974,46.2
0.258456166666667,1698,20000,7.828438,46.1
0.280154833333333,1677,20000,7.737729,46.1
```

## Building

### MacOS

Dependencies:
- XCode with command line tools
- CMake 3.11+

Installing command line tools after XCode is installed:
```
xcode-select --install
```

Then open XCode, open Preferences from the main menu, go to locations, and select the only option under 'Command line tools'.

Installing CMake on MacOS:

1. Download the binary distribution for MacOS, `cmake-*-Darwin-x86_64.dmg`
2. Install the usual way by dragging into applications.
3. Open a terminal and run the following:
```
/Applications/CMake.app/Contents/bin/cmake-gui --install
```
*Note: Errors may occur if older versions of CMake are installed.*

Building the analyzer:
```
mkdir build
cd build
cmake ..
cmake --build .
```

### Ubuntu 16.04

Dependencies:
- CMake 3.11+
- gcc 4.8+

Misc dependencies:

```
sudo apt-get install build-essential
```

Building the analyzer:
```
mkdir build
cd build
cmake ..
cmake --build .
```

### Windows

Dependencies:
- Visual Studio 2015 Update 3
- CMake 3.11+

**Visual Studio 2015**

*Note - newer versions of Visual Studio should be fine.*

Setup options:
- Programming Languages > Visual C++ > select all sub-components.

Note - if CMake has any problems with the MSVC compiler, it's likely a component is missing.

**CMake**

Download and install the latest CMake release here.
https://cmake.org/download/

Building the analyzer:
```
mkdir build
cd build
cmake ..
```

Then, build the newly created solution file located here: `build\can_analyzer.sln`
```
msbuild  pwm_analyzer.vcxproj -p:Configuration=Release
```

Copy the resulting dll from logic-pwm\build\Analyzers\Release\pwm_analyzer.dll into Program Files\Saleae Inc\Analyzers

## Installing

In the Develoepr tab in Logic preferences, specify the path for
loading new plugins, then copy the built plugin into that location:

    cp release/* /path/specified/in/Logic/preferences

[logic]: https://www.saleae.com/downloads
[sdk]: http://support.saleae.com/hc/en-us/articles/201104644-Analyzer-SDK
