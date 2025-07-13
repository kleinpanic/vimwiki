# Unsorted Knowledge 


## x-www-browser

- x-www-browser is a symbolic command name provided by Debian's update-alternatives system. It is not a real browser, but rather a symlink that points to a preferred graphical web browser. 
It runs whatever browser binary is linked to that name via Debina's alternatives system. This allows any script, user, or application to launch a web browser without hardcoding the name of a specific browser. 
The system uses the update-alternatives mechanism to maintain symbolic links like: 
```txt
/usr/bin/x-www-browser → /etc/alternatives/x-www-browser → /usr/bin/firefox-esr
```


