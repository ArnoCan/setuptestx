
.. _HOWTO_EXTENDED_TESTS:

Howto Extended the TestsX Class
-------------------------------

The *setuptestx* provides two call APIs.
The call by the imported class, which is used by the included *setup.py*,
and an entry point, for the standard application, which does not need any 
modification of the *setup.py*. 

0. The standard entry point does not require any modification of the *steup.py*.

1. For derived custom classes: 

   a. Import in your :ref:`setup.py <SETUP_PY>` for example:
   
         ::
         
            #
            # setup extension modules
            #
            from setuplib import usage
            from setuptestx.testx import TestX  # for unit tests
   
            class testx(TestX):
                def __init__(self, *args, **kargs):
                    TestX.__init__(self, *args, **kargs)
   
   b. Hook them in e.g. as a command in your :ref:`setup.py <SETUP_PY>` by:
   
         .. parsed-literal::
         
            setup(
                cmdclass={                           # see [setuppy]_ and :ref:`setup.py <SETUP_PY>` 
                    'testx': testx,
                },
                ...
            )

2. Use it from the command line call for example by:

      .. parsed-literal::
      
         python :ref:`setup.py <SETUPPYSRC>` :ref:`testx <setuplibCOMMANDS_testx>`

