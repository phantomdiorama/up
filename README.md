
  _    _
 | |  | |
 | |  | |  _ __
 | |  | | | '_ \
 | |__| | | |_) |
  \____/  | .__/
          | |
          |_|

get up. get on up.

#  setting up debian

## download and install

Download ISO from [aarnet mirror](https://mirror.aarnet.edu.au/pub/debian-cd/current-live/amd64/iso-hybrid/)

### grab essentials

```
# update
sudo apt update && sudo apt upgrade

# utilities
sudo apt install curl git wget thefuck make

# gui stuff
sudo apt install vim-gtk3 vlc timeshift thunderbird audacious
```

## set up

### fzf & z & fuck

```
# run all from
cd ~

# fzf
git clone --depth 1 https://github.com/junegunn/fzf.git ~/.fzf
~/.fzf/install

# z
wget https://raw.githubusercontent.com/rupa/z/master/z.sh
mkdir -p ~/.local/bin && mv z.sh ~/.local/bin/
echo "source ~/.local/bin/z.sh" >> ~/.bashrc

# thefuck -- installed above
echo "eval $(thefuck --alias)" >> ~/.bashrc

# reload bashrc
source ~/.bashrc
```

### keyd

```
git clone -b v2.4.3 https://github.com/rvaiya/keyd.git
cd keyd
make && sudo make install
sudo systemctl enable keyd && sudo systemctl start keyd

# config
wget https://gist.githubusercontent.com/phantomdiorama/dabd52a0899147830cb92257228ba2f0/raw/d93cab30f330ab50d9c03bba6896335f0e4e224f/default.conf
sudo mv default.conf /etc/keyd/default.conf
sudo keyd reload
```

### vim & writing & blog

```
# vim
sudo apt install moreutils wbritish
git clone https://github.com/phantomdiorama/vimfiles.git
mv vimfiles .vim
chmod +x ~/.vim/plugins.sh
~/.vim/plugins.sh

# markdown
sudo apt install pandoc nodejs npm
npm install -g markdownlint-cli
npm install -g pagedjs-cli

## manual install

# images
sudo apt install ffmpeg imagemagick jpegoptim pngquant
```

### network share

```
# install utils
sudo apt install cifs-utils

# make share folder
sudo mkdir /mnt/nas

# mount manually to check
sudo mount -t cifs //Syn/NAS /mnt/nas -o username={REMOTEUSER},password={REMOTEPASS},uid={LOCALUSER}

# then add to /etc/fstab
//Syn/NAS /mnt/nas cifs username={REMOTEUSER},password={REMOTEPASS},uid={LOCALUSER},x-systemd.automount 0 0
```

### firefox

- [Developer Edition](https://www.mozilla.org/en-US/firefox/developer/)
- [uBlock Origin](https://addons.mozilla.org/en-US/firefox/addon/ublock-origin/)
    - [medium blocking mode](https://github.com/gorhill/ublock/wiki/Blocking-mode:-medium-mode)
- [Compact mode](https://support.mozilla.org/en-US/kb/compact-mode-workaround-firefox)
    - browser.compactmode.show = true
- [Prevent Alt invoking menu] (https://support.mozilla.org/en-US/questions/1278533)
    - ui.key.menuAccessKeyFocuses = false

### non apt
- [Dropbox](https://linux.dropbox.com/packages/debian/)
 - [Fade In](https://www.fadeinpro.com/)
 - [Typos](https://github.com/crate-ci/typos/releases)
 - [yt-dlp](https://github.com/yt-dlp/yt-dlp)

### troubleshooting & bugs

- timeshift
    - install `pkexec` if no gui
- usb microphone
    - plug in *after* login if not recognised
- dropbox
    - may need manual install of dependencies and `apt --fix-broken install`


---

shortlink: https://is.gd/mydeb
