
# Linux Snippets

#### Debian-based bias.


## Chmod Server Directory

    find <dir>/ -type d -exec chmod 755 {} +

    find <dir>/ -type f -exec chmod 644 {} +


## Clear APT cache

Clear `/var/cache/apt/archives/` archive files.

    sudo apt-get clean


## Crashes

### Cinnamon restart

    Alt + F2
    r
    <Enter>                     # non-destructive action

    Ctrl + Alt + F1
    sudo service mdm restart    # destructive = logout, apps lost
    Ctrl + Alt + F8

### updates crash

    apt check                   # show errors on last install
    dpkg --configure -a         # fix last install errors
    <reboot>

### X

#### program crash in X

e.g. Firefox

    Ctrl + Alt + F1
    pgrep -lf firefox
    kill <pid>
    Ctrl + Alt + F8

#### restart frozen X

    Ctrl + Alt + Backspace


## Kernels - remove old

    dpkg --list | grep linux-image     # list

    sudo apt-get install byobu
    sudo purge-old-kernels --keep 4    # one of many ways, but quite safe, proven


## Search Codebase

### filename

    find <dir> -name <file>

### text

    grep -rn <cs_text> <dir>

### files created/modified in last day

    find <dir> -type f -mtime 0
