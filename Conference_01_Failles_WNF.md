# Conference Les entrailles du dispositif de notifications Windows (WNF)

Speakers : Alex Ionescu et Gabrielle Viala

WNF (Windows Notification Facility) est un système permet de gérer la distribution de notifications des évènements dans le système. Il fonctionne aussi bien dans l'espace kernel *(kernel mode)* que dans l'espace utilisateur a.k.a *userland*. WNF a été introduit avec W8
Son intérêt est de permettre une garantie de l'intégrité publisher/subscriber des évènements qu'il gère, par le kernel.
Le fonctionnement est simple : 
Une application va pouvoir s'inscrire (subscribe) à un certain type d'évènement (identifié par le StateName) et recevoir des notifications à chaque changement de son état.

Les évènements WNF sont désignés par des WNF States Names qui sont des nombres de 64 bits

On compte 4 types d'évènements :
- Well Known : créés par le kernel (les noms sont présents dans une dll)
- Permanent : subsiste au reboot
- Persistent : subsiste aux process
- Temporaire

Les évènements sont également limités à un Scope, défini à la création : 
- Process : restreint au processus spécifié
- Silo : L'ensemble des éléments appartenant au Silo
- Machine : l'ensemble de la machine.

La création de ces évènements peut-être explicite ou implicite, et chaque évènement est identifié par un ID unique.

Pour accéder à ces évènements, il existe une API bas niveau permettant aux publishers d'évènements de : 
- Register (créer un StateName)
- Update (publier un StateName)

et aux clients de :
- query (récupérer un évènement pour un consommateur)

Cette API bas niveau n'est censée être accessible qu'au kernel via ntdll, qui fournit une API plus haut-niveau via un système de callback.
