- ~~In `$HOME/.Xdefaults` `URxvt.geometry: 400x400` to fix terminal prompt spawning in the middle of the screen.~~
	- This messes up floating terminal size, making it larger than the screen for some reason, so instead `clear` in `.bashrc`.
- For [zapret](https://github.com/bol-van/zapret), [source](https://btt.community/t/linux-zapret-kurulum-rehberi/15989):
  ```bash
  # install dnscrypt-proxy
  sudo ./install_bin.sh
  sudo ./blockcheck.sh
  sudo ./install_easy.sh # <- replace necessary arguments here, e.g. change mode to nfqws and update with blockcheck's args.
	# NFQWS_OPT="--dpi-desync=fakeddisorder --dpi-desync-ttl=1 --dpi-desync-autottl=5 --dpi-desync-split-pos=1" # works now
  ```
- Setting up Python virtual environment:
  ```
  python -m venv envname
  source envname/bin/activate
  deactivate
  ```
- `noto-fonts-cjk` for Japanese characters, `noto-fonts-emoji` for emoji, not that that really matters.
-  ~~`rclone config` into Google Drive connection, setting root folder is done in advanced config when prompted.~~
	-  ~~`rclone ls mylogs_gd:` to check if successful.~~
	-  ~~`rclone mount mylogs_gd: ~/mylogs_local --daemon` to mount locally.~~
	-  ~~`export VISUAL=nano; crontab -e` to add a cronjob to re-mount on reboot: `@reboot rclone mount mylogs_gd: ~/mylogs_local --daemon`.~~
	- opted to go back to Dropbox due to entry lag, as well as some writing permission errors and file duplication.
- `pulseaudio` and `pavucontrol` for audio controls, although, possibly simply changing volumeicon's device might help?
	- actually `manjaro-pipewire` which replaces `pulseaudio`, which lets me use airpods directly. has to `forget device` from iphone, first.
- `sudo systemctl enable bluetooth.service` for bluetooth, `blueman-applet` for its usage.
- built-in `np-applet` seems to be more than capable of wi-fi and of course wired connections. 
- `timeshift` for back-ups, of course.
- `xprop | grep WM_CLASS | awk '{ print $4 }'` for class grabbing of anything.
- `ip addr` to get correct network interface for network module of `polybar`.
- `ibus` and `ibus-kkc` for Japanese input, couldn't compile `ibus-mozc`, unfortunately.
	- `ibus-daemon` for ongoing usage. `ibus-setup` for changing up keys and layouts, etc.
	- `ibus-pinyin` for Chinese input.
- Install `proton-vpn-gtk-app` for `protonvpn-app`.
- Dump manually* installed packages using `pacman -Qqe | grep -v "$(awk '{print $1}' /desktopfs-pkgs.txt)" > ~/dump.txt`
  - Checking both the following, it seems to be pretty much capable of dumping both default and AUR packages:
	  - `comm -12 <(grep -Poe '\[ALPM\] installed \K\S*' /var/log/pacman.log | sort | uniq) <(pacman -Qeqn | sort)`
		- `comm -12 <(grep -Poe '\[ALPM\] installed \K\S*' /var/log/pacman.log | sort | uniq) <(pacman -Qeqm | sort)`
		- Only exeptions seem to be noto-fonts mentioned above, as well as CPU driver related packages.
- `vnstat` to keep tabs on network usage. `vnstatd` for daemon, `vnstati` for image output.
  - `sudo EDITOR=/usr/bin/nano crontab -e` to setup a sudo cronjob for `@reboot sudo vnstatd -d`.
