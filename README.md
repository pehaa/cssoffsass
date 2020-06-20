# Triple Dare CSS Off revisité avec SASS

## Setup

- IDE: Visual Studio Code
- nous allons installer et utiliser l'extension **Live Server**
- nous allons installer et utiliser l'extention **Live Sass Compliler**
- nous allons [configurer](https://ritwickdey.github.io/vscode-live-sass-compiler/docs/faqs.html) **Live Sass Compliler**

## To do Step by Step

### Configurer **Live Sass Compliler**

### Partials

Incluer les fichiers "partials" dans `style.scss` respectons l'ordre.

- normalize
- settings
- functions
- mixins
- base
- header
- obstacles
- prizes
- form
- footer

```css
// ex.
@import "normalize";
```

**Nous allons apprendre** : qu'on peut diviser stylesheet en petit morceaux, et comments les assembler ensemble.

### Output CSS

Lier le fichier `.css` compilé dans le fichier `index.html`

### Normalize

Inclure normalize dans `scss/_normalize.scss`

**Nous allons apprendre** : on peut utiliser pur css dans un fichier .scss.

### Base

Mettre en place tous les styles de base, qui concernent tout le document.

Utiliser les variables sass définiés dans `scss/_settings.scss`

**Nous allons apprendre** : utiliser des variables.

### Functions

Mettre en place une fonction qui convertit pixels en rems.

**Nous allons apprendre** : comment nous faciliter la vie avec des fonctions.

### Header

Utiliser la fonction (built-in) `transparentize`

**Nous allons apprendre** : comment nous faciliter la vie avec des fonctions.

### Obstacles

Utiliser la technique de "nesting"

Créer un _mixin_ pour des grids d'obstacles

### Prizes

Media queries dans sass
