**Warning**: Not affiliated with Valve, Steam or anyone else. This script may corrupt your game saves, brick your device and make you reconsider Windows. You have been warned.

## What?

An experimental attempt to use [sniper-runtime](https://gitlab.steamos.cloud/steamrt/steamrt/-/blob/steamrt/sniper/README.md) without [pressure-vessel](https://gitlab.steamos.cloud/steamrt/steam-runtime-tools/-/blob/main/pressure-vessel/README.md).

The idea is to use upstream [bubblewrap](https://github.com/containers/bubblewrap) only and still be able to run Proton and games inside the container.

## Why?

In theory this may yield the following benefits:
- More control over the container, e.g. with `--unshare-net`, `--clearenv`. Only expose what you want to the target binaries
- Space saving (?) - use one shared `STEAM_COMPAT_DATA_PATH` and overlay parts that change between games (`pfx/drive_c/users`)

## So?

This currently kinda sorta works, but
- Is very heavily tied to an Arch host, with an AMD GPU. Most likely only works on my machine.
- Hardcodes a lot of library paths for the overrides. Expect it to break any day now after a `pacman -Syu`

## How?

If you want to try this you will need
- to read the warning again
- download [the sniper runtime image](https://repo.steampowered.com/steamrt-images-sniper/snapshots/latest-container-runtime-public-beta/com.valvesoftware.SteamRuntime.Platform-amd64%2Ci386-sniper-runtime.tar.gz) and unpack it to `~/.local/share/minipv/sniper-runtime`.
- download some version of Proton (e.g. GE-Proton) and extract/symlink to `~/.local/share/minipv/proton`
