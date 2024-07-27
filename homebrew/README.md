# Homebrew

Homebrew is the easiest and most flexible way to install the UNIX tools Apple didn’t include with macOS. It can also install software not packaged for your Linux distribution without requiring `sudo`.

```shell
# Install the package using Homebrew
brew install package

# Uninstall the package using Homebrew
brew uninstall package

# Clean up all outdated packages and their associated files
brew cleanup --prune=all

# Upgrade the package to the latest version using Homebrew
brew upgrade package

# Check for outdated packages installed via Homebrew
brew outdated

# Automatically update Homebrew and its packages
brew update --auto-update
```
