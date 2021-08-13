# Creating Nanotubes using Quantum Espresso

This example shows how to create input files for quantum espresso for nanotubes using WS2 monolayer. Same thing can be done for other monolayers.

**Download CIF file for WSe2 from Materials Project** (https://materialsproject.org/materials/mp-1821/) 

**Create Monolayer using Burai**
Open the downloaded CIF file using Burai, Delete the second layer, then shift the first layer to the middle of the cell using modeler. the monolayer should look like this:
![](https://github.com/Shihab-Haque/nanotubes-for-Quantum-Espresso-QE/blob/main/WSe2_burai.png) 

Now copy the contents of the input file and save it as *wse2.in*

**open scf input file using xcrysden**
open the *wse2.in* file using xcrysden and save it as XSF structure naming *wse2.xsf* as shown in the picture below
 ![](https://github.com/Shihab-Haque/nanotubes-for-Quantum-Espresso-QE/blob/main/WSe2_xcrsden.png) 
 
 **open xsf file using VESTA**
 open the previously saved *wse2.xsf* file using VESTA, choose export data from file menu, choose *cif as format and save it as *wse2.cif*
 ![](https://github.com/Shihab-Haque/nanotubes-for-Quantum-Espresso-QE/blob/main/WSe2_vesta.png) 
 
 **convert cif file into cell file format**
 open a terminal in the folder you have your *ws2_mono.cif* file and execute the following command

	cif2cell -f wse2.cif -p castep -o wse2.cell
	
This will create a .cell file necessary for c2x

**use c2x to generate a nanotube inpute file for QE**
We will finally use **c2x** (https://www.c2x.org.uk/nanotube.html) to generate the nanotune. 

**zigzag nanotube:**
For generating a (24,0) zig-zag nanotube

	c2x -y=24,0 -v --qe wse2.cell wse2_24_0.in
This will create an input file named *wse2_24_0.in* which can be used by QE for further calculations.

![](https://github.com/Shihab-Haque/nanotubes-for-Quantum-Espresso-QE/blob/main/wse2_24_0.png) 
![](https://github.com/Shihab-Haque/nanotubes-for-Quantum-Espresso-QE/blob/main/wse2_24_0_2.png) 

**armchair nanotube:**
For generating a (12,12) armchair nanotube

	c2x -y=24,12 -v --qe wse2.cell wse2_12_12.in

![](https://github.com/Shihab-Haque/nanotubes-for-Quantum-Espresso-QE/blob/main/wse2_12_12.png) 
![](https://github.com/Shihab-Haque/nanotubes-for-Quantum-Espresso-QE/blob/main/wse2_12_12_2.png)

**chiral nanotube:**
For generating a (18,12) chiral nanotube

	c2x -y=36,24 -v --qe wse2.cell wse2_36_24.in

![](https://github.com/Shihab-Haque/nanotubes-for-Quantum-Espresso-QE/blob/main/wse2_36_24.png) 
![](https://github.com/Shihab-Haque/nanotubes-for-Quantum-Espresso-QE/blob/main/wse2_36_24_2.png)

**calculated E-K Band Diagram:**
For Zigzag WSe2 Nanotube:
![](https://github.com/Shihab-Haque/nanotubes-for-Quantum-Espresso-QE/blob/main/wse2_12_0_band.png) 

For Armchair WSe2 Nanotube:
![](https://github.com/Shihab-Haque/nanotubes-for-Quantum-Espresso-QE/blob/main/wse2_6_6_band.png) 
