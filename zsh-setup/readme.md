
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

Set Dracula as your theme in `~/.zshrc`
```
ZSH_THEME="dracula"
```
Install [Dracula](https://draculatheme.com/iterm) iTerm theme


## Install [`kube-ps1`](https://formulae.brew.sh/formula/kube-ps1) and [`kubectx`](https://formulae.brew.sh/formula/kubectx)
```
brew install kube-ps1 kubectx
```

Add in *User configuration* section of `~/.zshrc`
```
# Setup kube-ps1
export KUBE_PS1_SYMBOL_ENABLE=false
export KUBE_PS1_SUFFIX=") "
export KUBE_PS1_CTX_COLOR="blue"
export KUBE_PS1_NS_COLOR="green"
export KUBE_PS1_DIVIDER=" #"

function get_cluster_short() {
  echo "$1" | cut -d . -f1
}

KUBE_PS1_CLUSTER_FUNCTION=get_cluster_short

source "/opt/homebrew/opt/kube-ps1/share/kube-ps1.sh"
PS1='$(kube_ps1)'$PS1
```
Add in *My aliases* section of `~/.zshrc`
```
alias kctx="kubectx"
alias kns="kubens"
```

## Additional changes to ~/.zshrc
```
plugins=(
  git
  kube-ps1
  zsh-autosuggestions
  zsh-syntax-highlighting
)
```