# Cisco VTP (Vlan Trunking Protocol) : Configuration Revision Risk & Safe Integration

## À travers ce lab

À travers ce laboratoire, j'ai cherché à aller au-delà de la simple configuration de VTP dans Packet Tracer. En reproduisant volontairement une intégration à risque puis en la corrigeant avec une procédure maîtrisée, j'ai pu constater concrètement que la **Configuration Revision ne correspond pas au nombre de VLANs** et qu'un switch apparemment prêt à être raccordé peut modifier la base VLAN du domaine s'il n'est pas vérifié au préalable.

## Ce que j'ai travaillé
- Comprendre VTP Server / Client.
- Comprendre le rôle réel de la Configuration Revision.
- Reproduire volontairement un scénario d'intégration à risque.
- Observer la synchronisation de la base VLAN.
- Identifier ce qui rend l'intégration d'un switch dangereuse.
- Mettre en place une procédure contrôlée avant intégration.
- Vérifier les résultats avec les commandes Cisco IOS.

## Scénarios

### 01 — Intégration risquée
[Voir la documentation du scénario](docs/01-risky-integration.md)

Accès direct au fichier Packet Tracer : [LAB-VTP-AVEC-RISQUE.pkt](labs/LAB-VTP-AVEC-RISQUE.pkt)

### 02 — Intégration sécurisée
[Voir la documentation du scénario](docs/02-safe-integration.md)

Accès direct au fichier Packet Tracer : [LAB-VTP-SANS-RISQUE.pkt](labs/LAB-VTP-SANS-RISQUE.pkt)

### 03 — Risque vs intégration maîtrisée
[Voir l'analyse comparative](docs/03-risk-vs-safe.md)

Les deux fichiers Packet Tracer restent également regroupés dans [labs/](labs/) pour conserver une organisation claire.

## Ma topologie

Pour réaliser ce travail, j'ai construit une petite infrastructure de **quatre commutateurs** : un VTP Server, deux VTP Clients et un quatrième commutateur utilisé comme équipement expérimental puis entrant. J'ai volontairement isolé ce dernier afin de préparer séparément le scénario à risque, puis de tester une méthode d'intégration plus contrôlée.

**Indication pour la capture :** ajouter ici la topologie initiale Packet Tracer avec les quatre commutateurs visibles et le commutateur expérimental isolé.

Voir [la partie Topologie](topology/README.md).

## Organisation du dépôt
```text
Cisco-VTP-Revision-Risk-Lab/
├── configurations/
├── docs/
├── labs/
├── tests/
│   └── screenshots/
├── topology/
└── README.md
```

- configurations/ → commandes et vérifications Cisco IOS.
- docs/ → déroulement et analyse des scénarios.
- labs/ → fichiers Packet Tracer.
- tests/ → éléments de preuve et captures.
- topology/ → présentation de l'architecture.

## Leçon clé

Ce laboratoire m'a surtout permis de comprendre une chose que je ne voulais pas simplement apprendre de manière théorique : **la Configuration Revision n'est pas le nombre de VLANs**.

En manipulant volontairement deux bases VLAN différentes, j'ai constaté qu'un switch possédant une révision plus élevée peut influencer la synchronisation du domaine VTP. C'est cette observation qui m'a amené à considérer l'intégration d'un nouveau switch comme une étape qui doit être **vérifiée avant d'être connectée**, et non comme une simple opération de câblage.

> **Avant d'intégrer, je vérifie. Avant de modifier, je comprends.**

Ce laboratoire reproduit un comportement historique de VTP dans un environnement Packet Tracer contrôlé. Dans une infrastructure moderne, il faut également évaluer si VTP est réellement adapté au besoin.