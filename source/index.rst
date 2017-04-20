.. Molecular Dynamics tutorial documentation master file, created by
   sphinx-quickstart on Thu Apr 20 14:06:31 2017.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

Molecular Dynamics tutorial
===========================

=================    ========
Status               |status|
Last modified        |today|
=================    ========

Molecular dynamics tutrial presenting posibilities given by vanila python and open source Python libraries. 


Tutorial covers in  detailes creating and analyzing trajectories produced by the most popular simulation packages. It also contains several good practices borrowed from software engineering like: version cotrol, workflow automation, data piplines, and scaling up / scaling out.


What you will learn
-------------------

* what are most popular tools to do MD
* popular data formats and python tools to work with them
* how to prepare robust and easy to set up work environment
* how to build MD system
* how to run MD simulations using most popuar packages
* how to dock small ligands
* how to scale up/out your simulations
* how to load a structure or a MD trajectory (popular formats)
* how to select parts of your system
* how to work with atoms, residues and molecules
* how to deal with large data-sets (bigger than RAM)
* how to analyze MD trajectories
* how to write out or convert trajectories
* how to use various algorithms in analysis (clusterization, structure, ML)
* how to build interactive visualizations

Table of Contents
-----------------

.. toctree::
   :maxdepth: 1

   tools
   formats
   hbonds
   beta
   native_contacts
   pca
   ramachandran
   rmsd
   rmsf
   solvent
   visualizations
   docking
   openmm



Indices and tables
------------------

* :ref:`genindex`
* :ref:`modindex`
* :ref:`search`


.. |status| image:: https://readthedocs.org/projects/md-how-to/badge/?version=latest
            :target: http://md-how-to.readthedocs.io/en/latest/?badge=latest
            :alt: Documentation Status
