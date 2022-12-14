
# My `zsh` setup
###### *Note: This assumes you already have `brew` installed under your current shell*
</br>

## Install and configure [`zsh`](https://www.zsh.org/)
```
brew install zsh
```
### Set it as your default shell
```
open -b com.apple.systempreferences /System/Library/PreferencePanes/Accounts.prefPane
```
Right click your user and select "Advanced Options...". Update the "Login shell" field with `/opt/homebrew/bin/zsh`.

### Reinstall and reconfigure [`brew`](https://brew.sh)
```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
echo '# Set PATH, MANPATH, etc., for Homebrew.' >> /Users/$(whoami)/.zshrc
echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> /Users/$(whoami)/.zshrc
eval "$(/opt/homebrew/bin/brew shellenv)"
```
</br>

## Install and configure [`oh my zsh`](https://ohmyz.sh/)
```
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

### Install [Dracula](https://draculatheme.com/zsh) theme
###### *Note: Change into your local Git directory, in my example that is `~/Git`*
```
cd ~/Git
git clone https://github.com/dracula/zsh.git
cd ~/.oh-my-zsh/themes
ln -s ~/Git/zsh/dracula.zsh-theme dracula.zsh-theme
```

Set Dracula as your theme in `~/.zshrc`. The other options I have set are detailed [here](https://github.com/dracula/zsh/blob/master/README.md).
```
ZSH_THEME="dracula"
```
Install [Dracula](https://draculatheme.com/iterm) iTerm theme \
</br>

## Install [`kube-ps1`](https://formulae.brew.sh/formula/kube-ps1) and [`kubectx`](https://formulae.brew.sh/formula/kubectx) plugins
```
brew install kube-ps1 kubectx
```
</br>

## My `.zshrc`
You up-to-date `.zshrc` can be found [here](https://github.com/alievrouw/my-configs/blob/main/zsh-setup/my-zshrc). It contains options that extend the installations and configurations from this readme.