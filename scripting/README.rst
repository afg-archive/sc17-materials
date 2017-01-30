Scripting exercises
===================

.. highlight:: bash

Deadline
--------

2/8 23:59

We will use ``$ stat filename`` to check your submission time.

Submission
----------

Create and put your scripts under the directory ``/home/username/homework/scripts``

Namely, if your username is QQ, then the scripts should be:

* ``/home/QQ/homework/scripts/recur-sha1sum``
* ``/home/QQ/homework/scripts/envmath``
* ``/home/QQ/homework/scripts/finddep``

Judge
-----

Type ``judge-scripts`` in the command line to judge sample testcases.

Type ``judge-scripts --all`` in the command line to judge all testcases.

Notes
-----

You are allowed to write the scripts in any programming language, just remember to mark the shebang!

For example, if your write your script in bash, then put::

  #!/bin/bash
  
at the beginning of the file.

If using python, then put::

  #!/usr/bin/env python3
