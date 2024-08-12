# Windows ~10~ 11 Clean Install

## Install the Windows Subsystem For Linux + Ubuntu
`wsl --install`

`wsl --install Ubuntu-24.04`

### Basic Terminal Stuff

[First, install these fonts](https://github.com/romkatv/powerlevel10k?tab=readme-ov-file#meslo-nerd-font-patched-for-powerlevel10k)

```bash
# install zsh
sudo apt-get update && sudo apt-get install -y zsh

# install oh-my-zsh
sh -c "$(wget -O- https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"

# grab powerlevel10k
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
vim ~/.zshrc # ZSH_THEME="powerlevel10k/powerlevel10k"

# configure everything
zsh
```

### Bash Config Stuff

```bash
# alias gitlog to show more detail and pretty colors
echo "alias gitlog=\"git log --graph --decorate --date=relative --format=format:'%C(bold blue)%H%C(reset) - %C(bold green)(%ar)%C(reset) %C(white)%s%C(reset) %C(red)- %an%C(reset)%C(bold yellow)%d%C(reset)' --all\"" >> ~/.zshrc

#set alias "sql" to local server
echo "alias sql=\"mysql --host='127.0.0.1' --user='root' --password='root'\"" >> ~/.zshrc
```

### Setup Github

```bash
ssh-keygen -t rsa -C "MY_EMAIL_ADDRESS"

#copy ssh key to clipboard for adding to github.com, then [go do that](https://github.com/settings/keys)
cat ~/.ssh/id_rsa.pub | clip.exe 

# test authentication
ssh -T git@github.com

#set git config values
git config --global user.name "inconsiderate" && \
git config --global user.email "YOUR_EMAIL" && \
git config --global github.user inconsiderate && \
git config --global core.editor "code -w" && \
git config --global color.ui true && \
git config --global push.default simple

#set git global ignore file
touch ~/.gitignore && \
git config --get core.excludesfile '~/.gitignore' && \
echo ".DS_Store" >> ~/.gitignore && \
echo ".gitignore" >> ~/.gitignore && \
echo ".idea" >> ~/.gitignore && \
echo "*.log" >> ~/.gitignore

#tell git to ignore chmod's
git config --global core.filemode false

```

### Visual Studio Code
---

Pro-tip: you can launch vscode and open your current directory by typing `code .` 

#### Install Extensions
```bash
echo "alexcvzz.vscode-sqlite
esbenp.prettier-vscode
felixfbecker.php-debug
GrapeCity.gc-excelviewer
kisstkondoros.vscode-gutter-preview
mblode.twig-language-2
mindpixel-labs.vsc-expressionengine
mrmlnc.vscode-apache
ms-azuretools.vscode-docker
ms-dotnettools.csharp
ms-vscode-remote.remote-containers
whatwedo.twig
junstyle.php-cs-fixer
editorconfig.editorconfig
yzhang.markdown-all-in-one" >> vs_code_extensions.md && xargs -n1 code --install-extension < vs_code_extensions.md && rm vs_code_extensions.md
```

#### Key Bindings
Access this file with `cmd+shift+p` and select Keyboard Shortcuts (JSON)

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

#### General Settings
Access this file with `cmd+shift+p` and select User Settings (JSON)

```json
"editor.largeFileOptimizations": false,
"editor.wordWrap": "on",
"security.workspace.trust.untrustedFiles": "open",
"files.trimFinalNewlines": true,
"workbench.editor.highlightModifiedTabs": true,
"editor.acceptSuggestionOnEnter": "off",
"editor.tabSize": 4,
"editor.defaultFormatter": "esbenp.prettier-vscode",
"prettier.tabWidth": 4,
"editor.formatOnPaste": false,
"editor.formatOnSave": false
```
