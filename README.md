# void-s6
experimental s6 init support for Void Linux

*Non-invasive*: doesn't touch the standard runit init and tree.
Booting into s6 is done via a kernel parameter (can be setup as a bootloader
entry).

## HOW-TO

* Build and install `s6-linux-init` and `void-s6` from [my void-packages branch](https://github.com/st3r4g/void-packages/tree/void-s6)

**Warning**: the packages contain INSTALL and REMOVE scripts run as root by
`xbps`, double-check before executing them. Install at own risk.

### Boot and shutdown

* Boot with kernel parameter: `init=/etc/s6-linux-init/current/bin/init`

Note: mistyping this into a nonexisting path still makes the system boot via
runit.

* Shutdown with binary: `/etc/s6-linux-init/current/bin/poweroff`

Note: if runit's `poweroff` is run by mistake, it will simply ~~error out with
no bad consequences~~ (now that we source `/etc/runit/1`) apparently do nothing.

Upon successful boot, you should see the usual Void messages on `tty1` and a
getty. In case of problems, an emergency getty is spawned on `tty7`.

### Service management

To enable a service, add it to `/etc/s6-rc/custom/enabled/contents` and run
`vs6-recompile`. It will be started next boot. To start it immediately, also
run `s6-rc change <service>`.

You can check service logs in `/run/uncaught-logs`.

## TODO

* turn `/etc/runit/1` into a series of oneshots
