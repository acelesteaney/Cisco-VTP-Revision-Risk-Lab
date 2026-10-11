# Topologie

Pour ce laboratoire, j'ai volontairement construit une petite infrastructure de **quatre commutateurs** afin de pouvoir isoler un équipement expérimental et observer son intégration dans un domaine VTP existant.

| Équipement | Rôle dans le laboratoire |
|---|---|
| ACANEY-SW-VTP-SERVER | Serveur VTP |
| ACANEY-SW-VTP-CLIENT-1 | Client VTP |
| ACANEY-SW-VTP-CLIENT-2 | Client VTP |
| ACANEY-SW-VTP-CLIENT-OTHER | Commutateur expérimental / entrant |

Le quatrième commutateur est volontairement séparé au début de l'expérimentation. Cette séparation m'a permis de préparer le scénario à risque, puis de reprendre le même principe avec une procédure d'intégration contrôlée.

## Topologie initiale

![Topologie initiale du laboratoire VTP](../tests/screenshots/topology-initial.png)

*La topologie montre les trois commutateurs du domaine initial et le commutateur entrant, laissé isolé avant les tests.*