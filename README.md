# sbsimple

Utility for setting up UEFI secure boot in a simple way.

Focused on Arch Linux + GRUB setups at the moment.

## Features

- Creates passphrase-protected keys & EFI signature lists for signing binaries
- Enrolls EFI keys in system keystore
- Creates two unified kernels (one for default initramfs and another for fallback initramfs)
	- Embeds CPU microcode updates within the unified kernel
- Signs unified kernels
- Creates standalone GRUB image embedding the bootloader configuration, to prevent config tampering
- Adds password protection to GRUB, which prevents unauthorized access to the GRUB command line at boot
- Signs standalone GRUB image
- Adds Pacman hooks to:
	- Update the unified kernels upon update of Linux
	- Update the GRUB standalone image upon update of GRUB

## Installation

### Arch AUR

AUR helper:
```
yay -S sbsimple
```

Manual:
```
git clone https://github.com/djandries/sbsimple
cd sbsimple
makepkg -si
```

### Other distros / manual

```
git clone https://github.com/djandries/sbsimple
cp ./sbsimple/sbsimple* /usr/local/bin/
```

## Usage

To perform everything described in the features list, run:

```
sudo sbsimple setup
```

To revert the setup, run:

```
sudo sbsimple remove
```

The actions described in the features list can also be executed independently/one-by-one. Run `sudo sbsimple` to display the available commands.
