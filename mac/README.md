# Mac

macOS is an operating system developed by Apple that runs on Macintosh computers. macOS is the first commercially successful operating system with a graphical user interface.

## Remove context menu uninstall residue

```shell
/System/Library/Frameworks/CoreServices.framework/Versions/A/Frameworks/LaunchServices.framework/Versions/A/Support/lsregister -kill -r -domain local -domain system -domain user
```

## Reset launchpad

```shell
defaults write com.apple.dock ResetLaunchPad -bool TRUE;
```

## Flush DNS cache

```shell
sudo killall -HUP mDNSResponder;
```

## Environment Variable

```bash
source ~/.bash_profile
printenv
```

### Proxy

```shell
scutil --proxy

# set the proxy
export http_proxy=http://127.0.0.1:7890
export https_proxy=https://127.0.0.1:7890
export all_proxy=socks5://127.0.0.1:7890

# Delete the proxy
export http_proxy=
export https_proxy=
export all_proxy=
```

### Pluginkit

```shell
# view pluginkit list
pluginkit  -mAD -p com.apple.FinderSync
# enable plugin
pluginkit -e "use" -i "cn.wflixu.RClick.FinderSyncExt"
# disable plugin
pluginkit -e "ignore" -i "cn.wflixu.RClick.FinderSyncExt"
```

### Example

```shell
export PATH=/usr/local/bin:/usr/bin:/bin:/usr/sbin:/sbin

# HomeBrew
export PATH=$PATH:/opt/homebrew/bin
export HOMEBREW_BOTTLE_DOMAIN=https://mirrors.aliyun.com/homebrew/homebrew-bottles

# Proxy
export https_proxy=http://127.0.0.1:7890
export http_proxy=http://127.0.0.1:7890
export all_proxy=socks5://127.0.0.1:7890

# Python
alias python="python3"
alias pip="pip3"
export PATH=$PATH:/Users/Ruobing/Library/Python/3.9/bin

# MySQL
export PATH=$PATH:/usr/local/mysql/bin

# Maven
export MAVEN_HOME=/usr/local/apache-maven-3.9.0
export PATH=$PATH:$MAVEN_HOME/bin

# MacTeX
export TEX_HOME=/usr/local/texlive/2024/bin/universal-darwin
export PATH=$PATH:$TEX_HOME

# MongoDB
export PATH=$PATH:/usr/local/mongodb/bin

# OpenAI
export OPENAI_API_KEY="sk-******"

# Conda
__conda_setup="$('/opt/anaconda3/bin/conda' 'shell.bash' 'hook' 2> /dev/null)"
if [ $? -eq 0 ]; then
    eval "$__conda_setup"
else
    if [ -f "/opt/anaconda3/etc/profile.d/conda.sh" ]; then
        . "/opt/anaconda3/etc/profile.d/conda.sh"
    else
        export PATH="/opt/anaconda3/bin:$PATH"
    fi
fi
unset __conda_setup
```
