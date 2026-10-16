# New Laptop Setup (Ubuntu)

Last Updated On: 2026-10-15

## General/Scratch

In the installer, choose Dvorak layout.

## Caps as Ctrl

$ sudo apt install build-essential curl wget git gnome-tweaks
$ gnome-tweaks

## SSH key and github

$ ssh-keygen -t ed25519
$ cat ~/.ssh/id_ed25519.pub

Login to Github and add the key

## Initial Repos

$ git clone git@github.com:dbrady/bin.git && \
  git clone git@github.com:dbrady/private_bin.git && \
  git clone git@github.com:dbrady/dotfiles.git && \
  git clone git@github.com:dbrady/prelude.git .emacs.d && \
  (cd ~/Documents && git clone git@github.com:dbrady/refdox.git)

# Link up dotfiles
$ for f in .aliases .bash_functions .bash_profile .emacstiny.el .irbrc .nav .nav.home .tmux.conf; do echo $f; rm $f; ln -s ~/dotfiles/$f; done

## Git config, global ignore, global hooks

COPY .gitconfig, don't symlink it: it has absolute home paths, and those are
/Users/dbrady on the Mac. The sed swaps them to /home/dbrady.

$ sed -e 's#/Users/dbrady#/home/dbrady#g' ~/dotfiles/dotgitconfig > ~/.gitconfig
$ ln -s ~/dotfiles/dotgitignore ~/.gitignore
$ ln -s ~/dotfiles/dotgithooks ~/.githooks

The global pre-commit hook is Ruby, and it calls git-current-branch and
git-main-branch from ~/bin. So commits fail until Ruby is installed (see
below) and ~/bin is cloned. It also blocks commits to main/master. For a
one-off, use `ALLOW_MAIN=true git commit ...`. To allow it permanently in a
repo, run `touch .git-allow-commits-to-main` there.

## Now Install a Very Nearly Complete Operating System

(...all it lacks is a simple text editor)

$ sudo apt install emacs

## Development, Finally

$ mkdir -p ~/devel
$ (cd ~/devel && git clone git@github.com:dbrady/scrapbin.git && git clone git@github.com:dbrady/cadaver.git)

### Ruby

--> go to https://rvm.io and follow along. (Note: they say gpg2. Just run `gpg`
instead.)

$ source .rvm/scripts/rvm
$ rvm install ruby-3.4.9
$ ruby ~/Documents/refdox/gems_i_always_want

### Python, Node, et al

$ sudo apt install nodejs

#### direnv + uv (Python projects, e.g. cadaver)

direnv auto-activates a project's venv on `cd` and deactivates it on the way
out. No more `source .venv/bin/activate`.

$ sudo apt install direnv

The hook already lives at the END of ~/dotfiles/.bash_profile. These
terminals (gnome-terminal and tmux) start login shells, and login shells
never read .bashrc, so don't follow direnv's docs and put it there. It has to
stay below ps1_set, because ps1_set overwrites PROMPT_COMMAND and that's
where direnv hooks in.

Python projects use uv to get a pinned Python (3.12) no matter what the
system Python is:

$ curl -LsSf https://astral.sh/uv/install.sh | sh
$ cd ~/devel/cadaver && direnv allow    # .envrc runs bin/setup on first entry

Sanity check: `cd` in should print "direnv: loading .envrc", and
`which python` should show .venv/bin/python.

Also nice for CAD: `sudo apt install f3d` (a spin-it-around STL viewer:
`f3d build/gudgeon.stl`).

Clipboard: ~/bin/pbcopy shims to xclip on Linux, so run `sudo apt install xclip`.

### bat - colorized cat

$ sudo apt install bat

Ubuntu installs it as `batcat` (another package already owns the name `bat`),
so add `alias bat=batcat`.
