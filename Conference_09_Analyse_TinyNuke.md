# Conférence Analyse TinyNuke

Speaker : Nha-Khanh Nguyen

Setup du Lab de Malware
	Host: Debian
	VM : Windows, bridgé et infecté

TinyNuke
	Trojan bancaire
	Identifié en mars 2017
	Jeune Français cherche à vendre un malware sur darkWeb
	Bypass tous les antivirus soi-disant. Pris pour un scammer, banni des forums du dark.
	Publie le code sur Github sur son repos perso mais public pour se venger. Plein de forks émergent.

	Malware effectue du phishing mail écrit en très bon français. Demande à télécharger un .zip.
	Contient un doc Excel, contenant des macros VB
	Extraction de la macro via des outils 
	Code obfusqué, pas trouvé d'outils permettant de tout désobfusquer.
	Replace execute() par MsgBox() normalement. Mais obfusqué également.
	Etude du code pendant 1 heure, avant de print une variable contenant une payload contenant un lancement powershell.exe lançant le download d'un exe malveillant.

	IDA sur .exe malveillant. 
	Run de l'exe ==> Crash. Anti-debug ?
	Techniques anti-VM et anti-debug. Anti-debug implémenté ici.
	Utilisation des breakpoints pour contourner les mesures. Utilisation des flags de lancement de programme pour lancer le programme malveillant lancé et le suspendre.

	Récupération du process en mémoire.
	Utilisation de procmon pour observer les fichiers et dossiers créés et utilisés.
		Des fichiers se démarquent : une image troll et des exe de Firefox, vieilles versions.
	Lancement du firefox.exe en mode suspendu
		Chargement des librairies 
		Charge un fichier spécifique contenant une DLL malveillante. Firefox charge automatiquement ce fichier au démarrage, et cette vulnérabilité n'a pas été dévoilée car Firefox a retiré la feature dans les versions d'après, et la vuln n'a donc pas eu de CVE
		Que fait la DLL ? Cherche les paramètres système, et vérifie que la langue chargée est française.
		XOR de la clé
		Déploiement de la persistence (création d'un dossier dans lequel il s'installe et crée un lien vers le firefox vérolé dans le menu de démarrage)
		Mise en place d'un mutex pour éviter de réinfecter un ordinateur déja infecté.
		Démarre un nouveau firefox
		Crée un nouveau process WinInet via DllHost.exe
		Check la version de l'OS pour télécharger la bonne configuration
		Initie la connexion au CNC (URL hardcodée)
		Reçoit les informations du CNC (chiffrées) et les mets en mémoire pour déchiffrer via XOR avec clé Hardcodée
		Une fois la configuration reçue, crée un nouveau DLLHost.exe en mode suspendu avec la nouvelle configuration.
		Lance des injections dans les pages Web pour injecter des keyloggers et faire fuiter les informations

Vague de malware calmée actuellement
