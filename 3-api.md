---
mainfont: Alegreya
title:  Les API  Requêtes et exports de données en masse
date: 1^er^ semestre 2024-2025
author: Sébastien Biay
---

 Les API  Requêtes et exports de données en masse
=====

Plan :

1. [Mérimée, mais pas tout…](#t1)
	1. [Télécharger en différents formats ](#t1-1)
	2. [Obtenir les données de l'API ](#t1-2)
2. [L'Inventaire du patrimoine](#t2)
	1. [Faire parler l'API : clauses WHERE complexes ](#t2-1)
	2. [Préparer une liste ordonnée des champs ](#t2-2)
	3. [Exporter le fichier de résultats ](#t2-3)
	4. [Transformer Json en CSV ](#t2-4)

[comment]: <> (FINET)


### <2>

Les institutions publiques pratiquent **l'ouverture des données** (*opendata*) : accès à la donnée brute indépendammant des sites webs qui les valorisent

- Les données de [POP](https://pop.culture.gouv.fr/opendata) --- *mais, quelles données et pour quel usage ? À lire attentivement…*
	
	- [Mérimée MH](https://data.culture.gouv.fr/explore/dataset/liste-des-immeubles-proteges-au-titre-des-monuments-historiques/table/?disjunctive.departement_en_lettres)

- Les données de l'[Inventaire du patrimoine](https://data.paysdelaloire.fr/explore/dataset/234400034_052-001_inventaire-du-patrimoine-rpdl/information/) \
(qui correspondent au site gertrude.paysdelaloire.fr)


<a id='t1'/>

# Mérimée, mais pas tout…
[comment1]: <2> (TITRE1)


<a id='t1-1'/>

## Télécharger en différents formats 

### <3>

**Immeubles protégés au titre des Monuments Historiques**

Il s'agit d'une partie seulement des notices de Mérimée, *sans les notices issues de l'Inventaire du patrimoine*.

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

## Obtenir les données de l'API 

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

[comment4]: <8> (On ne récolte que les sites protégés MH, dont les notices ont un identifiant en PA ; sur le site web de Mérimée, on avait aussi des notices de l'Inventaire du patrimoine, à l'identifiant en IA.)

[comment5]: <8> (On a donc accès à des données exportables, mais des données plus pauvres que celles du site Mérimée.)

[comment6]: <8> (On peut toujours espérer que toutes les notices IA de Mérimée soit aussi dans Gertrude… Il faudra évaluer la question.)


<a id='t2'/>

# L'Inventaire du patrimoine
[comment7]: <8> (TITRE1)


<a id='t2-1'/>

## Faire parler l'API : clauses WHERE complexes 

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

*Ouvrez-donc un éditeur de texte comme Notepad ++ pour taper vos clauses et pouvoir en écrire de nouvelles en faisant des copier-coller…*


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


<a id='t2-2'/>

## Préparer une liste ordonnée des champs 

### <16>

Les attributs ou champs d'une notice sont assez nombreux, et ne sont pas présentés dans un ordre très satisfaisant !\
On peut les passer en revue avec [cet exemple](https://data.paysdelaloire.fr/api/explore/v2.1/catalog/datasets/234400034_052-001_inventaire-du-patrimoine-rpdl/records?where=appellation_du_batiment_eglise_ferme_ou_de_l_objet%20LIKE%20%22pont%22%20OR%20appellation_du_batiment_eglise_ferme_ou_de_l_objet%3D%22passerelle%22%20OR%20appellation_du_batiment_eglise_ferme_ou_de_l_objet%3D%22viaduc%22&limit=1) où j'ai limité les résultats à 1 seul

L'objectif est de convertir une sélection de ces informations dans un ordre logique et d'éliminer ce qui ne nous intéresse pas


### <17>

À partir du résultat de la diapo précédente, je copie-colle dans un éditeur de texte l'ensemble du contenu de la notice

- Récupérer ce contenu en téléchargeant [ce fichier .txt](https://raw.githubusercontent.com/sbiay/td-num-vnp/main/txt/notice-inventaire-patrimoine.txt) (une fois le contenu afficher, un simple clic sur enregistrer sous)

- Ouvrir le fichier dans un éditeur de texte (Notepad ++)


### <18>

On commence par éliminer à la main les **lignes** qui ne comportent pas d'intitulé de champ :

- Les 4 premières lignes

**NB** : quand le curseur est sur une ligne ou lorsque l'on en sélectionne plusieurs, **Maj + Suppr** supprime toute la ou les lignes


### <19>

Puis on élimine les **valeurs** pour ne conserver que les intitulés des champs :

- Exemple : sur la première ligne, `identifiant	"IA85003243"`, on ne veut garder que `identifiant`

Pour cela on va effectuer des *cherche-remplace* à l'aide des **Expressions régulières** :

- Activer la boîte de dialogue *cherche-remplace* : **Ctrl + H**
- Cocher l'option **Expression régulière**
- Dans le champ **Recherche**, taper `\t` : cela exprime **Tabulation**, qui sert ici de séparateur entre l'intitulé du champ et la valeur placée entre guillemets


### <20>

- Dans le champ **Recherche** (vidé), taper maintenant `\n` : cela exprime **Retour à la ligne**

Pour conserver l'intitulé du champ, on va supprimer le séparateur (`\t`) et tous les caractères qui suivent, jusqu'au retour à la ligne (`\n`) qu'il faudra conserver… Voici comment :

- **Recherche** : `\t[^\n]+`
- **Remplacer par** : *laisser vide*


### <21>

**Traduction de cette chose** : `\t[^\n]+`

On recherche :

- `\t` une tabulation
- Suivie d'un ensemble de caractères défini entre `[]`
- `^` signifie "tout sauf" ; par exemple `[^a]` signifie "tout caractère sauf `a`" ; `[^\t]` signifie "tout caractère sauf une tabulation" ; or, après la tabulation, on veut éliminer tout caractère sauf un retour à la ligne, pour éliminer tout jusqu'à la fin de la ligne `[^\n]`
- `+` est un **quantificateur** signifie "entre 1 et l'infini" : or la suite de la ligne est constituée de "tout sauf un retour à la ligne" (`[^\n]`) un certain nombre (une infinité) de fois (`+`)


### <22>

**Pour bien maîtriser les expressions régulières** :

- Un [{vademecum}](https://github.com/sbiay/td-num-vnp/blob/main/tuto-regex.md) contenant les fondamentaux

- Un [didacticiel](https://regexlearn.com/fr/learn/regex101) complet


### <23>

Tous les champs sont-ils utiles ? *(Ctrl + Suppr pour supprimer une ligne)*

L'ordre est-il le plus logique ? *(Ctrl + Maj + flêche pour déplacer une ligne vers le haut ou vers le bas)*

Pour tous travailler au même diapason, voici la réorganisation que vous pouver télécharger avec 
[ce fichier .txt](https://raw.githubusercontent.com/sbiay/td-num-vnp/main/txt/champs-inventaire-patrimoine.txt)

On peut également personnaliser leur intitulé de cette façon :


- `nom_de_l_edifice_ou_de_l_objet AS nom`
- `appellation_du_batiment_eglise_ferme_ou_de_l_objet`\
`AS appellation`
- `edifice_contenant_l_objet_mobilier AS appartient_a`
- `code_insee_de_la_commune AS insee`


### <24>

Enfin, il faut convertir cette succession de lignes en une clause **select** écrite sur une seule ligne

On remplace donc les retours à la ligne par **virgule suivie d'une espace** :

- **Recherche** : `\n`
- **Remplacer par** : `, `

Et on copie-colle le résultat dans le champ **select**

Pour la clause **where**, on peut copier-coller à partir de [ce fichier](https://raw.githubusercontent.com/sbiay/td-num-vnp/main/txt/requete-complete-inventaire.txt)


<a id='t2-3'/>

## Exporter le fichier de résultats 

### <25>

Il reste un problème !

Nous avons 124 résultats,\
mais le droit d'en exporter jusqu'à 100…

Comment faire ?


### <26>

Solutions possibles :

- Isoler un département des autres en complétant la clause **where**
- Utiliser la clause **order_by** pour partager les résultats en deux moitiés
	
	1. D'abord :
		- order_by : `identifiant ASC`
		- limit : `62`
		- Résultats [ici](https://data.paysdelaloire.fr/api/explore/v2.1/catalog/datasets/234400034_052-001_inventaire-du-patrimoine-rpdl/records?select=identifiant%2C%20nom_de_l_edifice_ou_de_l_objet%20AS%20nom%2C%20appellation_du_batiment_eglise_ferme_ou_de_l_objet%20AS%20appellation%2C%20datation_de_l_oeuvre%20AS%20datation%2C%20commune%2C%20departement%2C%20code_insee_de_la_commune%20AS%20insee%2C%20code_departement%2C%20localisation%2C%20edifice_contenant_l_objet_mobilier%20AS%20appartient_a%2C%20materiau_du_gros_oeuvre%2C%20auteur_de_l_oeuvre%20AS%20auteur%2C%20historique_du_batiment_ou_de_l_oeuvre%2C%20description_du_batiment%2C%20type_de_protection%2C%20chercheur%2C%20copyright&where=appellation_du_batiment_eglise_ferme_ou_de_l_objet%20LIKE%20%22pont%22%20OR%20appellation_du_batiment_eglise_ferme_ou_de_l_objet%3D%22passerelle%22%20OR%20appellation_du_batiment_eglise_ferme_ou_de_l_objet%3D%22viaduc%22&order_by=identifiant%20ASC&limit=62)
	
	2. Puis :
		- order_by : `identifiant DESC`
		- limit : `62`
		- Résultats [ici](https://data.paysdelaloire.fr/api/explore/v2.1/catalog/datasets/234400034_052-001_inventaire-du-patrimoine-rpdl/records?select=identifiant%2C%20nom_de_l_edifice_ou_de_l_objet%20AS%20nom%2C%20appellation_du_batiment_eglise_ferme_ou_de_l_objet%20AS%20appellation%2C%20datation_de_l_oeuvre%20AS%20datation%2C%20commune%2C%20departement%2C%20code_insee_de_la_commune%20AS%20insee%2C%20code_departement%2C%20localisation%2C%20edifice_contenant_l_objet_mobilier%20AS%20appartient_a%2C%20materiau_du_gros_oeuvre%2C%20auteur_de_l_oeuvre%20AS%20auteur%2C%20historique_du_batiment_ou_de_l_oeuvre%2C%20description_du_batiment%2C%20type_de_protection%2C%20chercheur%2C%20copyright&where=appellation_du_batiment_eglise_ferme_ou_de_l_objet%20LIKE%20%22pont%22%20OR%20appellation_du_batiment_eglise_ferme_ou_de_l_objet%3D%22passerelle%22%20OR%20appellation_du_batiment_eglise_ferme_ou_de_l_objet%3D%22viaduc%22&order_by=identifiant%20DESC&limit=62)


### <27>

Sauvegarder les deux fichiers Json dans un dossier dédié :

`TD-ponts/`

=> `json/`

=> => `inventaire-pays-loire-debut.json`\
=> => `inventaire-pays-loire-fin.json`


<a id='t2-4'/>

## Transformer Json en CSV 

### <28>

Pour obtenir un tableau à partir de ces résultats, on utilisera une application en ligne de transformation : [convertcsv.com](https://www.convertcsv.com/json-to-csv.htm)

1. Charger le fichier Json
2. *Choose output options* : cliquer sur **optional**
	- Output Field Separator : **Tab**

3. Cliquer sur **Download results**

Effectuer l'opération pour les deux fichiers Json


### <29>

Sauvegarder les deux fichiers Json dans un dossier dédié :

`TD-ponts/`

=> `csv/`

=> => `inventaire-pays-loire-debut.csv`\
=> => `inventaire-pays-loire-fin.csv`

