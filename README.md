# Examples for PSCF (polymer self-consistent field theory) 

This directory contains a collection of input files for examples 
that can be run with the PSCF polymer self-consistent field theory 
software to compute properties of periodic microstructures of 
block copolymer materials. These examples are provided to
demonstrate the contents and syntax of the file formats used 
by PSCF, and as potentially useful starting points for new 
simulations.

The home page for the PSCF package, which provides links 
to the documentation and source code, and downloadable 
binary installers for some operating systems, is located 
at http://morse.cems.umn.edu/morse/code/pscf/home.php.html

The source code for PSCF is maintained in the github 
repository: https://github.com/dmorse/pscf
 
## Directory Structure

The top level subdirectories of this repository each contain 
examples of simulations involving different types of system. 
The main subdirectories are currently:

   diblock/

   triblock/

   solution/

Directory diblock/ contains examples for neat (one-component) 
diblock copolymer melts.  Directory triblock/ contains examples 
for neat ABC triblock terpolymer melts.  Directory ssolution/ 
contains examples of ordered phases of a mixture of  adiblock
copolymer and a selective small molecule solvent. We will refer 
to these top level subdirectories in what follows as "system 
level" directories. 

Subdirectories of these system level directoires each contain
simulations of a different possible phase (i.e., crystal structure)
of the system of interest. The names of these subdirectories are 
abbreviations of the names of the phases: lam for lamellar, hex for 
hexagonally packed cylinders, gyr for gyroid, etc. Each system level 
subdirectory contains a CONTENTS file explaining these abbrevations 
in greater detail. 

Directories that contain simulations of a particular phase may 
either contain either the input files for a single example, or 
subdirectories containing several examples of the same phase. 
Some such directories contain two subdirectories named iterate/ 
and sweep/. In this case, the iterate/ directory contains an 
example of a simulation that solves the SCF equations for a 
single set of parameters, and the sweep/ directory contains an 
example that uses the SWEEP parameter file command to perform
a series of simulations along a line in parameter space.

## Example Directory Contents

In what follows, we refer to a directory that contains an
initial omega file used as an input for one example or 
several closely related examples as an example directory.

In each example directory, there are two types of input files,
named
   
   - in.omega:  an input omega (chemical potential) field
   - param*  :  a parameter file or files

Each example file contains only one input omega file, but 
may contain one or more param files. In example directories
that contain more than one parameter files, the simplest
example is usually named simply 'param'.
 
Almost all example directories contains an initially empty 
subdirectory named 'out/'. This is where output files will 
be created when you run an example.  
 
## Running an an example:

  To run an example:

     * Change directory (cd) into the example directory of interest.

     * Enter the command: pscf < paramfile

  Here "paramfile" denotes the name of a particular parameter
  file.  This above command will run the example while outputting 
  information reporting the progress of the calculation to the 
  screen. Alternatively, the command

       pscf < paramfile > out/log &

  will run the example in the background and output this 
  information to a file named "log" in the out/ sub-directory.

## Output files

  #### ITERATE Examples:

  Examples that solve the SCFT equations for a single set of 
  input parameters create the following output files in the
  out/ directory:

      out/out   = output summary 
      out/rho   = output monomer volume fraction fields
      out/omega = output omega fields
  
  #### SWEEP Examples:

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

  where $(N) takes on integer values 0, 1, 2, etc. That is, the 
  directory will contain output summary files out/0.out, out/1.out, 
  etc.  and a similar sequence of number rho (volume fraction) 
  files named out/0.rho, out/1.rho, etc, and numbered output 
  chemical potential files named out/0.omega, out/1.omega, etc.

