
### get debian

Download ISO from [aarnet mirror](https://mirror.aarnet.edu.au/pub/debian-cd/current-live/amd64/iso-hybrid/)

### install essentials

```
# update
sudo apt update && sudo apt upgrade

# utilities
sudo apt install curl git wget thefuck make ffmpeg

# gui stuff
sudo apt install vim-gtk3 vlc timeshift thunderbird audacious
```

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
wget https://raw.githubusercontent.com/phantomdiorama/up/refs/heads/main/default.conf
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

# writing and blogging
sudo apt install pandoc jpegoptim pngquant nodejs npm
npm install -g markdownlint-cli
npm install -g pagedjs-cli
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
- [Prevent Alt invoking menu](https://support.mozilla.org/en-US/questions/1278533)
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

