# InterfaceLIFT-Wallpaper-Changer

A GUI-Tool that changes your wallpaper and is able to download fresh wallpapers from <http://interfacelift.com>.
Written in Python.

Please consider donating to InterfaceLIFT to keep their awesome website going!

Parts of the script are based on [``interfacelift-downloader`` by benjaminheng](https://github.com/benjaminheng/interfacelift-downloader).

## What does it do?

On startup, the application checks for new wallpapers on <http://interfaclift.com>. If it finds some that were not downloaded
previously, the user will be asked whether he likes the images or not.

![alt text](https://github.com/Chritzel/interfacelift-wallpaper-changer/raw/master/img/likedislike.png "Like or dislike")

The selected images will then be downloaded in the full resolution. All other images will be put on a blacklist, so not
to download them again.

![alt text](https://github.com/Chritzel/interfacelift-wallpaper-changer/raw/master/img/progress.png "Downloading images")
  
After downloading, the latest image will be set as the current desktop background. It will stay that way until either
- A newer wallpaper has been downloaded
- The user selects to set a random wallpaper from the tray window (see below)
- The "fresh"-period of the latest wallpaper has passed, so a random wallpaper will be selected (see section 
[Configuration File](#configuration-file)) for more information on this behaviour. This will be checked on start of the application.

![alt text](https://github.com/Chritzel/interfacelift-wallpaper-changer/raw/master/img/traywindow.png "Tray window")

From the tray, the user can select to manually check for new images, to change the wallpaper to a random wallpaper out 
of the downloaded ones. Additionally he can check out the interfacelift-page of the currently selected wallpaper by 
clicking on it.

## Requirements

You will need a working version of Python 3. (Not sure if it needs to be greater than 3.5 or something)

> __Mac OSX:__ Make sure you installed the ssl-certificates with Python by executing the command-file after installation.

## Installation

In your desired working folder, using your favorite terminal, do:
```bash
git clone https://github.com/Chritzel/interfacelift-wallpaper-changer.git
cd interfacelift-wallpaper-changer
```

__Important:__ Before installing the package, you should next modify the configuration file `interfacelift_wallpaper_changer/config.yaml`
to your wishes. See section [Configuration File](#configuration-file) for more details on the available options.

After editing the configuration file (especially the locations of the wallpapers and thumbnails), you can permanently install the script.
```
pip3 install --user .
```

The setup will install all requirements for the package. You can then simply call the package using

```
interfacelift-wallpaper-changer
```

from anywhere you want.

### Autostart on Boot

I wrote this software to autostart on boot with my PC, so that I am always up to date with the latest wallpaper. 
Here are ways of how you can accomplish this on Windows and Ubuntu.

To do...

## Configuration File

There is a configuration file at `interfacelift_wallpaper_changer/config.yaml`. The following options are currently available:

| Option  | Default value | Description  |
| ------- | ------------- | ------------ |
| `imageFolder` | `./wallpapers` | Directory where all full-size wallpapers will be stored. It is advisable to use an absolute path, since the relative path will be relative to the current working directory. |
| `thumbnailFolder` | `./thumbs` | Directory where all wallpaper-thumbnails will be stored. This should also be an absolute path. This directory will also contain a file named `wallpaper_info.dat`, which stores information about all downloaded wallpapers. |
| `freshDays` | 2 | How many days a wallpaper is considered "fresh" for. If the latest wallpaper is older than this amount of days, the application will select a random wallpaper on startup, instead of the latest one. The thought behind this is to always keep your wallpaper fresh! |
| `loadPages` | 1 | How many pages to load on an update (for example on startup). This should only be greater than one a) when the script is executed for the first time, and the user wants to download more than the wallpapers on the first page of interfacelift, or b), if the application only updates very irregularly, and the user thus might be in risk of missing some wallpapers. Be aware that increasing this setting leads to longer update and startup times! | 

If the configuration file should be changed after the application was install using `python setup.py install`, simply 
run this command again to update the configuration used.

## Open Points / Ideas

- Bugfixes? If you find any, please write an issue.
- Multi-Screen-Support
- Overview of disliked wallpapers, in case you decide you do want some of those back.
- Implement an interface to the Interfacelift-Media-RSS
- Add an option to check for new wallpapers on regular intervals.