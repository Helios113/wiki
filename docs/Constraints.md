# MoFEM Boundaries
Currently there is no set convention and no one executable which is detectable in the $PATH. Instead there are local executables in various folders. In addition there is a read_med tool which is used to generate config files and to convert the .med file to an understandable .h5m file used by MOAB.

The current BCs which I know of are:

1. Fully fixed: `FIX_ALL`
2. Fixed X: `FIX_X`


# FreeCAD Constrains 

| FreeCAD      | MoFEM |
| ----------------------    | -----------   |
| [Electrostatic potential](https://wiki.freecadweb.org/FEM_ConstraintElectrostaticPotential)   | N/A           |
| [Initial flow velocity](https://wiki.freecadweb.org/FEM_ConstraintInitialFlowVelocity)      | N/A           |
| [Flow velocity](https://wiki.freecadweb.org/FEM_ConstraintFlowVelocity)             | N/A           |
| [Plane rotation](https://wiki.freecadweb.org/FEM_ConstraintPlaneRotation)            | N/A           |
| [Section print](https://wiki.freecadweb.org/FEM_ConstraintSectionPrint)             | N/A           |
| [Transform](https://wiki.freecadweb.org/FEM_ConstraintTransform)                | N/A           |
| [Fixed](https://wiki.freecadweb.org/FEM_ConstraintFixed)                    | `FIX_ALL`     |
| [Displacement](https://wiki.freecadweb.org/FEM_ConstraintDisplacement)*            | `FIX_X,Y,Z`; N/A|
| [Contact](https://wiki.freecadweb.org/FEM_ConstraintContact)                  | N/A           |
| [Tie](https://wiki.freecadweb.org/FEM_ConstraintTie)                      | N/A           |
| [Force](https://wiki.freecadweb.org/FEM_ConstraintForce)                    | N/A           |
| [Pressure](https://wiki.freecadweb.org/FEM_ConstraintPressure)                 | N/A           |
| [Self Weight](https://wiki.freecadweb.org/FEM_ConstraintSelfWeight)               | N/A           |
| [Initial Temperature](https://wiki.freecadweb.org/FEM_ConstraintInitialTemperature)       | N/A           |
| [Heatflux](https://wiki.freecadweb.org/FEM_ConstraintHeatflux)                 | N/A           |
| [Temperature](https://wiki.freecadweb.org/FEM_ConstraintTemperature)              | N/A           |
| [Body heat source](https://wiki.freecadweb.org/FEM_ConstraintBodyHeatSource)           | N/A           |
| [Fluid Boundary](https://wiki.freecadweb.org/FEM_ConstraintFluidBoundary)            | N/A           |
| [Bearing](https://wiki.freecadweb.org/FEM_ConstraintBearing)                  | N/A           |
| [Gear](https://wiki.freecadweb.org/FEM_ConstraintGear)                      | N/A           |
| [Pulley](https://wiki.freecadweb.org/FEM_ConstraintPulley)                    | N/A           |
| [Constant vacuum permittivity](https://wiki.freecadweb.org/FEM_ConstantVacuumPermittivity)| N/A         |

\* - Displacement is used for setting displacements and fixing only specific directions (i.e roller supports).