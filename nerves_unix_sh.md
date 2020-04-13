Q: Is there a way to get access to a bash prompt via ssh? Regular shell access while debugging Nerves Systems (cpu's, linux drivers, etc)

A: There's an old project called [nerves_runtime_shell](https://github.com/nerves-project/nerves_runtime_shell
). it implements the erlang shell behaviour and gets you a semi functional shell

A: There is a setting in erlinit.conf called `run on exit`. You can set it to /bin/sh (or /bin/bash if you have that installed in your system) to mess around after exiting (or crashing) the Erlang VM. 

[Run-on-exit Example](https://github.com/nerves-project/nerves_system_rpi3/blob/master/rootfs_overlay/etc/erlinit.config#L37)

rootfs_overlay/etc/erlinit.config:37:
```shell
--run-on-exit /bin/sh
```
