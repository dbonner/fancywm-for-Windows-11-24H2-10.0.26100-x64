# FancyWM

This is a slightlly modified FancyWM fork, which has some minor modificatios for Windows 11 24H2 x64 (version 10.0.26100.0).

I noted that there is a FancyWM startup message stating that FancyWM is not compatible with my Windows 11 version (24H2).

I also noticed that FancyWM crashed a couple of times when I used it with Windows 11 24H2.

I have no great C Sharp or .NET skills. I ended up using Visual Studio 2022's GUI to make all the changes to the code.

I modified the properties of the projects contained in FancyWM.sln so that the target OS and .NET8 versions became Windows 11 24H2 (10.0.26100.0).

I also updated most of the NuGet packages. The NuGet packages that I did not update were: "Hardcodet.NotifyIcon.Wpf.NetCore (left at version 1.0.18)" and "Microsoft.Windows.CsWin32 (left at version 0.1.422-beta)". The app did not start properly if these NuGet packages were updated.

The whole process is summarised as follows:

In Visual Studio 2022:
  Open FancyWM.sln
  Set build to Release and x64.
	For each of the following 5 project names in Solution Explorer: 

	1. FancyWM
		 Properties:
		 	Change both "Target OS version" and "Supported OS version" to:
		 		10.0.26100.0

	2. FancyWM.Package
		Properties:
		 	Change both "Target version" and "Min version" to:
		 		Windows 10, version 24H2 (10.0; Build 26100)

	3. FancyWM.Tests
		 Properties:
		 	Change both "Target OS version" and "Supported OS version" to:
		 		10.0.26100.0

	4. ModernWpf
		Properties:
		 	Change both "Target frameworks" to:
		 		net8.0-windows10.0.26100.0

	5. WinMan.Windows
    Properties:
		 	Change both "Target OS version" and "Supported OS version" to:
		 		10.0.26100.0

	Right click the root of the Solution Explorer tree ["Solution 'ModernWpf' (16 of 16 projects)"] and select "Manage NuGet packages for Solution".
		Update all NuGet packages except:
			Hardcodet.NotifyIcon.Wpf.NetCore (leave at version 1.0.18)
			Microsoft.Windows.CsWin32 (leave at version 0.1.422-beta)

I'm not sure if I have usefully improved the experience or stability of FancyWM on Windows 11 24H2.
If my FancyWM fork is at all useful, all credit goes to the FancyWM dev: Vesko Karaganev (@veselink1).
Daniel (@dbonner)

[![Gitter](https://badges.gitter.im/FancyWM/community.svg)](https://gitter.im/FancyWM/community?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge)

FancyWM is a dynamic tiling window manager for Windows 10/11

<img align="right" src="https://store-images.s-microsoft.com/image/apps.53415.14517052119257390.d950e654-2004-4878-b902-94902f8f7a45.af24879e-636a-494c-ba1d-6ff7f858630b?background=transparent&w=175&h=175&format=jpg">

☑ Create dynamic tiling layouts with mouse or keyboard <br>
☑ Move window focus with keyboard ([⇧ Shift] + [⊞ Win], then [→]) <br>
☑ Swap windows with keyboard ([⇧ Shift] + [⊞ Win], then [⇧ Shift] + [→]) <br>
☑ Swap windows with mouse (hold [⇧ Shift] while dragging) <br>
☑ Horizontal panels ([⇧ Shift] + [⊞ Win], then [H]) <br>
☑ Vertical panels ([⇧ Shift] + [⊞ Win], then [V]) <br>
☑ Stack panels (tabbed layouts) ([⇧ Shift] + [⊞ Win], then [S]) <br>
☑ Panel embedding <br>
☑ Jump to virtual desktop ([⇧ Shift] + [⊞ Win], then [2]) <br>
☑ Move focused window to virtual desktop ([⇧ Shift] + [⊞ Win], then [⇧ Shift] + [2]) <br>
☑ Floating window mode ([⇧ Shift] + [⊞ Win], then [F] or rule-based) <br>
☑ Auto-float windows which cannot fit <br>
☑ Customizable keybindings <br>
☑ Support for multiple monitors <br>
☑ Support for virtual desktops <br>
☑ Allows window maximization <br>
☑ Toggle tiling on/off ([⇧ Shift] + [⊞ Win], then [F11]) <br>
☑ Low CPU usage (<1%) <br>
☑ Disable animations for longer battery life <br>
☑ Windows open in focused panel <br>
☑ Remap activation hotkey to [⇧ Shift] + [⊞ Win], [Ctrl] + [⊞ Win] or [Alt] + [⊞ Win] <br>

FancyWM uses [⇧ Shift] + [⊞ Win] as the start of a command sequence (Activation hotkey). To start a command sequence, press and release these keys simultaneously, then follow up by pressing one of the keybindings you have configured in the settings.

FancyWM only manages restored (not minimized, not maximized) top-level application windows, so it doesn't interfere with popups, and still allows you to use all of your available display area for when you need to focus on a window

## [Downloads](https://github.com/FancyWM/fancywm/releases)

Pre-built binaries can be downloaded from [Releases](https://github.com/FancyWM/fancywm/releases).

These are built by an automated GitHub Action and you can see all of the [build steps](https://github.com/FancyWM/fancywm/blob/main/.github/workflows/dotnet-desktop.yml) and [previous runs](https://github.com/FancyWM/fancywm/actions/workflows/dotnet-desktop.yml).

### Install via winget
```powershell
winget install fancywm
```

### Install from the Microsoft Store

<a href='//www.microsoft.com/store/apps/9p1741lkhqs9?cid=storebadge&ocid=badge'><img src='https://developer.microsoft.com/store/badges/images/English_get-it-from-MS.png' alt='English badge' width="138" height="50"/></a>

### Install .msixbundle (not recommended)
You can test the Microsoft Store packages by installing them using PowerShell.

#### PowerShell (as Administrator)
```powershell
certutil.exe -addstore TrustedPeople .\FancyWM.Package_1.0.0.0.x64.cer
Add-AppxPackage -Path .\FancyWM.Package_1.0.0.0.x64.msixbundle
```

## [User's Guide](https://github.com/FancyWM/fancywm/wiki#users-guide)
Head over to the [Wiki](https://github.com/FancyWM/fancywm/wiki).

## [Issues](https://github.com/FancyWM/fancywm/issues)
Please, take the time to report any problems you experience by:
- Opening an issue on https://github.com/veselink1/fancywm/issues (feature requests also welcome)
In case of crashes, please also remember to save and attach the log file produced by the application.

## Building from source

Clone this repo, including submodules.

```bash
git clone --recursive https://github.com/FancyWM/fancywm.git
```

Open the .sln file with Visual Studio 2022 and build the FancyWM project.

## WinMan & WinMan.Windows
FancyWM is based on [WinMan](https://github.com/veselink1/winman) and [WinMan.Windows](https://github.com/veselink1/winman-windows).

## Screenshots
<img src="https://store-images.s-microsoft.com/image/apps.47394.14517052119257390.5224238b-c5af-4852-a39a-2732c3935e69.60fa12a6-ac5a-47cb-9501-2ca7964d972d?w=1280&h=720&q=90&mode=letterbox&format=jpg" width="640">
Light theme, Vertical panel on the left

---

<img src="https://store-images.s-microsoft.com/image/apps.11856.14517052119257390.5224238b-c5af-4852-a39a-2732c3935e69.81bfbc4c-0b20-4b1e-a1b5-b8e6fa13f8a6?w=1280&h=720&q=90&mode=letterbox&format=jpg" width="640">
Dark theme, Vertical panel on the left, Stack panel with 3 VS Code windows on the right

---

<img src="https://store-images.s-microsoft.com/image/apps.11856.14517052119257390.5224238b-c5af-4852-a39a-2732c3935e69.81bfbc4c-0b20-4b1e-a1b5-b8e6fa13f8a6?w=1280&h=720&q=90&mode=letterbox&format=jpg" width="640">
Vertical panel on the left, Edge in the middle, Vertical panel on the right

---
