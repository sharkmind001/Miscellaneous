# Miscellaneous

## Install batcat
```
sudo apt install bat
```
## create symbolic link to use bat
```
sudo ln -s /usr/bin/batcat /usr/bin/bat
```
## If you want to urn man with bat
```
export MANPAGER="sh -c 'sed -u -e \"s/\\x1B\[[0-9;]*m//g; s/.\\x08//g\" | bat -p -lman'"
```
## Test it
```
man 2 write
```








