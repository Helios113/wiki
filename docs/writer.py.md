# writer.py

wiki: N/A

Not a necessary script but all current solver have one.
It provides helper function to write files to the system and stores paths. It is controlled by the `tasks.py` script.

For MoFEM it is implements a `MedWriterMoFEM` class which generates .geo files, adds MoFEM boundary conditions and then through the usage of .unv files creates a .med file and returns it's path.