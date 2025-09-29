La taxonomie de Flynn est la classification des architectures d'ordinateur proposée en 196..

Catégories définies selon le type d'organisation du flux de données et du flux d'instructions :

-  **SISD** (single instruction single data)    <-- Aucun paralléllisme
	Ordinateur séquentiel, qui n'exploite aucun parallélisme
	-  Ni au niveau des instructions
	-  Ni au niveau de la mémoire
	Cela correspond à l'architecture de non Neumann
-  **SIMD** (single instruction multiple data)    
	Ordinateur utilisant du parallélisme au niveau de la mémoire
	-  Les instructions SIMD sont souvent utilisés dans les calculs vectoriels (processeurs vectoriel)
-  **MISD** (multiple instructions single data) <-- ^-- v--- Parallélisme
	La même donnée est traitée par plusieurs unités de calcul en parallèle
	Peu utilisée
	-  Filtrage numérique ou vérification de redondance dans les systèmes critiques
-  **MIMD** (multiple instructions multiple data)
	Parallèle au niveau de la mémoire et instructions, plusieurs unités de calcul traitent des données différentes (possédant leur mémoire distincte)
	-  Architecture parallèle la plus élaborée et la plus utilisée
	-  MIMD à mémoire partagée
	-  MIMD à mémoire distribuée

![[Pasted image 20250929093035.png]]