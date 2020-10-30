# void-s6
experimental s6 init support for void

## HOW-TO

* Build and install `s6-linux-init` from [my void-packages branch](https://github.com/st3r4g/void-packages/tree/void-s6)

* Boot with kernel parameter: `init=/etc/s6-linux-init/current/bin/init`

Note: mistyping this into a nonexisting path still makes the system boot via
runit.

* Shutdown with binary: `/etc/s6-linux-init/current/bin/poweroff`

Note: if runit's `poweroff` is run by mistake, it will simply ~~error out with
no bad consequences~~ (after executing `/etc/runit/1`) apparently do nothing.

Upon successfull boot, an early getty is always spawned on `tty7`. Use it to
log in and shutdown if there are no services.

## TODO

* provide `void-s6` package
* turn `/etc/runit/1` into a series of oneshots
