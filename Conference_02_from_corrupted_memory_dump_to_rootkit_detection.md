# Conférence From corrupted memory dump to rootkit detection

Speaker : Clément ROUAULT from ExaTrack

La conférence traçait l'historique de la création d'un outil permettant d'analyser la mémoire à la recherche de rootkits à partir d'un dump mémoire qui, par essence, est potentiellement corrompu.

Le dump mémoire sur un système en cours d'exécution pose un problème : Le dump mémoire n'est pas instantané et le système continue de vivre durant le laps de temps nécessaire à la capture. Il faudrait pouvoir procéder à un freeze du système (comme dans une VM) pour avoir une représentation fidèle de la mémoire.
La conséquence directe est que lors d'un dump de mémoire vive, on obtient presque tout le temps des doublons ou des informations manquantes.

...
Récupération du dump mémoire
Mapping mémoire virtuelle <> mémoire physique
Analyse des traces
...

Conclusion : Les rootkits (même modernes) peuvent être détectés assez simplement à partir d'un dump mémoire.

Référence : Windows Internals (v6 et v7)