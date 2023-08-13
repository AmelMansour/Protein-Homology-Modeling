# Protein-Homology-Modeling
Modélisation comparative de la structure de l'α-amylase (AA) d'Alteromonas haloplanktis :

Introduction :

La modélisation structurale comparative (CSM) est une technique de prédiction de la conformation des protéines à partir de la séquence d'acides aminés et des structures connues des protéines homologues. La capacité d'une protéine à interagir avec d'autres dépend en grande partie de sa structure tridimensionnelle (3D). Comprendre cette structure est essentiel pour une meilleure appréhension de son mode d'action, que ce soit dans des rôles tels que l'activité enzymatique, le transport, la signalisation, ou encore la liaison avec des ligands, des récepteurs ou des membranes.

La détermination expérimentale de la structure 3D des protéines requiert souvent des ressources importantes en termes de temps et de moyens financiers. Dans certains cas, elle peut même s'avérer impraticable, notamment pour les protéines non solubles. Pour pallier ces défis, les méthodes prédictives in silico offrent une alternative rapide et économique. Ces approches reposent sur des principes issus des domaines de la physique, des statistiques et de la biologie.
Parmi les diverses méthodes de modélisation moléculaire, la modélisation comparative est actuellement considérée comme l'une des plus précises. Ce rapport se penchera sur l'application d'une telle modélisation comparative à l'exemple de l'α-amylase (AA) issue d'Alteromonas haloplanktis.

Étape 1 : Identification d'une protéine homologue en tant que modèle pour la séquence cible :

En se référant à la base de données UniProt (http://www.uniprot.org/), la séquence de l'α-amylase (AA) d'Alteromonas haloplanktis est recherchée. Pour obtenir la séquence de la protéine mature, les séquences de signalisation ainsi que les éventuels propeptides sont exclus. 
La séquence de la protéine mature est ensuite copiée au format FASTA dans un nouveau fichier baptisé « alpha_amy.txt ».

![cap1](https://github.com/AmelMansour/Protein-Homology-Modeling/assets/141269604/fb2e2f7a-c7a0-4906-b0f9-160d742a0c05)
![Capture2](https://github.com/AmelMansour/Protein-Homology-Modeling/assets/141269604/80c9effc-df29-46b5-84ff-53ee983f7d08)
![Capture3](https://github.com/AmelMansour/Protein-Homology-Modeling/assets/141269604/c8b5f2bb-53f9-47cf-80d8-311a39946523)
![Capture4](https://github.com/AmelMansour/Protein-Homology-Modeling/assets/141269604/19449bba-57f4-4957-a5dc-053c4d06ce8b)

* Utiliser l'outil Blast pour analyser la séquence cible :
- Sélectionner l'outil "blastP" spécifique aux protéines.
- Copier la séquence ou charger le contenu du fichier "alpha_amy.txt" .
- Choisir la base de données PDB.

![Capture5](https://github.com/AmelMansour/Protein-Homology-Modeling/assets/141269604/19e89504-0256-4156-aa4f-30c5899d3a4c)
![Capture6](https://github.com/AmelMansour/Protein-Homology-Modeling/assets/141269604/73b61f1a-f2ea-472c-a642-8b5a578e71de)
![Capture7](https://github.com/AmelMansour/Protein-Homology-Modeling/assets/141269604/c160bfdc-51b5-477c-a70d-e4bb4f2a1ff5)
![Capture8](https://github.com/AmelMansour/Protein-Homology-Modeling/assets/141269604/1d612110-3f5a-4667-9de3-59d6f7f6a5f6)


Le choix d'un modèle approprié est un aspect important de la modélisation structurelle comparative (CSM). Voici quelques critères importants à prendre en compte lors du choix d'un modèle :

• Similitude de séquence : la matrice doit avoir une similarité de séquence suffisamment élevée avec la protéine cible pour rendre les prédictions de structure plus fiables. En général, une similarité de séquence d'au moins 30 % est recommandée.

• Qualité de la structure : le modèle doit avoir une structure 3D qui est résolue avec une qualité adéquate, mesurée par des paramètres tels que la résolution, E-value, le nombre de résidus manquants, le taux de couverture….

• Fonction biologique : Nous devons savoir que la matrice à une fonction biologique similaire à celle de la protéine cible. Les protéines homologues ayant des fonctions biologiques similaires ont tendance à avoir des structures similaires.

• Disponibilité de la structure : le modèle doit être disponible dans une base de données de structure de protéines telle que la base de données PDB ou UniProt.

--> Le choix du modèle (Template) est porté sur « Chaîne A, ALPHA-AMYLASE [Pseudoalteromonas haloplanktis] » (1JD7).

![Capture9](https://github.com/AmelMansour/Protein-Homology-Modeling/assets/141269604/eeaae735-d762-4a92-9bde-cc524dd9b331)

* Téléchargez le fichier de coordonnées (1jd7 .pdb) depuis le serveur de la PDB. Ce fichier représente la structure qui servira de modèle (Template) pour la modélisation.

![Capture10](https://github.com/AmelMansour/Protein-Homology-Modeling/assets/141269604/2d5b2643-c45c-48e0-b978-5a650e34e60e)
![Capture11](https://github.com/AmelMansour/Protein-Homology-Modeling/assets/141269604/d5611222-753c-4183-96dc-f11d00604851)

Étape 2 : Alignement des séquences cible et modèle

* Préparation du modèle :
- Utiliser un logiciel de visualisation de structures protéiques tel que PyMOL ou Chimera pour ouvrir le fichier "1jd7.pdb".
- Éliminer tous les hétéroatomes et molécules autres que la protéine elle-même.

![Capture12](https://github.com/AmelMansour/Protein-Homology-Modeling/assets/141269604/fa08d068-d5ea-4c8e-9780-74b27feb156b)

** Méthode alternative :

On peut faire ces modifications directement avec un éditeur de texte (par exemple, Notepad, pluma pour Unix.)
- Sauvegarder le fichier du Template en format PDB « 1jd7_clean.pdb ».
-Convertir le fichier « 1jd7_clean.pdb » en format Fasta à l'aide d'un outil en ligne tel que https://zhanggroup.org/pdb2fasta/ .

![Capture13](https://github.com/AmelMansour/Protein-Homology-Modeling/assets/141269604/67e0599b-bc17-4f41-8ef9-4179bd6f2071)

Nous allons procéder à un alignement de séquences par paire entre le modèle et la cible à l'aide du programme Needle du logiciel EMBOSS.

- Accéder au site http://www.ebi.ac.uk/Tools/psa/emboss_needle
- Copier/coller les séquences de la cible et du Template dans les deux champs prévus à cet effet.

![Capture14](https://github.com/AmelMansour/Protein-Homology-Modeling/assets/141269604/06932274-2f3c-4ce2-8336-81047f808047)

Enregistrer le résultat obtenu dans un fichier « alignement.txt ».

![Capture15](https://github.com/AmelMansour/Protein-Homology-Modeling/assets/141269604/e7bd9dbf-a04f-4029-8afb-89e8ed9b4918)

À partir de ce fichier, générer un fichier d'alignement au format PIR appelé "ali.pir", en suivant les instructions fournies dans la documentation de Modeller (dans la section intitulée "Alignment file": https://salilab.org/modeller/manual/node13.html#SECTION00661200000000000000).

![Capture16](https://github.com/AmelMansour/Protein-Homology-Modeling/assets/141269604/7f71e329-3fe8-40b9-aa5d-45613ae9d1bc)

* Étape 3 : Édification du modèle d'homologie :

- Préparation du fichier de script Python :
À ce stade, le fichier d'alignement "ali.pir" ainsi que le fichier de structure du modèle "1jd7_clean.pdb" sont disponibles. À présent, il est essentiel de créer un fichier de script Python qui guidera Modeller à travers les différentes phases de modélisation.

Fabriquer un fichier de script Python intitulé "modeling.py" dans le même répertoire que les autres fichiers, en se conformant aux indications fournies dans la documentation de Modeller (section « Script file » : https://salilab.org/modeller/manual/node13.html#SECTION00661300000000000000 ).

Dans ce script, nous avons opté pour la production de 10 modèles distincts (plusieurs modèles afin d'évaluer la qualité et la cohérence des prédictions).

![Capture17](https://github.com/AmelMansour/Protein-Homology-Modeling/assets/141269604/739c4ca9-775b-4ab2-8fc2-363d862b72f1)

Exécution du script :
À l'aide du terminal de Modeller, lancez l'exécution du script en utilisant la commande ci-dessous :
$ mod10.4 modeling.py

![Capture18](https://github.com/AmelMansour/Protein-Homology-Modeling/assets/141269604/615a691a-cd59-46d6-bcc9-e1295deb9a43)

* Étape 4 : Évaluation de la qualité du modèle d'homologie

L'évaluation de la qualité du modèle d'homologie revêt une importance primordiale au sein du processus de modélisation de protéines. Cette étape implique la vérification de la validité stéréochimique et de la qualité locale du modèle généré, dans le but de déterminer sa proximité avec la structure native de la protéine. Pour ce faire, divers outils et plateformes en ligne sont disponibles, tels que le serveur SwissModel, le serveur Prosa, Verify3D, ERRAT, ainsi que l'estimation du score DOPE local. L'objectif principal est d'identifier le modèle présentant la meilleure qualité, en vue de son utilisation dans des analyses ultérieures relatives à la structure et à la fonction de la protéine.

- Score DOPE (Discrete Optimized Protein Energy) :

Est un potentiel statistique couramment utilisé dans la prédiction et la modélisation de la structure des protéines. Le score DOPE estime la qualité d'un modèle de protéine en fonction de sa capacité à s'adapter aux données expérimentales connues, telles que les données de la cristallographie aux rayons X ou de la résonance magnétique nucléaire (RMN).
En d'autres termes, le score DOPE est une mesure de la capacité d'un modèle protéique particulier à reproduire des données expérimentales, les scores les plus bas indiquant des modèles de meilleure qualité car cela signifie qu'il a la plus faible énergie et la plus grande probabilité d'être proche de la structure native de la protéine.

Le score DOPE du modèle est spécialement conçu pour choisir le modèle optimal parmi une série de modèles construits par le logiciel MODELLER.

![Capture19](https://github.com/AmelMansour/Protein-Homology-Modeling/assets/141269604/b471c29b-f54c-47c6-a712-548e302f31d1)

Calcul du score DOPE avec la commande « selection.assess_dope() »

![Capture20](https://github.com/AmelMansour/Protein-Homology-Modeling/assets/141269604/148db68f-9818-4f81-9186-eb89cca7942a)

Méthode alternative :

En utilisant la commande ci-dessous : « Get-ChildItem *.pdb | ForEach-Object {Select-String -Path $_.FullName -Pattern "DOPE score"} | Out-File -FilePath scores2.txt», l'ensemble des fichiers pdb dans le répertoire actuel (alpha_amy) est recherché. Ensuite, le score DOPE de chaque fichier est extrait et enregistré dans un fichier baptisé "scores2.txt".

![Capture21](https://github.com/AmelMansour/Protein-Homology-Modeling/assets/141269604/1abf21df-e2fc-4a8b-8702-9719e7b41d3f)

Calcul du score DOPE à l'aide de la commande Get dans PowerShell (équivalent de grep pour Unix)

Habituellement, le modèle présentant le score DOPE le plus bas est considéré comme le meilleur choix pour le modèle de la protéine cible. (Modèle 10 : alpha_amy.B99990010.pdb)

- DOPE normalisée
Les scores DOPE rendent difficile la comparaison des scores entre différentes protéines. Pour surmonter cette limitation, la méthode DOPE normalisée consiste à normaliser le score DOPE pour prendre en compte la taille de la protéine. Cela permet de comparer des modèles de protéines de tailles différentes. Pour surmonter cette limitation, la méthode DOPE normalisée permet de calculer un score Z, qui peut être utilisé pour comparer les scores DOPE de différents modèles.

Les scores positifs tendent à indiquer des modèles de moindre qualité, tandis que les scores en dessous de -1 ou plus sont plus susceptibles d'être proches du modèle natif. (Modèle 10 : alpha_amy.B99990010.pdb)

![Capture22](https://github.com/AmelMansour/Protein-Homology-Modeling/assets/141269604/b49a7014-fa5a-43a7-872c-2ee48c26b3d3)

Calcul du Z-score avec la commande « model.assess_normalized_dope()»

![Capture23](https://github.com/AmelMansour/Protein-Homology-Modeling/assets/141269604/5a4c01ab-c079-482d-b520-a5cc837955eb)

* Graphique de Ramachandran
  
Le diagramme de Ramachandran est un outil graphique utilisé pour évaluer la qualité de la structure des protéines en fonction des angles de torsion des liaisons peptidiques dans la chaîne polypeptidique. Il affiche les angles de torsion Phi (ϕ) et Psi (ψ) pour chaque résidu d'acide aminé dans une protéine. Les angles de torsion sont calculés à partir des positions des atomes de carbone alpha des résidus adjacents dans la chaîne polypeptidique.
Le diagramme de Ramachandran est largement utilisé pour évaluer la qualité des modèles de structures de protéines générées par modélisation informatique, ainsi que pour valider les structures expérimentales déterminées par cristallographie aux rayons X ou par résonance magnétique nucléaire.
-Soumettre les modèles sélectionnés au serveur Web : https://swissmodel.expasy.org/assess et vérifie leur validité stéréochimique.

![Capture 24](https://github.com/AmelMansour/Protein-Homology-Modeling/assets/141269604/80063506-bd3b-49e7-b23d-c25155d2af70)

Un modèle avec des scores Ramachandran favorisés élevés et des scores Ramachandran faibles sont considérés comme de haute qualité car cela signifie que la structure protéique est bien pliée et que les angles dièdres des acides aminés sont conformes aux régions Ramachandran favorisées. Cela suggère également que la structure est stable et biologiquement viable.
Des scores MolProbity et Clash faibles indiquent également une bonne qualité de modèle car ils mesurent la géométrie moléculaire et l'énergie stérique de la structure, respectivement. Des scores faibles signifient que la structure est bien pliée et que les atomes sont bien placés dans l'espace, ce qui est important pour le fonctionnement biologique de la protéine.
En somme, un modèle avec des scores Ramachandran favorisés élevés et des scores Ramachandran faibles et des scores MolProbity et Clash faibles est considéré comme de haute qualité et indique une structure protéique bien pliée, stable et biologiquement viable. 

--> Dans l'ensemble, tous les modèles démontrent une qualité stéréochimique acceptable avec des scores élevés dans les zones permises du graphique de Ramachandran et des pourcentages très faibles de conformations latérales inappropriées.

* Qualité locale du modèle
Le serveur Prosa analysera le modèle protéique et produira divers graphiques et résultats pour évaluer sa qualité.

- Accédez au site Web de Prosa : https://prosa.services.came.sbg.ac.at/prosa.php
- Cliquez sur "Choose File" et sélectionnez le fichier «alpha_amy.B99990010.pdb ».
- Cliquez sur "Submit Query" pour soumettre votre fichier.

![Capture25](https://github.com/AmelMansour/Protein-Homology-Modeling/assets/141269604/97217f06-2e29-4787-ac00-06982c769945)

* Évaluation de la fidélité du modèle d'homologie de l'α-amylase par comparaison avec la structure cristalline
  
L'alignement entre la structure modélisée et la structure cristalline constitue une étape essentielle pour évaluer la qualité du modèle. Cela permet de confronter la disposition spatiale prédite avec celle réellement observée dans la structure expérimentale. 
Le logiciel Pymol peut être utilisé pour effectuer l'alignement de la structure modélisée avec la structure expérimentale de référence et calculer le RMSD (signifie Root Mean Square Deviation, qui est une mesure de l'écart entre deux structures moléculaires) pour évaluer la précision de la modélisation d'homologie de l'α-amylase.

- Ouvrer les fichiers de modèle (alpha_amy.B99990010.pdb), de cristal (1aqm.pdb) et de modèle (1jd7_clean.pdb) dans une nouvelle session PyMol.
- Saisir les commandes suivantes :
select reference, 1aqm_1 and name CA
mob_model, alpha_amy.B99990010 and name CA
align mob_model, reference

Cela effectuera l'alignement entre le modèle mobile (votre modèle d'homologie), défini par les atomes CA, et la référence (la structure cristalline), également définie par les atomes CA.

![Capture26](https://github.com/AmelMansour/Protein-Homology-Modeling/assets/141269604/790206a2-5ae8-4b7f-89e2-8bae962ebe8e)

Les résultats signalent que l'alignement des atomes CA des deux structures (notre modèle et la structure de référence) s'est déroulé avec succès. Le RMSD, couramment exprimé en Å (angstroms), peut être employé pour évaluer la qualité de l'alignement. Dans ce cas précis, le RMSD de 0,355 angströms dénote une correspondance très précise entre les deux structures. Cette constatation suggère que notre modèle d'α-amylase se rapproche considérablement de la structure cristalline de référence et est apte à être utilisé pour des analyses et des prédictions ultérieures.

- De manière similaire, effectuez l'alignement entre la structure du modèle (alpha_amy.B99990010.pdb) et la structure cristalline (1aqm.pdb).
- Insérez les commandes suivantes :
select mob_template, 1jd7_clean and name CA
align mob_template, reference

Ceci permettra l'alignement entre la partie mobile du modèle (définie par les atomes CA), et le référentiel (la structure cristalline), également caractérisée par les atomes CA.

![Capture27](https://github.com/AmelMansour/Protein-Homology-Modeling/assets/141269604/7d2b8ab5-f1ae-4ff8-940e-6c26128762d6)

Les résultats révèlent que l'alignement du modèle avec la structure de référence présente un RMSD de 0,355 Å, tandis que l'alignement du modèle avec le Template présente un RMSD de 0,320 Å. Ces constatations suggèrent que tant le modèle que le Template sont étroitement alignés avec la structure de référence, et que le modèle est de qualité adéquate pour être exploité dans des études subséquentes.

* En conclusion :

Après les évaluations effectuées précédemment, il est plausible de considérer le modèle alpha_amy.B99990010 comme une approximation solide de la véritable structure de l'α-amylase issue d'Alteromonas haloplanktis.
