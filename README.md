# void-s6
experimental s6 init support for void

## HOW-TO

* Build and install `s6-linux-init`

* Boot with kernel parameter: `init=/etc/s6-linux-init/current/bin/init`

Note: mistyping this into a nonexisting path still makes the system boot via
runit.

* Shutdown with binary: `/etc/s6-linux-init/current/bin/poweroff`

Note: if runit's `poweroff` is run by mistake, it will simply error out with no
bad consequences.

Upon successfull boot, an early getty that allows login should be present.

## TODO

replicate void init scripts
