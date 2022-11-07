# MissionPlanner

[![Gitter](https://badges.gitter.im/Join%20Chat.svg)](https://gitter.im/ArduPilot/MissionPlanner?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge) [![Build status](https://ci.appveyor.com/api/projects/status/2c5tbxr2wvcguihp?svg=true)](https://ci.appveyor.com/project/meee1/missionplanner)

Website : http://ardupilot.org/planner/  

Forum : http://discuss.ardupilot.org/c/ground-control-software/mission-planner

Download latest stable version : http://firmware.ardupilot.org/Tools/MissionPlanner/MissionPlanner-latest.msi

Changelog : https://github.com/ArduPilot/MissionPlanner/blob/master/ChangeLog.txt  

License : https://github.com/ArduPilot/MissionPlanner/blob/master/COPYING.txt  


## How to compile

### On Windows (Recommended)

#### 1. Install software

##### Main requirements

Currently, Mission Planner needs:

- Microsoft .NET Framework 4.6.1
- Microsoft .NET standard 2.0

##### IDE

###### Visual Studio Community
The recommended way to compile Mission Planner is through Visual Studio. You could do it with Visual Studio Community (version 16.9 or newer to include .NET standard 2.0) : [Visual Studio Download page](https://visualstudio.microsoft.com/downloads/ "Visual Studio Download page").
Visual Studio suite is quite complet and comes with Git support. On installation phase, please install support for :
- ASP.NET and web development
- .NET Desktop Developement
- Desktop development with C++
- Universal Windows Platform deveopment
- Mobile development with .NET
- Visual Studio extension development
- .NET Core cross-platofrm developemnt

###### VSCode
Currently VSCode with C# plugin is able to parse the code but cannot build.

#### 2. Get the code

If you get Visual Studio Community, you should be able to use Git from the IDE. 
Just clone `https://github.com/ArduPilot/MissionPlanner.git` to get the full code.

In case you didn't install an IDE, you will need to manually install Git. Please follow instruction in https://ardupilot.org/dev/docs/where-to-get-the-code.html#downloading-the-code-using-git

#### 3. Build

To build the code:
- Open MissionPlanner.sln with Visual Studio
- Compile just the MissionPlanner project

### On other systems
Building Mission Planner on other systems isn't support currently.

## Launching Mission Planner on other system

Mission Planner can be use with Mono on non-Windows system. 
Be aware that all the functionnalities aren't working.

### On Linux

#### Requirements

Those instructions were tested on Ubuntu 18.04.
Please install Mono, either :
- ` sudo apt install mono-runtime libmono-system-windows-forms4.0-cil libmono-system-core4.0-cil libmono-winforms4.0-cil libmono-corlib4.0-cil libmono-system-management4.0-cil libmono-system-xml-linq4.0-cil`

or full Mono :
- `sudo apt install mono-complete`

#### Launching

- Get the lastest zipped version of Mission Planner here : https://firmware.ardupilot.org/Tools/MissionPlanner/MissionPlanner-latest.zip
- Unzip in the directory you want
- Go into the directory
- run with `mono MissionPlanner.exe`

You can debug Mission Planner on Mono with `MONO_LOG_LEVEL=debug mono MissionPlanner.exe`


[![FlagCounter](https://s01.flagcounter.com/count2/A4bA/bg_FFFFFF/txt_000000/border_CCCCCC/columns_8/maxflags_40/viewers_0/labels_1/pageviews_0/flags_0/percent_0/)](https://info.flagcounter.com/A4bA)

## MISSION PLANNER FIRE CHANGES
Software Code Parameters utilized for running the software.  The parameters below are viewable through on the Plan UI page as indicated by the photo below.
![Planner UI](https://github.com/swang63/MissionPlanner/blob/Test2/PlanUI.JPG?raw=true)

Window:
This value determines the size of the window of fire files to keep displayed on the map.  This window refers to each of the fire map “LOC######.TXT” where the number corresponds to a particular second of the fire as observed by the UAV.  The window thereby is set in seconds from last file to display.  300 seconds or 5 minutes is set as the default value

Update:
This value will update and reload the fireMap upon the number of files loaded.  Default value is set to 10.  This will update the map for values of time since last visit metrics for display.

Filter Value:
This value is set to 0.001 by default.  This value is the measure in degrees.  This filter value will include files of numerical order if the average latitude and longitude difference between the files is less than this value.  This will remove files in which the projected fire map appears to “jump” a far distance.  Files that have no preceding location file will be ignored so if there is a jump in the number of the location file.  The subsequent files will NOT be filtered.

Last Visit:
This will display fire files that exceed the time since the last visit in a green color.  This parameter is set in seconds and is defaulted to 60 seconds.

Grid Size:
This is the size in which the data is discretized from the fire files.  Default grid size is set to 500x500.  If there are issues with lag regarding the map interface and number of markers.

Grid Max:
This is the size of the box that bounds the fire values within a grid for discretization of the fire shape.  The grid max size is in meters and will produce a box of this size for bounding the fire shape.  A UI message box will occur indicating that fire points have been detected outside of the grid max.  In this instance, please increase the paramater to allow for the full fire shape to fit.


### Running the software

![Fire Toolbar](https://github.com/swang63/MissionPlanner/blob/Test2/PlanFireToolbar.JPG)

Steps to run the software are below
1) Select the Plan Tab
2) Choose the parmaeters for viewing the fire files.  The default values are shown in the figure above.
3) Click the Toggle Grid button to toggle the maximum grid size of the fire shape.
4) Click the Load Fire Folder Button. This will allow you to select the directory for where the fire files are located.  If files are added to this directory, they will automatically upload and display new information every 30 seconds.
5) Click the Stop Reading button to stop reading new incoming files.

The map displays the inner boundary of the fire shape with a yellow X, the average fire shape value from the last 5 values taken for that angle in a blue shape, and the outer boundary of the fire with a white X.
