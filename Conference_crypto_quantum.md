# Conference Reversing cryptographic primitives using quantum computing

Speaker : Renaud Lifchitz, Pentester & sécurité protocolaire 

Introduire des résultats pratiques avec la crypto et la quantique

Principes quantiques basiques

	Les objets petits (microscopiques et nanos) agissent aussi bien comme particles que comme ondes 
	Leurs propriétés dépendent de la façon dont on les mesurent (mesure comme onde = onde, mesure comme particule = particule)
	Une particule quantique possède toutes ses caractèristiques physiques à la fois à la naissance (peut être +, peut être -, etc... Cela ne devient vrai qu'à la mesure de ladite particule)
	Qubit : 0 et 1 == |0} et |1}
	Base à deux dimensions : |0} = |1/0|
	Vecteur colonne avec deux nombres complexes ou 3 nombres réels
	Valeur 0 = axe vertical vers le bas, valeur 1 = axe vertical vers le bas
	Bases des portes quantiques
		Superposition perdue si mesure effectuée (détermine alors la valeur, et empêche la superposition quantique)
		Environnement de calcul totalement isolé (pas de perturbations externes, ni d'échappatoires vers l'extérieur, pas d'échanges d'énergie)
		Principe thermodynamique : pas d'énergie échangée == opérations sans énergie
		Toutes les opérations doivent être parfaitement réversibles (pas d'énergie changée, donc opération réversible)
		Typiquement, opération ET pas réversible, mais opération NOT réversible
	Porte de Pauli-X = équivalent de la porte NOT
	Porte d'Hadamard = place qubit en état de superposition, est son propre inverse
	Porte CNOT = ET réversible, deux bits en sortie (un bit de controle et un bit de valeur, si bit de controle à 1, opération NOT sur bit de valeur)
	Porte SWAP = Echange les deux qubits d'entrée
	Ces portes permettent de retrouver les tables booléennes
	Portes universelles = ensemble de portes permettant de recréer les tables booléennes
	Opérations complexes : Ajouter 1 (prévoir retenue qubits), multiplier par x2 (décaler les têtes de lecture plutôt que shifter les qubits)
	Isolement parfait n'existent pas en pratique. Donc erreurs de calcul de temps en temps. D'où utilisation de codes correcteurs d'erreurs pour obtenir un résultat fiable (si possible)
	Limitation : profondeur du circuit, car chaque opération porte une probabilité d'erreur. Donc la multiplication des portes rend le résultat faux.


Simulateurs de computing quantiques

	Quantum Inspire
	Quirk
	Quantum Circuit Simulator sur Android
	Simulateurs de circuits quantiques 
	Syndrome du fantôme ou intrication : porte d'Hadamard : fait en sorte que les deux qubits aient la même valeur, qu'elle soit 0 ou 1. Or, tant qu'ils ne sont pas mesurés, ils valent techniquement les deux valeurs. Déclencher la mesure de l'un des qubits détermine la valeur du second, même à deux côtés opposés de l'univers.

Systèmes en Cloud quantique
	Bristol University
	Alibaba (11 Qubits)
	IBM (le plus user-friendly, jusqu'à 14 qubits)
	Rigeti (19 qubits, 128 pour les payants)
	D-Wave (Canada, décriée car puces avec beaucoup de qubits, mais toutes les opérations ne sont pas possibles dessus. Utilisée dans les problèmes d'optimisation)
	
Lien avec la cryptographie
	Etude d'une PBOX (primitive crypto effectuant une permutation sur un ensemble de bits)
	Décomposer la permutation en permutations simples (à deux éléments)
	Permutations = porte SWAP
	Porte SWAP équivalent 3 portes CNOT tête-bêche
	Réverser tout le circuit avec ces portes
	Simplifier le circuit après

	2 moyens de reverse une primitive crypto

		Implémenter un circuit réversible et l'exécuter à l'envers (algorithme avec uniquement des opérations réversibles)
		Mathématiquement certaines fonctions ou opérations ne sont pas réversibles
		Trick : Rajout de qubits en entrée ou en sortie pour envelopper la fonction non réversible pour al rendre réversible
		Les qubits sont toujours présents à la fin, mais peuvent ne pas être utilisés
		Si les qubits temporaires sont très peu nombreux, il y a très peu de résultats à chercher par rapport au résultat (2 qubits temporaires = 4 circuits à tester)

		Oracle de Grover : Algorithme spécifiquement quantique permettant de trouver l'entrée en racine de n opérations (par rapport aux algos classiques qui seraient plutôt en n2)
		
		Application de CRC-8
			Implementation de CRC-8 naïve
			Avec uniquement des portes CNOT
			8 qubits d'entrée et 8 qubits temporaires 
			Pas optimisé
			Fabrication d'une table de vérité de la fonction (entrées /sorties) pour créer une fonction booléenne en la simplifiant
			Utilisation du framework revkit permettant de trouver 
			Reverse de l'algorithme CRC-8 avec uniquement 12 portes CNOT
			Mise de la sortie de CRC-8 dans l'algorithme = retrouver l'entrée du CRC
			Dans simulation parfaite = 100% OK
			Avec bruit = 92% OK, quelques valeurs parasites

Démo en ligne sur IBM
	Lancement du programme 1024 fois pour bypass les erreurs dû à l'environnement non parfait

	Utilisation de 3 portes d'Hadamard en entrée avant les portes CNOT = Calcul parallèle de 8 CRC d'un coup

AES S-box modélisation et implémentation
	S-Box : substitution des bits par d'autres
	Reverse AES S-Box : Circuit optimum nécessite au moins 14 portes optimisé (au moins 281 portes dans le modèle basique présenté)

Reverse XOR avec Oracle de Grover
	Message en ASCII non étendu : bit de poids fort à 0. Utilisation d'Oracle de Grover pour faire tous les déchiffrements en parallèle. Si tous les bits de poids forts sont à 0, on retrouve principalement des caractères ASCII

Menaces
	Oracle de Grover : Capable de péter les chiffrements symétriques en divisant par deux la complexité (AES-128 bits => 64 bits de complex en quantique)
	Conséquences : doublement des tailles de clés symétriques pour rester hors de portée des attaques quantiques

	Asymétrique: Doubler taille de clé => Suffit de doubler la taille du circuit pour casser l'algorithme. CASSE BY DESIGN AVEC LE QUANTIQUE !

	Algorithmes post-quantum en remplacement des algorithmes asymétriques. Nombres de qubits en augmentation exponentielle, qui devrait permettre de bientôt casser le RSA ou l'AES.

	Cryptos résistantes :
		NTRU : algo de chiffrement + signature. Résiste actuellement aux attaques, pas nécessairement ad vitam eternam.
