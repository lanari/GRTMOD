# GRTMOD
GRTMOD is a program for modeling garnet growth and resorption stages in metamorphic rocks. It can be used for thermobarometry based on reactive bulk compositions. This version of GRTMOD requires any version of Theriak-Domino to run Gibbs energy minimizations.

Download the latest release [here](https://github.com/lanari/GRTMOD/releases)

Example files are available [here](https://cloud.cpag-research.ch/index.php/s/2N8JKzi5HgZD7cP)

Download Theriak-Domino [here](https://titan.minpet.unibas.ch/minpet/theriak/theruser.html)


## What is new and important to know?   (2.0-beta.1) 
- In the project file GRTMODin.txt, you need to add the path to the Theriak directory after the keyword THER (mandatory)
- Duplicate this setup file to work on a new project; note that the new entry "* THER:  /.../Theriak/" must be added to project files compatible with previous versions of GRTMOD.


## Installation
- Download the installer [here](https://github.com/lanari/GRTMOD/releases)
- Run the installer and follow the instructions to setup GRTMOD.

## How to use GRTMOD 2
- Prepapre a folder containing the file GRTMODin.txt and a database file
- Check that the path to the Theriak-Domino directory is properly set after the keyword THER (see above)
- Run GRTMOD.app (macOS) or GRTMOD.exe (WINDOWS)
- Press the button "Set Directory" and pick up a folder containing the file GRTMODin.txt 
- The program checks for the files in the directory. Repeat the previous step until all files are recognised and the button "Run GRTMOD" becomes available
- Press the button "Run GRTMOD"
- Open the file last_GRTMOD.txt to vizualise the progress of the calculation.

## Tutorial

### Getting started
1. Download the tutorial material [here](#)
2. Unzip the files GRTMODin.txt and JUN92.bs. Note that the folder containing these files will be used as working directory and result files will be generated by GRTMOD will be stored there
3. Copy the file Theriak.ini from the Theriak-Domino program folder to the working directory (required for Windows and for some macOS configurations)
4. Run GRTMOD.app (macOS) or GRTMOD.exe (WINDOWS)
5. Press the button "Set Directory" and pick up the right folder

### Stage 1
1. Open GRTMODin.txt using a text editor and maake sure that stage 2 is commented (the line not starting by ">", a minus is added in the example below)
        
        ->> STAGE 2
        * COMP: 1
        * OPTI: 1
        * REFI: 1
        
2. Save the file GRTMODin.txt
3. In the GRTMOD window, press the button "Run GRTMOD"

Note: You can open the file last_GRTMOD.txt with a text editor updating the content live to vizualise the progress of the calculation

4. Once the calculations for stage 1 are accomplished, a dialog window appears listing all the solutions for this stage: select the solution and press "Ok"; In this example, a single solution was found for stage 1 at T = 752°C and P = 8235 bar
5. Details results are saved in the file last_GRTMOD.txt
6. A restart file RESTART_Stage(1).mat has been generated
7. Two figures are displayed: a P-T diagram shwoing the result and uncertainty; a mode diagram showing the volume fraction of garnet modeled at each stage

### Notes on the optimization procedure of GRTMOD
The procedure of each stage is divided into three phases: optimization1, optimization2 and auto-refinement. During optimization1, successive minimizations are carried out from different starting P-T guesses in order to determine the global minimum within the P-T window. For stages i > 1, optimization2 refines the garnet fractions to be fractionated, as well as P-T. The starting guess for optimization2 is the best P-T couple obtained during optimization1. A go fast mode is available to run directly optimization2 from user’s favorite P-T initial guess. Finally, the auto-refinement stage checks the local variability of the objective function in order to provide a relative uncertainty on the P-T estimate.

In this example (stage 1) the solution of the RUN 1/4 is selected as the best solution.

### Stage 2
1. Open GRTMODin.txt
2. As it is not required to calculate the first stage again set the variable COMP of stage 1 to 0. GRTMOD will read the restart file.
                 
        >> STAGE 1
        * COMP: 0
        * OPTI: 1
        * REFI: 1
        
3. Activate stage 2 and set the variable COMP to 1: 
        
        >> STAGE 2
        * COMP: 1
        * OPTI: 1
        * REFI: 1
        
4. Save the file GRTMODin.txt
5. In the GRTMOD window, press the button "Run GRTMOD"
6. Select the second solution SOL-2 at T = 649°C and P = 15335 bar; the higher garnet volume fraction  predicted is in line with the observations in this sample
7. A restart file RESTART_Stage(1).mat has been generated
8. Two figures are displayed: a P-T diagram showing the result and uncertainty; a mode diagram showing the volume fraction of garnet modeled at each stage
9. A table containing a summary of the final results is saved in last_GRTMOD.txt

### Notes on the optimization procedure of GRTMOD (Stage 2)
During optimization1, GRTMOD runs 4 minimizations (see input variables for the initial P-T conditions). Two minimizations 1 and 3 fail to find a solution (residue of 1e+19) which mean that no garnet was predicted to be stable close to the starting conditions. For run 1, the fraction of garnet predicted to be stable (0.19872 vol-%) is too small and below the lower limit (1%) defined in the project file (variable CVAR-GARN-2-FVOL). For run 3, garnet is not predicted to be stable at the initial P-T conditions of TC = 800°C & P = 8000 bar. By contrast, minimizations 2 and 4 converged to a minimum with residue of 0.00010767 and 0.017066 respectively. The solution of minimization 2 (TC = 645 °C & P = 13296 bar) is selected as the best solution–from a statistical point of view-for optimization2.

During optimization2, three minimisations are performed starting from the best P-T solution of optimization1 (TC = 645 °C & P = 13296 bar, see above) with a variable fraction of Grt1 (X-1), fractionated from the bulk rock composition: 13.9369 vol-% (solution from stage 1 = no resorption); 4 vol-% (strong resorption); 8.9685 vol-% (moderate resorption). Note that minimization 1/3 converges to a solution at TC = 645 °C and P = 13298 bar for a X-1 of 13.9333 vol-% with 1.7033 vol-% of Grt2 stable. Minimization 2/3 converges to a solution at TC = 649 °C and P = 15335 bar for a X-1 of 11.25 vol-% with 4.6414 vol-% of Grt2 stable. Minimization 3/3 converges to a solution at TC = 649 °C and P = 15335 bar for a X-1 of 8.96 vol-% with 5.3526 vol-% of Grt2 stable. Minimizations 2 and 3 converge to an identical solution in P-T, and GRTMOD only stored solution 2.

Two auto-refinement stages are calculated, one for each of the solutions: solution 1 from minimization 1 and solution 2 from minimzation 2.

The second solution is selected here manually as best solution because ~4 vol-% of garnet from that stage is observed in the sample. The growth of Grt2 is modeled with a the resorption of 2.687 vol-% of Grt1 (Fig. 11).

## GRTMOD variables in GRTMODin.txt
### INIT block
    
    >> INIT
    * THER: /Users/pierrelanari/Geologie/Programs/TheriakDominoCompiled
    * THDB: JUN92.bs
    * SAMP: * Demo 
    * SYST: SIO2 TIO2 AL2O3 FEO FE2O3 MNO MGO CAO NA2O K2O
    * BULK: 64.09 0.95 17.12 6.99 0 0.00 2.34 0.72 1.05 3.13
    * NH2O: 1
    * NOFI: ?
    * NCFI: 0
    * NEXO: 0.00
    * STOL: 0.05
    * RESC: 0.015
    * SELS: 1
    * SELP: 1
    * TOLX: 0.001
    * TOLF: 0.001
    * DISP: off
    * TMIN: 500
    * TMAX: 900
    * PMIN: 4000
    * PMAX: 20000
    * TDI1: 20
    * TDI2: 5
    * PDI1: 500
    * PDI2: 125
    
- THDB: Thermodynamic database (e.g. JUN92.bs or tc55.txt). Any database compatible with Theriak-Domino can be used but **the name of the solution model for garnet in the database must be GARNET**.
- SAMP: End of theriak default line _* Sample Name_ must start with * ! could be used to define set a buffer *,buffer_name
- SYST: Chemical system (see above). **Do not edit this line!**
- BULK: Add your intial bulk composition (in oxide wt-%). **WARNING: Fe must be defined as FeO in the current version of GRTMOD. FE2O3 should not be used**.  
- NH2O: value of H(X) in therin
- NOFI: O(X) in therin (usually “?”) – If this a value is not defined default O(?) is applied
- NCFI: C(X) in therin; If no value is provided C(0) is applied instead
- NEXO: O(X) in therin – Excess Oxygen as in Thermocalc. NB: If this option is not set the excess O = 0. **Use this to work with Fe3+ instead of FE2O3 (see above)
- STOL: Tolerance for an acceptable solution (def. 0.05). From a statistical point of view a value of below 0.3 is excellent. 
- RESC: Residuum criteria to refine errors (def. 0.015)
- SELS: Mode to select the solution: _0_ auto (best), _1_ manual
- SELP: Mode to select the solution to be plotted: _0_ all, _1_ only the selected solution
- TOLX: Optimization parameter: Termination tolerance on x (def. 0.001)
- TOLF: Optimization parameter: Termination tolerance on the function value (def. 0.001)
- DISP: Display optimization info during each minimization: _off_ | _iter_ | _final_ | _notify_
- TMIN: Set Tmin of the problem (in °C)
- TMAX: Set Tmax of the problem (°C)
- PMIN: Set Pmin of the problem (in bar)
- PMAX: Set Pmax of the problem (bar)
- TDI1: T discretization first optimization (°C)
- PDI1: P discretization first optimization (bar)
- TDI2: T discretization refinement (°C)
- PDI2: P discretization refinement (bar)

### STAGE block
    
    >> STAGE 1
    * COMP: 1
    * OPTI: 1
    * REFI: 1
    * MAPC: 0
    * CVAR-GARN-1-COMP: 37.7 0.01 21.27 31.46 0	0.00 7.19 1.31 0 0.01
    * CVAR-GARN-1-WEIG: 3500 800 1300 5
    * CVAR-GARN-1-FVOL: 4
    * CVAR-GARN-1-MVOL: 40
    * OPTP: 749 8200
    * TRYI: 749 8190
    
    >> STAGE 2
    * COMP: 1
    * OPTI: 1
    * REFI: 1
    * MAPC: 0
    * CVAR-GARN-2-COMP: 37.95 0.01 21.44 27.94 0 0.00 5.33 6.72 0	0
    * CVAR-GARN-2-WEIG: 3100 2900 800 5
    * CVAR-GARN-2-FVOL: 1
    * MAXC: 13.94
    * MINC: 4

    
- COMP: _1_ compute or _0_ use a restart for this stage (e.g. RESTART_Stage(1).mat)
- OPTI: optimization (_1_ yes; _0_ no; _2_ Go fast mode: run directly opt2 using conditions defined in OPTP)
- REDI: P-T refinement with uncertainty estimation (_1_ yes, _0_ no)
- MAPC: map computation between TMIN TMAX and PMIN and PMAX (_1_ using TDI1, _2_ using TDI2)
- CVAR: composition variables; note that the number _Ref_Stage_ is required in the keyword
- CVAR-GARN-_Ref_Stage_-COMP: Define the garnet oxide wt-% composition (order: SIO2 TIO2 AL2O3 FEO FE3O3 MNO MGO CAO NA2O K2O; cannot be changed in this version)
- CVAR-GARN-_Ref_Stage_-WEIG: Define the weights: _wFe wCa wMg wMn_; weights; number of counts from the X-ray map for each element works (e.g. Lanari et al, 2017). **Note: If you do not have X-ray maps of your garnet, you can use my converter file that generates pseudo X-ray intensities from garnet spot analyses. NOTE: The weighting procedure can significantly affect the results, be sure that weight values are relevant**
- CVAR-GARN-_Ref_Stage_-FVOL: Final vol% of this garnet stage; used by the program as minimum volume fraction of garnet for calculating a residual during the minimization
- CVAR-GARN-_Ref_Stage_-MVOL: Maximal volume % value for this garnet (100% if not defined for stage > 1)
- TRYI: Try to run ptimizations (1 and 2) from this additional initial guess _T P_; Each row starting with the keyboard TRYI creates an additional starting position
- OPTP: run directly optimization 2 from this starting guess _T P_; required if OPTI = _2_ for this stage
- MAXC: Maximum garnet volume bounds (_0_ means don’t use it) vector with iStage-1 values – not used for stage 1. Note that this value can overwrite the upper limit and it is therfore possible to fractionate more Grt of the previous stage that predicted by the model by adjusting this value
- MINC: Minimum garnet volume bounds (_0_ means don’t use it) vector with iStage-1 values – not used for stage 1

