docker-experiments
==================

https://github.com/rsp/docker-experiments

Test what tools that are useful in shell scripts are available by default
in Docker containers with some popular distribution minimal images
(or any image).

Prerequisites
-------------
* [Bash](https://www.gnu.org/software/bash/)
* [Docker](https://www.docker.com/)

It should work on any standard Linux distribution. If it doesn't,
please [sumbit an issue](https://github.com/rsp/docker-experiments/issues).

It is written and tested on Ubuntu 14.04
with Docker version 1.5.0, build a8a31ef.

### Note:
Make sure you have sufficient permissions to run `docker`.
You may need to run the scripts with: `sudo ./script-name`.
You need to be in the same directory as the scripts
becasue they run each other with `./script-name`.

Commands
--------

### `check-images "image1 image2 ..."`

E.g. `sudo ./check-images "centos debian ubuntu"`

Checks if the given list of images can be run. Used by other scripts.

### `system-info "image1 image2 ..."`

E.g. `sudo ./system-info "centos debian ubuntu"`

Shows the name and version of the operating system distribution
that is run using that image name.

### `disk-usage "image1 image2 ..."`

E.g. `./disk-usage "busybox debian ubuntu centos"`

Show how much disk usage is shown by the command: `du -sh`
- see: [`du(1)`](http://man7.org/linux/man-pages/man1/du.1.html).

### `test-commands "image1 image2 ..." "command1 command2 ..."`

E.g. `sudo ./test-commands "ubuntu centos" "perl python"

Results of experiments
----------------------

Here are some results of experiments that were done with those scripts.

### Names and versions of OS distributions

Here are the names and versions of OS distros
used by some of the popular images - as of 2015-03-07:

Image | OS
----- | ---
debian | Debian GNU/Linux 7 (wheezy)
ubuntu | Ubuntu 14.04.2 LTS
centos | CentOS Linux 7 (Core)
fedora | Fedora 21 (Twenty One)
opensuse | openSUSE 13.2 (Harlequin) (x86_64)
mageia | Mageia 4
busybox | Buildroot 2014.02
python | Debian GNU/Linux 8 (jessie)
ruby | Debian GNU/Linux 8 (jessie)
perl | Debian GNU/Linux 8 (jessie)
php | Debian GNU/Linux 8 (jessie)
gcc | Debian GNU/Linux 7 (wheezy)
node | Debian GNU/Linux 8 (jessie)
iojs | Debian GNU/Linux 8 (jessie)
redis | Debian GNU/Linux 7 (wheezy)
nginx | Debian GNU/Linux 7 (wheezy)
postgres | Debian GNU/Linux 7 (wheezy)
mysql | Debian GNU/Linux 7 (wheezy)
mongo | Debian GNU/Linux 7 (wheezy)
rethinkdb | Debian GNU/Linux 8 (jessie)
wordpress | Debian GNU/Linux 8 (jessie)

(This data was collected using the command: `./system-info "debian ubuntu centos fedora opensuse mageia busybox python ruby perl php gcc node iojs redis nginx postgres mysql mongo rethinkdb wordpress"`)

Almost every image except specific distributions
seems to be based on Debian - some on version 7, some on 8.

### Disk usage

Here is the disk usage of some of the popular images - as of 2015-03-07:

Image | Disk usage
----- | ----------
busybox | **2.6M**
debian | 97M
nginx | 106M
redis | 123M
mageia | 172M
rethinkdb | 188M
ubuntu | 209M
centos | 224M
postgres | 229M
fedora | 254M
mongo | 261M
opensuse | 284M
mysql | 289M
php | 443M
wordpress | 524M
python | 708M
iojs | 731M
node | 740M
perl | 754M
ruby | 801M
gcc | **1.5G**

(This data was collected using the command: `./disk-usage "debian ubuntu centos fedora opensuse mageia busybox python ruby perl php gcc node iojs redis nginx postgres mysql mongo rethinkdb wordpress"`)

### Test commands

Here are some interesting commands available in some popular images - as of 2015-03-08:

(This data was collected using the command: `./disk-usage "debian ubuntu centos ..." "perl python ruby ..."`

#### Shells:


#### Scripting languages:

. | debian | ubuntu | fedora | centos
---- | ------ | ------ | ------ | ------
perl | YES | YES | NO | NO
python | NO | NO | YES | YES
python3 | NO | YES | NO | NO
lua | NO | NO | YES | YES
ruby | NO | NO | NO | NO

(data from 2015-03-14, collected with `./test-commands "debian ubuntu fedora centos" "perl python python3 lua ruby"`)

* Perl is available in Debian and Ubuntu, but not in Fedora and CentOS.
* Python 2 is available in Fedora and CentOS, but not in Debian and Ubuntu.
* Python 3 is available in Ubuntu, but not in Debian, Fedora and CentOS.
* Lua is available in Fedora and CentOS, but not in Debian and Ubuntu.
* Ruby is not available in either Debian, Ubuntu, Fedora or CentOS.

See also
---------
Those scripts are referenced in the following answers on Stack Exchange:

* [Docker: How to get image size?](http://unix.stackexchange.com/questions/134186/docker-how-to-get-image-size/188717#188717)

Author
------
Rafał Pocztarski - https://github.com/rsp

License
-------
MIT License (Expat). See [LICENSE.md](LICENSE.md) for details.
