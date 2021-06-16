# tasks.py

wiki: Module containing one task class per task required for a solver implementation. Those tasks divide the process of solving a analysis into the following steps: check, pretare, solve, results.

Those do the actual work of exporting the analysis into a format understood by the solver executable, starting the executable and loading the results back into FreeCAD.


## Class `Check`

### these classes are initiated by the GUI only

Checks to see if the mesh is ok.  
First it checks how many mesh objects exist. If there are more than one mesh the check returns an error. Hence we can solve only one mesh at a time.

After for Elmer and MoFEM we need to check if the mesh was made with gmsh, so we can export it to 

## Class `Solve`

Finds the binary location of the solver by name
If it fails it can default to a path provided by the user
We can also pass parameters to the binary

Hence we can run:

mofem -blah.m5h -blah.config

Then after the results class is called by the solve class