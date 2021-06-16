# MoFEM Boundaries
Currently there is no set convention and no one executable which is detectable in the $PATH. Instead there are local executables in various folders. In addition there is a read_med tool which is used to generate config files and to convert the .med file to an understandable .h5m file used by MOAB.

The current BCs which I know of are:

1. Fully fixed: `FIX_ALL`
2. Fixed X: `FIX_X`
