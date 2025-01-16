# Miscellaneous

## Install batcat
```
sudo apt install bat
```
## create symbolic link to use bat
```
sudo ln -s /usr/bin/batcat /usr/bin/bat
```
## You can open your file with bat command
```
bat program.py
```
## If you want to turn man with bat
```
export MANPAGER="sh -c 'sed -u -e \"s/\\x1B\[[0-9;]*m//g; s/.\\x08//g\" | bat -p -lman'"
```
## Test it
```
man 2 write
```








