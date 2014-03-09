OpenSuSE Mirroring Scripts
==========================

This is a set of scripts we use to maintain our local OpenSuSE packages mirror.

They use mostly rsync, when a mirror is available, but they resort using FTP
when older releases are not available anymore through rsync.

Usage
-----

Create a `mirror` user. Scripts will refuse running as a superuser.

Clone this repository somewhere, and add `CRON` entries in `/etc/cron.d`
for your preferred mirroring schedule.

We are currently mirroring the main opensuse repo and evergreen every
four hours, whilst the buildservice repos are mirrored every eight hours.

Of course, avoid overlapping rsyncs, as you'll exhaust the available
connection slots. 

Goodies
-------

The `ifad-private-repo-update` keeps track of what's in a directory tree,
storing a `.filelist` file in the directory. If something changes, then it
runs `createrepo`. A poor man's private repository, that can be used as
a zypper source, for your enterprise `rpm` packages that you god from your
vendor, and you want to install using standard means.

Customization
-------------

On your own, for now. Scripts rely on paths and repository names, referenced
through the usage of variables in the scripts themselves. If you have the
time to wrap things up and make a nice configuration file, a pull request
will be accepted gladly.

Also, there is some duplication across the scripts - a common `.subr` file
containing shared functions would be great.

Authors
-------

* Marcello Barnaba ([@vjt](https://github.com/vjt))
* Angelo Dell'Aera ([@buffer](https://github.com/buffer))
