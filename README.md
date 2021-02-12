# v4bl-o-matic

This repo contains scripts to automate the process of gathering and organizing files required for the [Vampire4 Boot Loader framework](http://www.apollo-core.com/knowledge.php?b=6&note=32334&z=lqh_vS), created by Willem Drijver.

## Prerequisites

 - commercial software such as [Amiga Forever](https://www.amigaforever.com/) as instructed in the V4BL instructions;
 - a Unixish environment. Windows 10 WSL may do the trick as well (untested);
 - some free command line utilities: [7z](https://7-zip.org), [aria2](https://aria2.github.io), [python3](https://python.org) and [GNU parallel](https://www.gnu.org/software/parallel/);
 - some hands-on experience with your computer's operating system to install packages. On macOS, [`brew`](https://brew.sh).

## Work in progress

This script does not cover all of the awesomeness of v4bl yet, namely:
 - (soon) fail fast if V4BL files have changed (not tested with upcoming 2.7);
 - (soon) any CF card of a different size than 128GB is not yet supported;
 - (soon, partially implemented) sha256 validation of all the downloaded files;
 - (soon) Automated super turbo mode using [fs-uae](https://fs-uae.net);
 - (after) some commercial software packages are not installed yet (iBrowse, etc.);
 - (later) Dockerfile so it can be built into a virtualized environment;
 - games/personal/etc remains a manual process at this time.

## USE AT YOUR OWN RISK.

This script destroys whatever directory you specify as working directory.
Hence, using a working directory such as `/home/yourname` or `C:\Users\yourname` is a BAD IDEA. If you don't understand this, stop RIGHT NOW and use the manual procedure instead.

The script happens to give you a suggestion, typically created in an area of your disk made for temporary files and directories. It is safe and you should not need to change it unless your temporary storage is small (think ramdisk).

## Q&A

### So slowwwwwwwww? And why is my computer heating up? Are you mining stuff on my machine?

A bunch of the files involved in the process are:
 - large;
 - compressed;
 - need to be downloaded;
 - must be serially deflated.

Also, it performs sha256 and integrity checks on some crucial files. This takes time but it fosters a predictable end result.a

Check your system's Activity Monitor/Task Manager/top output. It's likely leveraging all cores to parallelize the work as much as possible during downloads and extraction.
There's room for further optimizations, like extracting archives exactly upon download complete.

Pull requests are welcome, of course!

### How stable?

So far this script has been tested under a Funtoo Linux environment and macOS Big Sur.
As I consider this script to be still in early beta, YMMV.

### What's your development environment?

Developed under Funtoo Linux, with (generally) portability in mind.
Edited with vim, which happens to still be available on Amiga (amazing!)
Scripts are validated with `shellcheck` utility.

### Hey I found a bug...

Please open an issue so it can be tracked. This is a hobby project, contributions are welcome.

## License

MIT
