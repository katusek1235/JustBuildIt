<p align="center">
<img src="BuildIt.png" alt="drawing" width="200"/>
</p>

> [!WARNING]
> This is absolutely not production ready this is only hobbyist project

# Just Build It

Is a simple python 3.11+ build system for c++ that:
- Is designed for windows MinGW and Linux (But can adapt to many other toolchains)
- Works on projects 
- Can build them with one command in the terminal
- Uses only python (even makefile is optional)
- Helps with maintaining git repositories

# Usage

```
usage: buildit [options] [project_path]

Simple python build system for c++

positional arguments:
  project_path          path to the project

options:
  -h, --help            show this help message and exit
  -t, --template TEMPLATE_NAME
                        generate template
  -c, --clean           clean any build files
  -r, --rebuild         rebuild whole project
  -i, --init REMOTE_URL
                        init a git repo with remote
  -s, --push COMMIT_NAME
                        (-s - save) push to remote repo with commit name
  -l, --pull            (-l - load) pull lastest changes from remote repo
  -d, --discard         discard local changes and reset to remote repo

Available default templates are: cpp , glfw
```

###### Generating Templates

Is just coping a template project (directory) from `./cpp_project_templates/<template name>` 

## Dependencies

[argparse](https://pypi.org/project/argparse/)

## Quick Start

#### If you have make

```console
$ make package
$ buildit -t cpp test
```

#### If you dont

```console
$ python3 maker.py package
$ buildit -t cpp test
```

### Example `buildme.py` a.k.a. The Project description

```
create_vscode_settings = True                      # Create vscode workspace settings based on eg. include paths
run_after_build        = True                      # Run the executable after succesful build
proj_name              = "test"                    # Project name
proj_version           = "0.1.0.0"                 # Project version
file_name              = "test"                    # Output executable name (on windows .exe is autmatically added)
compiler               = "g++"                     # Compiler for c and c++ (you can add c_compiler or cxx_compiler for different compilers)
linker                 = "g++"                     # Linker for linking all object files
flags                  = ['-Wall','-Wextra','-O3'] # Flags for linker and compiler (you can specifiy compiler_flags and linker_flags)
output_path            = "bin"                     # Directory for the executable (and all objects in subdirectory specified by obj_dir default is obj)
source_path            = "src"                     # Directory with the source code (can be in subdirectories)
libs                   = []                        # List of Libraries to link with
pkgconf_libs           = []                        # List of Libraries passed to pkgconf
lib_paths              = []                        # List of Directories with libraries
include_paths          = []                        # List of Directories with headers

```