# Molecular dynamics parameters of trimeric Spike from the strains Delta (B.1.617.2) and Omicron (BA.2, BA.5, and BQ.1)

Homology modeling

We make available all input and/or output files containing parameters and codes for homology modeling, molecular dynamics, principal component analysis, statistical analysis script (in .R), and dynamical cross-correlation matrix in the Github (https://github.com/anacletosouza/molecular-dynamics-B.1.617.2-BA.2-BA.5-BQ.1) and in supplementary files S1-S6. In order to investigate how molecular dynamics may influence transmissibility and infectivity, we simulated the trimeric SpikeB.1.617.2 , SpikeBA.2,  SpikeBA.5 and SpikeBQ.1 ectodomains in a water-filled box. The available structures have mutations and/or unresolved regions. In order to correct these problems, we used cryogenic electron microscopy (Cryo-EM) of the SpikeBA.1 structure (PDB ID 7WK2) as a template to obtain the corrected structures in the Swiss-Model web server [52]. Initially, the genomic sequences of the B.1.617.2 (GISAID, accession code EPI_ISL_15728122), BA.2 (GISAID, accession code EPI_ISL_12905607), BA.5 (GISAID, accession code EPI_ISL_14439279) and BQ.1 (GISAID, accession code EPI_ISL_15731012) were translated in Translate tools (available on the Expasy web server) to obtain the primary sequence of the corresponding Spikes proteins. All primary sequences were submitted in the Swiss Model web service [52–54], ignoring the transmembrane regions. Furthermore, we considered the unglycosylated state of Spike because the difference between glycosylated and unglycosylated Spike is smaller than seen between different Spike variants [55]. In order to compare all molecular dynamics simulations, we used only the structures in the down conformation. 

Setup for molecular dynamics simulations

In order to study the structural features of the Spikes, initially we determined the protonation states of ionizable residues in an implicitly aqueous environment at pH 7.0 using the PROPKA module implemented in the Maestro program (academic version v. 2021-4, by Schrödinger) [56]. Thus, (1) all glutamic and aspartic residues were represented as non-protonated; (2) arginine and lysine residues were assumed to have a positive charge; (3) in the N- and C-terminal regions, the amino and carboxyl groups have been converted to charged groups;  (4) the histidines were protonated according to prediction of PROPKA and manual inspection, such as: SpikeB.1.617.2, δ-tautomer (H75, H664, H1067, H1073, H1092, H1097, and H1110) and ε-tatomer (H58, H78, H216, H254, H528, H634, H1057) and charged histidine in H155 residue; SpikeBA.2, δ-tautomer (H72, H251, H511, H960, H1054, H1064, H1070, 1089, 1094, 1107) and ε-tatomer (H55, H75, H152, H213, H525, H631, H687); SpikeBA.5, δ-tautomer (H72, H509, H629, H958, H1052, H1062, H1068, H1087, H1092, H1105) and ε-tatomer (H55, H150, H211, H249, H523, H685); SpikeBQ.1, δ-tautomer (H72, H149, H508, H628, H957, H1051, H1061, H1067, H1086, H1091, H1104) and ε-tatomer (H55, H210, H248, H522, H684). In SpikeB.1.617.2, the disulfide bridges were considered between residue pairs: C140/C175, C300/C310, C345/C370, C388/C441, C400/C534, C489/C497, C547/C599, C626/C658, C671/C680,  C747/C769, C752/C758, C1041/C1052, C1091/C1135. In SpikeBA.2, the disulfide bridges were considered between residue pairs: C137/C172, C297/C307, C342/C367, C385/C438, C397/C531, C486/C494, C544/C596, C623/C655, C668/C677,  C744/C766, C749/C755, C1038/C1049, C1088/C1132. In SpikeBA.5, the disulfide bridges were considered between residue pairs: C135/C170, C295/C305, C340/C365, C383/C436, C395/C529, C484/C492, C542/C594, C621/C653, C666/C675,  C742/C764, C747/C753, C1036/C1047, C1086/C1130. In SpikeBQ.1, the disulfide bridges were considered between residue pairs: C135/C169, C294/C304, C339/C364, C382/C435, C394/C528, C483/C491, C541/C593, C620/C652, C665/C674,  C741/C763, C746/C752, C1035/C1046, C1085/C1129. All structures were previously minimized in Chimera tools, using steepest descent steps of 500, steepest descent step size of 0.02 Å, conjugate gradient steps of 10 and update interval of 10.
	GROMACS is a widely used molecular simulation package that employs physical equations to describe the behavior of proteins of interest. The fundamental equations utilized in GROMACS include Newton's second law (F = ma), which relates the applied force F on a particle to its mass m and resulting acceleration a. Additionally, Coulomb and Lennard-Jones potentials are employed to represent particle interactions.
The interaction potentials are described by the following equations:
VCoul =140q0r
VLJ = 4dσ12r12-4dσ6r6
Where ε0, q0 and r are permittivity of vacuum, electric charge, and the distance between an electric charge and any point in three-dimensional space, considering the potential to be zero at infinity,  respectively. These equations describe the interaction potentials between particles, such as van der Waals forces (represented by the Lennard-Jones potential) and electrostatic forces (represented by the Coulomb potential). The repulsion term, due to van der Waals forces, is the term that scales with the distance r raised to the twelfth power, while the short-range term, scales with the distance r raised to the sixth power. On the other hand, the Coulomb potential originates from Coulomb's law.
All molecular dynamics simulations were performed using GROMACS, v. 2022.1 [57–60], using the OPLS-AA force field [61]. All systems were then explicitly solvated with TIP3P water models in a triclinic box and neutralized, maintaining the concentration of 150 mM NaCl and minimized until reaching a maximum force of 10.0 kJ/mol or a maximum number of steps in 50,000. The systems were consecutively equilibrated in isothermal-isochoric (NVT) ensembles by 2 ns (number of steps and intervals of 1.000,000 and 2 fs, respectively) and isothermal-isobaric (1 bar, 310 K, NpT) by 2,000 ps (number of steps and intervals of 1,000,000 and 2 fs, respectively). All simulations were then performed in a periodic triclinic box considering the minimum distance of 1.2 nm between any protein atom and the walls of the box. Molecular dynamics runs were performed in isothermal-isobaric (1 bar, 310 K, NpT) by 300 ns (number of steps and intervals of 150,000,000 and 2 fs, respectively) in the NpT ensemble. We use the leap-frog algorithm to integrate Newton equations. We selected LINCS (LINEar Constraint Solver) that satisfies the holonomic constraints, whose number of iterations and order were 1 and 4, respectively. We use neighbor search grid cells (Verlet clipping scheme, frequency to update 20-step neighbor list, and clipping distance for 12 Å2 short-range neighbor list). In the van der Waals parameters, we smoothly shift the forces to zero between 10 and 12 Å. In electrostatic Coulomb, we use Particle-Mesh Ewald (PME) fast and smooth electrostatics for long-range electrostatics. In addition, we set the distance for the Coulomb cut to 12 Å, order of interpolation for PME to value 4 (cubic interpolation) and grid spacing for Fast Fourier Transform (FFT) to 1.6 Å. In temperature coupling, we use velocity rescheduling with a stochastic term (V-resale, modified Berendsen thermostat). After obtaining two coupling groups (protein and water/ions), we consider the time constant (0.1 ps) and 310 K as the reference temperature. In the pressure coupling (NpT ensembles), we use the Parrinello-Rahman barostat (isotropic type, time constant of 2 ps, reference pressure of 1 bar and isothermal compressibility of 4.5x10-5 bar-1). We saved the compressed coordinates every 10.0 ps. In molecular dynamics calculations, we use periodic boundary conditions in xyz coordinates (3D space). We then calculated the percent hydrogen bond occupancy (all frames, considering cut-off of distance and angle of 4 Å and 20°, respectively), root-mean-square deviation (RMSD) and root-mean-square fluctuation (RMSF) using the GROMACS modules and Visual Molecular Dynamics (VMD) [62]. Analysis of Cα dynamical cross-correlation matrix (DCCM) was performed using the R-based package Bio3d [63]. The correlations were projected in the first frame (t = 0 ns from MD trajectory corresponding to each SARS-CoV-2 VOC). The scripts used to calculate DCCM, statistical test t, and average number of correlations and anti-correlations of intra-protomers and inter-protomers of  the Spike proteins of all strains, in R files, are available in the supplementary material S5.

Principal component analysis

PCA (Principal Component Analysis) is a statistical technique used to reduce the dimensionality of a dataset by identifying the main linear combinations of variables that capture the majority of the data's variation. This enables simplified visualization and analysis of the data while preserving the most relevant information. Principal component analysis was calculated using the GROMACS modules, covar and anaeig. Using simulated molecular dynamics trajectories, we determined the average position of the Spike backbone atoms and calculated covariance matrix fitting non-mass weighted. Covariance matrices were constructed using the backbone of the SpikeB.1.617.2 (30,591x30,591), SpikeBA.2 (30,537x30,537), SpikeBA.5 (30,483x30,483), and SpikeBQ.1 (30,456x30,456). From covariance matrices, we diagonalized them to obtain the eigenvalues (whose sum of all eigenvalues were of 510.3, 572.0, 561.8, and 385.8 nm²) and, afterwards, orthogonal eigenvectors. Using the first eigenvalue, we determined the eigenvector 1 (named principal component 1, PC1) that represents the first main movement detected along molecular dynamics trajectories. We projected molecular dynamics trajectories of the SpikeB.1.617.2, SpikeBA.2, SpikeBA.5, and SpikeBQ.1 in PC1, skipping 300 frames, to obtain 100 snapshots and to visualize the structural changes of these proteins. In order to quantify these conformational changes of the main movements of the Spike in 310 K, we calculated the entropy by Schlitter method [64] (ΔSSchlitter), using anaeig of the GROMACS. All input parameters are available in supplementary file S3.

Multivariate linear regression model 

One approach to establish the association between structural data and the functional activity of SARS-CoV-2 variants of concern (VOCs) is through the utilization of multiple linear regression. In order to increase the amount of data, we utilized the correlation matrices from SpikeWT and SpikeBA.1, which were published in our previous study [21]. The scripts used to calculate the correlations and anti-correlations within and between the Spike proteins of all strains, in R files, are available in the supplementary material S5. Subsequently, we searched for publications containing IC50 values of Sotrovimab tested against all strains studied in this research. IC50 is defined as the antibody concentration in ng/mL required to inhibit 50% of SARS-CoV-2 replication [65–69]. The independent variables considered in our analysis included the average frequency of intra-protomer correlations (corr_intra), the average frequency of intra-protomer anti-correlations (anti_corr_intra), the coefficient of variation for intra-protomer correlations (corr-CV_intra), the coefficient of variation for intra-protomer anti-correlations (anti-corr-CV_intra), the average count of interprotomer correlations (corr_inter), the average frequency of interprotomer anti-correlations (anti-corr_inter), the coefficient of variation for interprotomer correlations (corr-CV_inter), and the coefficient of variation for interprotomer anti-correlations (anti-corr-CV_inter). Based on the structural information and aiming to relate the structure and function throughout the evolutionary process of SARS-CoV-2 VOCs, we developed various models of multivariate linear regression (the scripts used to build the models, in R files, are available in the supplementary material S5). Specifically, we focused on models with F-statistics greater than 20, indicating strong overall significance. These models were used to explore the relationship between the dependent variable, IC50 values of Sotrovimab [65–69], and the independent variables, representing the structural data. This approach enabled us to investigate the interplay between structural characteristics and the functional activity of SARS-CoV-2 VOCs. Thus, we are interested in obtaining the model:

IC50 = β0 + β1*corr_intra + β2*anti_corr_intra + β3*corr-CV_intra + β4*anti-corr-CV_intra + β5*corr_inter + β6*anti-corr_inter + β7*corr-CV_inter + β8*anti-corr-CV_inter

where, β0, β1, β2,..., β8 are the regression coefficients. Assess the goodness of fit of the model by examining statistical measures such as p-values, F-statistics, adjusted r², and r². These measures provide insights into the significance and explanatory power of the independent variables. 
