
# Linux Snippets

#### Maintenance snippets for Debian-based distros.


----

#### [Chmod Server Directory](#chmod)
#### [Clear APT Cache](#apt)
#### [Crashes](#crashes)
#### [Remove Old Kernels](#kernels)
#### [Search Codebase](#search)

----


<a id="chmod"></a>
## Chmod Server Directory

    find <dir> -type d -exec chmod 755 {} +

    find <dir> -type f -exec chmod 644 {} +


<a id="apt"></a>
## Clear APT Cache

Clear `/var/cache/apt/archives/` updates files.

    sudo apt-get clean


<a id="crashes"></a>
## Crashes

### Cinnamon restart

    Alt + F2                    # non-destructive action
    r
    <Enter>

    Ctrl + Alt + F1             # destructive = logout, apps lost
    sudo service mdm restart
    Ctrl + Alt + F8

### updates crash

    apt check                   # show errors on last install

    dpkg --configure -a         # fix last install errors
    [reboot]

### X

#### program crash in X

e.g. Firefox is perpetrator

    Ctrl + Alt + F1
    pgrep -lf firefox
    kill <PID>
    Ctrl + Alt + F8

#### restart frozen X

    Ctrl + Alt + Backspace


<a id="kernels"></a>
## Kernels - remove old

    dpkg --list | grep linux-image     # list

    sudo apt-get install byobu         # install for first usage of following command
    sudo purge-old-kernels --keep 4    # one of many ways, this one is reasonably safe and proven


<a id="search"></a>
## Search Codebase

### filename

    find <dir> -name <file>

### text

    grep -rni <text> <dir>

### files created/modified in last day

    find <dir> -type f -mtime 0


## License

Licensed under the [MIT License](https://github.com/Tinram/Linux-Snippets/blob/master/LICENSE).
