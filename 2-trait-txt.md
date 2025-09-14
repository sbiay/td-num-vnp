---
mainfont: Alegreya
title: Traitement de texte
date: 1^er^ semestre 2025-2026
author: sebastien.biay@univ-nantes.fr
---

Traitement de texte
=====

Plan :

1. [Appliquer la feuille de style par défaut](#t1)
	1. [La structure d'abord, l'apparence ensuite ](#t1-1)
	2. [Styles de caractères ](#t1-2)
2. [Personnaliser les styles](#t2)
3. [Mettre en page un mémoire](#t3)
	1. [Les composants du volume de texte ](#t3-1)
	2. [Les pages de titre ](#t3-2)
	3. [Numéros de pages et titres courants ](#t3-3)
	4. [Imprimer ](#t3-4)
4. [Compléter le paratexte](#t4)
	1. [Préparer une table des matières ](#t4-1)
	2. [Illustrations ](#t4-2)
5. [Importer/exporter un style](#t5)
6. [Règles typographiques](#t6)
	1. [Les espaces insécables ](#t6-1)

<!--FINET-->



### <2>

 Mise en forme directe => Texte structuré

 Méthode --- appliquer des feuilles de styles :

- Caractères
- Paragraphes
- Pages

Avantages :<!--Montrer le fichier vertus-resultat-article-complet.odt en exemple-->

- Meilleure distribution des blocs
- Mise en page plus élaborée
- Navigation dans le document
- Évolutivité de la mise en forme
- Table des matières automatique
- Application du même modèle à plusieurs documents


<a id='t1'/>

# Appliquer la feuille de style par défaut
[comment1]: <2> (TITRE1)


<a id='t1-1'/>

## La structure d'abord, l'apparence ensuite 

### <3>

 Réinitialiser la mise en forme d'un document\
 en supprimant tout le formatage direct.\
Comme toute opération qui supprime des données, mieux vaut faire une archive (copie) de l'état antérieur auparavant.

Puis procéder ainsi :

- Ouvrir le fichier **exemple-mise-forme-directe.docx**
- Sélectionner tout : Ctrl + A
- Clic droit : **Effacer le formatage direct**

<!--
Si vous avez déjà l'habitude de gérer les styles de paragraphes et de caractères, allez à la diapo 21 et repartez du fichier **vertus-etape-02.odt**.
-->

### <4>

Nous allons appliquer la feuille de style par défaut de LibreOffice Writer pour les titres et les citations d'un document :

1. Ouvrir dans LibreOffice Writer le fichier **vertus-brut.odt**

2. Ouvrir le fichier **vertus-resultat.pdf** : il présente la mise en forme que l'on souhaite obtenir


### <5>

On va d'abord **appliquer des styles de paragraphes sans se préoccuper de leur apparence** :

1. Dans LibreOffice Writer, ouvrir le **panneau latéral** > Styles > Styles de paragraphe

2. En bas du panneau, avec le menu, choisir **Tous les styles**


### <6>

D'après le modèle, et les infos contenues dans les info-bulles, appliquer les styles suivants là où c'est pertinent **sans modifier manuellement l'apparence des styles** :

- Titre 1 --- *attention, il y en a au début et aussi à la fin du document : « Illustrations »*
- Titre 2
- Titre 3
- Titre 4

Appliquer aussi :

- Bloc de citation


### <7>

**Créer un style personnalisé**\
On veut rendre les citations en langue étrangère en italique :

1. Sélectionner la citation latine : cliquer 4 fois sur le bloc

2. Toujours dans le panneau latéral :\
	Ouvrir le menu **Actions sur les styles** >\
	Nouveau style à partir de la sélection

3. Nommer le nouveau style, par ex. : « Bloc langue étrangère »


<a id='t1-2'/>

## Styles de caractères 

### <8>

Dans la mise en forme d'écrits scientifiques, les styles de caractères sont beaucoup moins utiles que les styles de paragraphes.

On peut notamment les utiliser pour intégrer dans le texte des **commentaires pour soi-même** :

- Sélectionner la phrase *« Oups, j'ai écrit une connerie ! »* et lui appliquer le style de caractères **Accentuation forte**

On peut également commenter des passages avec\
	des bulles-commentaires :

- Sélectionner > **Insertion** > Commentaire

<!--On est arrivé à l'étape 1-->


<a id='t2'/>

# Personnaliser les styles
[comment4]: <8> (TITRE1)


### <9>

<!--

[comment5]: <9> (Faire appel aux styles de titres permet :)

[comment6]: <9> (- De modifier de manière homogène la mise en forme)

[comment7]: <9> (De répercuter les propriétés des styles sur leurs enfants : il y a des relations de hiérarchie entre les styles, les enfants héritent les caractères des parents)

[comment8]: <9> (- De bien gérer les enchaînements de paragraphes --un style de titre est toujours collé au paragraphe suivant)

[comment9]: <9> (- De créer une table des matières)

[comment10]: <9> (Auj. on va commencer par modifier ces styles en veillant à :)

[comment11]: <9> (Utiliser la hiérarchie des styles, on veut passer Titre 1, 2 et 3 en Georgia, on va mettre tous les titres en Georgia au lieu de faire la même chose trois fois)

[comment12]: <9> (- Ne pas utiliser la touche entrée, car encore une fois on veut gérer proprement les enchaînements de paragraphes)

[comment13]: <9> (- Faire des modifications basiques sur les polices, les effets de caractères etc.)

[comment14]: <9> (2^e^ chose. On a travaillé sur un document de type article ; mais ce qui nous intéresse c'est de faire un mémoire : on va travailler sur la mise en page.)

[comment15]: <9> (- Créer une page de titre, pour l'instant très basique, avec simplement un titre, on pourra l'élaborer plus tard)

[comment16]: <9> (- Prévoir l'impression du mémoire recto-verso.)

[comment17]: <9> (On entre dans de la typographie un peu spécifique : la mise en page d'imprimerie observe certaines règles pas évidentes à appliquer dans un traitement de texte basique.)

[comment18]: <9> (- Les **pages de titres** sont toujours à droite, même s'il faut laisser un blanc à gauche)

[comment19]: <9> (- La position des numéros alterne sur la page de droite et la page de gauche)

[comment20]: <9> (- Si on laisse un blanc avant une page de titre, il ne faut pas de numéro sur la page blanche)

[comment21]: <9> (- Et on ne veut évidemment pas de numéro sur la première et c'est mieux de ne pas en avoir non plus sur les autres pages de titre)

[comment22]: <9> (- On peut faire des titres courants : qui rappellent le chapitre et la sous partie)

[comment23]: <9> (Pour faire tout cela on va utiliser des styles de pages : pour avoir une Première page qui sera le titre du mémoire, et une succession de page gauche et de page droite)

[comment24]: <9> (Une fois qu'on aura fait cela, on ajoutera à notre titre de Chapitre la mention « Chapitre 1 »)

[comment25]: <9> (Puis on crééra la table des matières, à laquelle on donnera la même apparence qu'un Titre 1, mais si on en faisait un Titre 1 elle donnerait elle-même sa pagination.)

-->

Les styles ont des relations hiérarchiques.\
En bas du panneau latéral, ouvrir le menu et cliquer sur **Hiérarchie**.

Il existe un style **Titre** sous lequel sont énumérés les titres que l'on a utilisés : Titre 1, Titre 2…

On souhaite appliquer une propriété de style\
commune à Titre 1, Titre 2, Titre 3 : la police **Garamond**\
(ou à défaut, son équivalent commun à Win et Mac : Georgia).

Cliquer sur **Éditer le style** > Police :

- Famille : Garamond
- Taille : Normal	


### <10>

Faire de même avec **Style de paragraphe par défaut** :\
on lui applique la police Times New Roman.


**Bloc de citation** hérite aussitôt de cette police.\
On souhaite maintenant que celle-ci, ainsi que **Bloc langue étrangère**, partagent une propriété : une taille de police à **10 pt**.\
Appliquer cette propriété à **Bloc de citation**.

Enfin, **Bloc langue étrangère** aura une propriété qui lui est propre : sa police est en **italique**.\
Editer le style pour l'obtenir.


### <11>

Maintenant que l'on a appliqué les **styles qui nous seront utiles**, il est commode de n'afficher que ceux-là.

En bas du panneau latéral, ouvrir le menu et cliquer sur **Styles appliqués**.

On y voit plus clair !


### <12>

Travaillons un peu plus sur **Style de paragraphe par défaut** :

- Lui appliquer aussi un **Alignement** justifié
- Lui appliquer, dans **Retraits et espacement** 
	- Un retrait de première ligne de 1 cm
	- Un interligne de 1,5 pt\
		(affectionné par les correcteurs de mémoires)

On constate que les paragraphes de texte et de citations ont bien reçu ces propriétés, mais que les citations ont aussi conservé leur propriété spécifique : la taille à 10 pt.


### <13>

À présent, il faut appliquer les propriétés spécifiques\
de chaque style.

On souhaite en particulier **espacer les titres et les blocs de texte**, en laissant un grand espace sous le Titre 1.

Il ne faut pas sauter de ligne avec la touche **Entrée**\
--- toute personne qui fait cela sera excommuniée ! ---\
mais modifier le Titre 1 en intervenant sur les propriétés\
de **Retraits et espacement** > Espacement :

- Au-dessus du paragraphe : 0,5 cm
- Sous le par. : 2 cm


### <14>

Appliquer les autres modifications au Titre 1 :

- Alignement : Centrer

- Police : 

	- Style : Normal
	- Taille : 28 pt

- Effet de caractères > Effets > Casse : petites majuscules


### <15>

**Pour le Titre 2** :

- Retraits et espacements :

	- Espacement > Au-dessus du paragraphe : 1 cm

- Police : 

	- Style : Normal
	- Taille : 20 pt


### <16>

**Pour le Titre 3** :

- Retraits et espacements :

	- Espacement > Au-dessus du paragraphe : 1 cm

- Police : 

	- Style : Italique
	- Taille : 16 pt


### <17>

**Pour le Titre 4** :

- Retraits et espacements :
	- Retrait > Avant le texte : 1 cm
	- Espacement > Au-dessus du paragraphe : 0,5 cm

- Police : 
	- Famille : Times New Roman
	- Style : Gras
	- Taille : 14 pt


<!--On est arrivé à l'étape 2-->


Quand on arrive ici, on attend ses camarades !\
C'est le moment où jamais de prendre une pause…


<a id='t3'/>

# Mettre en page un mémoire
[comment26]: <17> (TITRE1)


<a id='t3-1'/>

## Les composants du volume de texte 

### <18>

On a désormais une mise en page très satisfaisante pour un article de revue.
Mais un mémoire est une composition plus complexe, avec :

- Plusieurs chapitres, voire des parties groupant plusieurs chapitres
- Des annexes
- Un riche paratexte :

	- Bibliographie
	- Table des illustrations
	- Table des matières, etc.

<!--
Les composants du volume de texte


Deux règles à suivre :

1. Séparer texte et illustrations dans deux fichiers différents 
2. Gérer la structure du document (mise en forme et mise en page) dès le début de la rédaction
-->

### <19>


Une page de titre\
 (titre du volume, d'une partie, d'un chapitre, etc.) :

- Apparaît toujours à droite\
	(sa numérotation est donc impaire)

- Peut omettre le numéro de page


<a id='t3-2'/>

## Les pages de titre 

### <20>

On imagine que notre **Titre 1** est un titre de chapitre

Il faut à présent créer une **pièce de titre** pour l'ensemble du volume de texte du mémoire :

- Sauter une ligne avant *Réinventer les Vertus à Cluny*
- Écrire un titre de mémoire (réel ou inventé)
- Chercher parmi tous les styles de paragraphes préexistants **Titre principal** et l'appliquer au titre du mémoire

### <21>

Quelques règles à suivre pour la pièce de titre :

- Distinguer titre et sous-titre par des choix typographiques ; ne pas les séparer par de la ponctuation, comme `:`


### <22>

On veut que chaque chapitre ou élément de paratexte\
(ici *Illustrations*) commence au début d'une page, il faut donc **modifier le Titre 1** :

- **Enchaînements** > Sauts > Insérer
	- Type : Page
	- Position : avant

Désormais notre chapitre ainsi que la table des illustrations commencent en haut d'une nouvelle page.

**N.B.** : un titre ne possède jamais de ponctuation finale. On n'écrit pas : `Bibliographie :`

### <23>

Si l'on veut faire une mise en page dans les règles de l'art,\
il faut que nos Titre 1 soient **sur une page impaire** (à droite quand on tient le mémoire imprimé ouvert entre ses mains),\
or votre titre *Réinventer les Vertus…* se trouve actuellement sur la p. 2…


### <24>

Il faut donc définir des **Styles de pages** (bouton situé dans le même menu que Styles de paragraphes et Styles de caractères).

- Se placer tout au début du document, à la pièce de titre
- Choisir comme Styles de pages > **Première page**

Une fois appliqué, modifier ce style Première page :

- **Page** > Paramètres de mise en page > Mise en page > Droite uniquement
- **Général** > Style de suite > Page gauche


### <25>

<!---->
Désormais la première page (impaire) est suivie d'une alternance de **Page gauche** (paire) et de **Page droite** (impaire) ; l'information doit apparaître tout en bas de la fenêtre de LibreOffice quand vous placez votre curseur dans les différentes pages du document.


### <26>

Nos débuts de chapitres, table des ill.
et biblio, bref, les **Titre 1** doivent toujours être placés à droite et se comporter comme la première page :

- Modifier le Titre 1
- **Enchaînements** > Sauts > Avec le style de page > Première page

Une page blanche invisible a été créée entre la page 1 et la page 3.


<a id='t3-3'/>

## Numéros de pages et titres courants 

### <27>

**Titre courant** : *titre imprimé en haut ou en bas de chaque page et rappelant le titre <!--de l'ouvrage ou--> d'une partie de l'ouvrage<!--cnrtl-->.*

Pour faire apparaître en **titre courant** nos titres de chapitres, de table des illustrations, etc., il faut définir une **numérotation des chapitres** :

- Se placer sur un Titre 1
- **Outils** > Numérotation des chapitres
- Style de paragraphe > Titre 1
- Nombre : Aucun[^400]

[^400]: On crée cette numérotation mais on ne l'affiche pas, pour ne pas se retrouver avec « Chapitre 2 Illustrations » ! C'est pourquoi on opte pour *aucun*. On écrira plus tard « Chapitre 1 » à la main.


### <28>

Il ne reste plus qu'à ajouter des **numéros de pages**\
et des **titres courants**.

Naturellement, on n'en veut pas sur la page de titre, mais comme nos pages ont maintenant leurs propres styles, numéroter les pages de droite et de gauche n'affectera pas les pages de titre.

Pour poser ces numéros et ces titres courants, il faut commencer par activer les en-têtes et pieds de page :

- Modifier le style de page **Page droite**
- Pied de page > Activer
- En-tête > Activer
- Réitérer pour **Page gauche**


### <29>

On peut désormais ajouter les numéros :

- Cliquer sur le bas d'une page gauche
- **Insertion** > Numéro de page
- **Aligner à gauche** le numéro que l'on vient de créer (cela se répercute sur toutes les pages du style)
- Réitérer pour créer les numéros de la page droite, où on alignera les numéros à droite


### <30>

On peut désormais ajouter les titres courants :

- Cliquer sur le haut d'une page droite
- **Insertion** > Champ > Autres champs
- Onglet **Document**
- Type : Contenu de chapitre
- Format : Nom de chapitre
- Niveau 1

**Aligner à droite** le titre courant créé.


### <31>

On peut afficher les titres courants des sous-parties (Titre 2) sur les pages gauches :

- Cliquer sur le haut d'une page gauche
- **Insertion** > Champ > Autres champs
- Onglet **Document**
- Type : Chapitre
- Format : Nom de chapitre
- Niveau 2


<a id='t3-4'/>

## Imprimer 

### <32>

 Félicitations !\
 Vous avez maintenant une mise en page très professionnelle !


### <33>

Vous pouvez transformer le document en pdf comme pour l'imprimer en recto-verso :

- **Fichier** > Imprimer
- Dans l'onglet **Standard** > Imprimante > Imprimer dans un fichier
- Dans l'onglet **Libre OfficeWriter** > Pages > Imprimer les pages blanches insérées automatiquement
- Lancer l'impression

La p. 2, au verso de la page de titre, reste blanche et sans numéro pour que le chapitre commence sur la page impaire suivante.

<!--On est arrivé à l'étape 3-->


<a id='t4'/>

# Compléter le paratexte
[comment31]: <33> (TITRE1)


<a id='t4-1'/>

## Préparer une table des matières 

### <34>

Notre titre de chapitre n'en est pas vraiment un…\
On voudrait **ajouter « Chapitre 1 »** au-dessus de « Réinventer les Vertus à Cluny », comme dans le modèle pdf. 

**Attention** ! Si on écrit « Chapitre 1 » au début de la ligne « Réinventer… » et que l'on tape **Entrée**, on a un gros problème : « Chapitre 1 » devient un Titre 1 à lui seul, et donc un saut de page sépare « Chapitre 1 » de « Réinventer… »

Pour revenir correctement à la ligne après « Chapitre 1 », il faut faire un *retour chariot* : **Maj + Entrée**


### <35>

Il est préférable de mettre en forme « Chapitre 1 » de façon plus discrète que le contenu du titre qu'il introduit.

Mais comme « Chapitre 1 » doit rester en style de paragraphe Titre 1, il faut **créer un style de caractère** que l'on pourra appeler, par ex. : Chapitre.

- Sélectionner « Chapitre 1 »
- Cliquer sur **Nouveau style à partir de la sélection**
- Modifier ce nouveau style :
	- Effets de caractère > Effets > Casse > (Sans)
	- Police > Taille > 22 pt


### <36>

On va à présent ajouter la table des matières pour de bon.\
Faire une **sauvegarde maintenant**, car le logiciel peut planter !

- Se placer à la fin du document
- Revenir à la ligne (`Entrée`) si le curseur est à la fin d'une ligne
- **Insertion** > Tables des matières et index >\
	Tables des matières, etc.[^401]
- Dans le menu, ne rien changer > **Ok**

[^401]: Si l'opération fait planter LibreOffice Writer, décaler la fenêtre de récupération de document sur le côté et décocher **Aperçu** dans la fenêtre de gestion de la table des matières. Redémarrer en récupérant le document.


### <37>

Nous avons une table des matières (TDM), collée à la fin de la table des illustrations.

On veut appliquer les mêmes caractéristiques visuelles au titre de la TDM qu'aux autres éléments du paratexte,
mais on ne veut pas transformer le titre de la TDM en Titre 1, car en faisant cela le titre « Table des matières » serait traité comme les chapitres et apparaîtrait lui aussi dans la TDM !

La solution est toute prête :\
de nouveaux styles de paragraphes sont apparus dans la liste des **Styles appliqués**, dont **Titre de table des matières**.


### <38>

Modifier **Titre de table des matières** pour le faire ressembler au Titre 1 :

- **Enchaînements** > Sauts 
	- Insérer :
		- Type : Page
		- Position : Avant
	- Avec le style de page : Première page
- Police : Garamond, normal, taille 28 pt
- Retraits et espacement : 0,5 au-dessus ; 2 en-dessous
- Effets de caractère : casse en Petites majuscules
- Alignement : centrer


### <39>

 Pour une meilleure présentation de la TDM,\
on pourra modifier les styles **Table des matières niveau *n***, afin de hiérarchiser ces niveaux de titres.

<!--
Page 1 : la pièce de titre <40>
[comment33]: <39> (TITRE2)

Si vous ouvrez un livre récent imprimé en France et que vous cherchez où est la p. 1 (en remontant depuis les premières pages numérotées), vous arriverez sans doute à la première feuille du livre.

Cette p. 1 peut :

1. Être blanche : c'est une *garde*
2. Présenter le seul titre de l'ouvrage : c'est le *faux titre*


Page 1 : la pièce de titre <41>

La mise en page d'un mémoire peut faire abstraction de cela : notre p. 1 sera la **pièce de titre**.

Voir le fichier **modele-piece-titre-….odt**.

On peut procéder par de la mise en forme directe sur la pièce de titre, car elle est unique et implique un grand nombre de variations typographiques (taille des caractères, polices, effets de caractères).
-->

<a id='t4-2'/>

## Illustrations 

### <40>

Il est fortement conseillé d'illustrer son mémoire de stage.


Il est préférable que les images soient de **grandes dimensions**
et de ne pas laisser de texte sur les côtés.\
Une fois l'image insérée :

- Cliquer droit sur l'image
- **Adaptation du texte** => Aucune

Toute image doit être légendée.\
Pour insérer une légende :

- Cliquer droit sur l'image
- **Insérer une légende…**

### <41>

Pour insérer une table des illustrations à la place de l'existante (conçue pour des illustrations hors texte) :

- **Insertion** => Table des matières et index
- Type => Index des figures
- Titre : `Table des illustrations`
- Réitérer la même opération pour le style de paragraphe **Titre de l'index des figures** que pour la table des matières

<!--
[comment35]: <41> (### Volume de planches)

**Il est déconseillé d'insérer les illustrations dans le texte**,\
car cela joue très souvent en défaveur de :

- La qualité des reproductions (trop petites)
- La facilité de consultation (allers-retours entre le texte et les images)
- La bonne santé du fichier qui, très lourd, peut dysfonctionner

Il faut donc constituer un tome d'illustrations à part, au choix :

- Un autre fichier .odt
- Un fichier créé avec un logiciel de Publication Assistée par Ordinateur (**PAO**).


Illustrations

Les logiciels de PAO les plus connus sont : 

- Adobe InDesign
- Microsoft Publisher
- QuarkXPress
- Scribus : **le seul gratuit** et pour PC comme pour Mac

[comment36]: <41> (Scribus fonctionne également sous Ubuntu.)

Vous voulez faire au plus simple ?\
LibreOffice Writer ou Word avec une seule image par page !

Table des illustrations
[comment37]: <41> (TITRE3)

Les illustrations étant hors du texte, on va gérer leur numérotation à partir de la **table des illustrations** de notre document :

- Sélectionner toutes les lignes de cette table
- Appliquer le style de paragraphe **Illustration**,\
	visible si l'on affiche tous les styles


Table des illustrations

Il faut quelque peu modifier ce style pour en faire une liste numérotée du type Fig. 1, Fig. 2, etc.

Modifier le style **Illustration** avec les caractéristiques suivantes :

- Police : style Normal
- Retraits et espacement :
	- Avant le texte : 0 cm
	- Première ligne : 0 cm
- Plan & liste :
	- Appliquer le style de liste > Numérotation 123
	- Éditer le style > Personnaliser
		- Avant : Fig.
		- Après : *rien*


Renvois aux illustrations
[comment38]: <41> (TITRE3)

Maintenant que notre table des illustrations est établie,\
on peut ajouter des renvois aux figures dans le texte :

- Placer le curseur au point d'insertion souhaité dans le texte, répéré par les bulles-commentaires
- Dans le menu principal : **Insertion** > Renvoi
- Type : **Paragraphes numérotés**
- Sélectionner la bonne figure
- **Référer en utilisant** : Numéro (contexte complet)

Si maintenant j'ajoute des éléments à ma table des illustrations, à chaque fois que j'enregristre le document, il met à jour les numéros.
-->


<a id='t5'/>

# Importer/exporter un style
[comment39]: <41> (TITRE1)


### <42>

Faire un style de document, c'est bien ; pouvoir le réutiliser, c'est mieux !
On va exporter le style que l'on vient d'élaborer pour l'appliquer à un nouveau document.

- Cliquer sur **Fichier** > Modèles > Enregistre comme modèle
- Sélectionner la catégorie du modèle : **Styles**
- Donner un nom, par ex. « Mémoire »

Le style est sauvegardé.


### <43>

Pour appliquer le style à un autre document :

- Ouvrir le nouveau document
- **Styles** > Charger des styles depuis un modèle
- Sélectionner dans la catégorie Styles notre modèle Mémoire
- Cliquer sur **Ecraser**, puis Ok.


<a id='t6'/>

# Règles typographiques
[comment40]: <43> (TITRE1)


<a id='t6-1'/>

## Les espaces insécables 

### <44>

En typographie français, une espace insécable --- oui, espace est féminin en typographie --- doit précéder :

- Deux points
- Point virgule
- Point d'exclamation
- Point d'interrogation
- Et séparer les guillemets français d'une citation


### <45>

- *Lexique des règles typographiques en usage à l'Imprimerie nationale* \[1^re^ éd. 1971\], Paris, Impr. nationale, 2002, [en ligne](https://archive.org/details/lexique-des-regles-typographiques-en-usage-a-l-imprimerie-nationale/mode/2up).

- Quelques règles propres au domaine culture et patrimoineà télécharger sur Madoc : **conventions-patrimoine.pdf**

<!--
D'autres codes typographiques :
https://www.associationdescorrecteurs.fr/outils/codes-typo/
-->


<!--
### <46>

On peut appliquer massivement ces règles\
grâce aux expressions régulières.

Appliquer des espaces insécables avant la ponctuation qui l'exige :

- Chercher : `(\S)[ ]?([:!? »])`\
	 On cherche un caractère qui n'est pas une espace,\
	suivi de 0 ou 1 espace justifiante (c'est-à-dire normale),\
	suivie de d'une caractère qui doit obligatoirement être précédé d'une espace insécable

- Remplacer : `$1 $2`\
	 Une espace insécable sépare \$1 et \$2 ; pour insérer ce caractère sous Windows, maintenez enfoncée la touche {Alt et, sur le pavé numérique, tapez 0160.}


### <47>

 Appliquer des espaces insécables après la ponctuation qui l'exige :

- Chercher : `(«)[ ]?`\

- Remplacer : `$1` + [espace insécable]\

Appliquer des espaces insécables entre une abréviation de type n. ou p. et le nombre qui le suit (*n.
1, p. 24* par exemple) :

- Chercher : `([ ][ntp].)[ ]?(\d)`\
	 On cherche une séquence qui commence par une espace justifiante,\
	suivie de la lettre n ou de la lettre p,\
	suivie d'un point,\
	suivi de 0 ou 1 espace justifiante,\
	suivie d'un chiffre.

- Remplacer : `$1` + [espace insécable] + `$2`


### <48>

Il est fréquent d'ajouter par erreurs plusieurs espaces les unes derrières les autres ; pour ramener leur nombre, quel qu'il soit, à 1) :

- Chercher : `[ ]2,`\

- Remplacer : [1 espace]

-->


