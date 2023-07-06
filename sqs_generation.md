Here we will understand the step-by-step procedure to understand how to generate **SQS(Special Quasirandom Structures)** by employing **Alloy Theoretic
Automated Toolkit(ATAT)**. I am assuming that you have already installed and compiled ATAT on your device. So brace yourselves for the journey:
1) Generate **rndstr.in** file according to the required symmetry. For example, for Pt-Cu binary random solid solution, the following is the format of
rndstr.in file;

**1 1 1 90 90 90 <br>
0.0 0.5 0.5 <br>
0.5 0.0 0.5 <br>
0.5 0.5 0.0 <br>
0.0 0.0 0.0 Pt=0.5,Cu=0.5**
For any queries regarding the input structure file, refer to ATAT documentation.

2) Once we have the rndstr.in file ready, we have to generate clusters according to our requirements. Use the following command line; 

**corrdump -l=rndstr.in -ro -noe -nop -2=1 -3=1 -4=1**

Here we have considered clusters up to quadruplets with cut-off distances equal to the lattice parameter. You can restrict yourself up to -2=_ or -3=1_.
Once we've ran this command, we will get **clusters.out** file. We can list all the clusters found using "getclus" command.

3) Finally, we can start to generate the SQS using the Monte Carlo simulation as follows;

**mcsqs -n N**
, substitute N = 64, if you want to generate a 64 atom SQS supercell. This code might take up to 48 hours to generate the SQS. The best way to check
the status of generation is to check the "**bestcorr.out**" file. The difference in the correlation function should be 0 for most of the clusters. 
