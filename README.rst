=========
|Experta|  
=========

|pypi| |version| |tests| |docs| |coverage|

Experta is a Python library for building expert systems strongly inspired
by CLIPS_.

.. code-block:: python

   from random import choice
   from experta import *


   class Light(Fact):
       """Info about the traffic light."""
       pass


   class RobotCrossStreet(KnowledgeEngine):
       @Rule(Light(color='green'))
       def green_light(self):
           print("Walk")

       @Rule(Light(color='red'))
       def red_light(self):
           print("Don't walk")

       @Rule(AS.light << Light(color=L('yellow') | L('blinking-yellow')))
       def cautious(self, light):
           print("Be cautious because light is", light["color"])


.. code-block:: python

   >>> engine = RobotCrossStreet()
   >>> engine.reset()
   >>> engine.declare(Light(color=choice(['green', 'yellow', 'blinking-yellow', 'red'])))
   >>> engine.run()
   Be cautious because light is blinking-yellow

Python Versions
---------------
Only a few recent Python versions are supported.   If you need support for an older Python, you will
need to install an older release.  We normally support the most recent Python  
supported by `PyPy <https://pypy.org>`_ and any versions of CPython with the same or later Python version as the PyPy version. 


Installing
----------
Install from Pypi::
      pip install experta
   

Development
-----------
Install `uv <https://docs.astral.sh/uv/>`_.  Use uv to install Python, set up your virtual environments, etc.

Install experta as an `editable install <https://pip.pypa.io/en/stable/topics/local-project-installs/>`_, including dev dependencies::  
    pip -e .[dev]




Migrating from Pyknow
---------------------

Experta is a Pyknow fork. Just replace any `pyknow` references in your
code/examples to `experta` and everything should work the same.


Examples
--------

You can find some more examples on GitHub_.

.. _CLIPS: http://clipsrules.sourceforge.net
.. _GitHub: https://github.com/nilp0inter/experta/tree/develop/docs
.. |Experta| image:: https://raw.githubusercontent.com/nilp0inter/experta/develop/docs/static/expertalogo_small.png
.. |pypi| image:: https://img.shields.io/pypi/v/experta.svg
    :target: https://pypi.python.org/pypi/experta

.. |version| image:: https://img.shields.io/pypi/pyversions/experta.svg
    :target: https://pypi.python.org/pypi/experta

.. |tests| image:: https://travis-ci.org/nilp0inter/experta.svg?branch=master
    :target: https://travis-ci.org/nilp0inter/experta

.. |docs| image:: https://readthedocs.org/projects/experta/badge/?version=stable
    :target: https://experta.readthedocs.io/en/stable/
    :alt: Documentation Status

.. |coverage| image:: https://codecov.io/gh/nilp0inter/experta/branch/develop/graph/badge.svg
    :target: https://codecov.io/gh/nilp0inter/experta
    :alt: codecov.io

