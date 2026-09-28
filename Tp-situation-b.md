# Remplacement d'une alim saturé
[← Retour au portfolio](tp-camille.html)
BE, 20 postes, juin 2026, Option SISR 

## Contexte
 Y a un poste au bureau d'études qui redémarrait tout seul, genre 3 ou 4 fois par jour, ça durait depuis une quinzaine de jours et la personne perdait son travail à chaque fois. J'ai regardé l'observateur d'événements, y avait des Kernel-Power 41. J'ai d'abord cru à Windows, j'ai fait les mises à jour, ça a rien changé. Après j'ai pensé à la RAM, j'ai lancé un memtest une nuit, 0 erreur. Du coup j'ai ouvert le poste, l'alim était pleine de poussière et le ventilateur faisait un bruit bizarre. J'ai mesuré la conso avec une prise wattmétrique, le poste tirait 310 W en pointe avec une alim de 350 W, donc limite. J'ai remplacé l'alim par une 550 W, j'ai nettoyé, et depuis plus aucun redémarrage en un mois. J'étais content parce que c'était ma première panne matérielle trouvée tout seul. Faudrait que je pense à vérifier l'alim plus tôt la prochaine fois. »

Ce qu'il manque et que vous devrez inventer de façon plausible : la date, le modèle exact du matériel, et la précaution prise avant d'ouvrir le poste.


## Problématique

Depuis 15 jours, les redémarrages intempestifs d’un poste informatique est survenus 3 à 4 fois par jour.

## Démarche

J'ai d'abord relevé les débits depuis un poste de l'atelier : 8 Mo/s en copie vers le serveur, contre 74 Mo/s depuis un poste du bureau. Trois hypothèses : le câblage, la carte réseau des postes, le switch.

J'ai écarté le câblage : les liens ont été certifiés en 2023 et un test au testeur de câble sur trois prises n'a rien montré. J'ai écarté la carte réseau : le problème touchait les 12 postes, pas un seul.

Restait le switch, un modèle 16 ports à 100 Mb/s dont les compteurs affichaient des erreurs de collision. Je l'ai remplacé par un switch administrable gigabit prêté par le fournisseur, pour valider l'hypothèse avant tout achat.

## Outils mobilisés

- Switch administrable 16 ports gigabit (modèle de prêt, puis modèle acheté)
- Testeur de câble RJ45
- Wireshark 4.2 pour observer les retransmissions
- GLPI 10.0 pour le suivi du ticket et la mise à jour de l'inventaire

## Précautions prises

J'ai sauvegardé la configuration de l'ancien switch, étiqueté les 16 câbles avant de les débrancher, et programmé l'intervention entre 12 h 30 et 13 h 15, hors production. J'ai prévenu le chef d'atelier la veille.

## Résultats

Le débit de copie est passé de 8 Mo/s à 74 Mo/s. La sauvegarde est redescendue à 6 minutes. Aucune coupure signalée dans les trois semaines qui ont suivi. L'inventaire GLPI a été mis à jour le jour même.

## Bilan personnel

J'ai perdu deux jours à suspecter le câblage alors que les compteurs d'erreurs du switch donnaient la réponse dès le premier relevé. La prochaine fois, je commencerai par interroger les équipements réseau en SNMP avant de tester les liens un par un.

---

**Compétences mobilisées** : gérer le patrimoine informatique ; répondre aux incidents et aux demandes d'assistance.
