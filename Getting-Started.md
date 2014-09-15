# Prerequisites

 > **Note:** This information is only for **developers** who want to get started with the source code. If you are a user of HearthstoneTracker looking for support, visit [hearthstonetracker.com](http://hearthstonetracker.com).

 * Microsoft Visual Studio 2013 (If you use 'Visual Studio for Desktop', also install 'Visual Studio for Web' for needed binaries).
 * .NET framework >= 4.5
 * Latest NuGet Addon installed in Visual Studio

Optional:

 * [NSIS (Nullsoft Scriptable Install System)](http://nsis.sourceforge.net) (only used for building an installer when releasing a new version)

# Getting started
Clone the git repository:

 `git clone https://github.com/HearthstoneTracker/HearthstoneTracker.git`

Open **'HearthCap.sln'** in Visual Studio. It contains all projects and you will use this solution file if building from within Visual Studio.

Alternatively, you can run a debug or release build by executing builddebug.cmd or buildrelease.cmd. There is also a 'makeinstaller.cmd', but this is only used for releasing a new version (it also requires NSIS installed).

# More information

You can find a description of the folders and files in the root folder below. More documentation can be found in other wiki pages.

 * [[Frameworks and architecture|Frameworks and architecture]]

# Root folder structure

A description of most folders and files in the root of the repository.

Name|Description
---|---
[.build](https://github.com/HearthstoneTracker/HearthstoneTracker/tree/master/.build)|contains build files (for now, only msbuild community tasks)
[.nuget](https://github.com/HearthstoneTracker/HearthstoneTracker/tree/master/.nuget)|NuGet configuration and dependencies
[Capture](https://github.com/HearthstoneTracker/HearthstoneTracker/tree/master/Capture)|Direct3D hook
[doc](https://github.com/HearthstoneTracker/HearthstoneTracker/tree/master/doc)|some documentation
[HearthCap](https://github.com/HearthstoneTracker/HearthstoneTracker/tree/master/HearthCap)|Main application / user interface (views/viewmodels, startup code, etc.)
[HearthCap.Core](https://github.com/HearthstoneTracker/HearthstoneTracker/tree/master/HearthCap.Core)|Hearthstone tracking logic (engines, game events, image utils)
[HearthCap.Data](https://github.com/HearthstoneTracker/HearthstoneTracker/tree/master/HearthCap.Data)|Data model (entities, database context, entityframework migrations, etc.)
[HearthCap.Updater](https://github.com/HearthstoneTracker/HearthstoneTracker/tree/master/HearthCap.Updater)|Simple winforms updater, to allow self-updating of main application.
[installer](https://github.com/HearthstoneTracker/HearthstoneTracker/tree/master/installer)|NSIS installer scripts
[lib](https://github.com/HearthstoneTracker/HearthstoneTracker/tree/master/lib)|3rd party libraries not managed by NuGet
[package](https://github.com/HearthstoneTracker/HearthstoneTracker/tree/master/package)|Output folder of release build and NSIS installer script
[packages](https://github.com/HearthstoneTracker/HearthstoneTracker/tree/master/packages)|NuGet packages folder
[PHash](https://github.com/HearthstoneTracker/HearthstoneTracker/tree/master/PHash)|PHash algorithm interface
[PHash.AForge](https://github.com/HearthstoneTracker/HearthstoneTracker/tree/master/PHash.AForge)|PHash algorithm implementation using Aforge.Imaging library
[.gitignore](https://github.com/HearthstoneTracker/HearthstoneTracker/tree/master/.gitignore)|files git should ignore
[Build.proj](https://github.com/HearthstoneTracker/HearthstoneTracker/tree/master/Build.proj)|Used by MSbuild community tasks (I think)
[builddebug.cmd](https://github.com/HearthstoneTracker/HearthstoneTracker/tree/master/builddebug.cmd)|run a 'Debug' build
[buildrelease.cmd](https://github.com/HearthstoneTracker/HearthstoneTracker/tree/master/buildrelease.cmd)|run a 'Release' build (note: also increases version number)
[HearthCap.sln](https://github.com/HearthstoneTracker/HearthstoneTracker/tree/master/HearthCap.sln)|Visual Studio 2013 solution file
[HearthCap.sln.DotSettings](https://github.com/HearthstoneTracker/HearthstoneTracker/tree/master/HearthCap.sln.DotSettings)|Resharper settings file
[LICENSE.txt](https://github.com/HearthstoneTracker/HearthstoneTracker/tree/master/LICENSE.txt)|HearthstoneTracker license
[makeinstaller.cmd](https://github.com/HearthstoneTracker/HearthstoneTracker/tree/master/makeinstaller.cmd)|Run a release build, then run NSIS to build the installer.
[README.md](https://github.com/HearthstoneTracker/HearthstoneTracker/tree/master/README.md)|Readme for github project page