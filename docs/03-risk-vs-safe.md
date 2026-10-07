# 03 — Ce que l'expérimentation m'a appris

## Deux scénarios, une même question

J'ai volontairement réalisé deux intégrations différentes avec le même objectif : comprendre ce qui change lorsque l'état du switch entrant est contrôlé avant son raccordement.

| | Intégration risquée | Intégration maîtrisée |
|---|---|---|
| État du switch entrant | Révision supérieure / base VLAN différente | Ancienne base supprimée |
| Domaine initial | Révision 8 / 9 VLANs | Révision 8 / 9 VLANs |
| Avant raccordement | État non neutralisé | État vérifié et nettoyé |
| Résultat observé | Révision 9 / 14 VLANs | Révision 8 / 9 VLANs |
| Approche | Synchronisation non maîtrisée | Intégration contrôlée |

## Mon constat

Le premier scénario m'a permis de voir le problème se produire. Le second m'a permis de comprendre comment éviter de reproduire cette situation.

Avant ce lab, la Configuration Revision pouvait facilement être comprise comme une simple information affichée par show vtp status. Après cette manipulation, je la considère plutôt comme **une information opérationnelle à vérifier avant l'intégration d'un équipement**.

J'ai également retenu qu'un équipement réseau ne doit pas être considéré comme « neutre » simplement parce qu'il vient d'être ajouté à une topologie. Il peut conserver un état provenant d'un environnement précédent et cet état peut avoir des conséquences sur le réseau auquel il est raccordé.

## Ce que ce lab démontre

À travers cette expérimentation, j'ai travaillé sur l'identification d'un risque de configuration, l'analyse de la Configuration Revision, la synchronisation d'une base VLAN avec VTP, l'observation de l'impact sur les clients, la préparation d'un équipement avant intégration et la vérification de l'état final.

## Leçon clé

**Ne pas seulement savoir configurer un protocole : savoir vérifier l'état d'un équipement avant de l'introduire dans une infrastructure.**

C'est finalement la partie que je retiens le plus de ce laboratoire : la compétence réseau ne consiste pas uniquement à connaître les commandes, mais aussi à comprendre **ce que l'équipement possède déjà, ce qu'il va annoncer au réseau et quelles conséquences son intégration peut produire**.

> **Avant d'intégrer, je vérifie. Avant de modifier, je comprends.**