# Protein-Homology-Modeling
Modélisation comparative de la structure de l'α-amylase (AA) d'Alteromonas haloplanktis :

Introduction :

La modélisation structurale comparative (CSM) est une technique de prédiction de la conformation des protéines à partir de la séquence d'acides aminés et des structures connues des protéines homologues. La capacité d'une protéine à interagir avec d'autres dépend en grande partie de sa structure tridimensionnelle (3D). Comprendre cette structure est essentiel pour une meilleure appréhension de son mode d'action, que ce soit dans des rôles tels que l'activité enzymatique, le transport, la signalisation, ou encore la liaison avec des ligands, des récepteurs ou des membranes.

La détermination expérimentale de la structure 3D des protéines requiert souvent des ressources importantes en termes de temps et de moyens financiers. Dans certains cas, elle peut même s'avérer impraticable, notamment pour les protéines non solubles. Pour pallier ces défis, les méthodes prédictives in silico offrent une alternative rapide et économique. Ces approches reposent sur des principes issus des domaines de la physique, des statistiques et de la biologie.
Parmi les diverses méthodes de modélisation moléculaire, la modélisation comparative est actuellement considérée comme l'une des plus précises. Ce rapport se penchera sur l'application d'une telle modélisation comparative à l'exemple de l'α-amylase (AA) issue d'Alteromonas haloplanktis.

Étape 1 : Identification d'une protéine homologue en tant que modèle pour la séquence cible :
En se référant à la base de données UniProt (http://www.uniprot.org/), la séquence de l'α-amylase (AA) d'Alteromonas haloplanktis est recherchée. Pour obtenir la séquence de la protéine mature, les séquences de signalisation ainsi que les éventuels propeptides sont exclus. 
La séquence de la protéine mature est ensuite copiée au format FASTA dans un nouveau fichier baptisé « alpha_amy.txt ».
![Aspose Words f7fc63ad-96a3-474b-ba4a-1ff6b42ed1cd 001](https://github.com/AmelMansour/Protein-Homology-Modeling/assets/141269604/4da670c4-31ea-4210-b49b-4c182ad15135)
![Aspose Words f7fc63ad-96a3-474b-ba4a-1ff6b42ed1cd 002](https://github.com/AmelMansour/Protein-Homology-Modeling/assets/141269604/78e02fad-71f8-4769-9f5d-3bd3adaad2c9)
![Aspose Words f7fc63ad-96a3-474b-ba4a-1ff6b42ed1cd 003](https://github.com/AmelMansour/Protein-Homology-Modeling/assets/141269604/2c4451ce-f330-47af-889d-6188ddc83b91)


Utiliser l'outil Blast pour analyser la séquence cible :

Sélectionner l'outil "blastP" spécifique aux protéines.

Copier la séquence ou charger le contenu du fichier "alpha_amy.txt", puis choisir la base de données PDB.

![Aspose Words f7fc63ad-96a3-474b-ba4a-1ff6b42ed1cd 004](https://github.com/AmelMansour/Protein-Homology-Modeling/assets/141269604/8e66fa03-7a53-491b-858b-4dfcd3599b59)
![Aspose Words f7fc63ad-96a3-474b-ba4a-1ff6b42ed1cd 005](https://github.com/AmelMansour/Protein-Homology-Modeling/assets/141269604/6e585e67-4242-46f2-8677-d776e4cb6af9)

Le choix d'un modèle approprié est un aspect important de la modélisation structurelle comparative (CSM). Voici quelques critères importants à prendre en compte lors du choix d'un modèle :

• Similitude de séquence : la matrice doit avoir une similarité de séquence suffisamment élevée avec la protéine cible pour rendre les prédictions de structure plus fiables. En général, une similarité de séquence d'au moins 30 % est recommandée.

• Qualité de la structure : le modèle doit avoir une structure 3D qui est résolue avec une qualité adéquate, mesurée par des paramètres tels que la résolution, E-value, le nombre de résidus manquants, le taux de couverture….

• Fonction biologique : Nous devons savoir que la matrice à une fonction biologique similaire à celle de la protéine cible. Les protéines homologues ayant des fonctions biologiques similaires ont tendance à avoir des structures similaires.

• Disponibilité de la structure : le modèle doit être disponible dans une base de données de structure de protéines telle que la base de données PDB ou UniProt.

--> Le choix du modèle (Template) est porté sur « Chaîne A, ALPHA-AMYLASE [Pseudoalteromonas haloplanktis] » (1JD7).

![Aspose Words f7fc63ad-96a3-474b-ba4a-1ff6b42ed1cd 006](https://github.com/AmelMansour/Protein-Homology-Modeling/assets/141269604/533fc441-db79-470f-abe8-3e88b47155bb)

Téléchargez le fichier de coordonnées (1jd7 .pdb) depuis le serveur de la PDB. Ce fichier représente la structure qui servira de modèle (Template) pour la modélisation.

![Aspose Words f7fc63ad-96a3-474b-ba4a-1ff6b42ed1cd 007](https://github.com/AmelMansour/Protein-Homology-Modeling/assets/141269604/5ef717a6-f049-4577-884e-995ba5ecb658)


Étape 2 : Alignement des séquences cible et modèle

Préparation du modèle :

Utiliser un logiciel de visualisation de structures protéiques tel que PyMOL ou Chimera pour ouvrir le fichier "1jd7.pdb".
Éliminer tous les hétéroatomes et molécules autres que la protéine elle-même, car ils ne sont pas requis pour la modélisation comparative.

![Aspose Words f7fc63ad-96a3-474b-ba4a-1ff6b42ed1cd 008](https://github.com/AmelMansour/Protein-Homology-Modeling/assets/141269604/4321e097-8c39-440c-b21f-139c37691ebd)

Méthode alternative :

Il est possible d'effectuer ces ajustements directement à l'aide d'un éditeur de texte (comme Notepad, Sublime Text, Atom, pluma pour Unix).

Enregistrer le fichier du modèle sous le format PDB en tant que « 1jd7_clean.pdb ».

Utiliser un outil en ligne tel que https://zhanggroup.org/pdb2fasta/ pour convertir le fichier « 1jd7_clean.pdb » en format FASTA.

![Aspose Words f7fc63ad-96a3-474b-ba4a-1ff6b42ed1cd 009](https://github.com/AmelMansour/Protein-Homology-Modeling/assets/141269604/fa1fade5-6b21-46af-ab52-e0570028692c)

Visiter le site http://www.ebi.ac.uk/Tools/psa/emboss\_needle/ et insérer les séquences de la cible et du modèle dans les champs désignés à cet effet. Ensuite, appuyer sur le bouton "submit" pour obtenir l'alignement.

![Aspose Words f7fc63ad-96a3-474b-ba4a-1ff6b42ed1cd 010](https://github.com/AmelMansour/Protein-Homology-Modeling/assets/141269604/4b915911-3c04-4d74-b6b2-478d335d634a)

Enregistrer le résultat obtenu dans un fichier « alignement.txt ».

![Aspose Words f7fc63ad-96a3-474b-ba4a-1ff6b42ed1cd 011](https://github.com/AmelMansour/Protein-Homology-Modeling/assets/141269604/a9627f1c-63c7-41aa-8945-089f7bf692c4)

À partir de ce fichier, générer un fichier d'alignement au format PIR appelé "ali.pir", en suivant les instructions fournies dans la documentation de Modeller (dans la section intitulée "Alignment file": https://salilab.org/modeller/manual/node13.html#SECTION00661200000000000000).

![Aspose Words f7fc63ad-96a3-474b-ba4a-1ff6b42ed1cd 012](https://github.com/AmelMansour/Protein-Homology-Modeling/assets/141269604/d84074c6-3a0f-4f24-932d-b1d29fb8e1f5)


Étape 3 : Édification du modèle d'homologie :

Préparation du fichier de script Python :
À ce stade, le fichier d'alignement "ali.pir" ainsi que le fichier de structure du modèle "1jd7_clean.pdb" sont disponibles. À présent, il est essentiel de créer un fichier de script Python qui guidera Modeller à travers les différentes phases de modélisation.

Fabriquer un fichier de script Python intitulé "modeling.py" dans le même répertoire que les autres fichiers, en se conformant aux indications fournies dans la documentation de Modeller (section « Script file » : https://salilab.org/modeller/manual/node13.html#SECTION00661300000000000000 ).

Dans ce script, nous avons opté pour la production de 10 modèles distincts (plusieurs modèles afin d'évaluer la qualité et la cohérence des prédictions).

![Aspose Words f7fc63ad-96a3-474b-ba4a-1ff6b42ed1cd 013](https://github.com/AmelMansour/Protein-Homology-Modeling/assets/141269604/0f2a8006-bd10-42b7-bfd0-34bae7e08031)

Exécution du script :
À l'aide du terminal de Modeller, lancez l'exécution du script en utilisant la commande ci-dessous :
$ mod10.4 modeling.py

![Aspose Words f7fc63ad-96a3-474b-ba4a-1ff6b42ed1cd 014](https://github.com/AmelMansour/Protein-Homology-Modeling/assets/141269604/d6732d72-a5ce-4491-b07f-46cf0fc5af7f)

Étape 4 : Évaluation de la qualité du modèle d'homologie

L'évaluation de la qualité du modèle d'homologie revêt une importance primordiale au sein du processus de modélisation de protéines. Cette étape implique la vérification de la validité stéréochimique et de la qualité locale du modèle généré, dans le but de déterminer sa proximité avec la structure native de la protéine. Pour ce faire, divers outils et plateformes en ligne sont disponibles, tels que le serveur SwissModel, le serveur Prosa, Verify3D, ERRAT, ainsi que l'estimation du score DOPE local. L'objectif principal est d'identifier le modèle présentant la meilleure qualité, en vue de son utilisation dans des analyses ultérieures relatives à la structure et à la fonction de la protéine.

Score DOPE (Discrete Optimized Protein Energy) :
Le score DOPE évalue la qualité globale du modèle en termes d'énergie et de probabilité de correspondre à la structure native. En général, un score DOPE plus bas indique un modèle de meilleure qualité, car cela traduit une énergie réduite et une plus grande probabilité de proximité avec la structure native de la protéine.

Le score DOPE du modèle est spécialement conçu pour choisir le modèle optimal parmi une série de modèles construits par le logiciel MODELLER.

![Aspose Words f7fc63ad-96a3-474b-ba4a-1ff6b42ed1cd 015](https://github.com/AmelMansour/Protein-Homology-Modeling/assets/141269604/5b11881a-97b2-4a4f-8299-7313cc242ed7)

Calcul du score DOPE avec la commande « selection.assess_dope() »

![Aspose Words f7fc63ad-96a3-474b-ba4a-1ff6b42ed1cd 016](https://github.com/AmelMansour/Protein-Homology-Modeling/assets/141269604/a5bbb752-d3c9-4290-94b4-133dc54ab05d)


Méthode alternative :

En utilisant la commande ci-dessous : « Get-ChildItem *.pdb | ForEach-Object {Select-String -Path $_.FullName -Pattern "DOPE score"} | Out-File -FilePath scores2.txt», l'ensemble des fichiers pdb dans le répertoire actuel (alpha_amy) est recherché. Ensuite, le score DOPE de chaque fichier est extrait et enregistré dans un fichier baptisé "scores2.txt".

![Aspose Words f7fc63ad-96a3-474b-ba4a-1ff6b42ed1cd 017](https://github.com/AmelMansour/Protein-Homology-Modeling/assets/141269604/7639705d-fe86-4c70-b5b4-98a8644dbdfd)

Calcul du score DOPE à l'aide de la commande Get dans PowerShell (équivalent de grep pour Unix)

Habituellement, le modèle présentant le score DOPE le plus bas est considéré comme le meilleur choix pour le modèle de la protéine cible. (Modèle 10 : alpha_amy.B99990010.pdb)

Approche DOPE normalisée :
Le score DOPE n'est pas normalisé par rapport à la taille de la protéine et est échelonné de manière arbitraire, ce qui complique la comparaison entre les scores de différentes protéines. Pour pallier cette limitation, la méthode DOPE normalisée permet de calculer un score Z, qui s'avère utile pour comparer les scores DOPE entre divers modèles.

Les scores positifs tendent à indiquer des modèles de moindre qualité, tandis que les scores en dessous de -1 ou plus sont plus susceptibles d'être proches du modèle natif. (Modèle 10 : alpha_amy.B99990010.pdb)

![Aspose Words f7fc63ad-96a3-474b-ba4a-1ff6b42ed1cd 018](https://github.com/AmelMansour/Protein-Homology-Modeling/assets/141269604/f9c2bdc6-efc3-4cb8-8e17-218cb9750888)

Calcul du Z-score avec la commande « model.assess_normalized_dope()»

![Aspose Words f7fc63ad-96a3-474b-ba4a-1ff6b42ed1cd 019](https://github.com/AmelMansour/Protein-Homology-Modeling/assets/141269604/48eeb66e-9c76-4e6f-bd1e-3cb7ca765c67)


Graphique de Ramachandran
Le graphique de Ramachandran constitue un outil de grande importance pour l'évaluation de la qualité stéréochimique d'un modèle. Il permet de visualiser la répartition des angles de torsion φ et ψ pour chaque résidu dans une structure protéique. Les angles de torsion admis sont regroupés en différentes zones sur le graphique de Ramachandran, incluant les zones permises, les zones favorables et les zones défavorables.

Pour évaluer la validité stéréochimique des modèles choisis, ils peuvent être soumis au serveur Web suivant : https://swissmodel.expasy.org/assess.

![Aspose Words f7fc63ad-96a3-474b-ba4a-1ff6b42ed1cd 020](https://github.com/AmelMansour/Protein-Homology-Modeling/assets/141269604/981ed6fa-cf0f-4f68-929f-d584fb99def3)

En général, un modèle qui affiche des scores élevés pour les conformations favorables sur le graphique de Ramachandran, ainsi que des scores bas pour les conformations atypiques (outliers) et des scores faibles pour MolProbity et Clash, est considéré comme étant de bonne qualité stéréochimique. Dans l'ensemble, tous les modèles démontrent une qualité stéréochimique acceptable avec des scores élevés dans les zones permises du graphique de Ramachandran et des pourcentages très faibles de conformations latérales inappropriées.

Qualité locale du modèle
Le serveur Prosa analysera le modèle protéique et produira divers graphiques et résultats pour évaluer sa qualité.

Accédez au site Web de Prosa : https://prosa.services.came.sbg.ac.at/prosa.php

Cliquez sur "Choose File" et sélectionnez le fichier «alpha_amy.B99990010.pdb ».

Cliquez sur "Submit Query" pour soumettre votre fichier.

Le deuxième graphique représente la distribution normalisée de l'énergie potentielle. Il expose la répartition de l'énergie potentielle de la structure par rapport à une distribution normale. Les pics dans l'histogramme signalent les régions où l'énergie potentielle est élevée, indiquant ainsi une moindre stabilité structurelle. (Selon ce graphique, le modèle semble bien stable)

Le premier graphique est le graphique des scores Z, illustrant l'énergie potentielle de la structure en fonction de la position de chaque résidu dans la séquence. Les zones en bleu foncé correspondent aux régions de la protéine où l'énergie potentielle est minimale, traduisant une stabilité accrue de la structure. Les zones en jaune ou rouge (absentes dans ce graphique) indiquent des régions où l'énergie potentielle est plus élevée, signalant une stabilité réduite de la structure.

![Aspose Words f7fc63ad-96a3-474b-ba4a-1ff6b42ed1cd 025](https://github.com/AmelMansour/Protein-Homology-Modeling/assets/141269604/54596b07-eb41-4237-87d2-5aee9defa45a)

Évaluation de la fidélité du modèle d'homologie de l'α-amylase par comparaison avec la structure cristalline
L'alignement entre la structure modélisée et la structure cristalline constitue une étape essentielle pour évaluer la qualité du modèle. Cela permet de confronter la disposition spatiale prédite avec celle réellement observée dans la structure expérimentale. Le logiciel PyMol permet d'effectuer cet alignement en utilisant les atomes de carbone alpha comme points de référence.

Ce genre d'analyse procure des informations quant à la précision de la prédiction de la structure et identifie les régions susceptibles de contenir des erreurs.

Pour ce faire, ouvrez les fichiers de modèle (alpha_amy.B99990010.pdb), de cristal (1aqm.pdb) et de modèle (1jd7_clean.pdb) dans une nouvelle session PyMol. Ensuite, saisissez les commandes suivantes :

select reference, 1aqm_1 and name CA
mob_model, alpha_amy.B99990010 and name CA
align mob_model, reference

Cela effectuera l'alignement entre le modèle mobile (votre modèle d'homologie), défini par les atomes CA, et la référence (la structure cristalline), également définie par les atomes CA.

![Aspose Words f7fc63ad-96a3-474b-ba4a-1ff6b42ed1cd 026](https://github.com/AmelMansour/Protein-Homology-Modeling/assets/141269604/cbd048e8-e736-453c-ba12-de6f6e0043bc)

Les résultats signalent que l'alignement des atomes CA des deux structures (notre modèle et la structure de référence) s'est déroulé avec succès. Le RMSD, couramment exprimé en Å (angstroms), peut être employé pour évaluer la qualité de l'alignement. Dans ce cas précis, le RMSD de 0,355 angströms dénote une correspondance très précise entre les deux structures. Cette constatation suggère que notre modèle d'α-amylase se rapproche considérablement de la structure cristalline de référence et est apte à être utilisé pour des analyses et des prédictions ultérieures.

De manière similaire, effectuez l'alignement entre la structure du modèle (alpha_amy.B99990010.pdb) et la structure cristalline (1aqm.pdb).

Insérez les commandes suivantes :
select mob_template, 1jd7_clean and name CA
align mob_template, reference

Ceci permettra l'alignement entre la partie mobile du modèle (définie par les atomes CA), et le référentiel (la structure cristalline), également caractérisée par les atomes CA.

![Aspose Words f7fc63ad-96a3-474b-ba4a-1ff6b42ed1cd 027](https://github.com/AmelMansour/Protein-Homology-Modeling/assets/141269604/bda796a5-bdd0-44ba-909a-175d222b8f73)

Les résultats révèlent que l'alignement du modèle avec la structure de référence présente un RMSD de 0,355 Å, tandis que l'alignement du modèle avec le Template présente un RMSD de 0,320 Å. Ces constatations suggèrent que tant le modèle que le Template sont étroitement alignés avec la structure de référence, et que le modèle est de qualité adéquate pour être exploité dans des études subséquentes.

En conclusion :

Après les évaluations effectuées précédemment, il est plausible de considérer le modèle alpha_amy.B99990010 comme une approximation solide de la véritable structure de l'α-amylase issue d'Alteromonas haloplanktis.
