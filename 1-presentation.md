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


<a id='t1-1'/>

## Le sujet : les ponts dans la région Pays de la Loire 

### <2>


**Image** : [Châteaubriant, H. Lalaisse et F. Benoist, lithographie, 1844-1851<a date='sans'/>](img/img_intro-chateaubriantb.jpg)

**Image** : [La Loire au Pont Haudaudine, phototype, 1901-1903](img/img_intro-nantesb.jpg)


<!--
	https://www.tablettes-rennaises.fr/app/photopro.sk/rennes/detail?docid=430788
	
	https://www.tablettes-rennaises.fr/app/photopro.sk/rennes/detail?docid=231
-->


<a id='t1-2'/>

## Objectifs 

### <3>

- Conceptualiser une base de données
- Récolter des données en ligne sur les sites pertinents
- Construire une base de données relationnelles dans un tableur
- Convertir la base dans un gestionnaire de bases de données professionnel : **Heurist**
- Produire des statistiques et les visualiser
- Publier la base de données dans un *système de gestion de contenu*[^1] libre : Omeka

[^1]: CMS pour *content management system*.


<a id='t1-3'/>

## Evaluation 

### <4>

- Contrôle continu intégral
- Atteindre les objectifs !
- Remettre des fichiers et des données de qualités
- Au fil des séances, un peu de travail à la maison


<a id='t1-4'/>

## Rythme et degré de difficulté 

### <5>

**Mes objectifs** :

- Que les personnes du groupe les moins à l'aise en informatique puissent avoir 20/20

[comment6]: <5> (Si j'ouvre un tableur, qui se sent déjà un peu mal ?)

- Que vous vous sentiez capables de réutiliser ces apprentissages pour vos propres recherches (SAV)

**Votre implication** :

- Assiduité
- Entraînement


<a id='t1-5'/>

## Accès aux documents 

### <6>

Tous les diaporamas sont accessibles en deux formats :

1. PDF
2. Markdown sur mon compte Github [ici](https://github.com/sbiay/td-num-vnp)

<!--
	- Créer une automatisation de mise en forme pour les liens hypertextes
	- Eliminer les balises latex dans les exports github
-->


<a id='t1-6'/>

## Logiciels requis 

### <7>

- Un éditeur de texte
	- [Notepad++](https://notepad-plus-plus.org/downloads/) : licence GNU, uniquement pour Windows
	- [Visual Studio Code](https://code.visualstudio.com/download) : pour tous les systèmes d'exploitation, développé par Microsoft, gratuit

- Un logiciel de tableur
	- [LibreOffice](https://fr.libreoffice.org/download/telecharger-libreoffice/) Calc : pour tous les systèmes d'exploitation, libre et gratuit
	- Microsoft Excel : suite Office payante Microsoft
	- Google Sheets : via navigateur web, gratuit

- [Heurist](https://heurist.huma-num.fr/heurist/startup/index.php) : service en ligne gratuit proposé par Humanum

- [Omeka](https://www.omeka.net/) : libre et gratuit, licence GNU


<a id='t2'/>

# Qu'est-ce qu'une base de donnée ?
[comment9]: <7> (TITRE1)


<a id='t2-1'/>

## Définition 

### <8>

Fichier ou ensemble de fichiers contenant des informations structurées.

**3 modèles logiques** de structuration des données :

1. Modèles en table
2. Modèle en arbre
3. Modèle en graphe


### <9>

- *Mode de structuration* : ligne et colonne
- *Format de fichier fréquemment associé* : **CSV**
- *Langage de requête (recherche, modification)* : SQL (*Structured query language*)

**Image** : [Exemple de table<a date='sans'/>](img/bdd_table.jpg)


### <10>

- *Mode de structuration* : parent-enfant(s)
- *Format de fichier fréquemment associé* :
	- **XML**
	- **Json**
- *Langage de requête (recherche, modification)* :
	- XML	=> XSLT, Xquery
	- Json	=> Javascript

Exemple de [fichier XML](https://uncloud.univ-nantes.fr/index.php/s/8aP2QmkLsrYM86b)


### <11>

- *Mode de structuration* : noeuds et arêtes (ou relations)
- *Format de fichier fréquemment associé* : **XML-RDF**
- *Langage de requête* : Sparql


```=latex
\beginflushright
```
![](/home/sbiay/bibliotheque-numerique/images/documents-divers/bdd/exemple_graphe_1.jpg)
```=latex
\endflushright
```
\vskip 12em
\beginfigure[!h]
\captionDonnées en graphe de la BnF
\endfigure


<a id='t3'/>

# Sauvegarder son travail
[comment11]: <11> (TITRE1)


<a id='t3-1'/>

## Au fait, comment sauvegardez-vous vos données ? 

### <12>

**Image** : [G. Courbet, Le Désespéré, 1843, collection particulière<a date='sans'/>](img/Courbet_desespere.jpg)


[comment13]: <12> (**Quelle est la méthode de préservation des données la plus durable ?**)

[comment14]: <12> (Il y a dans cette salle quelqu'un qui perdra tout son mémoire à un moment donné.)

[comment15]: <12> (Ce sera peut-être vous… *Prendre un volontaire pour qu'il raconte sa méthode*.)

[comment16]: <12> (Qui pense avoir une bonne méthode ?)

[comment17]: <12> (Projetons-nous dans un monde idéal, où on aurait le temps de faire tout bien comme il faut. Vous venez de soutenir votre mémoire de master: quelle méthode choisissez vous pour que vos arrières-arrières… petits enfants puissent le lire ?)


<a id='t3-2'/>

## Des méthodes très très durables 

### <13>


**Méthode n^o^ 1**

**Image** : [Code d'Hammurabi, musée du Louvre, v. 1750 av. JC<a date='sans'/>](img/code-hammurabi_detail-01.jpg)

[comment19]: <13> (Il a 3750 ans, et il tient toujours le coup.)

[comment20]: <13> (Le tout c'est de savoir **décoder…** Combien de temps saura-t-on décoder un fichier .docx ou .pages ?)


### <14>


**Méthode n^o^ 2**

**Image** : [Le manuscrit sur parchemin, ici 1^re^ moitié IX^e^ s.<a date='1re moitié IXe s.'/>](img/lat-5763_fol-001r-detail-a.jpg)

[comment21]: <14> (Ça tient bien aussi, depuis 11 siècles.)


<a id='t3-3'/>

## Des méthodes plus modernes 

### <15>


- Microfilm pour les photos : 100 ans et plus
- Papier : 50-100 ans
- Disque dur : 5-10 ans


### <16>

**Image** : [Le *cloud*, servi par un centre de données<a date='sans'/>](img/calcul-informatique_data-center.jpg)


### <17>

- ***Cloud*** :
	- Options d'accès : Accès à partir de plusieurs appareils
	- Sécurité des données : Fort mais peut être piraté
	- Technologie de synchronisation : Mises à jour automatiques
	- Coût par unité : Gratuit ou abonnement mensuel
	- Propriété : Peut partager vos fichiers avec n'importe qui
	- Fiabilité : Le serveur peut tomber en panne dans certains cas

- **Disque dur externe** :
	- Options d'accès : Utiliser une connexion USB
	- Sécurité des données : Fort mais on peut se le faire voler
	- Technologie de synchronisation : Mises à jour automatiques en cas de connexion
	- Coût par unité : Achat ponctuel
	- Propriété : Sûre
	- Fiabilité : Peut se casser, des secteurs peuvent être défectueux


<a id='t3-4'/>

## Conseils pratiques 

### <18>


**Au quotidien**

1. Je sauvegarde mon travail tous les jours

2. Un support physique ET un *cloud* : l'idéal !

[comment24]: <18> (Mais attention, le but n'est pas de tuer le plus d'ours polaires possibles : on ne mettra sur le cloud que les fichiers légers, ou les plus précieux.)


**Pour archiver**

- J'utilise deux supports physiques localisés en deux endroits

[comment25]: <18> (Votre disque dur ne va pas vous en envoyer un message -- au fait, à partir de demain je ne marche plus !)


<a id='t3-5'/>

## Des solutions cloud 

### <19>

- [One-Drive](https://onedrive.live.com) : avec Windows et un compte de messagerie Outlook
- [Dropbox](https://www.dropbox.com/home) : gratuit pour quelques Go et quelques appareils connectés
- [UN-Cloud](https://wiki.univ-nantes.fr/uncloud:web) : service offert par l'université de Nantes
