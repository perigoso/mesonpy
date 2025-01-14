:hide-toc:

***********************************
mesonpy (meson-python) |PyPI badge|
***********************************

.. image:: https://results.pre-commit.ci/badge/github/FFY00/mesonpy/main.svg
   :target: https://results.pre-commit.ci/latest/github/FFY00/mesonpy/main
   :alt: pre-commit.ci status


.. image:: https://github.com/FFY00/mesonpy/actions/workflows/checks.yml/badge.svg
   :target: https://github.com/FFY00/mesonpy/actions/workflows/checks.yml
   :alt: Github Action 'checks' workflow status


.. image:: https://github.com/FFY00/mesonpy/actions/workflows/tests.yml/badge.svg
   :target: https://github.com/FFY00/mesonpy/actions/workflows/tests.yml
   :alt: Github Action 'tests' workflow status


.. image:: https://codecov.io/gh/FFY00/mesonpy/branch/main/graph/badge.svg?token=xcb2u2YvVk
   :target: https://codecov.io/gh/FFY00/mesonpy
   :alt: Codecov coverage status


Python build backend (PEP 517) for Meson_ projects.

It enables Python package authors to use Meson_ as the build backend for their
packages.


How to use?
===========

Please see `getting started`_ for intructions on how to setup your project.

After setting it up, you can use `pypa/build`_ to build the distribution
artifacts.


.. code-block::

   python -m build


We provide a couple configuration options that should be exposed via the build
frontend, like ``builddir``, to specify the build directory to use/re-use. You
can find more information about them in the `build options page`_.


How does it work?
=================

We implement the Python build system hooks, enabling any standards compliant
Python tool (pip_, `pypa/build`_, etc.) to build and install the project.

``mesonpy`` will build a Python sdist (source distribution) or wheel (binary
distribution) from Meson_ project.

The source distribution is based on ``meson dist``, so make sure all your files
are inluded there. In git projects, Meson_ will not include files that are not
checked into git, keep that in mind when developing.

The binary distribution is built by running Meson_ and introspecting the build
and trying to map the files to their correct location. Due to some limitations
and/or bugs in Meson_, we might not be able to map some of the files with
certainty. In these cases, we will take the safest approach and warn the user.
In some cases, we might need to resort to heuristics to perform the mapping,
similarly, the user will be warned. These warnings are not necessarily a reason
for concern, they are there to help identifying issues. In these cases, we
recommend that you check if the files in question were indeed mapped to the
expected place, and open a bug report if they weren't.
If the project includes shared libraries that are needed by other files, those
libraries will be included in the wheel, and native files will have their
library search path extended to include the directory where the libraries are
placed.


What are the limitations?
=========================


Not yet supported
-----------------


Platform
~~~~~~~~

Currently, ``mesonpy`` is only tested on Linux, but it should work in most
Unix-like operating systems.

Windows and MacOS are not yet supported, but that is actively being worked on.


Executables that link against project libraries
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

If you have an executable in your project that links against a shared library
that is shipped by your project, ``mesonpy`` will not be able to correctly
bundle it to the wheel. The executable will be included in the wheel, but it
will not be able to find the project librar(y/ies) it links against.


No data
-------

Data (see |install_data|_) is not supported by the wheel standard. Project
should install data as Python source instead (Python source does not have to be
only Python files!) and use :py:mod:`importlib.resources` (or the
:py:mod:`importlib_resources` backport) to access the data.
If you really need the data to be installed where it was previously (eg.
``/usr/data``), you can do so at runtime.


.. toctree::
   :caption: Usage
   :hidden:

   usage/start
   usage/build-options


.. toctree::
   :caption: Release
   :hidden:

   changelog


.. toctree::
   :caption: Project Links
   :hidden:

   Source Code <https://github.com/FFY00/mesonpy>
   Issue Tracker <https://github.com/FFY00/mesonpy/issues>


.. |PyPI badge| image:: https://badge.fury.io/py/meson-python.svg
   :target: https://pypi.org/project/meson-python
   :alt: PyPI version badge


.. _Meson: https://github.com/mesonbuild/meson
.. _getting started: usage/start.html
.. _pip: https://github.com/pypa/pip
.. _pypa/build: https://github.com/pypa/build
.. _build options page: usage/build-options.html
.. _install_data: https://mesonbuild.com/Reference-manual_functions.html#install_data

.. |install_data| replace:: ``install_data``
