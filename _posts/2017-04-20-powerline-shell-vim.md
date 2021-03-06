---
title: Powerline for vim and bash prompt
author: Navy Su
layout: post
---
[Powerline](https://github.com/powerline/powerline) is very cool status line for vim and easy to setup. It also supports shell prompt. But [Powerline-shell](https://github.com/banga/powerline-shell) is better for shell prompt because it can suppor version control information.

## Installing fonts
* Installing font on Mac
1. Download font file form github
~~~shell
wget https://github.com/powerline/powerline/raw/develop/font/PowerlineSymbols.otf
~~~
2. Open Finder and double click the font file to open preview window
3. Click button "Install Font" to install font to user folder
4. Changing font for iTerm2 or Terminal (Preferences --> Profile --> Text --> Non-AsCII Font)

* Installing fonts on Windows
1. Download font from [Fantasque Sans Mono](https://github.com/belluzj/fantasque-sans/releases/latest)
2. Unzip the font file and click all ttf font files to install
3. Change font for Putty or other terminal tools

## Installing Powerline-shell
* Clone powerline-shell repository and install it
~~~shell
git clone git@github.com:banga/powerline-shell.git
cd powerline-shell
cp config.py.dist config.py
vi config.py # edit it before running install.py. if it is changed later, you need run install.py again
./install.py
~~~
* Creating a powerline-shell.py link at home directory
~~~shell
cd ~/
ln -s ~/powerline-shell/powerline-shell.py # powerline-shell repository folder is ~/powerline-shell
~~~
* Editing .bashrc or .bash_profile or .profile and add the following lines

~~~shell
function _update_ps1() {
    PS1="$(~/powerline-shell.py --cwd-max-depth 3 --colorize-hostname $? 2> /dev/null)"
}

if [ "$TERM" != "linux" ]; then
    PROMPT_COMMAND="_update_ps1; $PROMPT_COMMAND"
fi
~~~

## Installing Powerline for Vim
* Installing powerline
~~~shell
pip install powerline-status #for python2
pip3 install powerline-status #for python3
~~~
* Installing macvim (For Mac OS X only)
~~~shell
brew install macvim --env-std --with-override-system-vim
~~~
* Checking python version supported by Vim. If no python, it won't work for next step
~~~shell
vim --version | grep +python
~~~
* Editing .vimrc and add the following lines
~~~shell
# for python2
python from powerline.vim import setup as powerline_setup
python powerline_setup()
python del powerline_setup
~~~
or
~~~shell
# for python3
python3 from powerline.vim import setup as powerline_setup
python3 powerline_setup()
python3 del powerline_setup
~~~
