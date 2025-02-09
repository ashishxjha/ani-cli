<p align=center>
<br>
<a href="http://makeapullrequest.com"><img src="https://img.shields.io/badge/PRs-welcome-brightgreen.svg"></a>
<img src="https://img.shields.io/badge/os-linux-brightgreen">
<img src="https://img.shields.io/badge/os-mac-brightgreen">
<img src="https://img.shields.io/badge/os-windows-brightgreen">
<img src="https://img.shields.io/badge/os-android-brightgreen">
<br>
<h1 align="center">
<a href="https://matrix.to/#/#ani-cli:matrix.org"><img src="https://element.io/blog/content/images/2020/07/Logomark---white-on-green.png" width="80"></a>
<a href="https://discord.gg/aqu7GpqVmR"><img src="https://pnggrid.com/wp-content/uploads/2021/05/Discord-Logo-Square-1024x1024.png" width="80"></a>
<a href="https://nightly.revolt.chat/invite/4FKHbs78"><img src="https://developers.revolt.chat/img/logo.png" width="80"></a>
<br>
<a href="https://github.com/port19x"><img src="https://img.shields.io/badge/lead-port19x-lightblue"></a>
<a href="https://github.com/CoolnsX"><img src="https://img.shields.io/badge/maintainer-CoolnsX-blue"></a>
<a href="https://github.com/justchokingaround"><img src="https://img.shields.io/badge/maintainer-justchokingaround-blue"></a>
<a href="https://github.com/Derisis13"><img src="https://img.shields.io/badge/maintainer-Derisis13-blue"></a>

</p>

<h3 align="center">
A cli to browse and watch anime (alone AND with friends). This tool scrapes the site <a href="https://animixplay.to/">animixplay.</a>
</h3>
	
<h1 align="center">
	Showcase
</h1>

https://user-images.githubusercontent.com/44473782/160729779-41fe207c-b5aa-4fed-87db-313c83caf6bb.mp4

## Table of Contents

- [Fixing errors](#Fixing-errors)
- [New in v3](#New-in-v3)
- [Install](#Install)
  - [Linux](#Linux)
  - [MacOS](#MacOS)
  - [Windows](#Windows)
  - [Android](#Android)
- [Uninstall](#Uninstall)
- [Dependencies](#Dependencies)
- [Homies](#Homies)
- [Contribution Guidelines](./CONTRIBUTING.md)
- [Disclaimer](./disclaimer.md)

## Fixing errors

If you encounter "Video url not found" or any breaking issue, then make sure you are on latest version by typing
`sudo ani-cli -U` to update on Linux, Mac and Android. On Windows, run gitbash as administrator then there type `ani-cli -U`.
If after this the issue persists then open an issue.
<br>  
If after updating you get a similar error: ` "/usr/bin/ani-cli: line 470: (...)/player_mpv: No such file or directory"` then uninstall and reinstall ani-cli with the installation instructions provided below.

## New in v3
```txt
We now scrape animixplay instead of gogoanime, which allows for faster link fetching as well as getting new 
releases sooner.

New arguments:
-f use fzf for anime selection
-r [1-3] select provider to scrape first
-x print all video links from all providers to stdout (for debugging purpose)

To see a list with all the arguments, use the -h or --help argument
```

For more info on providers, please refer to [this](https://github.com/pystardust/ani-cli/discussions/786) discussion

## Install
# IMPORTANT: Please uninstall ani-cli before proceeding.
#### ani-cli V3.3 has breaking changes and is incompatible with previous versions install location. Please uninstall before proceeding.

### Native packages

[![Packaging status](https://repology.org/badge/vertical-allrepos/ani-cli.svg)](https://repology.org/project/ani-cli/versions)

*Native packages have a more robust update cycle, but sometimes they are slow to upgrade. If the one for your platform is up-to-date we suggest going with it.*

### Linux

Install dependencies [(See below)](#Dependencies)

```sh
sudo rm -rf "/usr/local/share/ani-cli" "/usr/local/bin/ani-cli" "/usr/local/bin/UI" /usr/local/bin/player_* #If some of these aren't found, it's not a problem
git clone "https://github.com/pystardust/ani-cli.git" && cd ./ani-cli
sudo cp ./ani-cli /usr/local/bin
cd .. && rm -rf "./ani-cli"
```
*Also note that mpv installed through flatpak is not compatible*

### MacOS

Install dependencies [(See below)](#Dependencies)

Install [HomeBrew](https://docs.brew.sh/Installation) if not installed.

```sh
rm -rf "$(brew --prefix)/share/ani-cli" "$(brew --prefix)/bin/ani-cli" "$(brew --prefix)/bin/UI" "$(brew --prefix)"/bin/player_* #If some of these aren't found, it's not a problem
git clone "https://github.com/pystardust/ani-cli.git" && cd ./ani-cli
cp ./ani-cli "$(brew --prefix)"/bin 
cd .. && rm -rf ./ani-cli
```

*To install (with Homebrew) the dependencies required on Mac OS, you can run:* 

```sh
brew install curl grep axel openssl@1.1 ffmpeg git && \
brew install --cask iina
``` 
*Why iina and not mpv? Drop-in replacement for mpv for MacOS. Integrates well with OSX UI. Excellent support for M1. Open Source.*  

### Windows

*Make sure git bash is installed [(Install)](https://git-scm.com/download/win)*

*Note that the installation instruction below must be done inside **Git Bash**, not in Command Prompt or Powershell*

```sh
rm -rf "/usr/local/share/ani-cli" "/usr/local/bin/ani-cli" "/usr/local/bin/UI" /usr/local/bin/player_* #If some of these aren't found, it's not a problem
git clone "https://github.com/pystardust/ani-cli.git" && cd ./ani-cli
cp ./ani-cli /usr/bin
cd .. && rm -rf ./ani-cli
```

*Run ani-cli in Git Bash (Running it in cmd or powershell may or may not work)*

### Android

Install termux [(Guide)](https://termux.com/)

```sh
pkg up -y
rm -rf "$PREFIX/share/ani-cli" "$PREFIX/bin/ani-cli" "$PREFIX/bin/UI" "$PREFIX"/local/bin/player_* #If some of these aren't found, it's not a problem
git clone "https://github.com/pystardust/ani-cli.git" && cd ./ani-cli
cp ./ani-cli "$PREFIX"/bin
cd .. && rm -rf ./ani-cli
```

Note : Vlc Android now works too ;)

You need to add any referrer in mpv by opening mpv [(playstore version)](https://play.google.com/store/apps/details?id=is.xyz.mpv), going into Settings -> Advanced -> Edit mpv.conf and adding (for example):

```
referrer="https://animixplay.to/"
```

## Uninstall

* Linux:  
```sh
sudo rm "/usr/local/bin/ani-cli"
```
* Mac:  
```sh
rm "$(brew --prefix)/bin/ani-cli"
```
* Windows:
In **Git Bash** run (as administrator):
```sh
rm "/usr/bin/ani-cli"
```
* Android:  
```sh
rm "$PREFIX/bin/ani-cli"
```

## Dependencies

- grep
- sed
- awk
- curl
- openssl
- mpv - Video Player
- iina - mpv replacement for MacOS
- axel - Download manager
- ffmpeg - m3u8 Downloader
- fzf (optional)

## Homies 

* [animdl](https://github.com/justfoolingaround/animdl): Ridiculously efficient, fast and light-weight (supports most sources: animixplay, 9anime...) (Python)
* [anime-helper-shell](https://github.com/Atreyagaurav/anime-helper-shell): A python shell for searching, watching, and downloading anime (Python)
* [anipy-cli](https://github.com/sdaqo/anipy-cli): ani-cli rewritten in python (Python)
* [dra-cla](https://github.com/CoolnsX/dra-cla): ani-cli equivalent for korean dramas (Shell)
* [kaa.si-cli](https://github.com/Soviena/kaa.si-cli): Stream anime from kaa.si and sync with anilist (Python)
* [lobster](https://github.com/justchokingaround/lobster): Life action movies and series fom the terminal (Shell)
* [manga-cli](https://github.com/7USTIN/manga-cli): Read manga in the cli (Shell)
* [mangal](https://github.com/metafates/mangal): Download & read manga from any source with anilist sync (Go)
* [mov-cli](https://github.com/mov-cli/mov-cli): Watch movies/tv shows in the cli (work in progress) (Python/Shell)
* [saikou](https://github.com/saikou-app/saikou): Best android app for anime/manga with anilist integration (Kotlin)
* [tv-cli](https://github.com/Spaxly/tv-cli): Watch live TV in the cli (Shell)
