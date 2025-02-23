# up :balloon:

## get debian

Download ISO from
[aarnet mirror](https://mirror.aarnet.edu.au/pub/debian-cd/current-live/amd64/iso-hybrid/)

## essentials

```
# update
sudo apt update && sudo apt upgrade

# install packages
cifs-utils curl git make thefuck thunderbird timeshift

# fzf
git clone --depth 1 https://github.com/junegunn/fzf.git ~/.fzf
~/.fzf/install

# z
wget https://raw.githubusercontent.com/rupa/z/master/z.sh
mv z.sh ~/.local/bin
echo "source ~/.local/bin/z.sh" >> ~/.bashrc

# keyd

git clone -b v2.4.3 https://github.com/rvaiya/keyd.git
cd keyd
make && sudo make install
sudo systemctl enable keyd && sudo systemctl start keyd

## config
wget https://raw.githubusercontent.com/phantomdiorama/up/refs/heads/main/default.conf
sudo mv default.conf /etc/keyd/default.conf
sudo keyd reload
```

## network share

```
# make share folder.
sudo mkdir /mnt/nas

# mount manually to check
sudo mount -t cifs //Syn/NAS /mnt/nas -o username={REMOTEUSER},password={REMOTEPASS},uid={LOCALUSER}

# then add to /etc/fstab
//Syn/NAS /mnt/nas cifs username={REMOTEUSER},password={REMOTEPASS},uid={LOCALUSER},x-systemd.automount 0 0
```

## non-apt

- [dropbox](https://linux.dropbox.com/packages/debian/)
    - might need `apt --fix-broken install`

## next

- [Look and Feel](lookfeel.md)
- [Multimedia](media.md)
- [Programming and blog](progblog.md)
- [Raspberry Pi setup](raspberry.md)
