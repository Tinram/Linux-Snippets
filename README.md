
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

```bash
    find <dir> -type d -exec chmod 755 {} +
    find <dir> -type f -exec chmod 644 {} +
```


<a id="apt"></a>
## Clear APT Cache

Clear `/var/cache/apt/archives/` updates files.

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
    sudo service mdm restart
```

<kbd>Ctrl</kbd> + <kbd>Alt</kbd> + <kbd>F8</kbd>


### kippered box

<kbd>Alt</kbd> + <kbd>SysReq</kbd> + ( <kbd>R</kbd> <kbd>E</kbd> <kbd>I</kbd> <kbd>S</kbd> <kbd>U</kbd> <kbd>B</kbd> )


### updates crash

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
    kill <PID>
```

<kbd>Ctrl</kbd> + <kbd>Alt</kbd> + <kbd>F8</kbd>

#### restart frozen X

<kbd>Ctrl</kbd> + <kbd>Alt</kbd> + <kbd>Backspace</kbd>


<a id="kernels"></a>
## Kernels - remove old

```bash
    sudo apt-get install byobu                     # install for first usage of following command
    sudo purge-old-kernels --keep 4
```

```bash
    dpkg --list | grep linux-image                 # list
    sudo apt-get --purge remove linux-image-XXX    # from above list
    sudo update-grub2
```

<a id="search"></a>
## Search Codebase

### filename

```bash
    find <dir> -name <file>
```

### text

```bash
    grep -rni <text> <dir>
```

### files created/modified in last day

```bash
    find <dir> -type f -mtime 0
```


## License

Licensed under the [MIT License](https://github.com/Tinram/Linux-Snippets/blob/master/LICENSE).
