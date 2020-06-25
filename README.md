# Vivado-vcontrol
Best practices Vivado

*Note: This file supports simpler projects. Has not been tested on more complicated ones*
## Build the project

1. Open VIVADO
2. Tools->Run Tcl Script (navigate to the tcl script from this repo)

## Automatic version control

### Set up PATH properly

Add to the end of your `~/.bashrc` file, substituting `<Xilinx_path>` with your
Xilinx installation path :

```
# Vivado version control
export PATH="$PATH:<Xilinx_path>/Xilinx/Vivado/2019.2/bin"
```

On my computer `<Xilinx_path>` was just `/opt`

### Version control

-   Run `vcontrol.py` from the folder which contains your Vivado project and pass the argument for the project relative path `<Proj_folder>/<Proj_name>.xpr`(`aep_design.tcl` file will be generated). Example:
```
$ python vcontrol.py my_vivado_proj/project.xpr
```
-   Keep in mind that all project files should be inside the project `.src` dir. Check header of generated TCL file for ERROR messages, generated if some files are not found
-   Constraint files should be under `<Proj_name>.srcs/constrs_1`


Automatic folder structure (adding `/imports` or appending `/new` after building or creating new files by vivado) is being changed:
-   `imports/sources_1` `imports/constrs_1` in the path is being ignored (paths with and without `imports/.../` in path name are treated as the same).
-   `new/` in path is being ignored

Addition info:
-   `debug_script.tcl` is being generated for debug purposes

## Improvement can be done:

-   Can all Vivado files be generated into current folder?
-   Vivado Tcl script is not being properly generated with Vivado tools  

[Version control for Vivado
projects](http://www.fpgadeveloper.com/2014/08/version-control-for-vivado-projects.html)  
[Xlinx suggestions about
GIT](https://www.xilinx.com/support/documentation/application_notes/xapp1165.pdf)
