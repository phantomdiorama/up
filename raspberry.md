# raspberry pi

Installed 2024-02-12
Reinstalled 2024-11-16

## get raspbian

- [Install Docs](https://www.raspberrypi.com/documentation/computers/getting-started.html#raspberry-pi-imager)
- [Remote Access Docs](https://www.raspberrypi.com/documentation/computers/remote-access.html)

## get IP address

```
ping raspberrypi.local
# or
ping raspberrypi.lan
```

## essentials

```
# update
sudo apt update && sudo apt upgrade

# install packages
sudo apt install cifs-utils git screen thefuck vim ffmpeg mplayer

# make folder if needed
mkdir -p ~/.local/bin

# fzf
git clone --depth 1 https://github.com/junegunn/fzf.git ~/.fzf
~/.fzf/install

# z
wget https://raw.githubusercontent.com/rupa/z/master/z.sh
mv z.sh ~/.local/bin/

# yt-dlp
wget https://github.com/yt-dlp/yt-dlp/releases/latest/download/yt-dlp -O ~/.local/bin/yt-dlp
chmod a+rx ~/.local/bin/yt-dlp
```

## network share

```
# make share folder
sudo mkdir /mnt/nas

# add to /etc/fstab
//{REMOTE}/{SHARE} /mnt/nas cifs username={USER},password={PASS},uid=pi 0 0

# copy over dot files
cp something somewhere
```

## non-apt

- [Fail2ban](https://pimylifeup.com/raspberry-pi-fail2ban/)

## usb soundcard

- raspi-config > general > audio device

