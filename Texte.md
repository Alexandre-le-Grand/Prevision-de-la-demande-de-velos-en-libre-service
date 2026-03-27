# Script de Présentation Orale : Prévision de la Demande de Vélos (VLS)

### Partie 1 - Définition du problème
"Dans cette première partie, j'ai posé le contexte métier : un service de vélos en libre-service doit anticiper la demande pour éviter les stations vides ou pleines. Mon objectif est de prédire le nombre de courses par heure. La variable cible est donc la demande horaire. Mes hypothèses de départ sont que la demande varie selon l'heure, le jour, le week-end et la période."

### Partie 2 - Collecte et compréhension des données
"J'ai utilisé les données du dossier 14-Hackathon, principalement les courses usagers de février et juin 2023. J'ai aussi chargé l'historique de remplissage des stations pour contextualiser la qualité des données. J'ai vérifié la présence des fichiers et la structure des colonnes. Un point technique important : les fichiers n'ont pas tous le même séparateur, donc j'ai intégré une lecture robuste pour gérer les deux formats."

### Partie 3 - Nettoyage et prétraitement
"Ensuite, j'ai converti les dates et les variables numériques, puis j'ai traité les incohérences : valeurs manquantes critiques, doublons, durées négatives ou nulles, et vitesses aberrantes. L'idée est de conserver un jeu de données propre et fiable avant de modéliser. J'ai aussi créé des variables temporelles utiles pour la prédiction, comme l'heure, le jour de semaine et des variables de retard (lags)."

### Partie 4 - EDA (Analyse exploratoire)
"Pendant l'analyse exploratoire, j'ai observé la dynamique de la demande dans le temps et les profils horaires. Les visualisations montrent des variations nettes selon les moments de la journée et des différences entre semaine et week-end. J'ai aussi utilisé une matrice de corrélation pour identifier les variables les plus liées à la demande. Cette étape confirme que la temporalité est centrale dans ce problème."

### Partie 5 - Modélisation
"Pour la modélisation, j'ai comparé deux approches : **Random Forest** et **Gradient Boosting**. J'ai fait un découpage temporel train/test pour respecter la logique d'une série temporelle, et j'ai complété avec une validation croisée adaptée. J'ai évalué les modèles avec la MAE, la RMSE et le R². Le meilleur modèle est retenu sur des critères objectifs de performance."

### Partie 6 - Interprétation et explicabilité
"L'interprétation montre que les variables temporelles et les lags ont un poids important dans la prédiction. Cela veut dire que la demande dépend à la fois du cycle journalier et de l'inertie récente. J'ai aussi présenté les limites : période d'observation courte et absence de variables externes comme la météo ou les événements. Enfin, j'ai proposé des pistes d'amélioration pour aller plus loin."

### Partie 7 - Conclusion
"En conclusion, le projet montre qu'on peut construire une prédiction utile de la demande horaire avec une méthode structurée et reproductible. Ce travail peut aider à la décision pour mieux rééquilibrer les stations. La suite logique est d'enrichir les données et de passer à une prédiction plus fine par station pour gagner en précision opérationnelle."