# aiostreams
All In One streams (aiostreams) is a pack of scripts, written in Python, that can be used to stream and watch videos from different online networks, like Twitch.tv and Lbry.tv.

All the scripts should be used from the shell, as well as from any web browser that support execution of scripts. It is really easy to configure a link context menu and open the URL with the script. And if "Autoplay" is enabled, then the video will start automatically using the configured default players.

Some of these networks have a search API, and you can use them to find available streams and videos, without the need to visit the website. This is a fast way to find what you want, without waiting huge amount of Javascript to be executed on your machine. Especially useful when your computer doesn't have the necessary horse power to support those websites.

All the scripts are developed and fully tested under AmigaOS 4.1 FE and MorphOS 3.x. There will be support for other systems in the future, like AmigaOS 3 and AROS, as long as Python is supported. The scripts work just fine under Linux and MacOS X, but those systems are not the target of this project. There are other solutions that might do a better job.

### Supported networks:
* [Twitch.tv](https://www.twitch.tv/)
* [YouTube.com](https://youtube.com/)
* [Vimeo.com](https://vimeo.com/)
* [Dailymotion.com](https://www.dailymotion.com)
* [Skaitv.gr](http://www.skaitv.gr/)
* [Dlive.tv](https://dlive.tv/)
* [PeerTube](https://joinpeertube.org/)
* [Wasd.tv](https://wasd.tv/)
* [Lbry.tv](https://lbry.tv/)

### A full list of requirements per OS:
#### AmigaOS 4.1 [<img src="https://pbs.twimg.com/profile_images/2319157842/lxuzbb11861j2p9e53lt_400x400.png" width="20" height="20">](https://www.amigaos.net/)
* [AmigaOS 4.1 FE upd1][amigaos]
* Python 2.5
* [Pythonssl][pythonssl]
* The Python modules: urllib, urllib2, sys, re, string, random. Usually they are part of the python Installation
* [ffplay][ffmpeg] for the online live streaming videos, or something equivalent
* [mplayer][mplayer] for the online recorded videos, or something equivalent
* internet access

#### MorphOS 3.x [<img src="https://upload.wikimedia.org/wikipedia/commons/6/6d/Morph_os.jpg" width="20" height="20">](https://www.morphos-team.net/)
* MorphOS 3.10 and above
* Python 2.5 and above
* Currently there is no suitable video player available on MorphOS, that could support the necessary streams. As soon as new video players are available, they can be used by aiostreams scripts.
* internet access

#### Windows 7+ [<img src="https://lh3.googleusercontent.com/proxy/GOp9vPBzwlkGTos8vN5s497h9WQgd7h6N9IUYBiuDH5mIUAdatfksDOddcfiRi8yobFyagCQLGequQaeDOmIqoz0djjRPSnShXzuQET-gh5NNqxzChcSFYRSJA" width="20" height="20">](https://www.microsoft.com/)
* Python 2.5
* internet access

#### Linux [<img src="https://i.imgur.com/71FsbfV.png" width="20" height="20">](https://www.linux.org/)
* Python 2.5
* internet access

### Docker for development
This is not necessary for using these scripts. It just provides a good development environment for other systems.
To run the script in a docker container with Python 2.7 installed, use the following on different shells, from the script folder.

```bash
docker run -it --rm --name aiostreams -v "$PWD":/usr/src/myapp -w /usr/src/myapp python:2
```
```bash
docker exec -it aiostreams bash
python twitch.py
```
### Setup on cfg.py
Incase of errors with the player make sure that your cfg.py has the following code that can be found in cfg.py.examples depending on the OS and the Player you want to use. Make sure that the code is pasted at the bottom of the cfg.py file
```bash
# AmigaOS 4.1 FE video players
vPlayer = "APPDIR:mplayer"
vPlayerArgs = "-quiet -really-quiet -forceidx -framedrop -cache 8192"
sPlayer = "APPDIR:ffplay"
sPlayerArgs = "-loglevel quiet -infbuf -skip_loop_filter all -skip_frame noref"

# AmigaOS 4.1 FE audio players
aPlayer = "APPDIR:AmigaAmp3"
aPlayerArgs = ""

# AmigaOS 4.1 FE Emotion player
vPlayer = "APPDIR:emotion"
vPlayerArgs = ""
sPlayer = "APPDIR:emotion"
sPlayerArgs = ""
aPlayer = "APPDIR:emotion"
aPlayerArgs = ""

# MacOS X video players
vPlayer = "~/Applications/VLC.app/Contents/MacOS/VLC"
vPlayerArgs = "-f --no-video-title-show 2> /dev/null"
sPlayer = "~/Applications/VLC.app/Contents/MacOS/VLC"
sPlayerArgs = "-f --no-video-title-show 2> /dev/null"
aPlayer = "~/Applications/VLC.app/Contents/MacOS/VLC"
aPlayerArgs = "-f --no-video-title-show 2> /dev/null"

# Linux VLC player
vPlayer = "/usr/bin/vlc"
vPlayerArgs = "-f --no-video-title-show 2> /dev/null"
sPlayer = "/usr/bin/vlc"
sPlayerArgs = "-f --no-video-title-show 2> /dev/null"
aPlayer = "/usr/bin/vlc"
aPlayerArgs = "-f --no-video-title-show 2> /dev/null"

# Linux MPV player
vPlayer = "/usr/bin/mpv"
vPlayerArgs = "--title='aiostreams' --really-quiet"
sPlayer = "/usr/bin/mpv"
sPlayerArgs = "--title='aiostreams' --really-quiet"
aPlayer = "/usr/bin/mpv"
aPlayerArgs = "--title='aiostreams' --really-quiet"

# Windows 10 VLC player
vPlayer = 'start vlc.exe'
vPlayerArgs = "-f --no-video-title-show"
sPlayer = 'start vlc.exe'
sPlayerArgs = "-f --no-video-title-show"
aPlayer = 'start vlc.exe'
aPlayerArgs = "-f --no-video-title-show"

```

[pythonssl]: http://os4depot.net/?function=showfile&file=library/misc/pythonssl.lha
[ffmpeg]: http://os4depot.net/?function=showfile&file=video/convert/ffmpeg.lha
[mplayer]: http://os4depot.net/index.php?function=search&tool=simple&f_fields=mplayer
[amigaos]: http://amigaos.net
[blog]: https://walkero.gr
