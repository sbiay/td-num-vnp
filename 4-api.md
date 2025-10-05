---
mainfont: Alegreya
title:  Les API ---

 Les API ---
=====

Plan :

1. [Mérimée, mais pas tout…](#t1)
	1. [Télécharger en différents formats ](#t1-1)
	2. [L'API Mérimée complète ](#t1-2)
2. [L'Inventaire du patrimoine en PDL](#t2)
	1. [Obtenir les données de l'API ](#t2-1)
	2. [Transformer du Json en CSV ](#t2-2)
	3. [Télécharger les données au format tabulaire ](#t2-3)

<!--FINET-->


### <2>

Les institutions publiques pratiquent **l'ouverture des données** (*opendata*) : accès à la donnée brute indépendammant des sites webs qui les valorisent.

On peut ainsi accéder :

- Aux données de [POP](https://pop.culture.gouv.fr/opendata) --- *mais, quelles données et pour quel usage ? À lire attentivement [ici](https://data.culture.gouv.fr/explore/dataset/liste-des-immeubles-proteges-au-titre-des-monuments-historiques/information/?disjunctive.departement_en_lettres)…*
	
	- [Mérimée MH](https://data.culture.gouv.fr/explore/dataset/liste-des-immeubles-proteges-au-titre-des-monuments-historiques/table/?disjunctive.departement_en_lettres)

- Aux données de l'[Inventaire du patrimoine](https://data.paysdelaloire.fr/explore/dataset/234400034_052-001_inventaire-du-patrimoine-rpdl/information/) \
(compétence régionale depuis 2004 --- publié pour les PDL sur [gertrude.paysdelaloire.fr](https://gertrude.paysdelaloire.fr/))


<a id='t1'/>

# Mérimée, mais pas tout…
[comment1]: <2> (TITRE1)


<a id='t1-1'/>

## Télécharger en différents formats 

### <3>

**Immeubles protégés au titre des Monuments Historiques**

Il s'agit d'une partie seulement des notices de Mérimée, *sans les notices issues de l'inventaire du patrimoine pour les sites non protégés*.

**Formats d'export**\
 généralement identique sur tous les sites de données ouvertes :

- CSV (*Comma-separated values*) : valeurs séparées par des virgules (ou un autre séparateur ; dans ce jeu, c'est le point-virgule) ; forme des **tableaux**
	
	- Cliquer sur le **Filtre** : Région => Pays de la Loire,\
	puis [exporter les enregistrements](https://data.culture.gouv.fr/api/explore/v2.1/catalog/datasets/liste-des-immeubles-proteges-au-titre-des-monuments-historiques/exports/csv?lang=fr&refine=region%3A%22Pays%20de%20la%20Loire%22&timezone=Europe%2FBerlin&use_labels=true&delimiter=%3B)


### <4>

**Formats d'export** (suite) : 

- Json (*JavaScript Object Notation*) : format de données textuel dérivé de la notation des objets du langage JavaScript

	- Là aussi, [exporter les enregistrements](https://data.culture.gouv.fr/api/explore/v2.1/catalog/datasets/liste-des-immeubles-proteges-au-titre-des-monuments-historiques/exports/json?lang=fr&refine=region%3A%22Pays%20de%20la%20Loire%22&timezone=Europe%2FBerlin)

- Et bien d'autres…


<a id='t1-2'/>

## L'API Mérimée complète 

### <5>

Cette API ne fait l'objet d'aucune publicité, pourtant, elle fonctionne.\
Voici son adresse :

[https://api.pop.culture.gouv.fr/merimee/](https://api.pop.culture.gouv.fr/merimee/PA00109550)


<a id='t2'/>

# L'Inventaire du patrimoine en PDL
[comment4]: <5> (TITRE1)


<a id='t2-1'/>

## Obtenir les données de l'API 

### <6>

On se déplace vers les données ouvertes de l'[Inventaire en Pays de la Loire](https://data.paysdelaloire.fr/explore/dataset/234400034_052-001_inventaire-du-patrimoine-rpdl/information/)

Pour interroger directement notre objet parmi les données ouvertes : utiliser l'**API** (*Application programming interface*).

Cette API permet de formuler des **requêtes SQL** (*Structured query language*), le langage d'exploitation des **bases de données relationnelles** (où les données ont une forme tabulaire).


### <7>

**Clauses** principales d'une requête :

- select : *sélectionne les données que l'on souhaite recevoir*
- where : *où se trouve une ou des informations précises*
- group_by : *clé réunissant plusieurs tables*
- order_by : *critère selon lequel on trie les résultats*
- limit : *limite du nombre de résultats attendus*


### <8>

Formulons une première requête, pour obtenir la **liste des sites protégés de la Loire-Atlantique**.

On se contentera de sélectionner (clause *select*) quelques informations simples : la référence de la notice, son titre, le nom de la commune.

Saisir les informations suivantes :

- **select** : `identifiant, nom_de_l_edifice_ou_de_l_objet, commune`
- **where** : `code_departement=44`


### <9>

**Comment trouver les ponts ?**

- Effacer le contenu des champs
- En examinant les données des notices affichés à droite, tenter de trouver comment formuler une requête sur les ponts (en utilisant la clause *where*)

Il faut trouver [104 résultats](https://data.paysdelaloire.fr/api/explore/v2.1/catalog/datasets/234400034_052-001_inventaire-du-patrimoine-rpdl/records?where=appellation_du_batiment_eglise_ferme_ou_de_l_objet%3D%22pont%22&limit=20)


### <10>

La bonne clause était :

- where : `appellation_du_batiment_eglise_ferme_ou_de_l_objet = "pont"`

Afficher le fichier Json et l'enregistrer sous.


<a id='t2-2'/>

## Transformer du Json en CSV 

### <11>

Pour obtenir un tableau à partir de ces résultats, on utilisera une application en ligne de transformation : [convertcsv.com](https://www.convertcsv.com/json-to-csv.htm)

1. Charger le fichier Json
2. *Choose output options* : cliquer sur **optional**
	- Output Field Separator : **Tab**

3. Cliquer sur **Download results**


<a id='t2-3'/>

## Télécharger les données au format tabulaire 

### <12>

D'autre termes que `pont` sont pertinents pour notre recherche.\
Pour bien connaître les données, la meilleure solution est de consulter un export en forme de tableau.

On exporte les données de l'Inventaire au format CSV [depuis cette page](https://data.paysdelaloire.fr/explore/dataset/234400034_052-001_inventaire-du-patrimoine-rpdl/export/).