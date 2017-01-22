envmath
=======

Practice of using environment variables.

Problem description
-------------------

Write a script ``envmath`` to do some simple math.

The script should support three operations: ``+``, ``-``, ``*``

The operands are passed with environment variables, which are ``A``, ``B``, as well as the operator ``OP``.

Standard output
---------------

Your script should output a single integer containing the result of the calculation.

Exit code
---------

Your script should indicate if any input is invalid.

* The return value should be masked with 8 if ``A`` is not a valid integer.
* The return value should be masked with 16 if ``B`` is not a valid integer.
* The return value should be masked with 32 if ``OP`` is not a valid operator.

Sample I/O
----------

operator ``+``::

  $ env A=3 B=34 OP='+' ./envmath 
  37
  $ echo $?
  0

operator ``-``::

  $ env A=91 B=183 OP='-' ./envmath 
  -92
  $ echo $?
  0

operator ``*``::

  $ env A=94 B=87 OP='*' ./envmath 
  8178
  $ echo $?
  0

missing ``B`` (output nothing, return 16)::

  $ env A=6 OP='+' ./envmath
  $ echo $?
  0
  
missing ``A`` and ``OP``::

  $ env B=65536 ./envmath
  $ echo $?
  40
  
bad values (``A`` and ``B`` are not integers, ``OP`` is not supported)::

  $ env A=3.5 B=4.5 OP='/' ./envmath
  $ echo $?
  56
  
large values should be supported::

  $ env A=123456789 B=123456789123456789123456789 OP='*' ./envmath
  15241578765432099765432099750190521
  $ echo $?
  0
  
Hints
-----

* ``bc`` -- if using the shell
* `os.getenv <https://docs.python.org/3/library/os.html#os.getenv>`_ `sys.exit <https://docs.python.org/3/library/sys.html#sys.exit>`_ -- if using python
