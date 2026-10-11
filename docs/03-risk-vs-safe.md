# 03 — Ce que l'expérimentation m'a appris

## Deux scénarios, une même question

J'ai réalisé deux essais pour observer les conséquences de l'état du commutateur entrant et de sa préparation avant raccordement.

| | Intégration à risque | Intégration avec préparation préalable |
|---|---|---|
| Préparation du commutateur entrant | Révision supérieure et base VLAN différente | Domaine VTP attendu configuré avant l'activation du trunk |
| Nettoyage complet de la base VLAN | Non | Non |
| Résultat observé | Le domaine passe à la révision 9 et 14 VLANs | Le domaine reste à la révision 8 et 9 VLANs |
| Ce que l'essai illustre | Le risque lié à l'intégration d'un commutateur à révision supérieure | L'effet observé de la configuration préalable du domaine dans ce lab |

## Mon constat

Le premier scénario m'a permis d'observer une synchronisation VTP à risque. Dans le second, j'ai configuré le domaine attendu sur le commutateur entrant avant d'activer le trunk, puis j'ai vérifié l'état final du domaine.

Il est important de préciser que **je n'ai pas supprimé `vlan.dat` ni effacé la configuration de démarrage** dans le second scénario. Je ne peux donc pas présenter cet essai comme une remise à zéro complète du commutateur.

## Ce que ce lab m'a appris

La Configuration Revision n'est pas le nombre de VLANs : c'est un compteur lié aux modifications de la base VLAN VTP. Un commutateur entrant doit donc être inspecté avant raccordement. La configuration préalable du nom de domaine ne remplace pas cette vérification et ne garantit pas, à elle seule, la remise à zéro de son état.

Pour une intégration réelle, je vérifierais au minimum `show vtp status` et `show vlan brief` avant le raccordement et je choisirais la procédure de préparation en fonction de l'état constaté.

Cette expérimentation m'a surtout appris à distinguer ce que j'ai réellement testé de ce qu'une procédure complète de remise à zéro exigerait.

**Avant d'intégrer, je vérifie. Avant de modifier, je comprends.**