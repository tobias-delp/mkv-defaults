# mkv-defaults

A small interactive command-line utility for setting the default audio and
subtitle tracks across a directory of Matroska (`.mkv`) files.

It is written in Python and uses MKVToolNix to edit Matroska headers in place.
Audio and video are not re-encoded.

## Features

- Lists all audio tracks and lets you choose the default.
- Lists all subtitle tracks and lets you choose the default.
- Applies the selection to all MKVs in a directory.
- Clears the default flag from all other audio/subtitle tracks.
- Checks track language, name, and codec against the first episode before editing.
- Works from Bash, Fish, Zsh, or any other shell.
- Accepts the current directory or a directory argument.

## Dependencies

- Python
- MKVToolNix CLI (`mkvmerge` and `mkvpropedit`)

The Arch package declares these dependencies, so `makepkg -si` can install
missing packages through pacman.

## Install on Arch Linux / Manjaro

Install the Arch build tools if needed:

```sh
sudo pacman -S --needed base-devel
```

Clone the repository and install:

```sh
git clone https://github.com/YOUR_USERNAME/mkv-defaults.git
cd mkv-defaults
makepkg -si
```

Before publishing your repository, replace `YOUR_USERNAME` in this README and
in `PKGBUILD`.

## Usage

Process MKVs in the current directory:

```sh
mkv-defaults
```

Process another directory:

```sh
mkv-defaults "/path/to/anime/Season 2"
```

Show help or version:

```sh
mkv-defaults --help
mkv-defaults --version
```

The program uses the first MKV as the reference, asks which audio and subtitle
tracks should be defaults, shows the choices, and asks for confirmation before
modifying any files.

## Safety

Before editing each file, the program compares its audio and subtitle layout
with the reference file using track language, track name, and codec. Files with
a different layout are skipped rather than edited blindly.

MKVToolNix changes only the relevant Matroska header metadata; the media streams
are not re-encoded.

## Uninstall

```sh
sudo pacman -Rns mkv-defaults
```

## Updating the package

After editing the `mkv-defaults` executable, update its checksum in `PKGBUILD`.

With `pacman-contrib` installed:

```sh
updpkgsums
```

Or calculate it manually:

```sh
sha256sum mkv-defaults
```

For a new release, update `VERSION` in `mkv-defaults`, update `pkgver` in
`PKGBUILD`, and reset `pkgrel` to `1`.

## License

MIT
