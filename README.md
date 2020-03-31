# Ultimate Hacky Terminal

## Installation
First of all make sure all packages are up to date.
`sudo apt-get install update -y && sudo apt-get install upgrade -y`

Install the `ZSH Shell` and make sure it is your default shell.
`chsh -s /bin/zsh`

Install the `Oh-My-Zsh` Framework on top.
- [Oh-My-Zsh](https://github.com/ohmyzsh/ohmyzsh)

Here are some usefull plugins for `Oh-My-Zsh`
- [Zsh Auto Suggestions](https://github.com/zsh-users/zsh-autosuggestions)

Install fonts and themes
- [Powerlevel0k](https://github.com/romkatv/powerlevel10k)
- [Nerd Fonts](https://github.com/ryanoasis/nerd-fonts)

Basically best IDE
- [YouCompleteMe](https://github.com/ycm-core/YouCompleteMe)

Super useful command line tools
- [dockly](https://github.com/lirantal/dockly)
clear and handy docker container manager

- [kubebox](https://github.com/astefanutti/kubebox)
pretty much dockly for k8s

- [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/)
necessary for kubernetes

- [kubectx](https://github.com/ahmetb/kubectx)
fast switch between your kubectls

- [neovim](https://github.com/neovim/neovim)
basically the future of vim - use vim if you spend serious time inside the terminal

- [fzf](https://github.com/junegunn/fzf)
useful search tool

- [fx](https://github.com/antonmedv/fx)
handy json viewer

- [Zsh syntax highlighting](https://github.com/zsh-users/zsh-syntax-highlighting)
smart syntax highlighter for shell

- [hacker-quotes](https://github.com/oldratlee/hacker-quotes)
not only because its fun also because you hear some names ;)

#### Alias
- `alias k=kubectl`
- `alias ll=ls -afhl`
- `alias wstorm=open -a /path/to/webstorm `
- `alias ports="lsof -i -P -n | grep LISTEN"`
- `alias dev=cd ~/dev`
- `alias nano=nvim` 
- `alias kubely="/path/to/kubebox"`
- `alias p3="python3"`


#### Misc
Display the current kubectx as iTerm2 Badge:
- `source ~/.iterm2_shell_integration.zsh`
- append `iterm2_print_user_vars() {iterm2_set_user_var kubectx $(kubectl config current-context 2>/dev/null)}` to `.zshrc`

Install GnuCoreUtils with g-prefix
- `brew install coreutils findutils gnu-tar gnu-sed gawk gnutls gnu-indent gnu-getopt grep\n`
