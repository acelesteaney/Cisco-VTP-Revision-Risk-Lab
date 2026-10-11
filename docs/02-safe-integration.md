# 02 — Intégration VTP avec préparation préalable

## Pourquoi j'ai réalisé ce scénario

Après avoir observé les conséquences d'une intégration à risque, j'ai voulu tester une autre méthode : préparer le commutateur entrant avant d'activer le trunk vers le domaine VTP existant.

## Principe retenu

Dans ce scénario, je n'ai pas supprimé `vlan.dat` ni effacé la configuration de démarrage. J'ai simplement configuré le domaine VTP attendu sur le commutateur entrant alors qu'il était encore isolé, puis j'ai activé le trunk.

Il s'agit donc d'une **préparation préalable du domaine avant raccordement**, et non d'une remise à zéro complète de la base VLAN.

## Déroulement et éléments de preuve

### Isolement du commutateur entrant

Le commutateur expérimental reste isolé du domaine existant pendant sa préparation.

### Configuration du domaine VTP attendu

J'ai configuré le domaine `ACANEY-VTP` sur le commutateur entrant avant d'activer le trunk.

### Activation du trunk

Une fois le domaine configuré, j'ai activé la liaison trunk vers le domaine existant.

### Vérification après intégration

Après le raccordement, j'ai vérifié l'état VTP des commutateurs. Dans l'état final observé, le domaine affichait 9 VLANs et la révision 8.

## Ce que j'ai constaté

Cette méthode m'a permis d'observer le résultat d'une préparation du domaine VTP avant l'activation du trunk. Toutefois, comme je n'ai pas supprimé l'ancienne base VLAN ni effectué une remise à zéro complète, je ne présente pas cette étape comme un nettoyage garanti de l'état VTP.

**Point technique à retenir :** changer le nom du domaine VTP ne garantit pas, à lui seul, que la base VLAN et la Configuration Revision ont été réinitialisées. Avant de connecter un commutateur provenant d'un autre environnement, il faut vérifier son état réel avec `show vtp status` et `show vlan brief`, puis choisir une procédure adaptée au contexte.

Cette expérience m'a appris à distinguer une préparation de configuration d'une véritable remise à zéro de l'état VTP.