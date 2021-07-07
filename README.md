# Fluidd Printer Definitions

Contains some useful files for creating a custom Fluidd + Klipper `printer.cfg`.

# To-Do

Create scripts within one `builder` script file which will assemble chosen files into one cohesive file with a `header`, `core`, and `macros` section in that order, where each is an assmbled collection of the unit files.

`edit` script takes choice of definition file name (before extension) or URI for `$definition`, and a list of macro file names (before extension) or URIs `$macros`, then populates a `~/build` folder with a `header.cfg` file containing loose section definitions (with preceeding comments) not contained within `$definition` file, a `~/build/core` folder with one `.cfg` file for each header (with comments preceeding) from the `$definition`, and a `~/build/macros` folder with one `.cfg` file for each remaining header (with comments preceeding) from `$macros` files. A manifest file is also added to build folder containing synthesized command line from options.

`build` script takes `$name`, then assembles contents of `~/build` folder; it combines all `.cfg` files into resultant `printer.cfg`, with stripped out comments, and denoted `header`, `core`, and `macros` sections with heading comments, and then it moves resultant file into `~/build/built/$name` and an appended version identifier (appends 1 to highest detected identifier), and the rest of the build folder (except for `~/build/built`) into `~/build/built/$name/build`.

Once the files are edited, they can be built. Built files should eventually also be editable via edit overload.

`edit` built overload takes `$name` and optional `$version` (will just use highest version found otherwise), then copies `"~/build/built/$name $version/build"` into build folder. The manifest file will be updated with an appended synthesized command line.

If `$clear` flag is set on any script it will clear build folder (except `~/build/built`).

# License

Derived works from Klipper or Fluidd all GPL Version 3, custom works MIT. Closest `LICENSE` file to work details license for work.