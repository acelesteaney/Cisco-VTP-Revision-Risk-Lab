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

<img width="476" height="180" alt="Capture d&#39;écran 2026-10-10 235957" src="https://github.com/user-attachments/assets/891fb9a9-de40-4e79-8d2b-22d29c903661" />

*La topologie montre les trois commutateurs du domaine initial et le commutateur entrant, laissé isolé avant les tests.*
