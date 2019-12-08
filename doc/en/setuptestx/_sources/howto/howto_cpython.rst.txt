
.. _HOWTO_CPYTHON:

Howto CPython
-------------

Howto Display Info on Called CPython
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
The data on the current called CPython implementation release could be
fetched by::

   python setup.py testx --print-vinfo           # as default on newer Linux
   python setup.py testx --print-vinfo -i python

Printing for example for Python-3.8.0::

   running testx
   category           = python
   disttype           = python3.8
   dist               = cpython
   distrel            = 3.8.0
   hexrelease         = 0xb4043200
   compiler           = GCC
   compiler_version   = 0.0.0
   implementation     = /home/acue/venv/3.8.0/bin/python


The same call for Python-2.7.15::

   python setup.py testx --print-vinfo -i python2

Printing for example for Python-2.7.15::

   running testx
   category           = python
   disttype           = python2.7
   dist               = cpython
   distrel            = 2.7.15
   hexrelease         = 0xa38421cf
   compiler           = GCC
   compiler_version   = 0.0.0
   implementation     = /usr/bin/python2
   
