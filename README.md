# Botbertd Package

This is an arch linux package for the botbert discord bot for convinent install

have fun using, and use at your own risk!

## installation

```bash
makepkg
```

## usage

to start the app run the following command

```bash
botbertd
```

the program looks for the DISCORD\_TOKEN environment variable
for it's connection to discord, make sure that it is set before running
or your going to get errors!

additionally the package installs a botbertd.service file that gets it's environment
variables from /etc/botbertd/env.txt

set the discord token in that file and you should be able to run the app using standard
systemd commands

```bash
systemctl start botbertd #start

systemctl enable botbertd #set on startup

systemctl stop botbertd # stop botbert from running

systemctl disable botbertd #unset on startup
```
