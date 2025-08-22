# New Laptop Setup (OSX)

General/scratch notes

Last updated for: Acima 2023 M1 Laptop. Note: IT was able to restore a bunch of
stuff from my previous laptop, so there will be some things recorded as
"preinstalled" that were from MY previous install, not from Apple. Worse yet:
that laptop was an Intel mac and this is an M1 so there may be some unusual
debugging here as well, as in "oh nice this is already preinstalled except oh no
it's all corrupted because it was built against the wrong cpu
architecture". This is not a script to run but rather a place to record things
so that I have a reminder list next time.

* System preferences
  * Keyboard
    * General: Set fastest repeat and shortest repeat delay
    * Dvorak
      * Keyboard > Input Sources: Add Dvorak.
      * Keybord > Shortcuts > Input Sources: Uncheck "select previous", change
        "select next source" shortcut to Ctrl-Shift-` (it's the same physical
        key combination on both layouts)
    * Enable caps as control on onboard keyboard (plus any external keyboard if
      available, I'll need to do this at home and at the office, even if both
      keyboards are the same make and model).
  * Mouse
    * Scroll speed: PRN. Depends on my mood. Usually bump up 1 or 2 steps.
    * Uncheck "Natural" scroll direction. It's 2023, Apple. Why haven't you
      figured out that mouse wheels are different hardware than a trackpad.
  * Apple ID
    * Use itunes@ account. Need: access to Liz's iPad for verification code.
    * Once signed in, click Apple ID and identify any old/expired laptop(s)
      still attached to itunes and remove them.
* Time Machine
  * It's 2023 and I still haven't figured out how to restore a TM from a
    previous laptop. But if I connect the NEW laptop to the same drive, all the
    old backups vanish. Yep. That is a thing that I know now. (Fortunately this
    was the most heavily alternatively-backed-up laptop I've ever had. So, inb4
    next laptop change: make sure alt backups are happening and can be
    restored.)
* Touch ID
  * Set it up.

# Chrome

* Open Safari
* Type "download google chrome" and hit enter
* Download and install
* Never open Safari again

# Terminal Stuff

* Get iTerm2 if it's not already on the laptop.
* Google homebrew installer & run it
* `ssh-keygen -t rsa`
* Login to github (will need Authenticator on phone), upload ssh key. Look for
  ssh keys from retired devices.

# Homebrew stuff

Note about Python: Just get latest; Python 3.7 is old enough that it literally
has no compilation target for Apple Silicon.

```bash
brew install python
brew install gdal
brew install gpg
brew install ag
brew install colordiff
brew install figlet
brew install tmux tmate
brew install watch
brew install wget

# Or try this:

brew install
ag
bat
colordiff
figlet
gdal
gpg
python
tmate
tmux
watch
wget

```


## My Repos
```bash
( \
cd ~ && \
git clone git@github.com:dbrady/bin.git && \
git clone git@github.com:dbrady/dotfiles.git && \
git clone git@github.com:dbrady/prelude.git .emacs.d && \
cd ~/Documents && \
git clone git@github.com:dbrady/refdox.git
)
```

## Ruby

* Visit https://rvm.io to get latest rvm
* rvm install ruby, rvm use ruby-??? --default
* `(cd ~/Documents/refdox && bash gems_i_always_want)` - As of March 2023, thin
  does not install. Probably a ruby-3 problem but could also be an M1
  problem. It's ok, I never use thin directly but rather as an automagic
  fallback for webrick.

## Terminal Apps Galore

`brew install emacs ag jq chafa tmux tmate markdown tree`


## Apps

* App Store
  * Moom (it will show as $9.99 but when I clicked Buy and approved the purchase
    it said "you have already purchased this, it will be updated for free".)
  * Amphetamine, though this time I just googled Caffeine and got that instead.

* Direct From Provider
  * Mousepose. Search catchall account for license code.
  * Caffeine. Alt: get Amphetamine from the App store.
