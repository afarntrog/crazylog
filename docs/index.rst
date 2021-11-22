Welcome to crazylog's documentation!
====================================
**crazylog** logs like crazy. Allows to add extensive logging at each step in the python execution cycle.

Installation
*************
.. code-block:: text

   $ pip install -U crazylog


Quick start
============
Run crazylog for everything executed under the context manager.

.. code-block:: python

   ## Basic example
   from crazylog import CrazyLogger
   def foo():
       print('running code ...')
   with CrazyLogger() as crazy:
       foo()



.. toctree::
   :maxdepth: 4
   :caption: Contents

   source/crazylog



Indices and tables
==================

* :ref:`genindex`
* :ref:`modindex`
* :ref:`search`
