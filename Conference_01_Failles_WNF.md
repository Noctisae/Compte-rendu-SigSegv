# Conference Les entrailles du dispositif de notifications Windows (WNF)

Speakers : Alex Ionescu et Gabrielle Viala

WNF - système d'évènements auxquels les process vont subscribe

Les évènements WNF sont désignés par des WNF States Names qui sont des nombres de 64 bits

	4 Types :
		- Well Known : créés par le kernel (les noms sont présents dans une dll)
		- Permanent : subsiste au reboot
		- Persistent : subsiste aux process
		- Temporaire

	Différents scopes (session, process, ...)

	La création peut-être explicite ou implicite
