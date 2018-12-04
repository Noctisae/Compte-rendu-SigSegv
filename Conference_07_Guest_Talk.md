# Conference Guest Talk

Retours d'expérience sur le Digital Forensic

	SWAT Cyber

		Task force lors de cyberattaques
		N'importe où et le plus rapidement possible
		Collecter les preuves sans les altérer
		Gérer le client (la victime) et ses différentes entités (direction, service technique, etc...)
			Eviter les restaurations immédiates de VM (pertes de traces et non effectif car les logiciels malveillants sont déja installés)
			Recréer une zone saine en isolant physiquement les machines infectées
			Au fur et à mesure des investigations, rétablir progressivement les services après désactivation des éléments malveillants
			Prendre en compte les méthodes de travail et les rediriger vers de bons comportements sans les brusquer
		Collecte de traces et de preuves
			Noter toutes les actions effectuées pour réduire les traces laissées sur le système
			Souvent plusieurs entrées et sorties mises en place pour réduire la traçabilité
			Traces à récupérer : comptes créés, les IP, etc... (pour vérification au niveau du groupe de l'entreprise visé)
			récupérer toutes les dates pour déterminer de grosses timelines d'attaques
		Créer une équipe avec multiples talents
			Pentesters
			Architectes
			etc...
			But : trouver comment les attaquants sont rentrés	

	Approche globale d'une investigation numérique

		"Interviewer" les personnes affectés au fur et à mesure pour écouter les versions et les visions
		Essayer de prendre en compte le maximum de choses
		Récupération de toutes les preuves (logs, disques durs, dump mémoires). 
		Travail sur les profils utilisateurs en priorité (car porte d'entrée principale sur le poste).
		Penser à vérifier les traces sur le SI du groupe pour investigation globale 
		Penser à adapter l'investigation rapidement selon les analyses effectuées pour repérer les choses les plus graves au sein du SI
		Investigations discrètes nécessaires parfois (investigation étatique, investigation grand groupe ne devant pas subir d'interruptions de service)
		Repartir en conseillant des contre-mesures contre les scénarios identifiés

	Scénarios et traces laissées par criminels

		But premier : comprendre le but des attaquants concernant l'attaque pour orienter les investigations 
		Scénarios classiques : 
			prises de contrôle postes et serveurs pour chiffrement des données et rançon
			prises de contrôle postes utilisateurs pour détournement AD
			prises de contrôle postes pour monter des tunnels pour effectuer des fuites d'informations
			phishing pour détournement de fonds
		Retrouver des traces d'outils (scanner, crackeur, etc...), des comptes, des répertoires partagés, des programmes spéciaux à but particulier (blocage antivirus), etc...
		
