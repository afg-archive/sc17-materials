Checksums
=========

.. highlight:: bash

``md5sum``, ``sha1sum``, ``sha256sum`` are a set of commands that compute the checksum of a file.

For example, to compute the SHA-1 checksum of the file ``report.pdf``, we type the following in the terminal::

  $ sha1sum report.pdf
  
And the command outputs the checksum as well as the filename::

  13d90ad492a888ffc89b235345ff0614228d0ed5  report.pdf
  
The command can also handle multiple files as well::

  $ sha1sum aclocal.m4 config.guess config.sub configure configure.ac install-sh
  db7c4781d04763cfc310626db025e35837aaedf7  aclocal.m4
  3646b015d9a91423feaf2bac86fd2df7ab3564f6  config.guess
  0a7de3085aaa4ea3655c4221574dc9e503035428  config.sub
  38f7ef2ce772fa18067537c4f8df22116196c6ad  configure
  8a589c7bee27c1e6d7f4b54a9c95d2ea295ca10b  configure.ac
  260ef3ac7ec99c50e8c45c82be49465d38f7bb89  install-sh
  
See ``man 1 sha1sum`` for more information.

Problem description
-------------------

SYNTAX: ``recur-sha1sum [DEPTH]``

Write a script ``recur-sha1sum`` to compute the sha1sum of files in a directory recursively.

The script should accept an optional argument to specify the depth of the directory; if the depth is not specified, then allow unlimited depth.

You may output the checksums in any order (e.g. which file's checksum got displayed first does not matter), just make sure that the checksums and files are correct.

The recursive scan should start at the current working directory, therefore it is not passed through the command line.

Sample I/O
----------

For the following directory tree::

  1
  2/
  ├── 3
  └── 4/
      ├── 5
      └── 6/
          ├── 7
          └── 8

``recur-sha1sum`` should output::

  e5fa44f2b31c1fb553b6021e7360d07d5d91ff5e  ./1
  a3db5c13ff90a36963278c6a39e4ee3c22e2a436  ./2/3
  5d9474c0309b7ca09a182d888f73b37a8fe1362c  ./2/4/5
  d3964f9dad9f60363c81b688324d95b4ec7c8038  ./2/4/6/7
  136571b41aa14adc10c5f3c987d43c02c8f5d498  ./2/4/6/8
  
(The leading ``./`` can be ommitted)

``recur-sha1sum 2`` should output::

  e5fa44f2b31c1fb553b6021e7360d07d5d91ff5e  ./1
  a3db5c13ff90a36963278c6a39e4ee3c22e2a436  ./2/3

Hints
-----

* ``find``
* ``xargs``
* type ``man COMMAND`` or ``COMMAND --help`` to see their usage
