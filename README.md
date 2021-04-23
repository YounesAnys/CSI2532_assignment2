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


