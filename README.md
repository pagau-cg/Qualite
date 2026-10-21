# Qualité, Construction Gauthier

Module Qualité de la plateforme Opérations. **Prototype** : il sert de référence
de comportement avant la reconstruction dans Somtech.

> **Données fictives seulement.** Projets, employés, sous-traitants et constats
> sont inventés. Le site est publié sur GitHub Pages, donc **public**. Voir
> [DEPLOIEMENT.md](DEPLOIEMENT.md).

## Le principe : ACC capte, la plateforme gère

Les inspections du PIE se remplissent dans ACC Forms et les déficiences dans ACC
Issues, comme aujourd'hui. Le module les lit, en tire les constats et les
actions, fait les rappels et calcule les indicateurs. Rien n'est ressaisi.

## Ce que l'outil fait

- **Tableau de bord** : NC et déficiences ouvertes, retards, délai de fermeture,
  points d'arrêt à venir, répartition par projet et par lot, coûts de reprise.
- **NC et déficiences** : chaque constat porte une action, un responsable, une
  échéance selon la gravité.
- **Fiche d'un constat** : mesure immédiate, recherche de cause (5 pourquoi ou 6M),
  compilation des coûts (refacturables au sous-traitant), abonnés, preuve de
  correction, fermeture validée par quelqu'un d'autre que le responsable,
  vérification de l'efficacité à 30 jours.
- **Demandes** : améliorations du terrain, actions correctives, approbations de documents.
- **Audits** : programme, portée, référentiel, résultat, conclusion, constats liés.
- **Plan qualité (PIE)** : inspections faites sur prévues par discipline, points
  sensibles de l'étude de code, points d'arrêt.
- **Synchro ACC** : démonstration de la lecture des formulaires PIE et de la
  création automatique des constats.
- **Sous-traitants** : documents exigés, note qualité calculée, évaluation de fin de lot.
- **Gabarits ACC** : correspondance entre les champs des formulaires et les constats,
  configurable par le département CQ.

Le sélecteur « Vue de » en haut change d'utilisateur, pour voir les règles de
rôle (fermeture d'une action). L'interrupteur **Notes pour Somtech** affiche les
tables visées et les règles côté serveur, écran par écran.

## Sources de données : un champ, une source

| Donnée | Source maîtresse |
|---|---|
| Formulaires PIE, issues, photos | ACC |
| Projets | Ops (Somtech) |
| Employés | Ma Place RH |
| Constats, actions, audits, plan qualité | Ce module |

## Lien avec le module SST

SST et Qualité sont deux modules distincts dans la plateforme. Recommandation :
un moteur commun en arrière (constats, actions, rappels, abonnés, portail
sous-traitants), pour ne pas le développer deux fois.

## Contraintes du prototype

| Contrainte | Pourquoi |
|---|---|
| **Un seul fichier** `index.html` | Se copie, s'ouvre, se courriel sans installation |
| **Aucun appel réseau** | Les données ne quittent jamais le poste |
| **Aucun stockage navigateur** | L'outil ne laisse rien derrière lui |
| **Aucune bibliothèque externe** | Rien à mettre à jour, rien qui casse à distance |

Seule exception : la police Inter chargée depuis Google Fonts (charte Somtech).

## Fichiers

```
index.html            l'outil
GUIDE-TEST.md         pour le département CQ
DEPLOIEMENT.md        publication et hébergement privé
outils/verifier.mjs   vérification des invariants
```

## Vérifier avant de pousser

```
node outils/verifier.mjs
```
