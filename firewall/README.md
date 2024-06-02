# Firewall

```shell
# Install the Uncomplicated Firewall (UFW)
sudo apt install ufw

# Show the status of UFW with verbose output
sudo ufw status verbose

# Enable UFW
sudo ufw enable

# Disable UFW
sudo ufw disable

# Set the default incoming policy to deny
sudo ufw default deny

# Allow incoming traffic on port 7474
sudo ufw allow 7474

```
