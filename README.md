# parallel-Mandelbrot
Virtualisation
Cette application permet d'afficher l'ensemble de Mandelbrot en utilisant Python, Taichi, numpy et Pygame.

Interface de l'utilisateur:

la fonction controle permet que l'utilisateur d'intéragir avec le serveur : 

flèche -> : augmenter le nombre d'itération max 

flèche <- : diminuer le nombre d'itération max

z : translation vers le haut

s : translation vers le bas 

q : translation vers la gauche 

d : translation vers la droite 


les packages utlisiées:

Taichi : est un langage spécifique à un domaine intégré à Python qui vous aide à écrire facilement des programmes parallèles performants.

Pygame : est une bibliothèque multiplateforme gratuite et open source pour le développement d'applications multimédias telles que des jeux vidéo utilisant Python. Il utilise la bibliothèque Simple DirectMedia Layer et plusieurs autres bibliothèques populaires pour résumer les fonctions les plus courantes, ce qui rend l'écriture de ces programmes plus intuitive. Dans ce projet, ça permet de fournir une interface graphique.

Numpy : est une bibliothèque pour le langage de programmation Python, ajoutant la prise en charge de grands tableaux et matrices multidimensionnels, ainsi qu'une grande collection de fonctions mathématiques de haut niveau pour opérer sur ces tableaux.


Taichi computing:

Concu pour exploiter le parallélisme (automatique/manuelle) dans les GPU et les processeurs multicœurs CPU.

Complier en Just In Time  Compiler (JIT) en binary executable kernels.

Prend en charge plusieurs backends, y compris les processeurs x64 et ARM, CUDA, Vulkan, Metal et OpenGL Compute Shaders ;





Technique de parallélisation automatique : 

1-Parse

Il s'agit de la première étape où l'analyseur lira les fichiers source d'entrée pour identifier toutes les utilisations statiques et externes. Chaque ligne du fichier sera comparée à des modèles prédéfinis pour les séparer en jetons. Ces jetons seront stockés dans un fichier qui sera utilisé ultérieurement par le moteur de grammaire. Le moteur de grammaire vérifiera les modèles de jetons qui correspondent aux règles prédéfinies pour identifier les variables, les boucles, les instructions de contrôle, les fonctions, etc. dans le code.

2-Analyser

L'analyseur est utilisé pour identifier les sections de code qui peuvent être exécutées simultanément. L'analyseur utilise les informations de données statiques fournies par le scanner-parser. L'analyseur trouvera d'abord toutes les fonctions totalement indépendantes et les marquera comme des tâches individuelles. L'analyseur trouve alors quelles tâches ont des dépendances.

3-scheduler 

Le planificateur listera toutes les tâches et leurs dépendances les unes par rapport aux autres en termes d'exécution et d'heures de début. L'ordonnanceur produira l'ordonnancement optimal en termes de nombre de processeurs à utiliser ou de temps d'exécution total de l'application.

4-Génération de codes

Le planificateur générera une liste de toutes les tâches et les détails des cœurs sur lesquels elles s'exécuteront, ainsi que la durée pendant laquelle elles s'exécuteront. Le générateur de code insérera des constructions spéciales dans le code qui seront lues lors de l'exécution par le planificateur. Ces constructions indiqueront au planificateur sur quel noyau une tâche particulière sera exécutée avec les heures de début et de fin.


Il est imporant de préciser que il y'a 2 grandes méthodes dans la parallélisation automatique, multi-threading en pipeline et Multi-threading cyclique. Par exemple, considérons une boucle qui, à chaque itération, applique une centaine d'opérations et s'exécute pendant mille itérations. Cela peut être considéré comme une grille de 100 colonnes sur 1 000 lignes, soit un total de 100 000 opérations. Le multithreading cyclique affecte chaque ligne à un thread différent. Le multi-threading pipeline affecte chaque colonne à un thread différent.

le Multi-threading cyclique est déployé dans ce projet vu que la suite de Mandelbrote est dépendante de l'expression précédante or que l'ensemble des points complexes C sont indépendants.


