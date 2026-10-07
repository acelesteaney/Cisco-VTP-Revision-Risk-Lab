# 01 — Intégration VTP risquée

## Pourquoi j'ai réalisé ce scénario

Je voulais vérifier concrètement ce qui pouvait se produire lorsqu'un switch provenant d'un autre environnement VTP était raccordé à un domaine existant sans avoir contrôlé son état au préalable.

L'objectif n'était donc pas seulement de configurer VTP, mais de **provoquer volontairement une situation à risque**, puis d'observer la réaction du domaine.

## Situation de départ

Le domaine existant était à : **Configuration Revision 8** et **9 VLANs**.

J'ai ensuite préparé le commutateur expérimental avec : **Configuration Revision 9** et **14 VLANs**.

La révision du commutateur expérimental était donc volontairement supérieure à celle du domaine existant.

## Déroulement et éléments de preuve

### Architecture initiale du laboratoire
**Indication pour la capture :** montrer la topologie complète avec le serveur VTP, les deux clients et le commutateur expérimental encore isolé.

### État initial du domaine VTP
**Indication pour la capture :** afficher le show vtp status du serveur avant l'intégration, avec la révision 8 et les 9 VLANs.

### Préparation du commutateur à révision supérieure
**Indication pour la capture :** afficher l'état VTP du commutateur expérimental montrant la révision 9 et les 14 VLANs.

### Comparaison avant raccordement
**Indication pour la capture :** mettre en évidence la différence entre l'état du domaine existant et celui du commutateur entrant avant de créer le lien.

### Établissement du trunk
**Indication pour la capture :** montrer la configuration ou la vérification du trunk entre le domaine existant et le commutateur expérimental.

### Synchronisation VTP après intégration
**Indication pour la capture :** afficher le show vtp status après raccordement et montrer que le domaine converge vers la révision 9 et les 14 VLANs.

### Propagation vers les clients
**Indication pour la capture :** afficher l'état VTP d'un ou des clients après synchronisation pour montrer la propagation de la nouvelle base VLAN.

### État final après l'intégration à risque
**Indication pour la capture :** montrer l'état final des équipements et la convergence de la révision et de la base VLAN.

## Ce que j'ai constaté

Le résultat m'a permis de comprendre concrètement que la Configuration Revision joue un rôle déterminant dans la synchronisation VTP. Le problème n'est donc pas simplement qu'un switch possède « plus de VLANs », mais qu'il arrive avec une base VLAN considérée comme plus récente par VTP.

Cette expérience m'a surtout montré pourquoi **l'état d'un switch entrant doit être vérifié avant son raccordement à un domaine VTP existant**.