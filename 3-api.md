---
mainfont: Alegreya
title: Les API Requêtes et exports de données en masse
date: 1^er^ semestre 2024-2025
author: Sébastien Biay
---

Les API Requêtes et exports de données en masse
=====

Plan :

1. [Les donnée ouvertes](#t1)
	1. [Mérimée, mais pas tout… ](#t1-1)
	2. [L'Inventaire du patrimoine ](#t1-2)
	3. [Exporter les données d'une API ](#t1-3)

[comment]: <> (FINET)


<a id='t1'/>

# Les donnée ouvertes
[comment1]: <1> (TITRE1)


### <2>

Les institutions publiques pratiquent **l'ouverture des données** (*opendata*) : accès à la donnée brute indépendammant des sites webs qui les valorisent

- Les données de [POP](https://pop.culture.gouv.fr/opendata) --- mais, quelles données et pour quel usage ? *À lire attentivement…*
	
	- [Mérimée](https://data.culture.gouv.fr/explore/dataset/liste-des-immeubles-proteges-au-titre-des-monuments-historiques/table/?disjunctive.departement_en_lettres)

- Les données de l'[Inventaire du patrimoine](https://data.paysdelaloire.fr/explore/dataset/234400034_052-001_inventaire-du-patrimoine-rpdl/information/) \
(qui correspondent au site gertrude.paysdelaloire.fr)


<a id='t1-1'/>

## Mérimée, mais pas tout… 

### <3>

**Immeubles protégés au titre des Monuments Historiques**

Il s'agit d'une partie seulement des notices de Mérimée, *sans les notices issues de l'Inventaire du patrimoine*.

**Formats d'export**\
\small généralement identique sur tous les sites de données ouvertes :

- CSV (*Comma-separated values*) : valeurs séparées par des virgules (ou un autre séparateur ; dans ce jeu, c'est le point-virgule) ; forme des **tableaux**
	
	- Cliquer sur le **Filtre** : Région => Pays de la Loire,\
	puis [exporter les enregistrements](https://data.culture.gouv.fr/api/explore/v2.1/catalog/datasets/liste-des-immeubles-proteges-au-titre-des-monuments-historiques/exports/csv?lang=fr&refine=region%3A%22Pays%20de%20la%20Loire%22&timezone=Europe%2FBerlin&use_labels=true&delimiter=%3B)


### <4>

**Formats d'export** (suite) : 

- Json (*JavaScript Object Notation*) : format de données textuel dérivé de la notation des objets du langage JavaScript

	- Là aussi, [exporter les enregistrements](https://data.culture.gouv.fr/api/explore/v2.1/catalog/datasets/liste-des-immeubles-proteges-au-titre-des-monuments-historiques/exports/json?lang=fr&refine=region%3A%22Pays%20de%20la%20Loire%22&timezone=Europe%2FBerlin)

- Et bien d'autres…


### <5>

Exporter les jeux de données oblige à aller chercher notre objet d'étude dans la masse des données.

Pour interroger directement notre objet parmi les données ouvertes : utiliser l'**API** (*Application programming interface*).

Cette API permet de formuler des **requêtes SQL** (*Structured query language*), le langage d'exploitation des **bases de données relationnelles** (où les données ont une forme tabulaire).


### <6>

**Clauses** principales d'une requête :

- select : *sélectionne les données que l'on souhaite recevoir*
- where : *où se trouve une ou des informations précises*
- group_by : *clé réunissant plusieurs tables*
- order_by : *critère selon lequel on trie les résultats*
- limit : *limite du nombre de résultats attendus*


### <7>

Formulons une première requête, pour obtenir la **liste des sites protégés de la Loire-Atlantique**

On se contentera de sélectionner (clause *select*) quelques informations simples : la référence de la notice, son titre, le nom de la commune

Saisir les informations suivantes :

- select : `reference, titre_editorial_de_la_notice, commune_forme_editoriale`
- where : `departement_format_numerique=44`

Les résultats s'affichent instantanément à droite et on accède à [ce fichier Json](https://data.culture.gouv.fr/api/explore/v2.1/catalog/datasets/liste-des-immeubles-proteges-au-titre-des-monuments-historiques/records?select=reference%2C%20titre_editorial_de_la_notice%2C%20commune_forme_editoriale&where=departement_format_numerique%3D44&limit=20&refine=region%3A%22Pays%20de%20la%20Loire%22) via le lien en bas de page


### <8>

**Comment trouver les ponts ?**

- Effacer le champ **where**
- En examinant les données des notices affichés à droite, tenter de trouver comment formuler une requête sur les ponts (en utilisant la clause *where*)

Il faut trouver [22 résultats](https://data.culture.gouv.fr/api/explore/v2.1/catalog/datasets/liste-des-immeubles-proteges-au-titre-des-monuments-historiques/records?select=reference%2C%20titre_editorial_de_la_notice%2C%20commune_forme_editoriale&where=denomination_de_l_edifice%20%3D%20%22pont%22&limit=100&refine=region%3A%22Pays%20de%20la%20Loire%22)

N'est-il pas étrange de ne trouver que 22 résultats ?\
Comment l'expliquer ?

[comment3]: <8> (On ne récolte que les sites protégés MH, dont les notices ont un identifiant en PA ; sur le site web de Mérimée, on avait aussi des notices de l'Inventaire du patrimoine, à l'identifiant en IA.)

[comment4]: <8> (On a donc accès à des données exportables, mais des données plus pauvres que celles du site Mérimée.)

[comment5]: <8> (On peut toujours espérer que toutes les notices IA de Mérimée soit aussi dans Gertrude… Il faudra évaluer la question.)


<a id='t1-2'/>

## L'Inventaire du patrimoine 

### <9>

[Données ouvertes de l'Inventaire en Pays de la Loire](https://data.paysdelaloire.fr/explore/dataset/234400034_052-001_inventaire-du-patrimoine-rpdl/information/)

Même opération, et même type de requête !\
Il s'agit de retrouver nos 121 résultats, et plus si affinité…

Commencer par examiner les notices d'exemple pour repérer le champ pertinent à interroger.

Une requête sur "pont" doit permettre de trouver 104 résultats.


### <10>

La bonne clause était :

- where : `appellation_du_batiment_eglise_ferme_ou_de_l_objet = "pont"`

Maintenant, pourquoi avons-nous moins de résultats que les [121](https://gertrude.paysdelaloire.fr/recherche/experte/results?q=(typeDossiers:(OeuvreArchitecture),blocs:((id:eabe2308-8749-4c1f-9a89-b55ce4298914,thematiqueType:LOCALISATION,operateur:AND,criteres:(),position:0),(id:e86ca9bb-906e-4f97-ba74-f1de08f543b3,thematiqueType:TYPE_OEUVRE,operateur:AND,criteres:((id:df7152f4-f47a-4a52-85fb-d9c4ad6d3b4c,champRecherche:TYPE_OEUVRE_DENOMINATION,valeur:http!:%2F%2Fwww.culture.fr%2Fthesaurus%2FL96-2280,operateur:EQUAL,label:pont,ancestorLabels:(g%C3%A9nie+civil,ouvrage+d%27art))),position:1)))) que donnait le site public ?

*Ouvrez-donc un éditeur de texte pour taper vos clauses et pouvoir en écrire de nouvelles en faisant des copier-coller…*


### <11>

Il faut parvenir à élargir la recherche sans perdre sa pertinence, en commençant par chercher les appellations qui *contiennent* "pont" sans être strictement égales à "pont".

On va ajouter au passage :

1. Une petite clause *select* pour balayer les résultats avec moins d'informations
2. On augmente le nombre de résultats (*limit*) au max autorisé : 100
2. Une clause *order_by* pour trier les communes en ordre "ascendant" (ASC), soit alphabétique ; on pourra ainsi faire DESC pour voir la fin de l'alphabet et ainsi visualiser plus de données


### <12>

À vous de jouer :

- select : `identifiant, nom_de_l_edifice_ou_de_l_objet, appellation_du_batiment_eglise_ferme_ou_de_l_objet, commune, code_departement`
- where : `appellation_du_batiment_eglise_ferme_ou_de_l_objet LIKE "pont"`
- order_by : `commune ASC`
- limit : 100

\small
Une fois la requête complétée, cliquer sur le lien en bas de page, et utiliser le filtre en haut de la page : en tapant `appellation` on ne visualise plus que la donnée qui contient ce terme, et on peut repérer plus vite les types d'appellation qui ne sont pas "pont".


```
```


### <13>


On monte donc à 107 résultats, avec les "pont mobile" ! Comment élargir encore et faire apparaître d'autres types pertinents ?…


### <14>

On peut chercher les notices qui contiennent le mot "pont" dans le champ **nom_de_l_edifice_ou_de_l_objet** mais dont l'**appellation** n'est pas pont, ce que l'on traduit ainsi :

- where : `nom_de_l_edifice_ou_de_l_objet LIKE "pont" AND NOT 
appellation_du_batiment_eglise_ferme_ou_de_l_objet LIKE "pont"`


### <15>

Par cette requête on a pu repérer de nouveaux types d'appellation pertinents :

- viaduc
- passerelle

À présent, formulons la requête exhaustive :

where :\
\scriptsize
`appellation_du_batiment_eglise_ferme_ou_de_l_objet LIKE "pont"`\
`OR appellation_du_batiment_eglise_ferme_ou_de_l_objet = "passerelle"`\
`OR appellation_du_batiment_eglise_ferme_ou_de_l_objet = "viaduc"`


Résultats : [124](https://data.paysdelaloire.fr/api/explore/v2.1/catalog/datasets/234400034_052-001_inventaire-du-patrimoine-rpdl/records?select=identifiant%2C%20nom_de_l_edifice_ou_de_l_objet%2C%20appellation_du_batiment_eglise_ferme_ou_de_l_objet%2C%20commune%2C%20code_departement&where=appellation_du_batiment_eglise_ferme_ou_de_l_objet%20LIKE%20%22pont%22%20OR%20appellation_du_batiment_eglise_ferme_ou_de_l_objet%3D%22passerelle%22%20OR%20appellation_du_batiment_eglise_ferme_ou_de_l_objet%3D%22viaduc%22&order_by=commune%20ASC&limit=100) !


<a id='t1-3'/>

## Exporter les données d'une API 

### <16>

Les attributs ou champs d'une notice sont assez nombreux, et ne sont pas présentés dans un ordre très satisfaisant !\
On peut les passer en revue avec [cet exemple](https://data.paysdelaloire.fr/api/explore/v2.1/catalog/datasets/234400034_052-001_inventaire-du-patrimoine-rpdl/records?where=appellation_du_batiment_eglise_ferme_ou_de_l_objet%20LIKE%20%22pont%22%20OR%20appellation_du_batiment_eglise_ferme_ou_de_l_objet%3D%22passerelle%22%20OR%20appellation_du_batiment_eglise_ferme_ou_de_l_objet%3D%22viaduc%22&limit=1) où j'ai limité les résultats à 1 seul

L'objectif est de convertir une sélection de ces informations dans un ordre logique et d'éliminer ce qui ne nous intéresse pas


### <17>

En recopiant la ligne des en-têtes du [jeu de données entier au format CSV](https://data.paysdelaloire.fr/api/explore/v2.1/catalog/datasets/234400034_052-001_inventaire-du-patrimoine-rpdl/exports/csv?lang=fr&timezone=Europe%2FBerlin&use_labels=true&delimiter=%3B) j'obtiens ceci :

\scriptsize
`Identifiant; type; Appellation du bâtiment (église, ferme …) ou de l'objet; Nom de l'édifice ou de l'objet; Commune; Code Insee de la commune; Nom de l'aire d'étude à laquelle est liée la notice; Edifice contenant l'objet mobilier; Catégorie de l'œuvre; Auteur de l'œuvre; Datation de l'œuvre; Historique du bâtiment ou de l'œuvre; Matériau du gros-œuvre; Matériau de la couverture; Description du bâtiment; Statut du bâtiment ou de l'œuvre; Type de protection; X location; Ylocation; Chercheur; Copyright; localisation; code_region; departement; code_departement`


