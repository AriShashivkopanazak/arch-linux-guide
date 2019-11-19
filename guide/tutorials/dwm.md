# How to configure your suckless tools with patching and git

### go to the (suckless)[https://www.suckless.org] website and download a patch

### reset your suckless application (for this tutorial, we will use simple terminal(st) the best terminal out there)
    # make clean && rm -f config.h && git reset --hard origin/master

### make a new branch called "clone"
    # git branch clone
### switch to new branch
    # git checkout clone
    # git branch dracula
    # git checkout dracula
    # git apply path/to/patch
    # git add -A
    # git commit
    # git checkout master
    # make clean && rm -f config.h && git reset --hard origin/master
    # git merge dracula
    # sudo make clean install
