# Triple Dare CSS Off revisité avec SASS

## Setup

- IDE: **Visual Studio Code**
- nous allons installer et utiliser l'extension **Live Server**
- nous allons installer et utiliser l'extention **Live Sass Compliler**
- nous allons configurer **Live Sass Compliler**

## To do Step by Step

### Configurer **Live Sass Compliler**

Nous allons profiter de faqs pour ceci - [_How to config the settings in my project?_](https://ritwickdey.github.io/vscode-live-sass-compiler/docs/faqs.html)

### Partials

Nous allons profiter de la simplicité des "partials". Notre code css va être diviser en plusieurs parties (partials) et assemblé dans style.scss.

```bash
├── scss
│   ├── _base.scss
│   ├── _footer.scss
│   ├── _form.scss
│   ├── _functions.scss
│   ├── _header.scss
│   ├── _mixins.scss
│   ├── _normalize.scss
│   ├── _obstacles.scss
│   ├── _prizes.scss
│   ├── _settings.scss
│   └── style.scss
```

Les fichiers "patials" qui sont uniquement destinés à être importés, et non compilés seuls, commencent par \_. Ceci indique aux outils Sass de ne pas essayer de compiler ces fichiers par eux-mêmes.

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

Vous pouvez laisser le \_ lorsque vous importez un partiel.

```css
// ex.
@import "normalize";
```

**Nous allons apprendre** : qu'on peut diviser stylesheet en petit morceaux, et comments les assembler ensemble.

### Output CSS

Lier le fichier `.css` compilé dans le fichier `index.html`

Sass compiler (l'extension Live Sass Compiler dans notre cas) crée ou met à jours des fichiers css à chaque fois où nous enregistrons une modification dans des fichiers .scss

L'arborescence dépend de not réglages (fichier .vscode/settings.json).

```bash
├── css
│   ├── style.css
│   └── style.css.map
├── dist
│   └── css
│       ├── style.min.css
│       └── style.min.css.map
```

Les fichiers .map permettent aux DevTools de navigateur (ceux que nous activons via "Inspecter Elément") de faire le lien entre le code étant exécuté et les fichiers sources originaux.

Nous ne les incluons pas, mais il ne faut pas les supprimer pour autant. Le navigateur va les chercher et trouver lui même grâce à

```html
<link rel="stylesheet" href="dist/css/style.min.css" />
```

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

```
// .scss - ex.
nav {
  height: 3rem;
  ul {
    display: flex;
  }
  a {
    color: red;
    &:hover {
      color: green;
    }
  }
}
```

Créer un _mixin_ pour des grids d'obstacles

**Nous allons apprendre** : la syntaxe et fonctionnement de "nesting" ainsi que comment nous faciliter la vie en réutilisans css via @mixins.

### Footer

Media queries dans sass

```
// .scss - ex.
.container {
  width: 80%;
  @media (min-width:40em) {
    width: 50%;
  }
}
```

**Nous allons apprendre** : qu'avec sass on peut aussi ajouter des media queries par selecteur.
