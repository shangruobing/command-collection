# Ubuntu

```shell
# install GUI desktop
sudo apt update
sudo apt upgrade
sudo apt install ubuntu-desktop
sudo reboot

# install chinese input
sudo apt-get install ibus-pinyin
```

## Solve slow boot

```text
vim /usr/lib/systemd/system/systemd-networkd-wait-online.service
# add
[Service]
TimeoutStartSec=1sec
```