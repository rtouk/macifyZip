# macifyZip

Tool for fixing zipped Mac app permissions

[Download for Windows](./macifyZip-windows.zip?raw=true) · [Download for Mac](./macifyZip-macos.zip?raw=true) · [Changelog](./CHANGELOG.md)

## The Problem

Have you ever zipped a MacOS app on another OS (eg. Windows) and then discovered it wouldn't run when unzipped on a Mac?

![](./example-error.png)

For it to work, the ZIP must contain the [correct UNIX executable permissions](https://superuser.com/questions/1345755/how-to-fix-the-application-cant-be-opened-on-mac) stored as ["External Attributes"](https://unix.stackexchange.com/questions/14705/the-zip-formats-external-file-attribute). Since MacOS 10.15 Catalina, [the files must also be marked as being zipped on UNIX](https://forum.xojo.com/t/catalina-unzip-file-permissions-problems/52435/11). When zipped on other OS, these attributes are usually different or blank!

## The Solution

The solution is to modify certain file attributes, as if it had been zipped on a Mac.

Specifically, the "Creation System" must be set to **3** (UNIX) and the "External Attributes" must be set to **0755** (typical Mac executable).

There are some [Python scripts](https://gist.github.com/Draknek/3ce889860cea4f59838386a79cc11a85) and similar tools that partially do this.  
*macifyZip* simplifies it to one terminal command (or one Explorer drag-and-drop), zero dependencies.

## Usage

*macifyZip* can apply the above fixes to one or more ZIP files at a time:

    macifyZip ZIPFILE
    macifyZip ZIPFILE1 ZIPFILE2 ...

On Windows, this is equivalent to drag-and-dropping the ZIP files onto `macifyZip.exe`

Since **v1.1**, you can pass `--browse` (or no args at all) for a browse dialog.

The input ZIP file will be overwritten, unless you specify `--outputZip FILE`

*macifyZip* looks for contained files in the format `*.app/Content/MacOS/*`, but you can modify specific contained files with `--modifyAttr FILE` or all files with `--all`

For the full output of `macifyZip --help`, see [help.txt](./help.txt)
