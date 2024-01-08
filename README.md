# Protein-Homology-Modeling
Comparative Modeling of the α-Amylase (AA) Structure from Alteromonas haloplanktis:

Introduction:

Comparative Structural Modeling (CSM) is a technique for predicting protein conformation based on the amino acid sequence and known structures of homologous proteins. A protein's ability to interact with others largely depends on its three-dimensional (3D) structure. Understanding this structure is essential for a better understanding of its mode of action, whether in roles such as enzymatic activity, transport, signaling, or binding with ligands, receptors, or membranes.

Experimental determination of the 3D structure of proteins often requires significant time and financial resources. In some cases, it may even be impractical, especially for insoluble proteins. To overcome these challenges, in silico predictive methods offer a quick and cost-effective alternative. These approaches are based on principles from the fields of physics, statistics, and biology. Among various molecular modeling methods, comparative modeling is currently considered one of the most accurate. This report will delve into the application of such comparative modeling using the example of α-amylase (AA) from Alteromonas haloplanktis.

Step 1: Identification of a homologous protein as a model for the target sequence:

Referring to the UniProt database (http://www.uniprot.org/), the sequence of α-amylase (AA) from Alteromonas haloplanktis is searched. To obtain the sequence of the mature protein, signal sequences, and any propeptides are excluded. The sequence of the mature protein is then copied in FASTA format into a new file named "alpha_amy.txt."

![cap1](https://github.com/AmelMansour/Protein-Homology-Modeling/assets/141269604/fb2e2f7a-c7a0-4906-b0f9-160d742a0c05)
![Capture2](https://github.com/AmelMansour/Protein-Homology-Modeling/assets/141269604/80c9effc-df29-46b5-84ff-53ee983f7d08)
![Capture3](https://github.com/AmelMansour/Protein-Homology-Modeling/assets/141269604/c8b5f2bb-53f9-47cf-80d8-311a39946523)
![Capture4](https://github.com/AmelMansour/Protein-Homology-Modeling/assets/141269604/19449bba-57f4-4957-a5dc-053c4d06ce8b)

*Using the Blast tool to analyze the target sequence:
- Select the "blastP" tool specific to proteins.
- Copy the sequence or load the content from the "alpha_amy.txt" file.
- Choose the PDB database.

![Capture5](https://github.com/AmelMansour/Protein-Homology-Modeling/assets/141269604/19e89504-0256-4156-aa4f-30c5899d3a4c)
![Capture6](https://github.com/AmelMansour/Protein-Homology-Modeling/assets/141269604/73b61f1a-f2ea-472c-a642-8b5a578e71de)
![Capture7](https://github.com/AmelMansour/Protein-Homology-Modeling/assets/141269604/c160bfdc-51b5-477c-a70d-e4bb4f2a1ff5)
![Capture8](https://github.com/AmelMansour/Protein-Homology-Modeling/assets/141269604/1d612110-3f5a-4667-9de3-59d6f7f6a5f6)


The selection of an appropriate template is a crucial aspect of Comparative Structural Modeling (CSM). Here are some important criteria to consider when choosing a template:

• Sequence Similarity: The template should have a sufficiently high sequence similarity with the target protein to make structure predictions more reliable. Generally, a sequence similarity of at least 30% is recommended.

• Structure Quality: The template should have a 3D structure that is resolved with adequate quality, measured by parameters such as resolution, E-value, the number of missing residues, coverage rate, etc.

• Biological Function: It is important to ensure that the template has a biological function similar to that of the target protein. Homologous proteins with similar biological functions tend to have similar structures.

• Availability of Structure: The template should be available in a protein structure database such as the PDB or UniProt.

--> he model (Template) is selected as "Chain A, ALPHA-AMYLASE [Pseudoalteromonas haloplanktis]" (1JD7).

![Capture9](https://github.com/AmelMansour/Protein-Homology-Modeling/assets/141269604/eeaae735-d762-4a92-9bde-cc524dd9b331)

* Download the coordinate file (1jd7.pdb) from the PDB server. This file represents the structure that will serve as the template for the modeling.

![Capture10](https://github.com/AmelMansour/Protein-Homology-Modeling/assets/141269604/2d5b2643-c45c-48e0-b978-5a650e34e60e)
![Capture11](https://github.com/AmelMansour/Protein-Homology-Modeling/assets/141269604/d5611222-753c-4183-96dc-f11d00604851)


Step 2: Alignment of Target and Template Sequences

* Model Preparation:
- Use a protein structure visualization software such as PyMOL or Chimera to open the "1jd7.pdb" file.
- Remove all heteroatoms and molecules other than the protein itself.

![Capture12](https://github.com/AmelMansour/Protein-Homology-Modeling/assets/141269604/fa08d068-d5ea-4c8e-9780-74b27feb156b)

** Alternative Method:

These modifications can be made directly using a text editor (e.g., Notepad, Pluma for Unix).

- Save the Template file in PDB format as "1jd7_clean.pdb".
- Convert the "1jd7_clean.pdb" file to Fasta format using an online tool such as https://zhanggroup.org/pdb2fasta/.

![Capture13](https://github.com/AmelMansour/Protein-Homology-Modeling/assets/141269604/67e0599b-bc17-4f41-8ef9-4179bd6f2071)

We are going to perform a pairwise sequence alignment between the model and the target using the Needle program from the EMBOSS software.

- Access the website http://www.ebi.ac.uk/Tools/psa/emboss_needle
- Copy/paste the sequences of the target and the template into the two designated fields.

![Capture14](https://github.com/AmelMansour/Protein-Homology-Modeling/assets/141269604/06932274-2f3c-4ce2-8336-81047f808047)

Save the obtained result in a file named "alignment.txt."

![Capture15](https://github.com/AmelMansour/Protein-Homology-Modeling/assets/141269604/e7bd9dbf-a04f-4029-8afb-89e8ed9b4918)

From this file, generate an alignment file in PIR format named "ali.pir," following the instructions provided in the Modeller documentation (in the section titled "Alignment file": https://salilab.org/modeller/manual/node13.html#SECTION00661200000000000000).

![Capture16](https://github.com/AmelMansour/Protein-Homology-Modeling/assets/141269604/7f71e329-3fe8-40b9-aa5d-45613ae9d1bc)

* Step 3: Homology Model Building:

- Preparation of the Python script file:
At this stage, the alignment file "ali.pir" and the model structure file "1jd7_clean.pdb" are available. Now, it is essential to create a Python script file that will guide Modeller through the various modeling phases.

Create a Python script file named "modeling.py" in the same directory as the other files, following the instructions provided in the Modeller documentation (section "Script file": https://salilab.org/modeller/manual/node13.html#SECTION00661300000000000000).

In this script, we have chosen to generate 10 distinct models (multiple models to assess the quality and consistency of predictions).

![Capture17](https://github.com/AmelMansour/Protein-Homology-Modeling/assets/141269604/739c4ca9-775b-4ab2-8fc2-363d862b72f1)

Script Execution:
Using the Modeller terminal, initiate the script execution with the following command:
$ mod10.4 modeling.py

![Capture18](https://github.com/AmelMansour/Protein-Homology-Modeling/assets/141269604/615a691a-cd59-46d6-bcc9-e1295deb9a43)

*Step 4: Evaluation of Homology Model Quality

The evaluation of homology model quality is crucial in the protein modeling process. This step involves checking the stereochemical validity and local quality of the generated model to determine its proximity to the native protein structure. Various tools and online platforms are available for this purpose, such as the SwissModel server, the Prosa server, Verify3D, ERRAT, and the estimation of local DOPE score. The main goal is to identify the model with the best quality for further analyses related to the protein's structure and function.

- DOPE Score (Discrete Optimized Protein Energy):
DOPE Score is a commonly used statistical potential in protein structure prediction and modeling. It estimates the quality of a protein model based on its ability to fit known experimental data, such as X-ray crystallography or nuclear magnetic resonance (NMR) data.
In other words, the DOPE score is a measure of how well a particular protein model reproduces experimental data, with lower scores indicating better-quality models as it signifies the model has the lowest energy and the highest probability of being close to the native protein structure.

The DOPE score of the model is specifically designed to select the optimal model from a series of models built by the MODELLER software.

![Capture19](https://github.com/AmelMansour/Protein-Homology-Modeling/assets/141269604/b471c29b-f54c-47c6-a712-548e302f31d1)

Calculation of the DOPE score using the command "selection.assess_dope()".

![Capture20](https://github.com/AmelMansour/Protein-Homology-Modeling/assets/141269604/148db68f-9818-4f81-9186-eb89cca7942a)

** Alternative Method:

By using the command below: Get-ChildItem *.pdb | ForEach-Object {Select-String -Path $_.FullName -Pattern "DOPE score"} | Out-File -FilePath scores2.txt, all pdb files in the current directory (alpha_amy) are searched. Subsequently, the DOPE score of each file is extracted and saved in a file named "scores2.txt".

![Capture21](https://github.com/AmelMansour/Protein-Homology-Modeling/assets/141269604/1abf21df-e2fc-4a8b-8702-9719e7b41d3f)

Calculating the DOPE Score Using the Get Command in PowerShell (equivalent to grep in Unix)

Typically, the model with the lowest DOPE score is considered the best choice for the target protein model. (Model 10: alpha_amy.B99990010.pdb)

- Normalized DOPE:
DOPE scores make it challenging to compare scores across different proteins. To overcome this limitation, the normalized DOPE method involves normalizing the DOPE score to account for the size of the protein. This allows for the comparison of models of different sizes. The normalized DOPE method calculates a Z score, which can be used to compare DOPE scores from different models.
Positive scores tend to indicate lower-quality models, while scores below -1 or more are more likely to be close to the native model. (Model 10: alpha_amy.B99990010.pdb)

![Capture22](https://github.com/AmelMansour/Protein-Homology-Modeling/assets/141269604/b49a7014-fa5a-43a7-872c-2ee48c26b3d3)

Calculating the Z-score using the command "model.assess_normalized_dope()".

![Capture23](https://github.com/AmelMansour/Protein-Homology-Modeling/assets/141269604/5a4c01ab-c079-482d-b520-a5cc837955eb)

* Ramachandran Plot
The Ramachandran plot is a graphical tool used to assess the quality of protein structure based on the torsion angles of peptide bonds in the polypeptide chain. It displays the Phi (ϕ) and Psi (ψ) torsion angles for each amino acid residue in a protein. Torsion angles are calculated from the positions of the alpha carbon atoms of adjacent residues in the polypeptide chain. The Ramachandran plot is widely used to assess the quality of protein structure models generated by computer modeling and to validate experimentally determined structures by X-ray crystallography or nuclear magnetic resonance.

Submit the selected models to the web server: https://swissmodel.expasy.org/assess and check their stereochemical validity.

![Capture 24](https://github.com/AmelMansour/Protein-Homology-Modeling/assets/141269604/80063506-bd3b-49e7-b23d-c25155d2af70)

A model with high favored Ramachandran scores and low disfavored Ramachandran scores is considered high-quality because it indicates well-folded protein structure with dihedral angles of amino acids conforming to favored Ramachandran regions. This also suggests that the structure is stable and biologically viable. Low MolProbity and Clash scores also indicate good model quality as they measure the molecular geometry and steric energy of the structure, respectively. Low scores mean that the structure is well-folded, and atoms are well-placed in space, which is crucial for the biological function of the protein.

In summary, a model with high favored Ramachandran scores, low disfavored Ramachandran scores, and low MolProbity and Clash scores is considered high-quality, indicating a well-folded, stable, and biologically viable protein structure.

--> Overall, all models demonstrate acceptable stereochemical quality with high scores in the allowed regions of the Ramachandran plot and very low percentages of inappropriate side-chain conformations.

* Local Model Quality
The Prosa server will analyze the protein model and produce various graphs and results to assess its quality.

- Access the Prosa website: https://prosa.services.came.sbg.ac.at/prosa.php
- Click on "Choose File" and select the file "alpha_amy.B99990010.pdb".
- Click on "Submit Query" to submit your file.

![Capture25](https://github.com/AmelMansour/Protein-Homology-Modeling/assets/141269604/97217f06-2e29-4787-ac00-06982c769945)

* Evaluation of the Fidelity of the α-Amylase Homology Model by Comparison with the Crystal Structure

Alignment between the modeled structure and the crystal structure is a crucial step in assessing the quality of the model. This allows comparing the predicted spatial arrangement with the one actually observed in the experimental structure. The Pymol software can be used to perform the alignment of the modeled structure with the reference experimental structure and calculate the RMSD (Root Mean Square Deviation, a measure of the difference between two molecular structures) to assess the accuracy of the α-amylase homology modeling.

- Open the model files (alpha_amy.B99990010.pdb), crystal file (1aqm.pdb), and template file (1jd7_clean.pdb) in a new PyMol session.
- Enter the following commands:
select reference, 1aqm_1 and name CA
mob_model, alpha_amy.B99990010 and name CA
align mob_model, reference

This will perform the alignment between the mobile model (your homology model), defined by CA atoms, and the reference (the crystal structure), also defined by CA atoms.

![Capture26](https://github.com/AmelMansour/Protein-Homology-Modeling/assets/141269604/790206a2-5ae8-4b7f-89e2-8bae962ebe8e)

The results indicate that the alignment of CA atoms in both structures (our model and the reference structure) was successful. The RMSD, commonly expressed in Å (angstroms), can be used to assess the quality of the alignment. In this specific case, the RMSD of 0.355 angstroms indicates a very precise correspondence between the two structures. This finding suggests that our α-amylase model closely resembles the reference crystal structure and is suitable for further analyses and predictions.

- Similarly, perform the alignment between the model structure (alpha_amy.B99990010.pdb) and the crystal structure (1aqm.pdb).
- Insert the following commands:
select mob_template, 1jd7_clean and name CA
align mob_template, reference

This will perform the alignment between the mobile part of the model (defined by CA atoms) and the reference (the crystal structure), also characterized by CA atoms.

![Capture27](https://github.com/AmelMansour/Protein-Homology-Modeling/assets/141269604/7d2b8ab5-f1ae-4ff8-940e-6c26128762d6)

The results reveal that the alignment of the model with the reference structure has an RMSD of 0.355 Å, while the alignment of the model with the template has an RMSD of 0.320 Å. These findings suggest that both the model and the template are closely aligned with the reference structure, and the model is of sufficient quality to be used in subsequent studies.

In conclusion:

After the evaluations conducted earlier, it is reasonable to consider the model alpha_amy.B99990010 as a solid approximation of the true structure of α-amylase from Alteromonas haloplanktis.
