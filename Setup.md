# Setup
### Configure SD Card
- Burn Strech SD Card
- Add ssh file in 'boot' partition
- add "wpa_passphrase SSID PASS" output to etc/wpa_supplicant/wpa_supplicant.conf
- cp /etc/wpa_supplicant/ifupdown.sh /etc/ifplugd/action.d/ifupdown
- Change "raspberrypi" in /etc/hostname and /etc/hosts to NEWHOSTNAME

### After first boot
- Login in ssh with pi@NEWHOSTNAME.local
- adduser *USER
- usermod -aG sudo,*** NEWUSER
- Logout of Pi and login in NEWUSER
- deluser pi
- rm -f /home/pi
- raspi-config camera on
- aptitude update && aptitude full-upgrade
- wget https://github.com/Motion-Project/motion/releases/download/release-4.2/pi_stretch_motion_4.2-1_armhf.deb
- dpkg -i pi_stretch_motion_4.2-1_armhf.deb   (It should failed due but will be fixed by next aptitude install)
- aptitude install -r git screen (with recommends)
- configure /etc/motion/motion.conf (daemon, target dir, image size, min motion frame, pre/post capture, picture on, movie off, webcont local off, webstream local off)
- configure /etc/default/motion daemon yes
- mkdire /home/USER/motion
- chown group motion, chmod 775
