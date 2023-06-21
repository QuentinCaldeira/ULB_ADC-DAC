# Tutoriel Gravure InkScape (FR)

## Contexte
Les plaques d'aluminium sont noires par défaut. On cherche à enlever toute la partie noir sauf aux endroits ou l'on souhaite faire apparaître des inscriptions. C'est un procédé un peu inverse à la gravure habituelle. Comme on cherche à faire l'inverse, la méthode utilisée est un peu différente.

## Préparation

Afin de pouvoir créer un fichier `.svg` pour la gravure laser, il faut d'abord préparer quelques chose. 
Dans un premier temps, un rectangle **rempli** d'une certaine couleur, de la dimension d'une plaque d'aluminium. Ces plaques font environ 128,5mm par 62 mm. Vous pouvez aussi utiliser le template disponible dans le dossier **Gravure**.

Avec une autre couleur, créer les éléments que vous voulez graver. Cela peut être du texte, des formes, ou autre. Une fois ces éléments créer, il faut les placer sur le rectangle comme vous voudriez que ce  soit graver.

## Outil différence
Le principe est donc de "soustraire" les formes que l'on veut graver au rectangle de départ. Pour ce faire on sélectionne d'abord la forme que l'on souhaite graver, puis le rectangle de départ en appuyant sur `'Ctrl'+'Shift'` pour faire une séléction multiple. une fois que les deux éléments sont sélectionnés, appuyer sur `'Ctrl'+'-'` pour faire la différence entre les deux objets.

Le rectangle de départ sera donc "creusé" par cette forme. Il faut ensuite répéter l'opération pour toutes les formes que l'on souhaite graver. J'ai remarqué qu'on ne peut pas faire une sélection multiple de textes pour ensuite les soustraire.

A la fin, il ne devrait vous rester qu'une seule forme : le rectangle creusé.


# InkScape Engraving Tutorial (EN)

## Background
Aluminium plates are black by default. We want to remove all the black except where we want the inscriptions to appear. It's the opposite of the usual engraving process. As we are trying to do the opposite, the method used is a little different.

## Preparation

In order to create an `.svg' file for laser engraving, you first need to prepare a few things. 
Firstly, a rectangle **filled** with a certain colour, the size of an aluminium plate. These plates are approximately 128.5 mm by 62 mm. You can also use the template available in the **Engraving** folder.

Using another colour, create the elements you want to engrave. This could be text, shapes or anything else. Once you have created these elements, place them on the rectangle as you would like them to be engraved.

## Difference tool
The principle is to 'subtract' the shapes you want to engrave from the starting rectangle. To do this, first select the shape you want to engrave, then the starting rectangle by pressing `'Ctrl'+'Shift'` to make a multiple selection. Once the two elements are selected, press `'Ctrl'+'-'` to make the difference between the two objects.

The starting rectangle will then be 'hollowed out' by this shape. You then need to repeat the operation for all the shapes you want to engrave. I noticed that you can't make a multiple selection of texts and then subtract them.

In the end, you should be left with just one shape: the hollowed-out rectangle.