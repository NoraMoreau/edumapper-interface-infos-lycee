# edumapper-interface-infos-lyc-e
Test FullStack edumapper ; interface d'enregistrement d'informations sur le lycée d'où vient le futur étudiant

# Edumapper Interface - Informations Lycée

## Description

Edumapper est une application **Vue 3 / Nuxt** permettant de sélectionner un lycée, une classe, le type de bac et de visualiser certaines informations associées. 

Fonctionnalités principales :

- Sélection automatique d’un lycée **au hasard** au premier chargement.
- Recherche d’un lycée par nom.
- Affichage des informations du lycée : nom, ville et statut (public / privé).
- Sélection de la **classe** (Seconde, Première, Terminale).
- Sélection du **type de bac** (Général, Technologique, Professionnel).

---

## Structure du projet


- **lycee.vue** : Affiche le lycée sélectionné, permet de modifier le lycée et choisir classe + type de bac.
- **selection-lycee.vue** : Permet de rechercher un lycée par nom et de le sélectionner.
- **list-lycee.js** : Contient la liste des lycées sous forme de tableau avec `id`, `name`, `ville` et `statut`.

---

## Installation et utilisation

1. Cloner le dépôt :  

```bash
git clone https://github.com/NoraMoreau/edumapper-interface-infos-lycee.git
cd edumapper-interface-infos-lycee/frontend
```

2. Installer les dépendances : 

```bash
npm install
```

3. Lancer le projet en local :
```bash
npm run dev
```

4. Ouvrir le projet dans le navigateur : 
```bash
http://localhost:3000
```

## Technologie utilisée
-Vue
-Nuxt
-Tailwind CSS



