# Tension-Anisotropy

Source code for the following manuscript:

Title:
Tension anisotropy drives phenotypic transitions of cells via two-way cell-ECM feedback

Authors:
Farid Alisafaei(1,2,#), Delaram Shakiba (1,3,#), Yuan Hong (1,3,#), Ghiska Ramahdita (1,3,4,#), Yuxuan Huang (1,4), Leanne E. Iannucci (4), Matthew D. Davidson (1,5,6), Mohammad Jafari (1,2), Jin Qian (1,3), Chengqing Qu (1,3), David Ju (1,3), Dashiell R. Flory (1,3), Yin-Yuan Huang (1,4), Prashant Gupta (3), Shumeng Jiang (1,3), Aliza Mujahid (1,2,3), Srikanth Singamaneni (3), Kenneth M. Pryse (3), Pen-hsiu Grace Chao (7), Jason A. Burdick (1,5,6), Spencer P. Lake (3,4,8), Elliot L. Elson (1,9), 
Nathaniel Huebsch (1,3,4,#), Vivek B. Shenoy (1,10,#), Guy M. Genin (1,3,4,#)

Affiliations:	
1	NSF Science and Technology Center for Engineering Mechanobiology
2	Department of Mechanical and Industrial Engineering, New Jersey Institute of Technology, Newark, NJ 07102, USA
3	Department of Mechanical Engineering & Materials Science Washington University in St. Louis, St. Louis, MO 63130, USA
4	Department of Biomedical Engineering, Washington University in St. Louis, St. Louis, MO 63130, USA
5	BioFrontiers Institute, University of Colorado Boulder, Boulder, CO 80303, USA
6	Department of Chemical and Biological Engineering, University of Colorado Boulder, Boulder, CO 80303, USA
7	Department of Biomedical Engineering, School of Engineering and School of Medicine, National Taiwan University, Taipei, Taiwan
8	Department of Orthopaedic Surgery, Washington University in St. Louis, St. Louis, MO 63130, USA
9	Washington University School of Medicine, Department of Biochemistry and Molecular Biophysics, St. Louis, MO 63130, USA
10	Department of Materials Science and Engineering, School of Engineering and Applied Science, University of Pennsylvania, Philadelphia, PA 19104, USA

----------------------------------------------------------------

Running the simulations using the three-dimensional cytoskeletal model

----------------------------------------------------------------

Prerequisites:

Ensure you have the following software installed and linked:

- Abaqus
- Visual Studio
- Intel Parallel Studio XE
(Instructions to find and download the compatible versions of Visual Studio and Intel Fortran and properly link Abaqus with Fortran can be found at https://www.youtube.com/watch?v=f_8CjAqcQNI)

Instructions:

1. Download and extract the Codes folder: After downloading the Codes folder, extract its contents to a directory of your choice.

2. Open Windows command prompt: Open the Windows command prompt by either opening the Start menu and searching for "cmd" or pressing the Windows key + R, typing "cmd" or "cmd.exe" in the Run command box, and pressing Enter.

3. Navigate to the simulation folder: Use the command prompt to navigate to the drive and the path where you extracted the Codes folder. For example:

C:
cd path\to\the\simulation\folder

4. Run Abaqus simulation: Execute either the "iso_34kpa.inp" (for circular substrate) or "aniso_34kpa.inp" (for rectangular substrate) from the command prompt:

abaqus job=iso_34kpa user=CellMatrixModel_11072018

Please note that the file "CellMatrixModel_11072018.for" contains a user subroutine UMAT code, which is based on the theoretical model for defining cytoskeletal material properties. Each section of the UMAT code is explained with annotations for clarity and ease of understanding.

5. Verify simulation completion: Check the last line in the "iso_34kpa.log" file to ensure the Abaqus job "iso_34kpa" is completed.

6. Open simulation results in Abaqus: Open the "iso_34kpa.odb" (or aniso_34kpa.odb) file generated by the simulation.

7. Adjust visualization settings to plot the cell contractility:
- From the Results Tree on the left, navigate to Output Databases > iso_34kpa.odb > Instances
- Right-click on the CYTOSKELETONPART-1 and pick Replace
- From the Menu bar, navigate to Plots > Contours > On Deformed shape
- Navigate to Results > Field Output > Primary Variable > SDV48 > OK
- Ensure the deformation scale factor is uniform and set to 1 (From Options > Common > Basic > Deformation Scale Factor).
- Enable the translucency to have the contractility plot within the cytoskeleton (From Options > Common > Other > Translucency)

Files Included:

- iso_34kpa.inp: Abaqus input file for the circular substrate.
- aniso_34kpa.inp: Abaqus input file for the rectangular substrate.
- CellMatrixModel_11072018.for: User subroutine UMAT code based on the theoretical model to define cytoskeletal material properties.

