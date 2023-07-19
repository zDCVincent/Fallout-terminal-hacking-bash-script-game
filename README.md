# Fallout-terminal-hacking-bash-script-game
A recreation of the fallout terminal in bash script. Happy birthday to my girlfriend!

I have no ownership over any items in the Fallout franchise and should this be requested to be taken down it will be.
All items in this repository can be used by anyone. No need to credit. To be noted that I took words used in the game from dictionary.com, fallout, and a pre-existing C# script made by u/JoshusB.
This script was made as a birthday gift to my girlfriend who loves fallout and specifically terminal hacking. Gonna marry her soon.

To run this bash script I recommend opening the fallouthackterm.sh file using gitbash to play.
If you want to use the same terminal as I did and are on windows/linux/mac. I used Cool-Retro-Term.

Setup that I used for Cool-Retro-Term for windows users (edited version of this guide:https://gist.github.com/h3r/2d5dcb2f64cf34b6f7fdad85c57c1a45) and this guide (https://tvc-16.science/cool-retro-term-wsl2.html) Credits to "Specifics" https://gist.github.com/specifics for his comment that helped grease the gears.
1. Enable the windows "Developer mode"
2. Run Powershell as administator and run:
Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux
3. Install a distro of your choice. I used Ubuntu. (Try 20.04.6 LTS if you need compatibility with qt5)
4. Install Windows Subsystem for Linux (WSL)
5. Run your distro terminal environment and make your username and pasword.
6. Exit and run WSL (WIN+R, then "wsl", then "OK")
7. Once WSL terminal is loaded run the following commands (Use CTRL+SHIFT+V to paste... I had to manually type it all the first time cause I didn't know this...)
cd /mnt/c/users/YOURWINDOWSUSERNAMEHERE
sudo apt-get install git
sudo apt-get update
sudo apt-get upgrade
sudo apt install build-essential qmlscene qt5-qmake qtbase5-dev qtchooser qt5-qmake qtbase5-dev-tools qtdeclarative5-dev qml-module-qtquick-controls2 qml-module-qtgraphicaleffects qml-module-qtquick-dialogs qml-module-qtquick-localstorage qml-module-qtquick-window2 qml-module-qt-labs-settings qml-module-qt-labs-folderlistmodel qtquickcontrols2-5-dev
strip --remove-section=.note.ABI-tag /usr/lib/x86_64-linux-gnu/libQt5Core.so.5
sudo apt install libfuse2         (or sudo apt-get install fuse libfuse2 for ubuntu < 22.04)
wget https://github.com/Swordfish90/cool-retro-term/releases/download/1.1.1/Cool-Retro-Term-1.1.1-x86_64.AppImage
chmod a+x Cool-Retro-Term-1.1.1-x86_64.AppImage
./Cool-Retro-Term-1.1.1-x86_64.AppImage
(inside the cool-retro-terminal)
cd /mnt/c/users/YOURWINDOWSUSERNAMEHERE/WHEREYOUPLACEDTHEFILE (desktop... downloads)

In the future to run this terminal again,
win+r, wsl, OK
cd /mnt/c/users/YOURWINDOWSUSERNAMEHERE
ls
./Cool-Retro-Term-1.1.1-x86_64.AppImage

For a quick start shortcut tutorial for the lazies like me:
https://tvc-16.science/cool-retro-term-wsl2.html
(Near bottom of the blog)

start /min wsl -d ubuntu [folder where you saved the appimage]/Cool-Retro-Term-1.1.1-x86_64.AppImage 
