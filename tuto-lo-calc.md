---
title: Tutoriel LibreOffice Calc
---

Plan :

1. [Navigation](#t1)
2. [Fonctions avancées](#t2)
	1. [RechercheV](#t2-1)

[comment]: <> (FINET)



<a id='t1'/>

# Navigation

- La souris ne sert pas à grand chose pour se déplacer dans un tableau : **privilégier les flèches**

	- **Ctrl + flèche** vous renvoie à la dernière case non vide dans la direction de la flèche

- Pour aller tout au début d'une ligne : touche **Début**
- Pour aller tout à la fin d'une ligne : touche **Fin**
- Pour aller à la case A1 : **Ctrl + Début**
- Pour aller à la case opposée (dernière ligne et dernière colonne de la partie non vide du tableau) : **Ctrl + Fin**


# Sélection et transformation

- **Pour modifier** le contenu d'une cellule :
	- Se placer sur la cellule avec les flèches ou les combinaisons précédentes
	- Écrire un nouveau contenu
	- Sortir de la cellule (par une touche flèche ou Entrée)
	- **Ctrl + Z** pour annuler une modification malheureuse

- **Pour sélectionner** un groupe de cellule :
	- Se placer sur une première cellule
	- Rester appuyer sur **Maj**
	- Se déplacer avec les flèches jusqu'à la dernière cellule souhaitée


- **Pour sélectionner** tout le tableau :
	- **Ctrl + Début**
	- Puis maintenir **Ctrl + Maj**
	- Appuyer sur **Fin**

- Pour poser des filtres : **Ctrl + Maj + L**

- **Pour déplacer** une ligne ou une colonne

	1. Cliquer sur l'en-tête de la colonne (B par exemple).
	2. Appuyer sur Alt et maintenir
	3. Cliquer gaucher sur une cellule de cette colonne et maintenir le clic gauche.
	4. Déplacer vers la destination le curseur (colonne H par exemple).



# Fonctions avancées


<a id='t2-1'/>

## RechercheV

Consiste à afficher dans une table (X) les données d'une autre table (Y) dès lors que les deux tables partagent une **clé** commune (une donnée identique).\
Il est important que les deux tables soient structurées en tableau dynamiques (avec auto-filtres).

La formule se décompose ainsi :

- Type de fonction : **RECHERCHEV** qui recherche ***V***erticalement dans un groupe de colonnes (ou *matrice*)
- Plusieurs clauses (entre parenthèses et séparées par des `;`) :
	- Le critère de recherche : *c'est la donnée commune aux deux tables*
	- La matrice : *c'est le groupe de colonnes de la table Y où se trouvent à la fois la clé commune aux deux tables et l'information que l'on souhaite afficher en X\
		Dans Y, la clé doit se trouver dans la première colonne de la sélection, tout à gauche\
		**NB** : il est plus facile de sélectionner à la souris les colonnes de la matrice plutôt que d'écrire ce paramètre à la main*
	- L'indice : *c'est le numéro de la colonne de la matrice correspondant à la donnée que l'on souhaite afficher en X*
	- Recherche dans une plage triée : toujours écrire `0` *pour FAUX (faites-moi confiance !)*

Exemple de formule complète : `=RECHERCHEV(A2;$Mérimée.A:C;1;0)`\
Elle se décompose ainsi :

- Le critère de recherche : `A2` *car on cherche si l'identifiant de la colonne A sera dans la feuille Mérimée*
- La matrice (ou groupe de colonnes où chercher) : `$Mérimée.A:C` *qui signifie chercher dans la feuille nommée Mérimée, dans les colonnes de A à C*
- L'indice : `1` *car c'est dans la 1^re^ colonne de la matrice que se trouve l'identifiant*
- Recherche dans une plage triée : toujours écrire `0` *pour FAUX*
