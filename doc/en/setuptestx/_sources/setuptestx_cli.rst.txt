
.. _SETUPTESTXCOMMANDSCLI:

**********************
Command Line Interface
**********************

The package *setuptestx* provides the extension command *testx* for the standard 
command line interface of *setup.py*.

   .. parsed-literal::

      :ref:`python setup.py testx <setuplibCOMMANDS_testx>`


With the additional common local options fo *setup.py*:

   .. raw:: html

      <div class="tmptab">
      <div class="overviewtab">
   
   +----------------------------------------------------------------------+-----------------------------------------------------+
   | :ref:`--sdk <setuptestxOPTIONS_sdk>`                                 | Extends the dependencies for development utilities. |
   +----------------------------------------------------------------------+-----------------------------------------------------+
   | :ref:`--no-install-requires <setuptestxOPTIONS_no-install-requires>` | Deactivates pre-requisites.                         |
   +----------------------------------------------------------------------+-----------------------------------------------------+
   | :ref:`--offline <setuptestxOPTIONS_offline>`                         | Deactivates PyPi access.                            |
   +----------------------------------------------------------------------+-----------------------------------------------------+
   | :ref:`--help-setuplib <setuptestxOPTIONS_help-setuplib>`             | Displays help for *setuplib*.                       |
   +----------------------------------------------------------------------+-----------------------------------------------------+

   .. raw:: html
   
      </div>
      </div>


.. _setuplibCLISYNOPSIS:

SYNOPSIS
========

.. parsed-literal::

   setup.py :ref:`[Global-OPTIONS] <setuplibCLIOPTIONS>` :ref:`[COMMANDS-with-context-OPTIONS] <setuplibCOMMANDS>` 

.. _setuplibCLIOPTIONS:


GLOBAL OPTIONS
==============

.. index::
   pair: options; --sdk
   pair: setuplib; --sdk

.. _setuptestxOPTIONS_sdk:

-\-sdk
------
Supports a separate dependency list for the build and packaging environment.
The following informal convention has to be implemented within the file *setup.py*.

   .. parsed-literal::
   
      __sdk = False
      """Set by the option "--sdk". Controls the installation environment."""
   
      if '--sdk' in sys.argv:
          _sdk = True
          sys.argv.remove('--sdk')
   
   
      _packages_sdk = find_packages(include=['setuplib'] )  # your development packages
      """Python packages to be installed."""
   
   
      if __sdk: # pragma: no cover
          try:
              import sphinx_rtd_theme  # @UnusedImport
          except:
              sys.stderr.write("WARNING: Cannot import package 'sphinx_rtd_theme', cannot create local 'ReadTheDocs' style.")

          _install_requires.extend(
              [
                  'sphinx >= 1.4',
                  'epydoc >= 3.0',
              ]
          )
   
          _packages = _packages_sdk

For an example refer to *setup.py* of *setuplib*.

.. index::
   pair: options; --no-install-requires
   pair: setuplib; --no-install-requires

.. _setuptestxOPTIONS_no-install-requires:

-\-no-install-requires
----------------------
Suppresses installation dependency checks,
requires appropriate PYTHONPATH.
The following informal convention has to be implemented within the file *setup.py*.

   .. parsed-literal::
   
      __no_install_requires = False
   
      if '--no-install-requires' in sys.argv:
          __no_install_requires = True
          sys.argv.remove('--no-install-requires')
   
   
      if __no_install_requires:
          print("#")
          print("# Changed to offline mode, ignore install dependencies completely.")
          print("# Requires appropriate PYTHONPATH.")
          print("# Ignored dependencies are:")
          print("#")
          for ir in _install_requires:
              print("#   "+str(ir))
          print("#")
          _install_requires=[]

For an example refer to *setup.py* of *setuplib*.

.. index::
   pair: options; --offline
   pair: setuplib; --offline

.. _setuptestxOPTIONS_offline:

-\-offline
----------
Sets online dependencies to offline, or ignores online
dependencies.
The following informal convention has to be implemented within the file *setup.py*.

   .. parsed-literal::
   
      __offline = False
   
      if '--offline' in sys.argv:
          __offline = True
          __no_install_requires = True
          sys.argv.remove('--offline')

For an example refer to *setup.py* of *setuplib*.

.. index::
   pair: options; --help-setuptestx
   pair: setuptestx; --help-setuptestx

.. _setuptestxOPTIONS_help-setuplib:

-\-help-setuptestx
------------------
Special help for *setuptestx*.

For an example refer to *setup.py*.

.. _setuplibCOMMANDS:


COMMANDS
========

   .. index::
      pair: command; build_docx
      pair: command; dist_docx
      pair: command; install_docx

   
   .. raw:: html

      <div class="tmptab">
      <div class="overviewtab">
   
   +---------------------------------------+-----------------------------------------------------------------------+
   | :ref:`testx <setuplibCOMMANDS_testx>` | Call regression tests, and poll information on execution environment. |
   +---------------------------------------+-----------------------------------------------------------------------+

   .. raw:: html
   
      </div>
      </div>


 
.. index::
   pair: commands; testx
   pair: setuplib; testx

.. _setuplibCOMMANDS_testx:

testx
-----
Calls *unittest* in the subdirectory *tests*.
Supports multiple *Python* implementations, including all major implementations. 

.. index::
   pair: testx; --abs

-\-abs
^^^^^^
Change all paths where possible to absolute.

   .. parsed-literal::
   
      setup.py testx --abs

.. index::
   pair: testx; --call

-\-call=
^^^^^^^^
Call of tests, default 'CallCase.py'.

   .. parsed-literal::
   
      setup.py testx --call=<call-program>  # see *unittest* '-p'
      setup.py testx -p <call-program>      # see *unittest* '-p'

.. index::
   pair: testx; --coff

-\-coff
^^^^^^^
JYTHON: set cache off

   .. parsed-literal::
   
      setup.py testx --coff

sets

   .. parsed-literal::
   
      jython -Dpython.cachedir.skip=true

.. index::
   pair: testx; --implementation

-\-implementation=
^^^^^^^^^^^^^^^^^^
The Python implementation, default is 'python' - CPython.
Changes to e.g. 'jython' needs eventually additional options.
Tested values are: python, jython, ipython, ipy, pypy.

Call of tests, default 'CallCase.py'.

   .. parsed-literal::
   
      setup.py testx --call=<python-implementation>
      setup.py testx -i     <python-implementation>

.. index::
   pair: testx; --jyjar

-\-jyjar=
^^^^^^^^^
JYTHON: switch to call of 'java -jar <use-jython-jar>',
requires absolute path.

   .. parsed-literal::
   
      setup.py testx --jyjar=<use-jython-jar>
      setup.py testx -j <use-jython-jar>

      # default: jython, not 'jython.jar'

The default executable names for *Jython* are

   .. parsed-literal::
   
      java -jar jython.jar


.. index::
   pair: testx; --jyjvm

-\-jyjvm=
^^^^^^^^^
JYTHON: Java JVM options for Jyhon: 

   .. parsed-literal::
   
      setup.py testx --jyjvm=<jvm-options>
      setup.py testx -J<jvm-options>

for example:

   .. parsed-literal::

      jython -J-Xmx512m


.. index::
   pair: testx; --jyprop

-\-jyprop=
^^^^^^^^^^
JYTHON: properties '<prop>=<value>',

   .. parsed-literal::
   
      setup.py testx --jyprop='<prop>=<value>'
      setup.py testx -D '<prop>=<value>'

for example:

   .. parsed-literal::

      jython -Dpython.path=/my/path

.. index::
   pair: install_docx; --noexec

-\-noexec
^^^^^^^^^
Print only, do not execute.

   .. parsed-literal::
   
      setup.py testx --noexec

.. index::
   pair: testx; --start

-\-start=
^^^^^^^^^
Start package, e.g. 'tests' or 'tests.setuplib'.

   .. parsed-literal::
   
      setup.py testx --start=<start-package>  # see *unittest* '-s'
      setup.py testx -s <start-package>       # see *unittest* '-s'

.. index::
   pair: testx; --testlib

-\-testlib=
^^^^^^^^^^^
The test library, default 'unittest discover'.

   .. parsed-literal::
   
      setup.py testx --testlb=<module-of-test-framework>  # see *unittest* '-m'
      setup.py testx -m       <module-of-test-framework>  # see *unittest* '-m'

.. index::
   pair: install_docx; --verbose

-\-verbose
^^^^^^^^^^
Verbose flag.

   .. parsed-literal::
   
      setup.py testx --verbose

Passes the verbose flag, e.g. 'jython -v' or 'python -v'.

 
DESCRIPTION
===========

The call interface 'settestx' provides command line extensions for 
the regression tests.

.. _setuplibEXAMPLES:
 

EXAMPLES
========

.. _examples:

* *CPython* - see :ref:`HOWTO_CPYTHON`::

      python setup.py testx --print-vinfo -i python
      python setup.py testx --print-vinfo -i python3
      python setup.py testx --print-vinfo -i python3.5
      python setup.py testx --print-vinfo -i python2

* *IPython* - see :ref:`HOWTO_IPYTHON`::

      python setup.py testx --print-vinfo -i ipython
      python setup.py testx --print-vinfo -i ipython2
      python setup.py testx --print-vinfo -i ipython3

* *IronPython* - see :ref:`HOWTO_IRONPYTHON`:

* *Jython*::

      python setup.py testx --print-vinfo -i jython

* *PyPy* - see :ref:`HOWTO_PYPY`::

      python setup.py testx --print-vinfo -i pypy
      python setup.py testx --print-vinfo -i pypy2
      python setup.py testx --print-vinfo -i pypy3

The *setuptestx* supports hereby basic subprocess calls by *os.system()*,
thus supports the modification of the called environment by shell inheritance.
For example in case of the *bash*::

   PATH=/opt/pypy/pypy3.5-5.10.1/bin/:$PATH python setup.py testx --print-vinfo -i pypy

For more advanced options refer to a never release of the *epyunit* [EPYUNIT]_.


SEE ALSO
========
   :ref:`setuplib <SETUPTESTXCOMMANDSCLI>`,
   [setuptools]_, [distutils]_


LICENSE
=======
   :ref:`modified Artistic License <MODIFIED_ARTISTIC_LICENSE_20>` = :ref:`ArtisticLicense20 <ARTISTIC_LICENSE_20>` + :ref:`Peer-to-Peer-Fairplay-amendments <LICENSES_AMENDMENTS>` 


COPYRIGHT
=========
   Copyright (C)2019 Arno-Can Uestuensoez @Ingenieurbuero Arno-Can Uestuensoez
