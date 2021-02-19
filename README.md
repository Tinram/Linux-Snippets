
# Linux Snippets

#### Quick-fix snippets for Debian-based distros.


----

#### [Chmod Server Directory](#chmod)
#### [Clear APT Cache](#apt)
#### [Crashes](#crashes)
#### [Low RAM](#lowram)
#### [Remove Old Kernels](#kernels)
#### [Search Codebase](#search)

----


<a id="chmod"></a>
## Chmod Server Directory

```bash
    find <dir> -type d -exec chmod 755 {} +
    find <dir> -type f -exec chmod 644 {} +
```


<a id="apt"></a>
## Clear APT Cache

Clear updates `/var/cache/apt/archives/` *.deb* files.

```bash
    sudo apt-get clean
```


<a id="crashes"></a>
## Crashes

### Cinnamon restart

#### non-destructive action

<kbd>Alt</kbd> + <kbd>F2</kbd>  
<kbd>r</kbd>  
<kbd>Enter</kbd>

#### destructive action &ndash; logout, apps lost

<kbd>Ctrl</kbd> + <kbd>Alt</kbd> + <kbd>F1</kbd>

```bash
    sudo service mdm restart     # Mint
    sudo service gdm3 restart    # Gnome
```

<kbd>Ctrl</kbd> + <kbd>Alt</kbd> + <kbd>F8</kbd>


### kippered OS

<kbd>Alt</kbd> + <kbd>SysReq</kbd> + ( <kbd>R</kbd> <kbd>E</kbd> <kbd>I</kbd> <kbd>S</kbd> <kbd>U</kbd> <kbd>B</kbd> )


### crash during updates

```bash
    apt check                  # show errors on last install
    dpkg --configure -a        # fix last install errors
    [reboot]
```


### X

#### program crash in X

e.g. Firefox is perpetrator

<kbd>Ctrl</kbd> + <kbd>Alt</kbd> + <kbd>F1</kbd>

```bash
    pgrep -lf firefox
    kill <pid>
```

<kbd>Ctrl</kbd> + <kbd>Alt</kbd> + <kbd>F8</kbd>

#### restart frozen X

<kbd>Ctrl</kbd> + <kbd>Alt</kbd> + <kbd>Backspace</kbd>


<a id="kernels"></a>
## Kernels &ndash; remove old

```bash
    sudo apt-get install byobu                       # install for first usage of following command
    sudo purge-old-kernels --keep 3
```

```bash
    dpkg --list | grep linux-image                   # list installed kernels
        [ii  linux-image-4.4.0-157-generic ...]
    sudo apt-get --purge remove linux-image-<XXX>    # XXX = kernel version output from previous command output
    sudo update-grub2
```


<a id="lowram"></a>
## Low RAM Machines

4GB of RAM is not enough now for the demands of resource-hungry websites and applications, which results in memory being swapped to disk (with swapping enabled).

+ HDD: swapping is far too slow
+ SSD: swapping potentially creates excessive wear

Preserve usability: disable swapping and use *earlyoom* to quickly kill a runaway memory hog (faster than the kernel's OOM).

```bash
sudo apt install earlyoom

sudo swapoff -a
```

Comment out the */etc/fstab* swap entry for swapoff permanence.


```bash
    free -m
               total       used       free
    ...
    Swap:          0          0          0
```


<a id="search"></a>
## Search Codebase

### filename

```bash
    find <dir> -name <file>
    find <dir> -not -path '*vendor/*' -name <file>
```

### text

```bash
    grep -rni <text> <dir>
    grep -rni --exclude=\*.{css,html} <text> <dir>
    grep -rni --exclude-dir={vendor,.git} <text> <dir>
```

### files created/modified in last day

```bash
    find <dir> -type f -mtime 0
```


## License

Licensed under the [MIT License](https://github.com/Tinram/Linux-Snippets/blob/master/LICENSE).
