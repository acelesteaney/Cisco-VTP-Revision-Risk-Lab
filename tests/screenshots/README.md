# Captures d'écran

Ce dossier regroupe les preuves visuelles utilisées dans la documentation du laboratoire. Les premières captures ont été préparées ; les suivantes pourront être ajoutées au fur et à mesure des scénarios.

## Topologie et état initial

- `topology-initial.png` — topologie Packet Tracer avec le commutateur entrant isolé.
- `initial-server.png` — sortie de `show vtp status` sur le serveur : domaine `ACANEY-VTP`, 9 VLANs, révision 8.
- `initial-client1.png` — sortie de `show vtp status` sur le client 1 : mode Client, 9 VLANs, révision 8 ; le MD5 correspond à celui du serveur.
- `initial-client2.png` — sortie de `show vtp status` sur le client 2.

## Scénario à risque

- `risky-other-before.png` — état VTP du commutateur entrant avant raccordement.
- `risky-vlans-before.png` — base VLAN du commutateur entrant avant raccordement.
- `risky-trunk.png` — état du trunk après raccordement.
- `risky-server-after.png` — état VTP du serveur après synchronisation.
- `risky-client-after.png` — état VTP d'un client après synchronisation.
- `risky-other-after.png` — état VTP du commutateur entrant après synchronisation.

## Scénario sécurisé

- `safe-other-before.png` — état initial du commutateur entrant.
- `safe-reset.png` — procédure de nettoyage, si cette capture est disponible.
- `safe-clean-state.png` — vérification de l'état propre avant intégration.
- `safe-trunk.png` — état du trunk après raccordement contrôlé.
- `safe-server-final.png` — état VTP final du serveur.
- `safe-client-final.png` — état VTP final d'un client.
- `safe-other-final.png` — état VTP final du commutateur entrant.

Chaque capture doit illustrer une étape réellement effectuée et correspondre aux résultats décrits dans les documents du laboratoire.