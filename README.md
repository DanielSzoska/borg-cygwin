# borg-cygwin

This creates a standard Windows installer for Borg Backup on 64bit Windows 7 and above.

* The only prerequisite is NSIS installed, available at http://nsis.sourceforge.net/Download
* About 1,5 GB free disk space required to build installer
* Borg install itself will require about ~400 MB
* Tested on Windows 10 Pro 1709 64-bit

---

Create the installer by running install.bat. After creating the installer, run it to install Borg.

Then use borg like this, noting that all file paths are in Cygwin notation e.g. /cygdrive/c/path/to/my/files

```
borg init /cygdrive/D/Borg
borg create -C lz4 /cygdrive/D/Borg::Test /cygdrive/C/Photos/
```

The install script first builds borg inside temporary CygWin subfolder, then installs a much smaller release version into the Borg-installer subfolder. Built packages are copied over, unnecessary files removed, and then NSIS is run.

Tested with CygWin 2.10.0, borgbackup 1.1.4 on Windows 10 Pro 1709 64-bit.
