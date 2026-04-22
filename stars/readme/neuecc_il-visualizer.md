# Forked

for Visual Studio 2017, remove Non-modal Visualizer.

Built binary is exists in [neuecc/il-visualizer/releases](https://github.com/neuecc/il-visualizer/releases) page.

# IL Visualiser

Originally developed by Haibo Luo in 2005 and posted in a series of blog posts ([part one](https://blogs.msdn.microsoft.com/haibo_luo/2005/10/25/debuggervisualizer-for-dynamicmethod-show-me-the-il/), [part two](https://blogs.msdn.microsoft.com/haibo_luo/2006/11/16/take-two-il-visualizer/)).

Converted to a Git repository and upgraded to Visual Studio 2015 by Drew Noakes

## Usage

When paused in the debugger, select an instance of a subclass of `MethodBase` (such as `DynamicMethod`, `MethodBuilder`, `ConstructorBuilder`, ...) and launch a visualiser:

![](Images/launching-visualizer.png)

### IL Visualizer (Modal)

Selecting _"IL Visualizer"_ pops up a window showing the IL code.

![](Images/il-visualizer.png)

This window is modal and debugging may only continue once the window is closed.

## Installation

(Notes apply to Visual Studio 2015, but are similar for earlier versions)

1. [Download the latest release](https://github.com/drewnoakes/il-visualizer/releases/latest), or build from source

2. Copy `ILDebugging.Decoder.dll` and `ILDebugging.Visualizer.dll` to either

    > %USERPROFILE%\Documents\Visual Studio 2015\Visualizers
    
    or
    
    > _VisualStudioInstallPath_\Common7\Packages\Debugger\Visualizers

3. Restart the debugging session (you don't have to restart Visual Studio)

## Earlier Visual Studio Versions

You can target earlier versions of Visual Studio by updating the assembly references for
`Microsoft.VisualStudio.DebuggerVisualizers.dll` to the relevant version.

## License

THE CODE IS PROVIDED "AS IS", WITH NO WARRANTIES INTENDED OR IMPLIED. USE AT YOUR OWN RISK!