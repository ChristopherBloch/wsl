# Memory/CPU limit settings

turn off all wsl instances such as docker-desktop
-------------------------------------------------

wsl --shutdown

notepad "$env:USERPROFILE/.wslconfig"

Edit .wslconfig file with notepad and write down these settings
-------------------------------------------------
[wsl2]

memory=3GB   # Limits VM memory in WSL 2 up to 3GB

processors=4 # Makes the WSL 2 VM use two virtual processors

move docker data to another disk
-------------------------------------------------
wsl --export docker-desktop-data d:\dockerdata

wsl --unregister docker-desktop-data d:\dockerdata

wsl --import docker-desktop-data d:\volumes\docker-data D:\dockerdata --version 2
