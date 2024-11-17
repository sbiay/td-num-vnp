---
mainfont: Alegreya
title: Présentation des TD
date: 1^er^ semestre 2024-2025
author: Sébastien Biay
---

Présentation des TD
=====

Plan :

1. [Ce que l'on va faire](#t1)
	1. [Le sujet : les ponts dans la région Pays de la Loire ](#t1-1)
	2. [Objectifs ](#t1-2)
	3. [Evaluation ](#t1-3)
	4. [Rythme et degré de difficulté ](#t1-4)
	5. [Accès aux documents ](#t1-5)
	6. [Logiciels requis ](#t1-6)
2. [Qu'est-ce qu'une base de donnée ?](#t2)
	1. [Définition ](#t2-1)
	2. [Avantages et inconvénients du modèle en table ](#t2-2)
3. [Sauvegarder son travail](#t3)
	1. [Au fait, comment sauvegardez-vous vos données ? ](#t3-1)
	2. [Des méthodes très très durables ](#t3-2)
	3. [Des méthodes plus modernes ](#t3-3)
	4. [Conseils pratiques ](#t3-4)
	5. [Des solutions cloud ](#t3-5)

[comment]: <> (FINET)


<a id='t1'/>

# Ce que l'on va faire
[comment1]: <1> (TITRE1)

[comment2]: <1> (***Avant de commencer*** : lancer ma base Heurist.)

[comment3]: <1> (Vous êtes des utilisateurs des bases de données ; la plupart du temps sans le savoir ; mais pratiquement toute recherche sur un site web --catalogue de bibliothèque ou autre, site commercial-- s'appuie sur une ou plusieurs bases de données.)

[comment4]: <1> (1. On va apprendre à utiliser de manière experte et critique certaines bases de données patirmoniales)

[comment5]: <1> (2. On va découvrir l'envers du décor : comment faire sa base de données sur un objet patrimonial ? On va découvrir ensemble les principes de conception et quelques techniques de réalisation d'une base de données)


<a id='t1-1'/>

## Le sujet : les ponts dans la région Pays de la Loire 

### <2>

**Image** : [Ponts de Mauves-sur-Loire, 44, achevé en 1882<a date='sans'/>](img/ponts-pays-loire_IA44007206-008-IVR52_20194400172NUCA.jpg)

[comment7]: <2> (Nous allons appréhender ce sujet sous l'angle de l'information numérique ; pour cela, nous allons découvrir l'univers des bases de données patrimoniales.)


<a id='t1-2'/>

## Objectifs 

### <3>

Principaux :

- Conceptualiser une base de données
- Récolter des données en ligne sur les sites pertinents
- Construire une base de données relationnelles dans un tableur

Bonus :

- Convertir la base dans un gestionnaire de bases de données professionnel : **Heurist**
- Proposer une [interface web de consultation](https://heurist.huma-num.fr/heurist/?db=sbiay_ponts_pays_loire&website&id=199&pageid=663)
	- identifiant : `etudiant`
	- mot de passe : `etudiant`

<!--Je rencontre des problèmes de connexion avec Firefox à la maison-->

<!--
Autres objectifs possibles :
- Produire des statistiques et les visualiser
- Publier la base de données dans un *système de gestion de contenu*^1^ libre : Omeka

\textsuperscript{1} CMS pour content management system.
-->


<a id='t1-3'/>

## Evaluation 

### <4>

- Contrôle continu intégral
- Atteindre les objectifs !
- Remettre des fichiers et des données de qualités


<a id='t1-4'/>

## Rythme et degré de difficulté 

### <5>

**Mes objectifs** :

- Que les personnes du groupe les moins à l'aise en informatique puissent avoir 20/20

[comment11]: <5> (Si j'ouvre un tableur, qui se sent déjà un peu mal ?)

- Que vous vous sentiez capables de réutiliser ces apprentissages pour vos propres études (SAV)

**Votre implication** :

- Assiduité
- Entraînement

<!--


<a id='t1-5'/>

## Accès aux documents 

### <6>

Tous les diaporamas sont accessibles en deux formats :

1. PDF
2. Markdown sur mon compte Github [ici](https://github.com/sbiay/td-num-vnp)

-->


<a id='t1-6'/>

## Logiciels requis 

### <7>

- Un éditeur de texte
	- [Notepad++](https://notepad-plus-plus.org/downloads/) : licence GNU, uniquement pour Windows
	- [Visual Studio Code](https://code.visualstudio.com/download) : pour tous les systèmes d'exploitation, développé par Microsoft, gratuit

- Un logiciel de tableur
	- [LibreOffice Calc](https://fr.libreoffice.org/download/telecharger-libreoffice/) : pour tous les systèmes d'exploitation, libre et gratuit
	- Microsoft Excel : suite Office payante Microsoft
	- Google Sheets : via navigateur web, gratuit

- [Heurist](https://heurist.huma-num.fr/heurist/startup/index.php) : service en ligne gratuit proposé par Humanum

<!--
- [Omeka](https://www.omeka.net/) : libre et gratuit, licence GNU
-->


<a id='t2'/>

# Qu'est-ce qu'une base de donnée ?
[comment14]: <7> (TITRE1)


<a id='t2-1'/>

## Définition 

### <8>

**Base de données** :\
Fichier ou ensemble de fichiers contenant des informations structurées.

**3 modèles logiques** de structuration des données :

1. Modèles en table
2. Modèle en arbre
3. Modèle en graphe


### <9>

- *Mode de structuration* :
	- **Entité** : prend la forme d'une *table*\
		(*feuille* dans les logiciels de tableur)
	- **Enregistrement** : prend la forme d'une ligne : 
	- **Attribut** ou *champ* : prend la forme d'une colonne

**Image** : [<a date='sans'/>](img/bdd_table.jpg)


### <10>

- *Format simple fréquemment associé* :\
	**CSV** --- *comma separated values*
- *Format professionnel (structuration, requête)* :\
	SQL --- *Structured query language*


![](/home/sbiay/bibliotheque-numerique/images/documents-divers/bdd/table.jpg)


### <11>

- *Mode de structuration* : parent-enfant(s)
- *Format de fichier fréquemment associé* :
	- **XML**
	- **Json**
- *Langage de requête (recherche, modification)* :
	- XML	=> XSLT, Xquery
	- Json	=> Javascript

- Exemple de [fichier XML](https://uncloud.univ-nantes.fr/index.php/s/8aP2QmkLsrYM86b)


### <12>

- *Mode de structuration* : triplet sujet-prédicat-objet
- *Format de fichier fréquemment associé* : **XML-RDF**
- *Langage de requête* : Sparql


```=latex
\beginflushright
```
![](/home/sbiay/bibliotheque-numerique/images/documents-divers/bdd/exemple_graphe_1.jpg)
```=latex
\endflushright
```

\beginfigure[!h]
\captionDonnées en graphe de la BnF
\endfigure


<a id='t2-2'/>

## Avantages et inconvénients du modèle en table 

### <13>

- Simplicité de conception et d'utilisation :skip 

	- Facile à comprendre, sutructuration de données toujours lisibleskip
	- Facile à créer, compléter, modifierskip
	- Les logiciels de tableur suffisent
	- Formats de fichiers très partagésskip

- Risque majeur : déstructurer ses données

- Contre les risques de déstructuration des données :skip
	- Privilégier le transfert vers un système de type SQL comme Heuristskip
	- Acquérir **une bonne méthode de sauvegarde**


<a id='t3'/>

# Sauvegarder son travail
[comment17]: <13> (TITRE1)


<a id='t3-1'/>

## Au fait, comment sauvegardez-vous vos données ? 

### <14>

**Image** : [G. Courbet, Le Désespéré, 1843, collection particulière<a date='sans'/>](img/Courbet_desespere.jpg)

[comment19]: <14> (Projetons-nous dans un monde idéal, où on aurait le temps de faire tout bien comme il faut. Vous venez de soutenir votre mémoire de master : quelle méthode choisissez vous pour que vos arrières-arrières… petits enfants puissent le lire ?)

[comment20]: <14> (**Quelle est la méthode de préservation des données la plus durable ?**)


<a id='t3-2'/>

## Des méthodes très très durables 

### <15>


**Méthode n^o^ 1**

**Image** : [Code d'Hammurabi, musée du Louvre, v. 1750 av. JC<a date='sans'/>](img/code-hammurabi_detail-01.jpg)

[comment22]: <15> (Il a 3750 ans, et il tient toujours le coup.)

[comment23]: <15> (Le tout c'est de savoir **décoder…** Combien de temps saura-t-on décoder un fichier .docx ou .pages ?)


### <16>


**Méthode n^o^ 2**

**Image** : [Le manuscrit sur parchemin, ici 1^re^ moitié IX^e^ s.<a date='1re moitié IXe s.'/>](img/lat-5763_fol-001r-detail-a.jpg)

[comment24]: <16> (Ça tient bien aussi, depuis 11 siècles.)


<a id='t3-3'/>

## Des méthodes plus modernes 

### <17>


- Microfilm pour les photos : 100 ans et plus
- Papier : 50-100 ans
- Disque dur : 5-10 ans


### <18>

**Image** : [Le *cloud*, servi par un centre de données<a date='sans'/>](img/calcul-informatique_data-center.jpg)

[comment26]: <18> (Il y a toujours un risque que dans cette salle quelqu'un perde son rapport de stage ou un gros travail…)

[comment27]: <18> (Qui pense avoir une bonne méthode de sauvegarde ? *Prendre un volontaire pour qu'il raconte sa méthode*.)


### <19>

- ***Cloud*** :
	- Options d'accès : Accès à partir de plusieurs appareils
	- Sécurité des données : Fort mais peut être piraté (attention au détournement des contenus personnels voire intimes)
	- Technologie de synchronisation : Mises à jour automatiques
	- Coût par unité : Gratuit ou abonnement mensuel
	- Propriété : Peut partager vos fichiers avec n'importe qui
	- Fiabilité : Le serveur peut tomber en panne dans certains cas

- **Disque dur externe** :
	- Options d'accès : Utiliser une connexion USB
	- Sécurité des données : Fort mais on peut le perdre ou se le faire voler
	- Technologie de synchronisation : Mises à jour automatiques en cas de connexion
	- Coût par unité : Achat ponctuel
	- Propriété : Sûre
	- Fiabilité : Peut se casser, ne plus démarrer, des secteurs peuvent être défectueux


<a id='t3-4'/>

## Conseils pratiques 

### <20>


**Au quotidien**

1. Je sauvegarde mon travail tous les jours

2. Un support physique ET un *cloud* : l'idéal !

	Versions de mon fichier dans [Uncloud](https://uncloud.univ-nantes.fr/index.php/apps/files/files/1870556428?dir=/Enseignement/NUMPonts#)

[comment29]: <20> (Mais attention, le but n'est pas de tuer le plus d'ours polaires possibles : on ne mettra sur le cloud que les fichiers légers, ou les plus précieux.)


**Pour archiver**

- J'utilise deux supports physiques localisés en deux endroits
- Je ne fais pas confiance à un disque dur de plus de 10 ans (écrire la date de mise en service sur une étiquette !)

[comment30]: <20> (Votre disque dur ne va pas vous en envoyer un message -- au fait, à partir de demain je ne marche plus !)


<a id='t3-5'/>

## Des solutions cloud 

### <21>

- [One-Drive](https://onedrive.live.com) : avec Windows et un compte de messagerie Outlook
- [Dropbox](https://www.dropbox.com/home) : gratuit pour quelques Go et quelques appareils connectés
- [UN-Cloud](https://wiki.univ-nantes.fr/uncloud:web) : service offert par l'université de Nantes
