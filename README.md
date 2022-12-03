# N64 Decomp Template

The absolute minimum to start decompiling an N64 game.

# WARNING
This repository is completely unfinished, but it may provide some useful information to those starting.
It is not recommended to use this template at this time unless you know exactly what is missing to get going.

# Usage
### Prerequisites
- Your legally obtained desired game's rom in Z64 format
- CLONE AS RECURSIVE
    - ex: `git clone --recursive https://github.com/BttrDrgn/n64decomp-template`
- Some form of Linux; whether it be WSL, virtual machine, or booted
- python >=3.8
- pip
- mips binutils
    - [mips64-binutils](https://aur.archlinux.org/packages/mips64-elf-binutils) (Arch)
    - mips-linux-gnu (Ubuntu)
    - TODO: more options

### Steps
#### Prereq #2
- Install the required python packages for splat by running `pip install -r tools/splat/requirements.txt`
    - This installs all depdencies used by splat
- Place your obtained rom in the root of the repo named `baserom.z64`
    - ex: `baserom.us.z64`
    - Recommended region codes:
        - us
        - eu
        - jp

#### Splat Yaml
- Run `python3 tools/splat/create_config.py baserom.z64` to initalize your yaml for splat
- Copy the SHA1 at the top, make a new file on root named `(GAME).sha1` and do the following inside the file
    - `(COPIED-SHA1) build/(GAME).z64`
    - SHA1 is not in parentheses! Just paste it.

#### Makefile
- Edit `BASENAME = my-game` at the top to `BASENAME = (GAME)`

#### Compiling
- Extract the ROM files with `make extract`
- Build the dumped ROM with `make`
    - Optionally add the `-j(n)` argument to increase the thread count
- Run `make distclean` to completely clean your directory
- All-in-one version: Run `./tools/clean-build.sh`
    - This runs `make distclean && make extract && make -j6`
- If all is well, you should see `build/(GAME).z64: OK` in the terminal!