#Conference Introduction au Hardware

Franck (@Requiem_FR) / Ingénieur CERT Société Générale

Bloomberg Octobre 2018 : découverte sur Supermicro des implants chinois ==> fail, c'est faux. Démenti

Pourtant, de vrais attaques via implants hardware sont effectuées. 

Catalogue NSA : implants "Cottonmouth" créés par l'agence pour détourner des adaptateurs USB. Pilotables à distance, communications entre implants, etc...

Attaque Evil Maid : Supply Chain Attack. Remplacement du BIOS par un BIOS malveillant, en moins de 5 minutes. Coût inférieur à 400 dollars pour le matériel.

Ordinateurs censés être protégés par TBM Trusted Boot Module. Censé effectuer une signature du boot pour garantir l'intégrité. Cependant, failles d'implémentations détectés.

https://github.com/certsocietegenrale

Pourquoi l'analyse de malware et de matériel ?
	Explosion des IoT (Mirai/Hajime, Reaper, Satori, VPNFilter, etc...)
	Diversité des buts (DDoS, minage de monnaie, vol d'infos, rançon, etc...)
	Intérêt pour blue/red : récupération d'infos pour contrer, pour utiliser (découverte notamment de faiblesses de chiffrement sur les SSD), etc....

Exemples de malwares IoT:
	Mirai/Hajime
	Reaper
	Satori(cryptomining -> pas vraiment efficace sur de l'IoT)
	VPN Filter 

A quoi on peut s'attendre:
	Beaucoup de docs (manuels, docs d'archi, etc...)
	Etudes / attaques / PoC déja fait
	Se salir les mains
		Désassembler les devices
		Souder / Désouder

Process basique
	Inspection externe
	Inspection interne
	Identification des interfaces de com
	Connection aux interfaces de com
	Interactions avec le matériel

Regarder plusieurs choses:
	Récupérer tous les FCC ID disponibles sur le matériel. Récupération des photos internes via le site du FCC pour identifier les matériaux intéressants sans ouvrir le matériel
	Identifier les composants de base (résistance, condensateur, etc...)
	Types de mémoires : RAM, Mémoires non volatiles (disques dur, NOR / NAND flash, Mémoire flash)
	Package de composants (TSOP, SOIC, etc...)
	Chercher les interfaces de communication UART (généralement présent partout). 4 types habituellement là.
	Chercher les unités basiques dans le système avec multimètre (GND, TX, etc...) à différents moments (boot, utilisation, etc...)
	SPI : Serial Peirpheral Interface. Utilisé pour communications entre composants. 4 fils à surveiller. Si le nom est présent, récupération de la data sheet possible.
	Récupération des données possibles via des chips pirates pour lire les mémoires internes.
	I2C : autre norme utilisée.
	JTAG : Utilisée pour lire la mémoire des téléphones. Similaire à SPI.

Matériel nécessaire
	Multi-mètre
	MINI-TS100
	Câbles
	Logical analyzer (visualisation des données numériques de manière intelligible)

Soudage / Désoudage
	Practice / Try and Die
	Utilisation de low-temp solder paste pour les travaux de précision

Hardware analysis: evil mouse
	Injection de WinInjector dans le matériel d'une souris. Capacité de prendre le contrôle à distance de la souris, de faire fuiter les données, etc...)
	Utilise deux puces pour séparer les données. Possibilité de récupérer ces données également.

Hardware analysis : Skimmer
	Dongle Bluetooth utilisé par les Skimmer. Utilise les mots de passe par défaut pour détourner les dongles.

Meilleur moyen de progresser : Casser des trucs
