<!-- .slide: class="chapter dotfiles" -->
# dotfiles
<br/><br/>


----

<!-- .slide: class="dotfiles bulletpoints" -->
# dotfiles

* Dateien/Ordner die **mit einem <span>.</span> beginnen sind versteckt**
* meist direkt in `$HOME`: **/home/user/<span>.</span>file**
* **Konfiguration** für diverse Programme und Tools
  * AWS, GCP, kubernetes, terraform, ...

notes:

* Format je nach Programm/Tool
* Erleichtern den Arbeitsalltag sehr
* Sehr persönlich, Geschmackssache!
* Lokal auf dem Server/PC

----

<!-- .slide: class="dotfiles" -->
# bashrc

```bash
## custom shell design
if [[ ${EUID} == 0 ]] ; then
    PS1='(\t) \[\033[01;31m\]\h\[\033[01;34m\] \W \$\[\033[00m\] '
else
    PS1='(\t) \[\033[01;32m\]\u@\h\[\033[01;34m\] \w \$\[\033[00m\] '
fi

## aliases
alias l='ls -lh'
alias lh='ls -lh'
alias ..='cd ..'

# history configuration
export HISTTIMEFORMAT='%Y-%m-%d %H:%M:%S: '
export HISTFILESIZE=10000000
export HISTSIZE=500000
```

----

<!-- .slide: class="dotfiles bulletpoints" -->
# bashrc alias

* Install *Pygments*, a syntax highlighting library in Python 🐍
```bash
apt install python-pip
pip install Pygments
````

* Create an alias for convenient usage via **`pcat`**
```bash
alias pcat='pygmentize -f terminal16m -O style=monokai -g'
```

----

<!-- .slide: class="chapter" -->
# Demo! 🤓💻
## `pcat` with Pygments
#### ... <span>|</span> `apt` <span>|</span> `pip` <span>|</span> `pcat` <span>|</span> ...

----

<!-- .slide: class="dotfiles" -->
# vimrc

```vim
" enable syntax processing
syntax on
" always with ruler
set ruler
" show command in bottom bar
set showcmd
" highlight matching [{()}]
set showmatch
" search as characters are entered
set incsearch
" highlight matches
set hlsearch
```

----

<!-- .slide: class="dotfiles" -->
# gitconfig

```ini
[user]
    name = Ben Lebherz
    email = git@benleb.de
[core]
    editor = code-insiders --wait
    excludesfile = /Users/ben/.gitignore_global
    autocrlf = input
[alias]
    pom = !git push origin master
    set-upstream = !git branch --set-upstream-to=origin/...
```
