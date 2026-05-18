# Steam Deck fan control for debian-based distributions

`jupiter-fan-control` package from SteamOS, repackaged for Ubuntu (and possibly other Debian-based distributions, but haven't tested it on anything else). Controls the fan speed more intelligently than the default BIOS fan curve, based on the temperature of various components, and the current power state of the system. Relies on steamdeck hwmon. Please install the [DKMS module](https://github.com/firlin123/steamdeck-dkms) to get the necessary hwmon support (or use SteamOS kernel, which has it built-in). Works only on Steam Deck, and won't do anything on other hardware.

## Installation
Download the latest .deb file from releases page and install it.

## Building from source
```bash
sudo apt update
sudo apt install -y dpkg-dev debhelper git
git clone https://github.com/firlin123/jupiter-fan-control-deb.git
cd jupiter-fan-control-deb
dpkg-buildpackage -us -uc
```

## Pulling updates from upstream
```bash
sudo apt update
sudo apt install -y dpkg-dev debhelper git wget
git clone https://github.com/firlin123/jupiter-fan-control-deb.git
cp jupiter-fan-control-deb/prepare.sh ./
# Edit the prepare.sh file to set the version variables to the desired version, then run it.
./prepare.sh
cd jupiter-fan-control-deb
rm -r *
mv ../jupiter-fan-control/*/* ./
git add .
# Choose a desired commit message, usually - the version number.
git commit -m "<package version>"
git push
```
