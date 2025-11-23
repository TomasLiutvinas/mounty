# mounty / unmounty

CLI helpers for quickly mounting and unmounting removable storage devices on Linux.  

## Features

### mounty
- Shows only real partitions (never whole disks)
- Excludes swap, already-mounted partitions, and internal system partitions under 10 GiB
- Displays: device path, size, filesystem, label, model
- Only offers free `/mnt/*` directories
- Fully interactive via `fzf`

### unmounty
- Uses `findmnt -P` for stable key=value parsing
- Lists all active mounts under `/mnt/*`
- Cleans noisy source names (e.g. `/dev/sda2[/mnt/...`)
- Pretty aligned table
- Safe unmount by numeric index

## Requirements

- Python 3
- fzf
- util-linux tools (`mount`, `umount`, `lsblk`, `findmnt`)

### Install on Arch Linux

```bash
sudo pacman -S python fzf util-linux
```

## Installation

Clone the repository:

```bash
git clone https://github.com/<yourname>/mounty
cd mounty
```

Make scripts executable:

```bash
chmod +x mounty
chmod +x unmounty
```

add user-level commands:

```bash
ln -s "$(pwd)/mounty" ~/.local/bin/mounty
ln -s "$(pwd)/unmounty" ~/.local/bin/unmounty
```

ensure `~/.local/bin` is in your path:

```bash
echo $path
```

## usage

### mount a device

```bash
sudo mounty
```

1. choose a device  
2. choose a mountpoint under `/mnt/*`  
3. mounty performs the mount

### unmount a device

```bash
sudo unmounty
```

1. choose a mounted entry under `/mnt/*`  
2. unmounty performs the unmount

## suggested mountpoint layout

```bash
sudo mkdir -p /mnt/{sdcard,12tb,dexter,floki,vbear,temp}
```

mounty will show only unused mountpoints.

## Safety

### mounty
- Never mounts raw disks (`/dev/sdX`)
- Never shows small internal OS partitions
- Never creates directories automatically

### unmounty
- Only touches mounts under `/mnt/*`
- Never touches system mounts (`/`, `/home`, `/boot`, …)
- Works safely with labels containing spaces

## License

MIT
