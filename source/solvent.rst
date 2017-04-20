.. _solvent:

Solvent accesibility
====================

We'll use the algorithm from Shrake and Rupley for computing the SASA. 

http://mdtraj.org/1.8.0/examples/solvent-accessible-surface-area.html

Notes

This code implements the Shrake and Rupley algorithm, with the Golden Section Spiral algorithm to generate the sphere points. The basic idea is to great a mesh of points representing the surface of each atom (at a distance of the van der waals radius plus the probe radius from the nuclei), and then count the number of such mesh points that are on the molecular surface – i.e. not within the radius of another atom. Assuming that the points are evenly distributed, the number of points is directly proportional to the accessible surface area (its just 4*pi*r^2 time the fraction of the points that are accessible).

There are a number of different ways to generate the points on the sphere – possibly the best way would be to do a little “molecular dyanmics” : put the points on the sphere, and then run MD where all the points repel one another and wait for them to get to an energy minimum. But that sounds expensive.

This code uses the golden section spiral algorithm (picture at http://xsisupport.com/2012/02/25/evenly-distributing-points-on-a-sphere-with-the-golden-sectionspiral/) where you make this spiral that traces out the unit sphere and then put points down equidistant along the spiral. It’s cheap, but not perfect.

The gromacs utility g_sas uses a slightly different algorithm for generating points on the sphere, which is based on an icosahedral tesselation. roughly, the icosahedral tesselation works something like this http://www.ziyan.info/2008/11/sphere-tessellation-using-icosahedron.html


# These van der waals radii are taken from
# https://en.wikipedia.org/wiki/Atomic_radii_of_the_elements_(data_page)
# which references 
# A. Bondi (1964). "van der Waals Volumes and Radii". J. Phys. Chem. 68: 441. doi:10.1021/j100785a001 and doi:10.1021/jp8111556. 
# M. Mantina et al. (2009). "Consistent van der Waals Radii for the Whole Main Group". J. Phys. Chem. A. 113 (19): 5806--12. doi:10.1021/jp8111556
# Where no van der Waals value is known, a default of 2 angstroms is used.
# However, because certain atoms in biophysical simulations have a high 
# chance of being completely ionized, we have decided to give the 
# following atoms their ionic radii their ionic radii:
# +2: Be, Mg, Ca, Ba
# +1: Li, Na, K, Cs
# -1: Cl
# These ionic radii are were taken from:
# Shannon, R. D. Revised effective ionic radii and systematic studies of interatomic distances in halides and chalcogenides. Acta Crystallographica Section A 32, 751--767 (1976). doi:10.1107/S0567739476001551
# For most atoms, adding electrons usually doesn't change the radius much 
# (<10%), while removing them changes it substantially (>50%). Further, 
# when atoms like N, S, and P, are positive, they are bound to atoms in such 
# a way that would "hide" their radii anyway. We have therefore chosen to just 
# use their vdW radii.
