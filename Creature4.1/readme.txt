**********************************************Creature 4.1*******************************************************
Telechargez breveIDE sur: 
http://www.spiderland.org/breve/download.php
Les documentations sont disponible sur: 
http://spiderland.org/breve/documentation.php

Pour lancer Creature 4.1, il suffit d'avoir les 4 fichiers dans le meme repertoire puis lancer creatureMain.tz avec breve. Modifiez les parametres dans constants.tz (sauf position d'abri1) pour tester la simulation.
- Duong

*****************************************************************************************************************
Les regles des agents:

Proie: 
- Cherche des voisins dans sa portee (defini dans fichier constants.tz avec NBH_SIZE_PROIE)
- Si il detecte la nourriture, il avance vers la nourriture. En collision avec la nourriture, il gagne de l'energie de la nourriture. 
- Si il detecte un predateur, il retourne vers l'un des 3 abris, chaque abri a 33% pour etre choisi.
- Si il ne detecte pas de voisin, il peut se-balader justqu'il detecte un autre voisin.


Predateur:
- Cherche des voisins dans sa portee. (defini dans fichier constants.tz avec NBH_SIZE_PRED)
- Si il se trouve dans une proximite de l'abri1 (se trouve a l'origine de l'univers), il recule.
- Si il detecte un Proie, il avance vers le proie, il gagne d'energie equivalent au (energie du proie mange)/4 
- Si il est en collision avec un Pred et que son energie est 2*(energie du pred) alors il le tue, et gagne d'energie equivalent a (energie du pred tue)/6
- Si il ne detecte pas de voisin, il peut se balader justqu'il detecte un autre voisin (si voisin est nourriture, il ignore).


Nourriture et Abris:
- La nourriture immobile et s'autogenere en fonction de parametres NUM_SCHEDUL_GENERE (nbre de fois genere) et INTERVAL_SCHEDUL_GENERE (interval du temps entre chaque generation).


*******************************************************************************************************************
Notes:

- Les methodes principales sont: instinct-proie et instinct-pred (se trouve dans creatureMain.tz). C'est ici que je definis les regles.
- Les methodes et attributs communs du preds et proies sont dans le fichier creatureClass.tz.
- Les definitions des objets immobiles (Abri, Nourritures) sont dans le fichier immobileClass.tz. Abri est une sphere de rayon 20.
- Le fichier constant est utile pour tester la simulation avec different parametre. Par exemple: (on peut changer le nombre des proies avec NUM_PROIE, sa portee avec NBH_SIZE_PROIE etc.)

- Ce que je peux remarquer c'est que, bien que le choix d'abri (defini dans le methode choix-dabris du proie) est equivalent, les proies se concentre plus au centre, les predateurs forme en general une sorte de perimetre autour de l'abri. Cela peut etre interessant au niveau d'intelligence artificielle. C'est quelque chose qu'on n'a pas definit mais a partir des regles simple, les predateurs forme leur propre strategie.

- Ce qui est interresant est peutetre de reduire le nombre des creatures pour voir si un objet suit les regles correctement.

- Il reste des bugs que plus avance dans la simulation, les objets deviennent moins actives, c'est peut etre un problem de memoire, de l'algo du methode "se-balader", ou un problem de portee des creatures. 



