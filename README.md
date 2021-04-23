# CSI2532_assignment2

## Sommaire

| Sommaire | Valeur |
| --- | --- |
| Cours | CSI 2532 |
| Session | Hiver 2021 |
| Professeur | Andrew Forward |
| Equipe | Younes Anys (300145843) |

## Q1 : Normalisation

a) 
Les clés candidates sont :
AB

BC

BD

b)

Indiquez toutes les violations BCNF pour R et décomposez les relations en ensembles de relations qui se trouvent dans BCNF.
C et D ne sont pas des super clés
Pour être dans BCNF, le côté gauche de tous les FD de R doit contenir une clé.
''
(AB) + -> ABC
(C) + -> CD
(D) + -> AD
''

Aucun des FD de R ne contient B ou AB. Nous pouvons décomposer R en relations BCNF avec jointure sans perte.
''
S1 (A, B, C) // Attributs dans AB -> C
- Seul FD est AB -> C
- AB est la clé pour S1
- Seul FD a une clé sur le côté gauche, donc S1 est en BCNF
S2 (A, B, D) // Tous les attributs du côté gauche + les attributs manquants
- FD: AB -> C, C -> D
- Clé: AB
- La clé n'est pas dans tous les FD, donc S2 pas dans BCNF
- Décomposer davantage
S3 (C, D) // C -> D
- Seul FD est C -> D
- C est la clé pour FD
- Seul FD a la clé sur le côté gauche, donc S3 est en BCNF
S4 (C, A, B) // Tous les attributs du côté gauche + les attributs manquants
- Seul FD est AB -> C
- AB est la clé de FD
- Seul FD a la clé sur le côté gauche, donc S4 est en BCNF
''

Le schéma final contient 2 relations:
''
S1 (A, B, C)
S3 (C, D)
''

 c. Indiquez quelles dépendances, le cas échéant, ne sont pas conservées par la décomposition BCNF.
La décomposition n'est pas sans perte car il n'y a pas d'attribut commun dans S1 et S3. On perd la dépendance suivante: D -> A.

## Q2 : Dépendances fonctionnelles

a) Identifions les quatre dépendances fonctionnelles décrites :

Normalisation 

les dépendances fonctionnekkes décrites :

NIN --> eName

contratNo --> hotelNo, hotelLocation

hotelNo --> hotelLocation 

NIN, contratNo --> hoursPerWeek, eName, hotelNo

b) Identifions les clés :

clés primaires :

NIN

contratNo

hotelNo

clés étrangere :

hotelNo

c) 
La table est en 2NF car tous les attributs sont atomiques (1NF) et il n'y a pas de dépendance partielle (2NF).

HotelEmployeeInsurance (NIN, contratNo, hoursPerWeek, eName, hotelNo, hotelLocation)

3NF (Supprimer la dépendance transitive)

Dépendance transitive:

hotelNo -> hotelLocation

Tableaux dans 3NF

Assurance (NIN, contracNo, hoursPerWeek, eName, hotelNo)

Hôtel (hotelNo hotelLocation)

## Q3. Langages purs
Considérez les schémas relationnels suivants:
''
Marins (sid, sname, classement, âge)
Réserves (sid, bid, day)
Bateau (enchère, bname, bcolor)
''
 une. (RA) Liste les couleurs des bateaux réservés par Albert.
π bcolor [(σ sname = 'Albert' (marins)) ⋈ Réserves ⋈ Bateau]

 b. (RA) Dressez la liste des identifiants de tous les marins qui ont une cote d'au moins 8 ou un bateau réservé 103.
π sid (σ rating> = 8 (Sailors)) ∪ π sid [σ bid = 103 (Reserves)]

 c. (TRC) Dressez la liste des noms et des âges de tous les marins qui ont une cote inférieure à 3.
{X | S ∈ Sailors ∧ S.rating <3 ∧ X.name = S.name ∧ X.age = S.age}

 ré. (RDC) Liste les identifiants de tous les bateaux qui ont été réservés le 2019-04-28.
{<B> | <S, B, D> ∈ Réserves ∧ D = '2019-04-28'}

 e. (RDC) Liste les couleurs de tous les bateaux réservés par Lubber.
{<C> | <I, N, C> ∈ Bateaux ∧ <S, I, D> ∈ Réserves ∧ <S, 'Lubber', R, A> ∈ Marins}

 ## Q4. RAID
1 -> B
Je peux utiliser une technique de niveau RAID 0 car je ne suis pas préoccupé par la perte de données. Mon objectif principal est de pouvoir lire et écrire à grande vitesse.

2 -> C
Je peux utiliser une technique RAID de niveau 1 car je n'ai que deux disques disponibles qui représentent plus du double de la capacité dont j'ai besoin pour mon application et je suis soucieux de pouvoir récupérer des données si nécessaire.

3 -> E
Je peux utiliser une technique de niveau RAID 5 car la tolérance aux pannes est importante pour mon application mais je n'ai pas beaucoup d'espace disponible.

4 -> A
Je peux utiliser une technique de niveau RAID 6 car la tolérance aux pannes est importante pour mon application et je dois protéger mes données même si deux disques tombent en panne en même temps.

5 -> C
Je préfère utiliser une approche basée sur la parité au lieu d'une approche en miroir car j'ai 6 disques disponibles mais j'ai besoin de la capacité de 5 d'entre eux, ce qui signifie que je ne peux épargner que l'espace correspondant à un seul disque pour assurer la redondance.

## Q5. B + -arbre
 une. Afficher l'arbre B + qui résulte après l'insertion (dans l'ordre donné) 56, 50, 75, 87, 48.
''
[65]
[24 | 50] [75 | 88]
[2 | 10] [24 | 45 | 48] [50 | 56] [65 | 72] [88 | 93]
''

b. En utilisant l'arbre B + précédemment obtenu dans a, montrez l'arbre B + qui résulte après la suppression (dans l'ordre donné) 50, 24, 65, 93, 75.
''
[48 | 72]
[2 | 10 | 45] [48 | 56] [72 | 87 | 88]
''
## Q6. Bitmap d'index
### une. Construisez un index bitmap pour les attributs Marque et Couleur de cette table.
Marque
| Opel | Peugeot | BMW |
| --- | --- | --- |
| 1 | 0 | 0 |
| 1 | 0 | 0 |
| 0 | 1 | 0 |
| 0 | 0 | 1 |

Couleur
| Gris | Rouge | Noir |
| --- | --- | --- |
| 1 | 0 | 0 |
| 0 | 1 | 0 |
| 0 | 0 | 1 |
| 0 | 0 | 1 |

### b. Montrez comment les index bitmap peuvent être utilisés pour répondre aux requêtes:
je. Montrez la marque de toutes les voitures qui ne sont pas noires.
Nous analysons le bitmap pour le noir: [0 0 1 1]. Nous prenons les tuples dans la relation où les entrées sont 1. Ainsi, les 3e et 4e tuples sont pris. Le résultat final est les tuples correspondants.

ii. Donnez le nombre total de voitures Opel rouges avec un score de risque moyen.
Nous analysons le résultat de (bitmap pour Opel) AND (bitmap pour Red): [0 1 0 0]. Nous prenons les tuples dans la relation où les entrées sont 1. Nous vérifions ensuite les tuples où Risque = moyen. Les tuples qui satisfont à cette condition sont comptés. Ainsi, seuls les 2ièmes tuples sont comptés. Le résultat final est 1.

## Q7. Hashing

Considérez la fonction de hachage suivante:
''
h (x) = x mod 4
''
### une. Utilisez cette fonction pour créer l'index de hachage des valeurs de clé de recherche suivantes: 2, 4, 6, 12, 13, 16, 20, 24, 28, 40.

| 000 | 001 | 010 | 011 | 100 | 101 | 110 | 111 |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 4, 12, 16, 20 (trop-plein) | 13 | 2, 6 | / | / | / | / | / |

### b. Compte tenu des valeurs de clé de recherche, cette fonction est-elle une bonne fonction de hachage? Expliquez votre réponse.

Non. Il y a trop de valeurs de clé de recherche qui doivent entrer dans le compartiment 000, bien que vous ayez précédemment fractionné les compartiments 0 et 00 et modifié leur contenu pour les valeurs restantes. Il serait préférable d'utiliser des valeurs de clé de recherche qui ne sont pas des multiples de 4.
