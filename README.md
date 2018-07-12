# Xdebug


## MacOS

In order for Xdebug to work on Docker for MacOS, the container needs a well known IP address
for its Xdebug remote host. To circumvent the Docker installation on MacOS, an additional
alias is required to have a fixed IP address.

This can be either done manually and only persists until a reboot or via a boot persistent
plist script.

### Manual
```bash
sudo ifconfig lo0 alias 10.254.254.254
```

### Boot persistent

##### Install
```bash
sudo curl -o \
  /Library/LaunchDaemons/org.devilbox.docker_10254_alias.plist \
  https://raw.githubusercontent.com/devilbox/xdebug/master/osx/org.devilbox.docker_10254_alias.plist
```
##### Enable without reboots
```bash
sudo launchctl load /Library/LaunchDaemons/org.devilbox.docker_10254_alias.plist
```

### Credits

https://gist.github.com/ralphschindler/535dc5916ccbd06f53c1b0ee5a868c93
