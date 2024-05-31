
# Site de Recettes

Bienvenue sur le site de recettes utilisant Hugo et le thème Anubis2.

## Prérequis

- [Hugo](https://gohugo.io/getting-started/installing/)

## Installation

### Cloner le dépôt

```sh
git clone https://github.com/antoinegreuzard/recette.git
cd recette
```

### Ajouter le thème Anubis2

```sh
git submodule add https://github.com/Junyi-99/hugo-theme-anubis2 themes/anubis2
```

### Configurer le site

Ouvrez le fichier `config.toml` et ajoutez ou modifiez les paramètres suivants :

```toml
baseURL = "https://votre-site.com"
languageCode = "fr-fr"
title = "Site de Recettes"
theme = "anubis2"
summaryLength = 70
enableRobotsTXT = true
defaultContentLanguage = "fr"
paginate = 10

[params]
  description = "Un site de recettes pour tous les gourmands"
  author = "Votre Nom"
  showDate = true

[menu]
  [[menu.main]]
    identifier = "recettes"
    name = "Recettes"
    url = "/recettes/"
    weight = 1
```

### Créer le contenu

#### Créer le dossier des recettes

```sh
mkdir -p content/recettes
```

#### Ajouter une recette

Créez un fichier `content/recettes/exemple-de-recette.md` avec le contenu suivant :

```markdown
---
title: "Exemple de Recette"
date: 2023-05-31T00:00:00Z
draft: false
tags: ["dessert", "chocolat"]
categories: ["Desserts"]
ingredients:
  - 100g de sucre
  - 200g de chocolat
  - 3 œufs
steps:
  - Préchauffez le four à 180°C.
  - Faites fondre le chocolat au bain-marie.
  - Mélangez tous les ingrédients.
  - Versez dans un moule et enfournez pendant 20 minutes.
---

# Introduction

Cette recette de gâteau au chocolat est parfaite pour toutes les occasions.
```

### Personnaliser les modèles

Créez un fichier `layouts/recettes/single.html` avec le contenu suivant :

```html
{{ define "main" }}
<article>
  <h1>{{ .Title }}</h1>
  <p>{{ .Date }}</p>
  <div>
    <h2>Ingrédients</h2>
    <ul>
      {{ range .Params.ingredients }}
      <li>{{ . }}</li>
      {{ end }}
    </ul>
  </div>
  <div>
    <h2>Étapes</h2>
    <ol>
      {{ range .Params.steps }}
      <li>{{ . }}</li>
      {{ end }}
    </ol>
  </div>
  <div>
    {{ .Content }}
  </div>
</article>
{{ end }}
```

### Lancer le site

Pour construire le site et lancer un serveur de développement, exécutez :

```sh
hugo server
```

Le site sera disponible à l'adresse `http://localhost:1313`.

## Déploiement

Pour déployer le site, construisez les fichiers statiques :

```sh
hugo
```

Les fichiers seront générés dans le dossier `public` et peuvent être déployés sur n'importe quel service d'hébergement de sites statiques.

## Contributions

Les contributions sont les bienvenues ! Veuillez ouvrir une issue ou soumettre une pull request pour toute suggestion ou amélioration.

## Licence

Ce projet est sous licence MIT. Voir le fichier [LICENSE](LICENSE) pour plus de détails.
