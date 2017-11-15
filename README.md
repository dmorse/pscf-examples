Examples for PSCF (polymer self-consistent field theory) Package
----------------------------------------------------------------

This repository contains input files for a set of examples for
the PSCF polymer self-consistent field theory software. The
source code is maintained in a separate github repository at
https://github.com/dmorse/simpatico . See the README file in
that repository for links to the home page, users manual etc.

I. Example directory structure:

   In each example directory, there are two types of input files,
   named
   
      param*   = parameter files
      in.omega = input omega (chemical potential) field

   Each example file contains only one input omega file, but
   may contain one or more param files. In example directories
   that contain more than one parameter files, the simplest
   example, usually named simply 'param', contains instructions
   to solve the SCFT equations at a single set of parameters.
   Other parameter files in the same directory then have names
   of the form param.<suffix>, where the suffix describes the 
   type of calculation. For example, files named param.sweep 
   generally include a SWEEP command, which instructs PSCF to
   carry solve the SCFT equations for a sequence of parameter
   choices along a line in parameter space.
 
   Almost all example directories contains an initially empty 
   subdirectory named 'out'. This is where output files will
   be placed when you run the example.  Some example directories 
   also contain a directory named 'ref'. If present, the ref/
   directory contains the output files produced by a previous 
   run of the example, for reference.  
 
II. Running an an example:

    To run an example:

    1) Change directory (cd) into the example directory 
    containing the parameter and omega file of interest.

    2) Enter the command

       pscf < paramfile

    where paramfile denotes the name of a particular parameter
    file.  This command will run the example while outputting 
    information reporting the progress of the calculation to 
    the screen. The command

       pscf < paramfile > out/log &

    will instead run the example in the background and output
    this information to a file named "log" in the out/
    sub-directory.

III. Output files

   ITERATE Examples:

   Examples that solve the SCFT equations for a single set of 
   input parameters create the following output files:

      out/out   = output summary 
      out/rho   = output monomer volume fraction fields
      out/omega = output omega fields
  
   SWEEP Examples:

   Examples in which the parameter file contains a SWEEP command
   cause the program to solve the SCF equations for a set of input 
   parameters along a line in parameter space. The SWEEP command
   can specify any line along which one or more of the parameters 
   are incremented in uniform increments, with increment values 
   that are specified in the input script.  The output files 
   produced by running a SWEEP example are also placed in the out
   subdirectory, and have names of the form

      out/$(N)out     = output summary fields
      out/$(N)rho     = output density fields
      out/$(N)omega   = output omega fields

   where $(N) takes on integer values 0, 1, 2, etc. That is, 
   the directory will contain files out/0.out, out/1.out, etc. 
   and similarly for *.rho and *.omega output files. If a 'ref'
   subdirectory is provided, it contains a similar set of files.

