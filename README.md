
## Table of Contents

- [Workflow 🖨️](#workflow)
- [Keybinds ✍️](#keybinds)
- [Installation 🤵‍](#inst)
  - [Arch Install 🌇](#arch)
  - [Other Install 🚂](#other)
- [Dependencies 📊](#deps)
- [Troubleshooting 🔫](#trouble)

<a id="about"></a>


<a id="gal"></a>
<img src='/screenshots/modified.png'>

<a id="workflow"></a>

## Workflow 🖨️

<p align="center">
  <img src="https://github.com/Axarva/gifs/blob/main/workflow.gif">
</p>

<a id="keybinds"></a>
## Keybinds ✍️

These are the basic keybinds. Read through the `xmonad/xmonad.hs` file for more keybinds like increasing gaps and restoring gaps.

|        Keybind         |                 Function                 |
| ---------------------- | ---------------------------------------- |
| `Win + Shift + Enter`  | Launch terminal (alacritty)              |
| `Win + Shift + C`      | Close window                             |
| `Win + O`              | Open rofi menu                           |
| `Win + Shift + Q`      | Open rofi powermenu                      |
| `Win + S`              | Open sidebar                             |
| `Win + Shift + S`      | Close sidebar                            |
| `Win + P`              | Open dashboard                           |
| `Win + Shift + P`      | Close dashboard                          |
| `Win + B`              | Toggle the main bars                     |
| `Win + Z`              | Activate inhibitor (Stops autolocking)   |
| `Win + Shift + Z`      | Dectivate inhibitor (Enables autolocking)|
| `Win + Ctrl + G`       | Toggle gaps (toggle to get screen space) |
| `Win + J`              | Navigate through windows                 |
| `Win + K`              | Navigate through windows                 |
| `Win + Space`          | Switch through layouts                   |
| `Win + T`              | Make a floating window tiled             |

Note: `Toggling` means to enable if inactive or to disable if active.


Note: `Win` refers to the `Super` key.


<a id="inst"></a>
## Installation 🤵‍
Alright, let's get to the main stuff.


Note: Whatever method you follow, if you want the weather and quote features to work as well, you need to modify your crontab as follows: <br>
(To edit your crontab, `crontab -e` as a normal user.)



```
0,30 * * * * /home/{Your-username}/.config/eww/scripts/getweather
@reboot /home/{Your-username}/.config/eww/scripts/getquotes
```


And please follow these next few steps as well:
- Add `export PATH="$PATH:$HOME/bin"` to your `~/.bashrc` file (or a shell of your choice).
- Edit the script in `~/.config/eww/scripts/getweather`. Further steps are specified within that file.
- Open `tint2conf` and edit the theme `panellauncher.tint2rc`. In there, head over to the `Launcher` tab and set the icon theme as candy-icons.
- Get the Museo Sans 300 (ONLY THE 300 WEIGHT PLEASE, OTHERS LOOK WEIRD) font from Adobe itself or any other sources, put the `.ttf` or `.otf` file in your `~/.local/share/fonts`
  - Run `fc-cache -f` after getting the font.
- If the widgets don't work properly, go to [the main repository](https://github.com/elkowar/eww) and install `eww` as documented. Make sure the resulting binary is stored in `~/bin`.
- Issue `xmonad --recompile` after you complete all the steps, and relogin to xmonad.
- For the profile picture to load, it needs to have the full path in `eww.scss`. Open the file, search for the string containing `~/.config`(line number 329 to be exact) and edit it to point it to your image. Full path required. For example: `$HOME/path/to/image.png`.

<a id="arch"></a>

### For Arch Linux and it's derivatives (make sure you have git installed): 🌇
**Piece of good advice**: Since you are on an Arch-based distro, it is likely you use `systemd`. In case you don't, go ahead and ignore this and skip to [Going Ahead: Arch Edition](#ga-arch).


In case you do, I recommend opening this repository in a text editor after you clone it, and global-replace the stuff specified in [Stuff for sysd users](#sysd-replace). After that, go ahead with [Going Ahead: Arch Edition](#ga-arch).


<a id="ga-arch"></a>

#### Going Ahead: Arch Edition 

Note: THIS MAKES BACKUPS TOO, SO YEAH. JUST DO IT. DO IT!


```bash
$ git clone https://github.com/Axarva/dotfiles-2.0.git
$ cd ./dotfiles-2.0
$ chmod +x ./install-on-arch.sh
$ ./install-on-arch.sh
```



That'll do the basic stuff. For a complete kang (kang means copying, don't mind my jargon), look at the list of dependencies below.

AND DON'T FORGET TO READ WHAT'S WRITTEN AT THE END OF THE MAIN INSTALLATION SECTION [UP THERE](#inst). Further steps are specified there. (Yes. Absolutely needs to be shouty capitals.)



<a id="deps"></a>
## Dependencies 📊
Ahhhhh the other main stuff. Here you go, peeps. Make sure you have em all.



-    xmonad (OF COURSE, DUH)
-    eww (ElKowar's Wacky Widgets, binary included, but I encourage you to build it yourself and put the binary in your ~/bin). [Link](https://github.com/elkowar/eww)
-    firefox (Yup)
-    rofi version 1.7.0 (Configs originally come from @adi1090x, been edited by me).
-    tint2 (Please use [this fork](https://github.com/Axarva/tint2-1) ONLY, or issues will occur. Binaries provided already.)
-    acpi
-    Museo Sans Font by Adobe (I think it needs some sort of acount, but get it) Or just search for it on the web and get it somewhere
-    Nerd Font. I include some, but you can use any of your choice. [Link](https://github.com/ryanoasis/nerd-fonts/tree/master/patched-fonts/Iosevka) 
-    playerctl
-    brightnessctl. [Link](https://github.com/Hummer12007/brightnessctl)
-    candy-icons. [Link](https://github.com/EliverLara/candy-icons)
-    dunst
-    Spotify (for cover art, else edit the eww/scripts/getart script accordingly)
-    An OpenWeatherMap Account, (view eww/scripts/getweather script for more info)
-    feh
-    NetworkManager
-    greenclip
-    alacritty
-    picom (fork of ibhagwan or jonaburg)
-    jq: Command line json parser (Needed for widgets)
-    maim and xclip for screenshots
-    mpv for low-battery sound playing (Not exactly necessary, you'll get the notification, but the sound depends on it.)
-    *Might need to be updated, so please tell me*

<a id="trouble"></a>
## Troubleshooting 🔫
And here we are:


1. If xmonad doesn't build make sure you have `xmonad-contrib`
2. Bar looks weird: Try editing it a bit using `~/bin/tint2conf`. 
3. Alacritty configs are faulty: I'm not sure about this one, works perfectly fine for me. 
4. Widgets positioning weird: I hardcoded them for a 1366x768 screen, will create others if I can
5. Fonts: GET THOSE FONTS!
6. **MAKE SURE YOUR `~/bin` DIRECTORY IS IN YOUR PATH, OR NOTHING WILL WORK!** (Yes. Absolutely needs to be shouty capitals.)
7. Anything else? Open up an issue.
8. ~~Workspace indicator bar lost colors: This has a very long explanation, but the fix is as follows:~~
   - ~~Open up the `~/.config/tint2/workspaces.tint2rc` file, and scroll down to the taskbar module at around line 120~~
   - ~~Add this line in that block: `taskbar_name_unoccupied_font_color = #ffd5cd 100`~~
   - ~~Save the file, and refresh the bar with hitting the keybind `Win + B` twice.~~
   - ~~Remember not to edit that particular file with `tint2conf`, or you'll have to do this again!~~
9. The workspace indicator bar issue has been solved through the binaries in my fork.
10. For instructions regarding use on VirtualMachine, please do check the `VM` folder of this repository.
   
   
<h1 align="center">🌟 Good Luck and Cheers! 🌟</h1>
