# GRTMOD
GRTMOD is a program for modeling garnet growth and resorption stages in metamorphic rocks. It can be used for thermobarometry based on reactive bulk compositions. This version of GRTMOD requires any version of Theriak-Domino to run Gibbs energy minimizations.

Download the latest release [here](https://github.com/lanari/GRTMOD/releases)

Example files are available [here](https://cloud.cpag-research.ch/index.php/s/2N8JKzi5HgZD7cP)

Download Theriak-Domino [here](https://titan.minpet.unibas.ch/minpet/theriak/theruser.html)


## What is new and important to know?   (2.0-beta.1) 
- In the setup file GRTMODin.txt, you need to add the path to the Theriak directory after the keyword THER (mandatory)
- Duplicate this setup file to work on a new project; note that the new entry "* THER:  /.../Theriak/" must be added to project files compatible with previous versions of GRTMOD.


## Installation
- Download the installer [here](https://github.com/lanari/GRTMOD/releases)
- Run the installer and follow the instructions to setup GRTMOD.

## How to use GRTMOD 2
- Prepapre a working folder containing the file GRTMODin.txt and a database file
- Check that the path to the Theriak-Domino directory is properly set after the keyword THER (see above)
- Run GRTMOD.app (macOS) or GRTMOD.exe (WINDOWS)
- Press the button "Set Directory" and pick up a folder containing 
- The program checks for the files in the directory. Repeat the previous step until all files are recognised and the button "Run GRTMOD" becomes available
- Press the button "Run GRTMOD"
- Open the file last_GRTMOD.txt to vizualise the progress of the calculation.



