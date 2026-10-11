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
<img width="476" height="180" alt="Capture d&#39;écran 2026-10-10 235957" src="https://github.com/user-attachments/assets/12b86cbb-cfe8-4c59-8b60-aba2025d15ae" />

### État initial du domaine VTP
<img width="404" height="194" alt="SERVER-Init - Copie" src="https://github.com/user-attachments/assets/8b444bdf-39c4-4a55-977c-5e53930c5069" />

### Préparation du commutateur à révision supérieure
<img width="386" height="173" alt="Other-Init" src="https://github.com/user-attachments/assets/995ee907-701a-4ed1-a0e8-92eb050596bb" />

### Établissement du trunk
<img width="422" height="175" alt="Topologie" src="https://github.com/user-attachments/assets/484f1343-f96c-4fe5-853d-03cab398f7af" />

### Synchronisation VTP après intégration
<img width="390" height="193" alt="Capture d&#39;écran 2026-10-11 005741" src="https://github.com/user-attachments/assets/a7a9f701-e390-47a3-8609-add02db47214" />

### Propagation vers les clients
<img width="390" height="193" alt="Capture d&#39;écran 2026-10-11 005741" src="https://github.com/user-attachments/assets/5becef26-f920-4757-8863-1f687313c9dd" />

### État final après l'intégration à risque
<img width="448" height="249" alt="Capture d&#39;écran 2026-10-11 012646" src="https://github.com/user-attachments/assets/850510b8-e454-420c-83e3-e0202afe7214" />

## Ce que j'ai constaté

Le résultat m'a permis de comprendre concrètement que la Configuration Revision joue un rôle déterminant dans la synchronisation VTP. Le problème n'est donc pas simplement qu'un switch possède « plus de VLANs », mais qu'il arrive avec une base VLAN considérée comme plus récente par VTP.

Cette expérience m'a surtout montré pourquoi **l'état d'un switch entrant doit être vérifié avant son raccordement à un domaine VTP existant**.
