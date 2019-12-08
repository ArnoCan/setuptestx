
.. _HOWTO_JYTHON:

Howto Jython
------------
   
Howto Install Setuptools
^^^^^^^^^^^^^^^^^^^^^^^^
For the installation of the setuptool see the 
'The Definitive Guide to Jython' [JythonGuide]_.
   
Howto Online Help
^^^^^^^^^^^^^^^^^
The online help for the *testx* module is displayed by the call:

.. parsed-literal::  

   jython setup.py


Howto Install Java Native Access Modules
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
The 'Java Native Access' - *JNA* - modules are required 
by some of the basic prerequired modules of the author
for *Jython* on *Windows* systems.
For example for *platformids*.
The installation is simply done by copying the required modules, see also [JNA]_.

For example in case of *Windows-10* with the native *OpenSSH* server:

.. parsed-literal::  

   rsync -avHPS  \\
     jna.jar \\
     jna-platform.jar \\
     win32-x86-64.jar \\
     --rsync-path='c:\\\\cygwin64\\\\bin\\\\rsync.exe' \\
     test@w10p:tmp



Howto display information on called Jython
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
The data on the current called Jython implementation release could be
fetched by::

   python setup.py testx --print-vinfo -i jython

Printing for example::

   running testx
   category           = python
   disttype           = python2.7
   dist               = jython
   distrel            = 2.7.1
   hexrelease         = 0xa39821c1
   compiler           = Java
   compiler_version   = 1.8.0.131
   implementation     = /usr/share/jython/bin/jython

By using an alternative local installation::

   PATH=/opt/jython/jython-2.7.0/bin/:$PATH python setup.py testx --print-vinfo -i jython

Printing for example::

   category           = python
   disttype           = python2.7
   dist               = jython
   distrel            = 2.7.0
   hexrelease         = 0xa39821c0
   compiler           = Java
   compiler_version   = 1.8.0.131
   implementation     = /opt/jython/jython-2.7.0/bin/jython


Jython Launcher
"""""""""""""""
available soon

Jython Options
""""""""""""""
available soon

E.g.:


.. parsed-literal::  

   jython -Dpython.cachedir.skip=true setup.py --help

   python -J-Dpython.cachedir.skip=true setup.py --help

Java Options
""""""""""""
available soon

Howto Application Sever
^^^^^^^^^^^^^^^^^^^^^^^
The applications of *Jython* include in particular the configuration and customization of 
Java based application servers.
This requires for several use-cases the deployment of native Java modules/packages as glueware
for the integration - which is supported by the provided *setuplib* 
commands ':ref:`setup.py build_java <setuplibCOMMANDS_build_java>`'
and ':ref:`setup.py build_jy <setuplibCOMMANDS_build_jy>`'.
The application servers with support for *Jython* scripting are for example:

* *Boss Application Server*
* *Oracle Weblogic Server*
* *IBM WebSphere Application Server*


JBoss Application Server
""""""""""""""""""""""""
available soon

Oracle Weblogic Server
""""""""""""""""""""""
available soon

IBM WebSphere Application Server
""""""""""""""""""""""""""""""""
available soon


