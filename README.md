# SAE SQLLM — Interface d’interrogation d’une base de données en langage naturel

Projet réalisé dans le cadre de la SAE *Modélisation statistique pour les données complexes et le Big Data* — Université Lumière Lyon 2.

## Objectif du projet

L’objectif est de développer une interface capable de :

- comprendre une question en français,
- la traduire en requête SQL grâce à un LLM local,
- interroger une base SQLite,
- produire :
  - un tableau de résultats,
  - des statistiques descriptives,
  - des visualisations graphiques.

Exemple de question :

> "Afficher l’évolution des vols en Auvergne-Rhône-Alpes entre 2020 et 2023"

---

# Technologies utilisées

- Python
- Pandas
- SQLite
- Hugging Face Transformers
- TinyLlama / Phi-2
- Matplotlib
- Gradio
- Google Colab

---

# Architecture du projet

```text
Question utilisateur
        ↓
LLM local (Hugging Face)
        ↓
Génération SQL
        ↓
SQLite
        ↓
Résultats pandas
        ↓
Statistiques + graphiques
        ↓
Interface Gradio
```

---

# Structure du projet

```text
sql-natural-language-interface/
│
├── data/
│   └── donnees.csv
│
├── notebooks/
│   └── SAE_SQLLM.ipynb
│
├── src/
│   ├── database.py
│   ├── llm.py
│   ├── prompts.py
│   ├── visualization.py
│   └── app.py
│
├── requirements.txt
├── README.md
└── .gitignore
```

---

# Fonctionnalités

- Chargement des données CSV
- Création automatique d’une base SQLite
- Génération de requêtes SQL à partir du langage naturel
- Exécution des requêtes
- Affichage des résultats
- Génération de graphiques
- Interface utilisateur avec Gradio

---

# Modèles testés

Le projet compare plusieurs LLMs locaux :

- TinyLlama
- Phi-2

---

# Expérimentations de prompting

Trois stratégies de prompting sont étudiées :

- Zero-shot
- One-shot
- Few-shot

---

# Installation

## Cloner le dépôt

```bash
git clone https://github.com/votre-utilisateur/sql-natural-language-interface.git
cd sql-natural-language-interface
```

---

## Installer les dépendances

```bash
pip install -r requirements.txt
```

---

# Lancer le projet

```bash
python src/app.py
```

Ou ouvrir le notebook :

```text
notebooks/SAE_SQLLM.ipynb
```

---

# Exemple d’utilisation

Question :

```text
Quel est le nombre de cambriolages à Lyon en 2022 ?
```

SQL généré :

```sql
SELECT *
FROM crime
WHERE ville='Lyon'
AND annee=2022
AND type='Cambriolage'
```

---

# Résultats attendus

L’interface affiche :

- les données sélectionnées,
- les statistiques descriptives,
- les graphiques associés.

---

# Limites du projet

- Compréhension limitée du langage naturel
- SQL parfois incorrect selon le prompt utilisé
- Performance dépendante du LLM choisi

---

# Auteurs

- Muriel Rita ZOUZZOU
- [Nom des membres du groupe]

---

# Université

Université Lumière Lyon 2 — 2026
