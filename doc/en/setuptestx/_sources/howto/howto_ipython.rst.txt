
.. _HOWTO_IPYTHON:

Howto IPython
-------------

Howto Display Info on Called IPython
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
The implementation *IPython* is here a bit a special case, because it consists mainly on
a set of  libraries based on the standard *CPython* implementation.
Anyhow, due it's specific support for interactive processing a number of details are different
from the standard *CPython*.

The data on the current called IPython implementation release could be
fetched by::

   python setup.py testx --print-vinfo -i ipython
   python setup.py testx --print-vinfo -i ipython3

Printing for example for IPython-7.8.0::

   category           = python
   disttype           = python3.8
   dist               = cpython
   distrel            = 7.8.0
   hexrelease         = 0xb4047200
   compiler           = GCC
   compiler_version   = 0.0.0
   implementation     = /home/acue/venv/3.8.0/bin/python3


The same call for IPython-5.5.0::

   python setup.py testx --print-vinfo -i ipython2

Printing for example for IPython-5.5.0::

   category           = python
   disttype           = python2.7
   dist               = cpython
   distrel            = 5.5.0
   hexrelease         = 0xa3845140
   compiler           = GCC
   compiler_version   = 0.0.0
   implementation     = /usr/bin/python2
   
