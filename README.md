# parallel-Mandelbrot
Virtualisation


Technique de parallélisation automatique

1-Parse

Il s'agit de la première étape où l'analyseur lira les fichiers source d'entrée pour identifier toutes les utilisations statiques et externes. Chaque ligne du fichier sera comparée à des modèles prédéfinis pour les séparer en jetons. Ces jetons seront stockés dans un fichier qui sera utilisé ultérieurement par le moteur de grammaire. Le moteur de grammaire vérifiera les modèles de jetons qui correspondent aux règles prédéfinies pour identifier les variables, les boucles, les instructions de contrôle, les fonctions, etc. dans le code.

2-Analyser

L'analyseur est utilisé pour identifier les sections de code qui peuvent être exécutées simultanément. L'analyseur utilise les informations de données statiques fournies par le scanner-parser. L'analyseur trouvera d'abord toutes les fonctions totalement indépendantes et les marquera comme des tâches individuelles. L'analyseur trouve alors quelles tâches ont des dépendances.

3-scheduler 

Le planificateur listera toutes les tâches et leurs dépendances les unes par rapport aux autres en termes d'exécution et d'heures de début. L'ordonnanceur produira l'ordonnancement optimal en termes de nombre de processeurs à utiliser ou de temps d'exécution total de l'application.

4-Génération de codes

Le planificateur générera une liste de toutes les tâches et les détails des cœurs sur lesquels elles s'exécuteront, ainsi que la durée pendant laquelle elles s'exécuteront. Le générateur de code insérera des constructions spéciales dans le code qui seront lues lors de l'exécution par le planificateur. Ces constructions indiqueront au planificateur sur quel noyau une tâche particulière sera exécutée avec les heures de début et de fin.
