### OSX Stuff
---

```bash

# install CLI developer tools because El Capitan is a bitch
xcode-select --install

# Enable character repeat on keydown
defaults write -g ApplePressAndHoldEnabled -bool false

# reduce key repeat delay
defaults write NSGlobalDomain InitialKeyRepeat -int 12

# Set a blazingly fast keyboard repeat rate
defaults write NSGlobalDomain KeyRepeat -int 0

# Disable window animations ("new window" scale effect)
defaults write NSGlobalDomain NSAutomaticWindowAnimationsEnabled -bool false

# Turn on dashboard-as-space
defaults write com.apple.dashboard enabled-state 2

# Set default Finder location to home folder (~/)
defaults write com.apple.finder NewWindowTarget -string "PfLo" && \
defaults write com.apple.finder NewWindowTargetPath -string "file://${HOME}"

# Show hidden files in Finder
defaults write com.apple.finder AppleShowAllFiles YES

# Expand save panel by default
defaults write NSGlobalDomain NSNavPanelExpandedStateForSaveMode -bool true

# Disable ext change warning
defaults write com.apple.finder FXEnableExtensionChangeWarning -bool false

# Check for software updates daily, not just once per week
defaults write com.apple.SoftwareUpdate ScheduleFrequency -int 1

# Use current directory as default search scope in Finder
defaults write com.apple.finder FXDefaultSearchScope -string "SCcf"

# Show Path bar in Finder
defaults write com.apple.finder ShowPathbar -bool true

# Show Status bar in Finder
defaults write com.apple.finder ShowStatusBar -bool true

# Avoid creating .DS_Store files on network volumes
defaults write com.apple.desktopservices DSDontWriteNetworkStores -bool true

# Disable disk image verification
defaults write com.apple.frameworks.diskimages skip-verify -bool true && \
defaults write com.apple.frameworks.diskimages skip-verify-locked -bool true && \
defaults write com.apple.frameworks.diskimages skip-verify-remote -bool true

# Trackpad: map bottom right corner to right-click
defaults write com.apple.driver.AppleBluetoothMultitouch.trackpad TrackpadCornerSecondaryClick -int 2 && \
defaults write com.apple.driver.AppleBluetoothMultitouch.trackpad TrackpadRightClick -bool true && \
defaults -currentHost write NSGlobalDomain com.apple.trackpad.trackpadCornerClickBehavior -int 1 && \
defaults -currentHost write NSGlobalDomain com.apple.trackpad.enableSecondaryClick -bool true

# Even though we hate Safari, enable the Dev tools in Safari
defaults write com.apple.Safari IncludeInternalDebugMenu -bool true && \
defaults write com.apple.Safari IncludeDevelopMenu -bool true && \
defaults write com.apple.Safari WebKitDeveloperExtrasEnabledPreferenceKey -bool true && \
defaults write com.apple.Safari com.apple.Safari.ContentPageGroupIdentifier.WebKit2DeveloperExtrasEnabled -bool true && \
defaults write NSGlobalDomain WebKitDeveloperExtras -bool true

# Show the ~/Library folder
chflags nohidden ~/Library

# Show absolute path in finder's title bar. 
defaults write com.apple.finder _FXShowPosixPathInTitle -bool YES

# Enable text copying from Quick Look
defaults write com.apple.finder QLEnableTextSelection -bool YES

# Enable AirDrop over Ethernet and on unsupported Macs
defaults write com.apple.NetworkBrowser BrowseAllInterfaces -bool true

# Disable WebkitNightly.app's homepage
defaults write org.webkit.nightly.WebKit StartPageDisabled -bool true

```

### Shell
---

### Install Oh-My-ZSH

```bash
curl -L https://github.com/robbyrussell/oh-my-zsh/raw/master/tools/install.sh | sh
```


#### Homebrew

```bash
# install package manager
ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

# install homebrew packages
brew install \
tree \
node \
ssh-copy-id \
wget \
ack \
caskroom/cask/brew-cask
```

```bash
brew install \
nginx \
```

#### Homebrew Cask Apps

```bash

# install mac apps
brew cask install \
codekit \
ghostlab \
google-chrome \
macdown \
slack \
spectacle \
sublime-text3 \
vagrant \
virtualbox \
webstorm
```

#### Update .zshrc

```bash
wget https://gist.githubusercontent.com/saetia/2764210/raw/ab099b587689640eb32cbc1afdb6a19b62be7fb0/.zshrc -O \
~/.zshrc

# syntax highlighting
git clone git://github.com/zsh-users/zsh-syntax-highlighting.git \
~/.oh-my-zsh/custom/plugins/zsh-syntax-highlighting
```

#### Set hostname

```bash
sudo scutil --set HostName kantbook
```

### Agree To Xcode
```bash
sudo xcrun cc
```

### Git

---

#### Setup Github

```bash
ssh-keygen -t rsa -C "contact@michaelkant.com"

# Copy ssh key to clipboard for adding to github.com
pbcopy < ~/.ssh/id_rsa.pub

# Test connection
ssh -T git@github.com

# Set git config values
git config --global user.name "Michael Kant" && \
git config --global user.email "meiskant@gmail.com" && \
git config --global github.user inconsiderate && \
git config --global core.editor "code" && \
git config --global color.ui true && \
git config --global push.default simple

# Set git global ignore file
touch ~/.gitignore && \
git config --get core.excludesfile '~/.gitignore' && \
echo ".DS_Store" >> ~/.gitignore && \
echo ".gitignore" >> ~/.gitignore && \
echo ".idea" >> ~/.gitignore && \
echo "*.log" >> ~/.gitignore

# Tell git to ignore chmod's
git config --global core.filemode false

# Alias gitlog to show more detail and pretty colors in ZSH
echo 'alias gitlog="git log --graph --decorate --date=relative --format=format:'%C(bold blue)%H%C(reset) - %C(bold green)(%ar)%C(reset) %C(white)%s%C(reset) %C(red)- %an%C(reset)%C(bold yellow)%d%C(reset)' --all"' >> ~/.zshrc
```

### Visual Studio Code
---

```json
//keybindings.json
[
    {
      "key": "ctrl+shift+up",
      "command": "editor.action.moveLinesUpAction",
      "when": "editorTextFocus"
    },
    {
      "key": "ctrl+shift+down",
      "command": "editor.action.moveLinesDownAction",
      "when": "editorTextFocus"
    },
    {
      "key": "ctrl+D",
      "command": "editor.action.copyLinesDownAction",
      "when": "editorTextFocus"
    }
  ]
```


### Etc

---

```

### Ruby version manager
---
```bash
curl -L https://get.rvm.io | bash -s stable --rails
```
