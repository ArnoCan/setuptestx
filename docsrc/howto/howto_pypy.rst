
.. _HOWTO_PYPY:

Howto PyPy
----------

Howto Display Info on Called PyPy
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
The data on the current called PyPy implementation release could be
fetched by::

   python setup.py testx --print-vinfo -i pypy

Printing for example for PyPy-5.8.0::

   category           = python
   disttype           = python2.7
   dist               = pypy
   distrel            = 5.8.0
   hexrelease         = 0xa3a05200
   compiler           = Python
   compiler_version   = 2.7.13
   c_compiler         = GCC
   c_compiler_version = 7.2.1
   implementation     = /usr/bin/pypy


The same call for PyPy-5.10.1::

   PATH=/opt/pypy/pypy3.5-5.10.1/bin/:$PATH python setup.py testx --print-vinfo -i pypy
   PATH=/opt/pypy/pypy3.5-5.10.1/bin/:$PATH python setup.py testx --print-vinfo -i pypy3.5

Printing for example for PyPy-5.10.1::

   category           = python
   disttype           = python3.5
   dist               = pypy
   distrel            = 5.10.1
   hexrelease         = 0xb2a05281
   compiler           = Python
   compiler_version   = 3.5.3
   c_compiler         = GCC
   c_compiler_version = 7.2.0
   implementation     = /opt/pypy/pypy3.5-5.10.1/bin/pypy3.5
   
   
