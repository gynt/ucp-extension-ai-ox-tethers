# IA : longes à bœufs

L’IA construit normalement jusqu’à 3 longes à bœufs par carrière. Elle place aussi automatiquement une longe chaque fois qu’elle construit ou reconstruit une carrière.

Ces longes automatiques peuvent épuiser la capacité de logement de l’IA et empêcher l’arrivée de nouveaux paysans. Cette extension permet de les désactiver et de personnaliser les règles de construction des longes supplémentaires.

Une **longe rattachée** appartient à la carrière où son ouvrier a récupéré de la pierre pour la dernière fois. Ce rattachement est mis à jour dynamiquement au lieu d’être fixe.

## Fonctionnalités
- Autoriser plus de 3 longes à bœufs par carrière
- Personnaliser les règles de décision pour construire davantage de longes
- Personnaliser les règles par IA via l’AIC

## Paramètres AIC

### `AIOxTethers_Logic`
0 : Logique d’origine du jeu.
1 : Logique dynamique utilisant les plafonds et les règles de charge de pierre ci-dessous.

### `AIOxTethers_MaxOxTethers`
Plafond total de longes à bœufs par joueur.

### `AIOxTethers_DynamicMaxOxTethers`
Plafond total de longes = cette valeur × nombre de carrières.
Le plus bas des 2 plafonds totaux s’applique à tout moment.

### `AIOxTethers_ThresholdStoneLoad`
Si `pierres/longes rattachées` dépasse cette valeur pour une carrière, une autre longe est construite, dans la limite des plafonds. Sans longe rattachée, la quantité de pierre est utilisée directement.

### `AIOxTethers_DisableInitialOxTether`
0 : Placer automatiquement une longe à chaque construction ou reconstruction d’une carrière.
1 : Désactiver ce placement automatique.

Ce réglage est indépendant de la logique dynamique et de ses plafonds.

### `AIOxTethers_MinimumOxTethersPerQuarry`
Si une carrière a moins de longes rattachées que cette valeur, une autre est construite quelle que soit la charge de pierre, dans la limite du plafond total.

### `AIOxTethers_MaximumOxTethersPerQuarry`
Plafond des longes rattachées construites pour une carrière selon sa charge de pierre. Le minimum doit rester inférieur ou égal à ce plafond.
