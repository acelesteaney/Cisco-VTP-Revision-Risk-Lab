# 02 — Intégration VTP sécurisée

## Pourquoi j'ai réalisé ce scénario

Après avoir volontairement provoqué le scénario à risque, je voulais tester l'approche inverse : **comment intégrer le même type de switch sans lui permettre d'imposer son ancienne base VLAN au domaine existant ?**

J'ai donc repris le problème sous l'angle d'une intégration contrôlée.

## Principe retenu

Le commutateur entrant doit être : isolé, inspecté, nettoyé de son ancienne base VLAN et de sa configuration, préparé avec les paramètres attendus, puis seulement raccordé au domaine existant.

## Déroulement et éléments de preuve

### Isolement du commutateur entrant
**Indication pour la capture :** montrer que le commutateur expérimental est encore séparé du domaine existant avant toute opération de nettoyage.

### Inspection préalable de l'état VTP
**Indication pour la capture :** afficher les informations VTP du commutateur avant son intégration afin d'identifier son domaine, son mode, sa révision et sa base VLAN.

### Nettoyage de la base VLAN
**Indication pour la capture :** montrer les commandes ou l'étape utilisée pour supprimer l'ancienne base VLAN avant l'intégration.

### Vérification de l'état propre
**Indication pour la capture :** afficher l'état VTP/VLAN après le nettoyage et avant tout raccordement au domaine.

### Préparation du domaine VTP attendu
**Indication pour la capture :** montrer la configuration du domaine ACANEY-VTP sur le commutateur encore isolé.

### Intégration du commutateur nettoyé
**Indication pour la capture :** montrer l'établissement du trunk entre le commutateur préparé et le domaine VTP existant.

### Synchronisation contrôlée
**Indication pour la capture :** afficher les informations VTP après intégration afin de vérifier que le commutateur adopte la base VLAN attendue.

### Vérification finale de l'intégration
**Indication pour la capture :** montrer l'état final du domaine et confirmer que celui-ci reste à la révision 8 avec 9 VLANs.

## Ce que j'ai constaté

La différence avec le premier scénario est importante : cette fois, le commutateur entrant n'arrive pas avec une ancienne base VLAN susceptible d'influencer le domaine.

Cette manipulation m'a permis de comprendre qu'une intégration réseau propre commence **avant même de connecter l'équipement au réseau existant**.

Le point essentiel que je retiens est donc la vérification préalable de l'état d'un équipement entrant, surtout lorsqu'il peut participer à un mécanisme de synchronisation comme VTP.