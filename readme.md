# Projet Data & IA - Prevision de la demande de velos en libre service

## Apercu
Ce projet repond au sujet d'evaluation Data/IA avec un cas concret: **predire la demande horaire de velos en libre service** a partir de donnees Open Data.

Le travail principal est dans le notebook:
- `Projet_Demande_Velos_Libre_Service.ipynb`

Le projet suit les etapes obligatoires demandees:
1. Definition du probleme
2. Collecte/comprehension des donnees
3. Nettoyage/pretraitement
4. EDA
5. Modelisation (2 modeles minimum)
6. Interpretation/explicabilite
7. Conclusion

---

## Structure du dossier

```text
Evaluation/
├─ 14-Hackathon/
│  ├─ 01_Courses_usagers/
│  │  ├─ 2023_02/All_data_courses.csv
│  │  ├─ 2023_06/All_data_courses_usagers_06_2023.csv
│  │  └─ Descriptif_courses_usagers.txt
│  ├─ 02_Historique_remplissage_stations/
│  │  ├─ 2023_02/All_data_remplissage.csv
│  │  └─ Descriptif_historique_remplissage_stations.txt
│  └─ ... (autres dossiers non utilises directement dans ce notebook)
├─ Projet_Demande_Velos_Libre_Service.ipynb
├─ Sujet - Evaluation Projet Data.ipynb
└─ readme.md
```

---

## Objectif metier
Anticiper la demande de courses par heure pour:
- limiter les stations vides/pleines,
- aider le reequilibrage de flotte,
- ameliorer l'experience usager.

### Variable cible
- `demand`: nombre de courses agregees par heure.

---

## Donnees utilisees

### Sources principales
- `14-Hackathon/01_Courses_usagers/2023_02/All_data_courses.csv`
- `14-Hackathon/01_Courses_usagers/2023_06/All_data_courses_usagers_06_2023.csv`

### Source contextuelle
- `14-Hackathon/02_Historique_remplissage_stations/2023_02/All_data_remplissage.csv`

### Point technique important
Les fichiers n'ont pas tous le meme separateur CSV (`;` et `,`).
Le notebook gere ce cas automatiquement via une lecture robuste.

---

## Environnement et prerequis

### Version Python recommandee
- Python 3.10+ (3.11 ok)

### Librairies
- `pandas`
- `numpy`
- `matplotlib`
- `seaborn`
- `scikit-learn`

Installation rapide:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn jupyter
```

---

## Comment executer le projet

1. Ouvrir un terminal dans le dossier `Evaluation`.
2. Lancer Jupyter:

```bash
jupyter notebook
```

3. Ouvrir `Projet_Demande_Velos_Libre_Service.ipynb`.
4. Executer les cellules dans l'ordre (**Run All** recommande).

> Le notebook contient une cellule `%pip install ...` commentee si besoin.

---

## Methodologie (resume)

### 1) Preparation des donnees
- chargement des CSV,
- harmonisation des colonnes,
- conversion des types (dates/numeriques),
- suppression des incoherences (duree <= 0, valeurs aberrantes, doublons).

### 2) Feature engineering
- variables temporelles: mois, jour, jour de semaine, heure,
- indicateur week-end,
- variables cycliques (`sin/cos`),
- variables de retard: `lag_1`, `lag_24`.

### 3) EDA
- evolution temporelle de la demande,
- profil moyen par heure,
- comparaison semaine vs week-end,
- matrice de correlation.

### 4) Modelisation
Deux modeles testes:
- `RandomForestRegressor`
- `GradientBoostingRegressor`

Evaluation:
- split temporel train/test (80/20),
- validation croisee temporelle (`TimeSeriesSplit`),
- metriques: `MAE`, `RMSE`, `R2`.

---

## Resultats attendus dans le notebook
- un tableau comparatif des performances des modeles,
- un graphe reel vs prediction sur le jeu de test,
- les importances de variables du meilleur modele,
- une interpretation des limites et pistes d'amelioration.

---

## Livrables inclus
- `Projet_Demande_Velos_Libre_Service.ipynb`: livrable principal (code + explications + graphiques),
- `Texte.md`: script de presentation orale par partie,
- `readme.md`: documentation projet (ce fichier).

---

## Conseils pour la soutenance orale
- suivre la structure 1 a 7 du notebook,
- expliquer les choix methodologiques (pas seulement les chiffres),
- commenter les graphiques clefs (pics horaires, semaine/week-end),
- justifier le meilleur modele avec les metriques.

Tu peux t'appuyer sur `Texte.md` comme trame de presentation.

---

## Limites connues
- seulement deux mois de donnees (fevrier et juin 2023),
- variables exogenes absentes (meteo, jours feries, evenements),
- possibles incoherences capteurs dans les donnees brutes.

---

## Pistes d'amelioration
- ajouter meteo/calendrier,
- predire la demande **par station** (niveau local),
- tester des modeles specialises serie temporelle (XGBoost/LightGBM/Prophet).

---

## Depannage rapide

### Erreur `ModuleNotFoundError: No module named 'pandas'`
Installer les dependances:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn
```

### Erreur de lecture CSV
Verifier que:
- les fichiers existent aux chemins indiqués,
- le notebook est lance depuis le dossier `Evaluation`.

### Graphiques qui ne s'affichent pas
Dans Jupyter, executer les cellules dans l'ordre depuis le debut.

---

## Auteur
Projet realise pour l'evaluation Data/IA (demande de velos en libre service).

(Tu peux ajouter ici les noms/prenoms du groupe.)
