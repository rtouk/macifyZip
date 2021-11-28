# macifyZip

See [README](./README.md) for more information

## Changelog

### Version 1.3

- If exactly one file exists in ZIP, assume you intend to modify that file's permissions
- Improved normalization of input file paths

### Version 1.2

- Hide directory records in ZIP contents list unless `--directories` is specified
- Show UNIX permissions in standard octal format
- Fixed bug where relative ZIP path may not be resolved to absolute path
- Improved error messages and output word-wrapping

### Version 1.1

- Added `--browse` mode, and made it the default if no commandline args specified
- Added build for MacOS and packaged binaries into `-windows`, `-macos` ZIPs
- Improved README

### Version 1.0

- Initial release
