# cue-normalize

Minimal Bash CLI for normalizing and repairing problematic `.cue` files in large music archives.

## Features

- Recursively scans `.cue` files from the current directory
- Converts legacy encodings to UTF-8
- Removes UTF-8 BOM and CRLF line endings
- Repairs common broken `TITLE`, `PERFORMER`, `SONGWRITER`, `FILE`, and `TRACK` lines
- Tries to resolve broken `FILE` references from adjacent audio files
- Creates centralized backups in `Original_CUE/`
- Uses temporary files and only replaces originals after validation
- Supports `--dry-run` and `--verbose`

## Usage

Run from the root of a music archive:

```bash
cue-normalize --dry-run --verbose
cue-normalize
```

Show help:

```bash
cue-normalize --help
```

Show version:

```bash
cue-normalize --version
```

## Dependencies

Required at runtime:

- `bash`
- `coreutils`
- `findutils`
- `grep`
- `sed`
- `gawk`
- `perl`
- `file`

Optional:

- `uchardet` for better encoding detection

`iconv` is used for charset conversion and is typically provided by `glibc` on Arch Linux.

## Design Philosophy

- Keep it a single Bash script
- Prefer conservative fixes over speculative rewriting
- Use simple Unix tools
- Back up first, then modify
- Skip unsafe cases instead of forcing changes

## Limitations

- Does not fully implement the CUE specification
- Focuses on real-world corruption cases seen in music archives
- Not a full validator
- Cannot make ambiguous `FILE` references safe if multiple audio files match
- Some `libcue` limitations, such as very large track counts, are outside the scope of this tool

## AUR Packaging Notes

The included `PKGBUILD` installs:

- the `cue-normalize` executable to `/usr/bin`
- the MIT license to `/usr/share/licenses/cue-normalize/`

## License

MIT
