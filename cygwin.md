Cygwin Operation
=============================

Xserver
---------------------------------------
1. Install `xorg-server` `xinit` `xorg-docs` `xlaunch` according to [ref](https://x.cygwin.com/docs/ug/setup.html).
2. Find the short-cut of `Xwin Server` and edit its property: add parameters `-- -listen tcp`.
3. Edit `~/.bashrc` in Cygwin and add
    ```
    if [[ -z "$DISPLAY" ]]
    then
        DISPLAY="localhost:0.0"
        export DISPLAY
    fi
    ```
4. Start `Xwin Server` using the short-cut.
5. Connect remote server using `ssh -Y user@server` and try `gedit`.
