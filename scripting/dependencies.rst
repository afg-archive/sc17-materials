Dependencies
============

Problem description
-------------------

SYNTAX: ``finddep REPODATA [PACKAGE]...``

* Write a script/program to find the dependency of the specified package(s).

* REPODATA, the first argument, is a directory, in which the packages' dependencies are specified.

* The packages' dependecies are specified with a file in REPODATA named with the package's name, each separated by a newline.

* PACKAGE, the second to last arguments, are the package(s) the user wishes to install.

* Your script should output what packages will be installed eventually, separated by newlines.

* You are safe to assume that package names do not contain whitespaces.

Example
-------

A user wishes to install ``gcc``, and the repository's data is located at ``/home/shared/repodata``, then he/she would type::

  ./finddep /home/shared/repodata gcc

Your script should read the files in repodata to decide which program are to be installed.  

For example ``gcc`` dependes on ``gcc-libs`` ``binutils`` ``libmpc``, then the file ``gcc`` in REPODATA will be::

  $ cat gcc
  gcc-libs
  binutils
  libmpc
  
And ``gcc-libs`` depends on ``glibc``, ``binutils`` depends on ``glibc`` and ``zlib``...

By resolving the dependencies recursively, your script should output something like::

  gcc
  libmpc
  mpfr
  gmp
  bash
  ncurses
  gcc-libs
  glibc
  filesystem
  iana-etc
  tzdata
  linux-api-headers
  readline
  binutils
  zlib
  
Notes
-----

* The order of the output does not matter
* The output should not contain duplicates

Sample I/O
----------

.. code-block:: text

  $ ./finddep /home/shared/repodata gcc
  gcc
  libmpc
  mpfr
  gmp
  bash
  ncurses
  gcc-libs
  glibc
  filesystem
  iana-etc
  tzdata
  linux-api-headers
  readline
  binutils
  zlib
  
.. code-block:: text

  $ ./finddep /home/shared/repodata openssh
  openssh
  ldns
  dnssec-anchors
  openssl
  perl
  glibc
  filesystem
  iana-etc
  tzdata
  linux-api-headers
  db
  bash
  ncurses
  gcc-libs
  readline
  gdbm
  libedit
  krb5
  keyutils
  libldap
  e2fsprogs
  libutil-linux
  libsasl

.. code-block:: text

  $ ./finddep /home/shared/repodata netcdf
  netcdf
  curl
  libpsl
  icu
  bash
  ncurses
  gcc-libs
  glibc
  filesystem
  iana-etc
  tzdata
  linux-api-headers
  readline
  zlib
  openssl
  perl
  db
  gdbm
  libssh2
  krb5
  keyutils
  libldap
  e2fsprogs
  libutil-linux
  libsasl
  ca-certificates
  ca-certificates-cacert
  ca-certificates-utils
  p11-kit
  libffi
  libtasn1
  findutils
  coreutils
  libcap
  attr
  gmp
  acl
  ca-certificates-mozilla
  hdf5
