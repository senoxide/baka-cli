# baka cli

system utility cli for gentoo/arch based desktops, written in lua.

commands are just lua modules and config lives in one file, so it's easy to extend or rip apart. works on systemd and openrc.

## install
```bash
git clone https://github.com/sixteenjune/baka-cli
cd baka-cli
chmod +x baka.lua
./baka.lua init
```

## usage

baka <command> [args]

- init — initial setup or reconfigure
- status — system overview
- update — sync and update packages
- rebuild — full system rebuild
- clean — remove old packages and orphans
- backup — timestamped backups of dotfiles and /etc
- kernel — build and install the kernel from /usr/src/linux
- services — interactive start/stop menu for systemd/openrc
- cpu, temp, battery, network, storage, ports — system info
- doctor — sanity-check the setup
- help — list everything

## writing your own commands

copy `commands/_template.lua` to `commands/<name>.lua` and register it in `commands/init.lua`. if your command needs distro/init/vpn backends, require them inside `M.run`, not at the top level.

## requirements

- lua 5.1+
- doas or sudo
- gentoo or arch; systemd or openrc

optional: nerd font for icons, netbird/tailscale for vpn status, dracut + grub/limine for the kernel workflow.
