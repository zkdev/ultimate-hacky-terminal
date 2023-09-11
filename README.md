# Ultimate Hacky Terminal for Mac

## I don't want to work without these

#### Homebrew
Install [Homebrew](https://brew.sh/), the "missing package manager for macOS"<br>
`/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"`

#### iTerm2
Install [iTerm2](https://www.iterm2.com/)

#### ZSH Shell
Install the `ZSH Shell` and make sure it is your default shell.<br>
`brew install zsh`<br>
`chsh -s /bin/zsh`

#### Install the `Oh-My-Zsh` Framework on top.
- [Oh-My-Zsh](https://github.com/ohmyzsh/ohmyzsh)

#### Here are some usefull plugins for `Oh-My-Zsh`
- [Zsh Auto Suggestions](https://github.com/zsh-users/zsh-autosuggestions)

#### Install fonts and themes
- [Nerd Fonts](https://github.com/ryanoasis/nerd-fonts)
- [Powerlevel10k](https://github.com/romkatv/powerlevel10k)

### Tools and Programs
- [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/)<br>
necessary for kubernetes

- [kubectx](https://github.com/ahmetb/kubectx)<br>
fast switch between your kubectls

- [vundle](https://github.com/VundleVim)<br>
the vim package manager

- [fzf](https://github.com/junegunn/fzf)<br>
useful search tool

- [YouCompleteMe](https://github.com/ycm-core/YouCompleteMe)<br>
basically best "IDE"

- [Zsh syntax highlighting](https://github.com/zsh-users/zsh-syntax-highlighting)<br>
smart syntax highlighter for shell

- [bpytop](https://github.com/aristocratos/bpytop)<br>
personal recommendation when it comes to system monitoring

- [dive](https://github.com/wagoodman/dive)<br>
tool for exploring a docker image and its layer contents

- [watch](https://gitlab.com/procps-ng/procps)<br>
executes a program periodically, showing output fullscreen

## Suggestions

- [dockly](https://github.com/lirantal/dockly)<br>
clear and handy docker container manager

- [k9s](https://github.com/derailed/k9s)<br>
pretty much dockly for k8s

- [httpie](https://github.com/httpie/httpie)<br>
universal HTTP REST client, better than postman!

- [neovim](https://github.com/neovim/neovim)<br>
basically the future of vim - use vim if you spend serious time inside the terminal

- [fx](https://github.com/antonmedv/fx)<br>
handy json viewer

- [jq](https://stedolan.github.io/jq/)<br>
lightweight and flexible command-line JSON processor

- [hacker-quotes](https://github.com/oldratlee/hacker-quotes)<br>
why not

- [cpulimit](https://github.com/opsengine/cpulimit)<br>
limit cpu usage of a process, helpful in diverse ways

- [step-cli](https://smallstep.com/docs/step-cli/installation)<br>
inspect JWT tokens

- [colima](https://github.com/abiosoft/colima)<br>
Container Runtime without unnecessary UI (I'm looking at you DockerDesktop)

#### Alias
- `alias watch='watch '` # required to make alias work with watch
- `alias sudo='sudo '`
- `alias k=kubectl`
- `alias ktx=kubectx`
- `alias ll="ls -color -ahl"`
- `alias ports="lsof -i -P -n | grep LISTEN"`
- `alias nano=nvim`
- `alias p3="python3"`
- `alias gpgkeys="gpg --list-secret-keys --keyid-format LONG"`
- `alias open="xdg-open"`
- `alias trim="sed -i 's/[ \t]*$//'"`
- `alias ggrep="git grep -n"`
- `alias dc=docker-compose`
- `alias pip=noglob pip`


#### Git Alias
- `git config --global alias.cp cherry-pick`
- `git config --global alias.pr pull --rebase`


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

### Macro

#### Kill Docker
```bash
function whaling() {
  ps ax|grep -i docker|egrep -iv 'grep|com.docker.vmnetd'|awk '{print $1}'|xargs kill
}
```

#### Force restart Logitech Mouse Daemon
```bash
function mouse() {
  ps ax|grep -i Options.app/Contents/Support/LogiMgrDaemon.app/Contents/MacOS/LogiMgrDaemon|egrep -iv 'grep --color=auto --exclude-dir'|awk '{print $1}'|xargs kill
}
```

#### JWT Decoder
```bash
function jwtd() {
    if [[ -x $(command -v jq) ]]; then
         jq -R 'split(".") | .[0],.[1] | @base64d | fromjson' <<< "${1}"
         echo "Signature: $(echo "${1}" | awk -F'.' '{print $3}')"
    fi
}
```

#### Misc
Display the current kubectx as iTerm2 Badge:
- install `iTerm2 Shell Integration`: `wget https://iterm2.com/misc/install_shell_integration.sh`
- to prevent misconfiguration adapt the script do directly detect `zsh` as your shell (line 10)
- execute install script (`chmod +x ...`)
- append following function to `.zshrc` right after `source iterm_shell_integration`
```sh
function iterm2_print_user_vars() {
  iterm2_set_user_var kube_context $(kubectl config current-context 2>/dev/null)
  iterm2_set_user_var kube_ns $(kubectl config view --minify --output 'jsonpath={..namespace}'; echo)
}
```
- go to iTerm > Preferences > Profiles > General and set `\(user.kube_context)\n\(user.kube_ns)` as badge
- I recommand to re-init `zsh` the the very end of `.zshrc`

Install GnuCoreUtils with g-prefix
- `brew install coreutils findutils gnu-tar gnu-sed gawk gnutls gnu-indent gnu-getopt grep`<br>
If you want to use them without g-prefix, adjust your PATH and MANPATH (add before anything else).
```bash
PATH="/usr/local/opt/coreutils/libexec/gnubin:$PATH"
MANPATH="/usr/local/opt/coreutils/libexec/gnuman:$MANPATH"
```
