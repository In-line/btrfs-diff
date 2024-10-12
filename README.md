
# btrfs-diff

`btrfs-diff` is a Python script designed to compare two Btrfs snapshots and identify recently modified files, outputting the results in a JSON format. It also provides options for human-readable file sizes and customizable output formatting.

## Features
- Compares two Btrfs snapshots to find recently modified files (using `btrfs subvolume find-new`)
- Outputs results in a hierarchical JSON format showing files and directories.
- Supports human-readable file size output (e.g., KB, MB, GB).
- Configurable JSON indentation for output formatting.
- Can output results to stdout or a specified file.

## Caveats
- `btrfs subvolume find-new` is known to not 100% acurately track all changes. For example it misses deleted files. For further information refer to the BTRFS docs and source code.

## Requirements
- Python 3.x
- btrfs-progs installed on your system
- Root privileges to access Btrfs commands (uses `pkexec`)

## Installation
Clone the repository and make sure you have the necessary dependencies:

```bash
git clone https://github.com/yourusername/btrfs-diff.git
cd btrfs-diff
chmod +x btrfs-diff
```

## Usage

```bash
$ ./btrfs-diff [OPTIONS] <snapshot_old> <snapshot_new>
```

## Options
- -o, --output: Path to the output file (default: stdout).
- -i, --indent: Set the JSON indentation level (default: 4).
- --human, --human-readable-sizes: Output file sizes in human-readable format.

## Example

```bash
su
# Compare Snapper snapshots 8 and 9
btrfs-diff --human /.snapshots/8/snapshot/ /.snapshots/9/snapshot/ | less
```

## License

This script is licensed under the GNU General Public License v3.0 or later.. See the LICENSE file for details.