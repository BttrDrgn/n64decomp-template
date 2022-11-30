# N64 Decomp Template

The absolute minimum to start decompiling an N64 game.

# Usage
### Prerequisites
- Your legally obtained desired game's rom in Z64 format
- CLONE AS RECURSIVE
    - ex: `git clone --recursive https://github.com/BttrDrgn/n64decomp-template`
- (Optional, but recommended) Arch Linux; whether it be WSL, virtual machine, or booted
    - You can also use Ubuntu
- python >=3.10
- pip3
- [mips64-binutils](https://aur.archlinux.org/packages/mips64-elf-binutils) (AUR)
    - mips-linux-gnu (Ubuntu)

### Steps
### ALL SHELL SCRIPTS ARE RAN FROM ROOT
#### Prereq #2
- Install the required python packages for splat by running `./tools/init-splat.sh`
- Place your obtained rom in the root of the repo named `baserom.(REGION).z64`
    - ex: `baserom.us.z64`
    - Recommended region codes:
        - us
        - eu
        - jp
#### Splat Yaml
- Run `./tools/make-yaml.sh` to initalize your yaml for splat
- Rename the `(GAME).yaml` to `(GAME).(REGION).yaml`
- Open `(GAME).(REGION).yaml` and rename `basename: (GAME)` to `basename: (GAME).(REGION)`
- Copy the SHA1 at the top, make a new file on root named `(GAME).(REGION).sha1` and do the following inside the file
    - `(COPIED-SHA1) build/(GAME).(REGION).z64`
    - SHA1 is not in parentheses! Just paste it.

#### Makefile
- Edit `BASENAME = my-game` at the top to `BASENAME = (GAME)`

#### Compiling
- All-in-one version: Run `./tools/clean-build.sh`
- Otherwise:
    - Run `make extract`
    - Run `make -j6` (or however many threads you desire)
- If all is well, you should see `build/(GAME).(REGION).z64: OK` in the terminal!

### Video Reference
https://user-images.githubusercontent.com/49764143/204761354-8a6ae697-70c3-4142-99a1-1ad0dd4a7274.mp4
