# ZSH

Zsh (Z-shell) is a shell for interactive use and can also be used as a script interpreter.

```shell
# check the type of shell used
echo $SHELL

# check install
cat /etc/shells

# install
sudo apt install zsh
sudo apt install git

# change the shell
sudo chsh -s /bin/zsh
```

## Oh-My-Zsh

```shell
# auto install oh-my-zsh
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
# or
sh -c "$(curl -fsSL https://install.ohmyz.sh/)"

# manual install oh-my-zsh
git clone https://github.com/ohmyzsh/ohmyzsh.git ~/.oh-my-zsh

# execute install script
sh ~/.oh-my-zsh/tools/install.sh

# copy the zsh template
cp ~/.oh-my-zsh/templates/zshrc.zsh-template ~/.zshrc

# activate config file
source ~/.zshrc

# check oh-my-zsh version
omz version
```

### Oh-My-Zsh Plugins

```shell
# install oh-my-zsh plugins
git clone https://github.com/zsh-users/zsh-autosuggestions \
	${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions

git clone https://github.com/zsh-users/zsh-syntax-highlighting.git \
	${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting

# write these lines into ~/.zshrc
plugins=(
	git
	zsh-autosuggestions
	zsh-syntax-highlighting
)

# activate config file
source ~/.zshrc
```
