# Quick Reference to Linux File Paths 

Linux File system directory/folder paths as recommended by the Filesystem Hierarchy Standard 3.0 - modified (reduced for quick reference).   

This quick reference is to help you find/organise things quickly.  

If you are actually developing software for distribution on Linux systems, then you should read the LSB [standard](https://refspecs.linuxfoundation.org/FHS_3.0/index.html) in full. 

## Definitions
- "Shareable" files are those that can be stored on one host and used on others.
- "Unshareable" files are those that are not shareable. For example, the files in user home directories are shareable whereas device lock files are not.
- "Static" files include binaries, libraries, documentation files and other files that do not change without system administrator intervention. 
- "Variable" files are files that are not static.

## Top-level directories summary

| Directory | Purpose |
|-|-|
| /bin | Essential command binaries (e.g. cat, ls) that need to be available in single-user mode, including to bring up the system or repair it, for all users. |
| /boot | Static files of the boot loader |
| /dev | Device files |
| /etc | Host-specific system configuration, sometimes referred to as "Editable Text Configuration" |
| /home | User home directories (optional |
| /lib | Essential shared libraries and kernel modules |
| /lib\<qual\> | Alternate formation essential shared libraries (optional) |
| /media | Mount point for removable media |
| /mnt | Mount point for mounting a filesystem temporarily |
| /opt | Add-on application software packages |
| /root | Home directory for the root user (optional) |
| /run | Data relevant to running processes |
| /sbin | Essential system binaries |
| /srv | Data for services provided by this system |
| /tmp | Temporary files |
| /usr | Secondary hierarchy (complex, shareable, read-only data) |
| /var | Variable data (complex) |

## Full directory breakdown 
(For specific notes on which paths could/should just be symbolic links etc., see the standard.)

| Path | | |Purpose |
|-|-|-|-|
| / ||| Root directory |
| /bin ||| Essential user command binaries (for use by all users). No subdirectories. |
| /boot ||| Static files of the boot loader |
| /dev ||| Device files |
| /etc ||| Host-specific system configuration |
|| /opt || Configuration files for add-on packages stored in /opt |
|| /X11 || Configuration for the X Window System v11 (optional) |
|| /sgml || Configuration files for SGML (optional) |
|| /xml || Configuration files for XML (optional) |
| /home ||| User home directories (optional) |
| /lib ||| Essential shared libraries and kernel modules, i.e. essential for binaries in /bin and /sbin |
| /lib\<qual\> ||| Alternate format essential shared libraries, e.g. 32/64 bit (optional) |
|| /modules || Loadable kernel modules (optional) |
| /media ||| Mount point for removable media (e.g. /media/cdrom) |
| /mnt ||| Mount point for a temporarily mounted filesystem |
| /opt ||| Add-on application software packages. A package to be installed in /opt must locate its static files in a separate /opt/\<package\> or /opt/\<provider\> directory tree. |
| /proc ||| Virtual filesystem providing process and kernel information as files. In Linux, corresponds to a procfs mount. Generally, automatically generated and populated by the system, on the fly. |
| /root ||| Home directory for the root user (optional) |
| /run ||| Run-time variable data. Information about the running system since last boot, e.g., currently logged-in users and running daemons. Files under this directory must be either removed or truncated at the beginning of the boot process, but this is not necessary on (most modern Linux) systems that provide this directory as a temporary filesystem (tmpfs) |
| /sbin ||| Essential system binaries |
| /srv ||| Data for services provided by this system. Site-specific data served by this system, such as data and scripts for web servers, data offered by FTP servers, and repositories for version control systems |
| /sys ||| Kernel and system information virtual filesystem |
| /tmp ||| Temporary files (see also /var/tmp). Often not preserved between system reboots and may be severely size-restricted. |
| /usr ||| Secondary hierarchy for read-only user data; contains the majority of (multi-)user utilities and applications. Should be shareable and read-only data. That means that /usr should be shareable between various FHS-compliant hosts and must not be written to. Any information that is host-specific or varies with time is stored elsewhere. Large software packages must not use a direct subdirectory under the /usr hierarchy |
|| /bin || Non-essential command binaries (not needed in single-user mode), for all users |
|| /include || Directory for standard include files/c header files |
|| /lib || Libraries for programming and packages, i.e. libraries for the binaries in /usr/bin and /usr/sbin. |
|| /libexec || Binaries run by other programs (optional) |
|| /lib\<qual\> || Alternate format libraries (optional) |
|| /local || Tiertiary, local hierarchy - The /usr/local hierarchy is for use by the system administrator when installing software locally. Local data, specific to this host. Typically has further subdirectories (e.g., bin, lib, share). It needs to be safe from being overwritten when the system software is updated. It may be used for programs and data that are shareable amongst a group of hosts, but not found in /usr. Locally installed software must be placed within /usr/local rather than /usr unless it is being installed to replace or upgrade software in /usr |
||| /share | Local architecture-independent hierarchy |
|| /sbin || Non-essential standard system binaries (e.g. daemons for various network services) |
|| /share || Architecture-independent shared data |
||| /color | Color management information (optional) |
||| /dict | Word lists (optional) |
||| /man | Manual pages |
||| /misc | Miscellaneous architecture-independent data |
||| /ppd | Printer definitions (optional) |
||| /sgml | SGML data (optional) |
||| /xml | XML data (optional) |
|| /src || Source code (optional) |
| /var ||| /var contains variable data files - files whose content is expected to continually change during normal operation of the system, such as logs, spool files, and temporary e-mail files. This includes spool directories and files, administrative and logging data, and transient and temporary files. Some portions of /var are not shareable between different systems. For instance, /var/log, /var/lock, and /var/run. Other portions may be shared, notably /var/mail, /var/cache/man, /var/cache/fonts, and /var/spool/news. /var is specified here in order to make it possible to mount /usr read-only. Everything that once went into /usr that is written to during system operation (as opposed to installation and software maintenance) must be in /var. If /var cannot be made a separate partition, it is often preferable to move /var out of the root partition and into the /usr partition. (This is sometimes done to reduce the size of the root partition or when space runs low in the root partition.) However, /var must not be linked to /usr because this makes separation of /usr and /var more difficult and is likely to create a naming conflict. Instead, link /var to /usr/var. Applications must generally not add directories to the top level of /var. |
|| /account || Process accounting logs (optional) |
|| /crash || System crash dumps (optional) |
|| /cache || Application cache data |
||| /fonts | Locally-generated fonts (optional) |
||| /man | Locally-formatted manual pages (optional) |
|| /crash || System crash dumps (optional) |
|| /games || Variable game data (optional) |
|| /lib || Variable state information |
||| /\<editor\> | Editor backup files and state (optional) |
||| /color| Color management information (optional) |
||| /hwclock | State directory for hwclock (optional) |
||| /misc | Miscellaneous variable data |
|| /local || Local files |
|| /lock || Lock files |
|| /log || Log files and directories |
|| /mail || User mailbox files (optional) |
|| /opt || Variable data for /opt |
|| /run || Run-time variable data (now deprecated in favour of /run) |
|| /spool || Application spool data (queues) for jobs waiting to be processed |
||| /cron | cron and at job data |
||| /lpd | Line-printer daemon print queues (optional) |
||| /news | News |
||| /rwho | Rwhod files (optional) |
|| /tmp || Temporary files preserved between system reboots |
|| /yp || Network Information Service (NIS) database files (optional) |   


## Notes from [Wikipedia](https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

- Most Linux distributions follow the Filesystem Hierarchy Standard and declare it their own policy to maintain FHS compliance.
- Some distributions generally follow the standard but deviate from it in some areas. 
- The FHS is a "trailing standard", and so documents common practices at a point in time.

---

## FHS 3.0 Standard Copyright Notice

LSB Workgroup, The Linux Foundation
Version 3.0

Copyright © 2015 The Linux Foundation

Copyright © 1994-2004 Daniel Quinlan

Copyright © 2001-2004 Paul 'Rusty' Russell

Copyright © 2003-2004 Christopher Yeoh

All trademarks and copyrights are owned by their owners, unless specifically noted otherwise. Use of a term in this document should not be regarded as affecting the validity of any trademark or service mark.

Permission is granted to make and distribute verbatim copies of this standard provided the copyright and this permission notice are preserved on all copies.

Permission is granted to copy and distribute modified versions of this standard under the conditions for verbatim copying, provided also that the title page is labeled as modified including a reference to the [original standard](https://refspecs.linuxfoundation.org/FHS_3.0/index.html), provided that information on retrieving the original standard is included, and provided that the entire resulting derived work is distributed under the terms of a permission notice identical to this one.

Permission is granted to copy and distribute translations of this standard into another language, under the above conditions for modified versions, except that this permission notice may be stated in a translation approved by the copyright holder.

March 19, 2015


