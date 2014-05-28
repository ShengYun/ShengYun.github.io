---
layout: post
title: Migrate from wordpress to github pages
---

<div class="message">
  The following content was on my wordpress blog page, I'm now migrating to github pages.
</div>

## This is my first blog, so hello:)

> I’m going to write something about my new Macbook Air. I was really cynic, refused to use any apple’s products, just because apple’s control freak and arrogant attitude. Anyway I switched back to OSX after 2 years experience with some popular linux distros, ubuntu, fedora, and opensuse. Just being tired to fix my computer before working, or entertaining. And by the way, most software I use runs on OSX nice. After all, OSX gave me the Unix feeling I love. And their hardware really rocks, seriously. I’m going to make a checklist about the software I installed on my MBA. Just in case I need to install them again in the future.

### Softwares to install
- Update the system, if any is required
- Assign Capslock to Ctrl
- Install XCode from App Store
- While waiting for XCode, install the following(These software’s official website’s can be googled by their names):
- firefox(with xmarks, imacro, firebug, flash, Vimperator)
- chrome
- Dash (App Store)
- AppCleaner
- Adium
- QQ
- Android adt-bundle
- calibre
- Copy
- Dropbox
- Go2Shell
- iTerm2 (with the solarized theam)
- Sublime Text 3 (ofcourse with Package Control)
- mplayerx
- Keka
- Microsoft Office 2011
- SourceTree
- uTorrent
- VMware Fusion
- sogou input method
- Love Wallpaper HD
- DeJavu fonts
- Paragon NTFS (is there any opensource alternatives?)
- a bunch of games:)
- I think now XCode is installed:), so open it and install the command line utitlies. (XCode -> Preferences -> Downloads -> Command Line Tools)
- Ok now lets brew something:)
- Install brew (instructions [here](http://brew.sh/))
- brew install python ([need to override OSX’s python path](http://stackoverflow.com/questions/5157678/python-homebrew-by-default/14645426#14645426), [here](https://gist.github.com/ShengYun/6887784) is my bash_profile)
- brew install kdiff3
- brew install macvim (update it with my vim settings [here](https://github.com/ShengYun/dbsvim), also put mvim in a folder which exists in PATH, usually ~/bin)
- brew install ctags
- brew install cscope
- brew install global
- brew install wget
- brew install curl
- brew install git ([here](http://www.codethatmatters.com/2010/01/git-autocomplete-in-mac-os-x/) is how to let git auto complete, and [here](https://gist.github.com/ShengYun/6864130) is my .gitconfig)
- brew install ack
- pip install autopep8
- pip install pep8
- pip install jedi
- pip install virtualenv
- Install the latest wxPython from their official website
- The last thing is to configure kdiff3 a little, version 0.9.97 has a bug, and we need to upgrade kdiff3 to an upper version
- brew uninstall kdiff3
- git clone git://git.code.sf.net/p/kdiff3/code kdiff3-code
- compile it (./configure qt4)
