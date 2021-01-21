.. image:: https://img.shields.io/badge/dmtn--148-lsst.io-brightgreen.svg
   :target: https://dmtn-148.lsst.io
.. image:: https://travis-ci.com/lsst-dm/dmtn-148.svg
   :target: https://travis-ci.com/lsst-dm/dmtn-148

#######################
DM Calibration Products
#######################

DMTN-148
========

The goal of this tech note is to provide a plan for the handling of calibration products in the Gen-3 Butler environment, including the construction, validation, certification, and deprecation.  This process is equally challenging with the current Gen-2 Butlers, but the hope is that with a clear goal in mind, the currently existing calibrations, for all calibration types and cameras, can be migrated to a common design that will be shared with Gen-3.  The current state, the end goal, and the transition steps between these are defined.

Links
=====

- Live drafts: https://dmtn-148.lsst.io
- GitHub: https://github.com/lsst-dm/dmtn-148

Build
=====

This repository includes lsst-texmf_ as a Git submodule.
Clone this repository::

    git clone --recurse-submodules https://github.com/lsst-dm/dmtn-148

Compile the PDF::

    make

Clean built files::

    make clean

Updating acronyms
-----------------

A table of the technote's acronyms and their definitions are maintained in the `acronyms.tex` file, which is committed as part of this repository.
To update the acronyms table in ``acronyms.tex``::

    make acronyms.tex

*Note: this command requires that this repository was cloned as a submodule.*

The acronyms discovery code scans the LaTeX source for probable acronyms.
You can ensure that certain strings aren't treated as acronyms by adding them to the `skipacronyms.txt <./skipacronyms.txt>`_ file.

The lsst-texmf_ repository centrally maintains definitions for LSST acronyms.
You can also add new acronym definitions, or override the definitions of acronyms, by editing the `myacronyms.txt <./myacronyms.txt>`_ file.

Updating lsst-texmf
-------------------

`lsst-texmf`_ includes BibTeX files, the ``lsstdoc`` class file, and acronym definitions, among other essential tooling for LSST's LaTeX documentation projects.
To update to a newer version of `lsst-texmf`_, you can update the submodule in this repository::

   git submodule update --init --recursive

Commit, then push, the updated submodule.

.. _lsst-texmf: https://github.com/lsst/lsst-texmf


The GitHub Actions workflow file.
---------------------------------

**Tip:** GitHub Actions provides a flexible Python environment.
It's likely easier to run preprocessing scripts directly from the GitHub actions environment, rather than within the lsst-texmf Docker container:

Install additional Python dependencies in the `Python install` step.
- Add additional bash commands for preprocessing steps to run before the `docker run` step.
- Structure your `Makefile` so that files built in advance in the GitHub actions environment are automatically used as-is by the `docker run` command.

For more information about using the CI environment, see the [GitHub actions workflow documentation](https://help.github.com/en/actions/reference/workflow-syntax-for-github-actions).
