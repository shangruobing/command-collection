# Mac

Remove context menu uninstall residue

```shell
/System/Library/Frameworks/CoreServices.framework/Versions/A/Frameworks/LaunchServices.framework/Versions/A/Support/lsregister -kill -r -domain local -domain system -domain user
```

Reset launchpad

```shell
defaults write com.apple.dock ResetLaunchPad -bool TRUE;
```

Flush DNS cache

```shell
sudo killall -HUP mDNSResponder;
```

Auto discover the proxy and set global proxy

```shell
scutil --proxy
export http_proxy=http://127.0.0.1:7890
export https_proxy=https://127.0.0.1:7890
export all_proxy=socks5://127.0.0.1:7890
```

Delete the proxy

```shell
export http_proxy=
export https_proxy=
export all_proxy=
```

Activate the Env Variable

```bash
source ~/.bash_profile
printenv
```

# Homebrew

```shell
brew install package
brew uninstall package
brew cleanup --prune=all
```

