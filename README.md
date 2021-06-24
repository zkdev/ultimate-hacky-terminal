# Ultimate Hacky Terminal

## Installation
First of all make sure all packages are up to date.<br>
`sudo apt-get install update -y && sudo apt-get install upgrade -y`<br>

#### iTerm2 ####
Install [iTerm2](https://www.iterm2.com/)

#### ZSH Shell ####
Install the `ZSH Shell` and make sure it is your default shell.<br>
`chsh -s /bin/zsh`

#### Install the `Oh-My-Zsh` Framework on top.
- [Oh-My-Zsh](https://github.com/ohmyzsh/ohmyzsh)

#### Here are some usefull plugins for `Oh-My-Zsh`
- [Zsh Auto Suggestions](https://github.com/zsh-users/zsh-autosuggestions)

#### Install fonts and themes
- [Powerlevel10k](https://github.com/romkatv/powerlevel10k)
- [Nerd Fonts](https://github.com/ryanoasis/nerd-fonts)

#### Basically best IDE
- [YouCompleteMe](https://github.com/ycm-core/YouCompleteMe)

#### Super useful command line tools
- [dockly](https://github.com/lirantal/dockly)<br>
clear and handy docker container manager

- [kubebox](https://github.com/astefanutti/kubebox)<br>
pretty much dockly for k8s

- [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/)<br>
necessary for kubernetes

- [kubectx](https://github.com/ahmetb/kubectx)<br>
fast switch between your kubectls

- [httpie](https://github.com/httpie/httpie)<br>
universal HTTP REST client, better than postman!

- [neovim](https://github.com/neovim/neovim)<br>
basically the future of vim - use vim if you spend serious time inside the terminal

- [vundle](https://github.com/VundleVim)<br>
the vim package manager

- [fzf](https://github.com/junegunn/fzf)<br>
useful search tool

- [fx](https://github.com/antonmedv/fx)<br>
handy json viewer

- [Zsh syntax highlighting](https://github.com/zsh-users/zsh-syntax-highlighting)<br>
smart syntax highlighter for shell

- [bpytop](https://github.com/aristocratos/bpytop)<br>
personal recommendation when it comes to system monitoring

- [hacker-quotes](https://github.com/oldratlee/hacker-quotes)<br>
why not

- [cpulimit](https://github.com/opsengine/cpulimit)<br>
limit cpu usage of a process, helpful in diverse ways

#### Alias
- `alias k=kubectl`
- `alias ktx=kubectx`
- `alias ll=ls -color -ahl`
- `alias ports="lsof -i -P -n | grep LISTEN"`
- `alias nano=nvim` 
- `alias kubely="/path/to/kubebox"`
- `alias p3="python3"`
- `alias gpgkeys="gpg --list-secret-keys --keyid-format LONG"`
- `alias open="xdg-open"`
- `alias trim="sed -i 's/[ \t]*$//'"`
- `alias ggrep="git grep -n"`
- `alias dc=docker-compose`


#### Git Alias
- `git config --global alias.cp cherry-pick`
- `git config --global alias.pr 'pull --rebase`


#### Fix gnupg
Errors regarding gnupg might occurre once you want to sign your commits using gpg keys.
- `brew upgrade gnupg`
- `brew link --overwrite gnupg`
- `brew install pinentry-mac`
- `echo "pinentry-program /usr/local/bin/pinentry-mac" >> ~/.gnupg/gpg-agent.conf`
- `killall gpg-agent`

#### Conditional Git Config
Load Git config depending on repo path
```
[user]
    name = zk
    email = dev@zeekay.dev
    signingkey = foobar
    gpgsign = true
[alias]
    cp = cherry-pick
    pr = pull --rebase
[includeIf "gitdir:/Users/zk/dev/github.com/**"]
    path = /Users/zk/.gitconfig-zk
[includeIf "gitdir:/Users/zk/dev/github.work/**"]
    path = /Users/zk/.gitconfig-work
```

#### Misc
Display the current kubectx as iTerm2 Badge:
- install `iTerm2 Shell Integration`: `wget https://iterm2.com/misc/install_shell_integration.sh`
- to prevent misconfiguration adapt the script do directly detect `zsh` as your shell (line 10)
- execute install script (`chmod +x ...`)
- append `iterm2_print_user_vars() {iterm2_set_user_var kubectx $(kubectl config current-context 2>/dev/null)}` to `.zshrc` right after `source iterm_shell_integration`
- go to iTerm > Preferences > Profiles > General and set `\(user.kube_context)` as badge

Install GnuCoreUtils with g-prefix
- `brew install coreutils findutils gnu-tar gnu-sed gawk gnutls gnu-indent gnu-getopt grep`
