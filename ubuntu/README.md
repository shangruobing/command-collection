# Ubuntu

```shell
# install GUI desktop
sudo apt update
sudo apt upgrade
sudo apt install ubuntu-desktop
sudo reboot

# install chinese input
sudo apt-get install ibus-pinyin

# install .deb
sudo dpkg -i *.deb
```

## Solve slow boot

```text
vim /usr/lib/systemd/system/systemd-networkd-wait-online.service
# add
[Service]
TimeoutStartSec=1sec
```

## Gazebo

```shell
sudo apt-get update
sudo apt-get install curl lsb-release gnupg
sudo curl https://packages.osrfoundation.org/gazebo.gpg --output /usr/share/keyrings/pkgs-osrf-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/pkgs-osrf-archive-keyring.gpg] http://packages.osrfoundation.org/gazebo/ubuntu-stable $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/gazebo-stable.list > /dev/null
sudo apt-get update
sudo apt-get install gz-harmonic
```

> https://gazebosim.org/docs/garden/install_ubuntu/
