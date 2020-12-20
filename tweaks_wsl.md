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
