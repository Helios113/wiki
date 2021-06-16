# Creating the GUI

## 1. Add the name of the new FEM module as a command to:  
`src/Mod/Fem/Gui/Workbench.cpp`
in two places ToolBarItem and MenuItem

The file looks like this:

### ToolBarItem
```c++
    Gui::ToolBarItem* solve = new Gui::ToolBarItem(root);
     solve->setCommand("Solve");
     *solve
        << "FEM_SolverMoFEM"  <---- added
        << "FEM_SolverCalculixCxxtools"  
        << "FEM_SolverCalculiX"  
        << "FEM_SolverElmer"  
```
### MenuItem

```c++
    root->insertItem(item, solve);
    solve->setCommand("&Solve");
    *solve
        << "FEM_SolverMoFEM" <---- added
        << "FEM_SolverCalculixCxxtools"
        << "FEM_SolverCalculiX"
        << "FEM_SolverElmer"
```

## 2. Add a solver object to:  
`src/Mod/Fem/ObjectsFem.py`

```python
    def makeSolverMoFEM(
        doc,
        name="SolverMoFEM"
    ):
        """makeSolverMoFEM(document, [name]):
        makes a MoFEM solver object"""
        import femsolver.mofem.solver
        obj = femsolver.mofem.solver.create(doc, name)
        return obj
```

## 3. Create a solver class in:  
`src/Mod/Fem/femcommands/commands.py`

```python
class _SolverMoFEM(CommandManager):
    "The FEM_SolverElmer command definition"
    def __init__(self):
        super(_SolverMoFEM, self).__init__()
        self.menuetext = "Solver MoFEM"
        self.accel = "S, M"
        self.tooltip = "Creates a FEM solver MoFEM"
        self.is_active = "with_analysis"
        self.do_activated = "add_obj_on_gui_noset_edit"
```

```python
    FreeCADGui.addCommand(
        "FEM_SolverMoFEM",
        _SolverMoFEM()
    )
```

## 4. Add the new solver command to:  
`src/Mod/Fem/femcommands/manager.py`

```python
def solver_mofem_selected(self):
        sel = FreeCADGui.Selection.getSelection()
        if len(sel) == 1 and is_of_type(sel[0], "Fem::SolverMoFEM"):
            self.selobj = sel[0]
            return True
        else:
            return False
```
in addition add `elif` statement at around line 137 as:

```python
elif self.is_active == "with_solver_mofem":
            active = (
                FemGui.getActiveAnalysis() is not None
                and self.active_analysis_in_active_doc()
                and self.solver_mofem_selected()
            )
```

## 5. Add solver to settings file:
`src/Mod/Fem/femsolver/settings.py`
```python
"MoFEMSolver": _SolverDlg(
        default="MoFEMSolver",
        param_path=_PARAM_PATH + "MoFEM",
        use_default="UseStandardMoFEMLocation",
        custom_path="MoFEMBinaryPath"),
```

## 6. The three main components of the solver need to be ammended to incorporate the new features.

These components are:  

+ [solver.py](solver.py.md)  
+ [tasks.py](tasks.py.md)
+ [writer.py](writer.py.md)  

Prefrences GUI is in GUI folder of FEM a design in Qt is needed; however, it is not needed for this to work.