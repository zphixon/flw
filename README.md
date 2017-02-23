
# flw

**f**ocus **l**ast **w**indow

This script came from the fact that [windowchef](https://github.com/tudurom/windowchef)
doesn't focus the last window when the current window is closed. Hacked
together with [microlight](https://github.com/stevedonovan/Microlight),
[wtf](https://github.com/wmutlis/core), and [wew](https://github.com/wmutils/opt).

flw requires wtf and wew to be installed and in `$PATH` to work. Also assumes
that `os.execute` works on your system.

Execute flw with the following:

```
wew -m 2097152 | /path/to/flw
```

You should put this line in your .xsession/.xinitrc to start flw when your WM starts.
Additionally, ml.lua needs to be in a place accessible to the lua interpreter, like
`/usr/share/lua/<lua version>/ml.lua`

