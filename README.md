# WinLIRC Remote Control Script

By Neumann Gregor

# WinLIRC Client
This is the default WinLIRC Client, updated for working with Unicode version of AHK (https://www.autohotkey.com/) and any infrared receiver, I use a serial one, is very easy to build and use.

####Easy to build serial IR receiver
![Schematic](WinLIRC/Schematic1.png)

![Schematic](WinLIRC/Schematic2.gif)

5 parts only !!! The sensor and the parts can easily be scavenged.
*Guide on how to build [HERE](http://web.archive.org/web/20061022051641/lnx.manoweb.com/lirc/?partType=section&partName=introduction).*

## How to install

• Install WinLIRC http://winlirc.sourceforge.net

*Guide on how to configure [HERE](http://winlirc.sourceforge.net/usageguide.html).*

• Install AutoHotKey https://www.autohotkey.com

• Install OBS https://obsproject.com
*set keybinding as :
![KeyBindings1](OBS_REMOTE_SHORTCUTS_1.PNG)
![KeyBindings2](OBS_REMOTE_SHORTCUTS_2.PNG)*

## Usage

• Start WinLIRC (configured already)
• Edit the [WinLirc_OBS.ahk](WinLirc_OBS.ahk)

1. Specify the path to WinLIRC executable and port number if you are using not the default one, the IP is changed if WinLIRC is on another machine that the script.
```autohotkey
; Specify the path to WinLIRC, such as C:\WinLIRC\winlirc.exe
WinLIRC_Path = C:\UTILS\WinLIRC\winlirc.exe

; Specify WinLIRC's address and port. The most common are 127.0.0.1 (localhost) and 8765.
WinLIRC_Address = 127.0.0.1
WinLIRC_Port = 8765
```
2. Specify the path to PotPlayer executable, it is needed for the custom icon in the tray
```autohotkey
; Set icon of script in tray same as OBS
; Set FileName to target the OBS
FileName := "C:\UTILS\Portable OBS\OBSPortable.exe"  
```
3. Now choose what buttons of your remote, i use a Technisat remote see the config file [MyTechnisat.cf](WinLIRC/MyTechnisat.cf), and edit the script

```autohotkey
; --------------------------------------------
; ASSIGN ACTIONS TO THE BUTTONS ON YOUR REMOTE
; --------------------------------------------
; Configure your remote control's buttons below. Use WinLIRC's names
; for the buttons, which can be seen in your WinLIRC config file
; (.cf file) -- or you can press any button on your remote and the
; script will briefly display the button's name in a small window.
; 
; Below are some examples. Feel free to revise or delete them to suit
; your preferences.


RED:
IfWinExist, OBS 24.
{
	Controlsend,,^+{F10},ahk_class Qt5QWindowIcon ; This class name is for OBS Studio.
}
else
{
	guidisp("OBS NOT running",0, 0)
}
return
```

Function diagram:

![Diagram](DiagramOBS.PNG)
