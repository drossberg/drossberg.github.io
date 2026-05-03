[back](index.md)

# Compiling

* `<~>` represents a term which has to be set on user's demand.
* If you want to use the MS Visual Studio compiler, use the corresponding Visual Studio command shell in the following build steps.

## Building the [bext](https://github.com/BRL-CAD/bext) reposity
In an empty directory, created for the bext build files, open a command shell and type:
```
cmake <path to the cloned bext repository> -DCMAKE_BUILD_TYPE=<build type> -DENABLE_ALL=ON
```

`<build type>` can be either `Debug` or `Release`. In all steps, the same build type should be used.

I recommend to switch of the build of Qt after the first configuration and before the build.
It's better to use an official Qt distribution, e.g. the one provided via the Linux package manager.

The binaries can be buid via the selected build environment (make, MS Visual Studio, ...) or by typing `cmake --build .` in the above command shell.

## Building the [brlcad](https://github.com/BRL-CAD/brlcad) reposity
In an empty directory, created for the brlcad build files, open a command shell and type:
```
cmake <path to the cloned brlcad repository> -DCMAKE_BUILD_TYPE=<build type> -DCMAKE_INSTALL_PREFIX=<path to a directory, where your user has writing permission> -DBRLCAD_EXT_DIR=<path to the bext build directory from the step before>
```

If you see compiler errors, unset `BRLCAD_ENABLE_STRICT`, e.g. by adding `-DBRLCAD_ENABLE_STRICT=OFF` to the cmake command line.

After building the binaries, they should be installed (i.e., build the "install" target), to get the default directory structure.

## Building the [MOOSE](https://github.com/BRL-CAD/MOOSE) reposity
In an empty directory, created for the MOOSE build files, open a command shell and type:
```
cmake <path to the cloned MOOSE repository> -DCMAKE_BUILD_TYPE=<build type> -DCMAKE_INSTALL_PREFIX=<path to another directory, where your user has writing permission>
```

If the BRL-CAD installation isn't found automatically, set `BRLCAD_BASE_DIR` too:
```
cmake <path to the cloned MOOSE repository> -DCMAKE_BUILD_TYPE=<build type> -DCMAKE_INSTALL_PREFIX=<path to another directory, where your user has writing permission> -DBRLCAD_BASE_DIR=<the path to where brlcad was installed>
```

After building the binaries, they should be installed, to get the default directory structure.

## Building the [arbalest](https://github.com/BRL-CAD/arbalest) reposity
In an empty directory, created for the arbalest build files, open a command shell and type:
```
cmake <path to the cloned arbalest repository> -DCMAKE_BUILD_TYPE=<build type> -DBRLCAD_MOOSE_DIR=<the path to where MOOSE was installed>
```
