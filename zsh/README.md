# ZSH

```shell
# install
sudo apt install zsh
sudo apt install git
git clone https://github.com/robbyrussell/oh-my-zsh
chsh -s /bin/zsh

# install plugins
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions

git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
 
mkdir ~/.oh-my-zsh/plugins/incr
wget -P ~/.oh-my-zsh/plugins/incr  http://mimosa-pudica.net/src/incr-0.2.zsh
source ~/.oh-my-zsh/plugins/incr/incr*.zsh

# activate config file
source ~/.zshrc   
```