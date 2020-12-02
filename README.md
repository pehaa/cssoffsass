# Triple Dare CSS Off revisité avec SASS

## Setup

- IDE: **Visual Studio Code**
- nous allons installer et utiliser l'extension **Live Server**
- nous allons installer et utiliser l'extention **Live Sass Compliler**
- nous allons configurer **Live Sass Compliler**

**Lien super utile** : [SassMeister - online compiler](https://www.sassmeister.com/)

## To do Step by Step

### Configurer **Live Sass Compliler**

Nous allons profiter de faqs pour ceci - [_How to config the settings in my project?_](https://ritwickdey.github.io/vscode-live-sass-compiler/docs/faqs.html)

**TO DO 👉** Configurer votre sass compiler

---

## Partials

**Nous allons apprendre** qu'on peut diviser stylesheet en petit morceaux, et comments les assembler.

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

Les fichiers "patials"  commencent par "\_" (*underscore*, tiret bas). Ceci indique aux outils Sass de ne pas essayer de compiler ces fichiers par eux-mêmes.

Vous pouvez ommettre le "\_" lorsque vous importez un partiel :

```css
@import "normalize";
```

et la façon plus concise de dire :

```css
@import "_normalize.scss";
```

**TO DO 👉** Inclure les fichier partials dans `style.scss` en respectant l'ordre comme ceci

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

---

## Output CSS

Le compilateur Sass (l'extension Live Sass Compiler dans notre cas) crée ou met à jours des fichiers css à chaque fois où nous enregistrons une modification dans un des fichiers `.scss`

L'arborescence où seront placés les fichiers générés dépend de not réglages (fichier `.vscode/settings.json`).

```bash
├── css
│   ├── style.css
│   └── style.css.map
├── dist
│   └── css
│       ├── style.min.css
│       └── style.min.css.map
```

Les fichiers `.map` permettent aux DevTools de navigateur de faire le lien entre le code étant exécuté et les fichiers sources originaux.

Nous ne les incluons pas, mais il ne faut pas les supprimer pour autant. Le navigateur va les chercher et trouver lui même grâce à la dernière ligne dans les fichier .css générés

```css
/*# sourceMappingURL=style.min.css.map */
```

```html
<!-- html -->
<link rel="stylesheet" href="dist/css/style.min.css" />
```

**Attention** Est-ce déjà clair que nous ne modifions pas de fichiers `.css` manuellement ? Si nous utilisons Sass dans le projet, c'est Sass qui se charge de la génération des fichiers `.css.` **Nous n'y touchons plus. ⛔️**

**TO DO 👉** Lier le fichier `.css` compilé dans le fichier `index.html`

---

## Normalize

**Nous allons apprendre** qu'on peut utiliser pur css dans un fichier .scss.

**TO DO 👉** Inclure normalize dans `scss/_normalize.scss`

---

## Base

**Nous allons apprendre** comment utiliser des variables sass.

**TO DO 👉** Mettre en place tous les styles de base, ceci dit des styles qui concernent tout le document. Utiliser les variables sass définiés dans `scss/_settings.scss`

** Exemple **

```css
/* scss */
$brand-color: red;
$base-spacing: 24px;

h1 {
  color: lighten($brand-color, 10%);
  margin-bottom: $base-spacing;
  padding: $base-spacing/2 $base-spacing/3;
}
```

est compilé vers :

```css
/* css */
h1 {
  color: #ff3333;
  margin-bottom: 24px;
  padding: 12px 8px;
}
```

---


## Functions

**Nous allons apprendre** comment nous faciliter la vie avec des fonctions.

```css
/* scss */
@function function-name($parameter1, $parameter2) {
  @return ....;
}
```

**TO DO 👉** Mettre en place une fonction qui convertit pixels en rems.

---


## Header

**Nous allons apprendre** comment nous faciliter la vie avec des fonctions de sass.

Sass vient avec un nombre de fonctions déjà prédéfinies, y compris quelques fonctions qui permettent de modifier des couleurs.

```css
/* scss */
nav {
  background: mix(red, yellow);
}

header {
  background: transparentize(red, 0.8);
}
```

est compilé vers

```css
/* css */
nav {
  background: #ff8000;
}
header {
  background: rgba(255, 0, 0, 0.2);
}
```

**TO DO 👉** Utiliser la fonction (built-in) `transparentize`

---

## Obstacles

**Nous allons apprendre** la syntaxe et fonctionnement de "nesting"

Voici comment fonctionne nesting (regardez bien la disposition des accolades dans le code ci-dessous).

Ce code en scss...

```scss
// .scss
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

...donne ceci, une fois compilé :

```css
/* css */
nav {
  height: 3rem;
}
nav ul {
  display: flex;
}
nav a {
  color: red;
}
nav a:hover {
  color: green;
}
```

Le symbole "&" peut être aussi utilisé comme ceci :

```scss
// .scss
.btn {
  &-small {
    padding: 0.5rem;
  }
  &-medium {
    padding: 1rem;
  }
  &-large {
    padding: 2rem;
  }
}
```

qui est compilé vers :

```css
/* .css */
.btn-small {
  padding: 0.5rem;
}
.btn-medium {
  padding: 1rem;
}
.btn-large {
  padding: 2rem;
}
```

**TO DO 👉** Utiliser la technique de "nesting"

## Mixins

**Nous allons apprendre** comment nous faciliter la vie en réutilisans css via `@mixins`.

On peur imaginer que *mixin* est un snippet de css qu'on peut utiliser dans plusieurs endroits pour ne pas se répéter.

La syntaxe est comme ceci :

```css
/* scss */
@mixin mixin-name {
  property1: value1;
  property2: value2;
}
```

exemple

```scss
/* scss */
@mixin topleft {
  position: absolute;
  top: 0;
  left: 0;
}

section {
  position: relative;
  .promo {
    @include topleft;
  }
}
```

donne

```css
/* css */
section {
  position: relative;
}
section .promo {
  position: absolute;
  top: 0;
  left: 0;
}
```

**TO DO 👉** Créer un _mixin_ pour des grids d'obstacles

## Footer - Media queries dans sass

**Nous allons apprendre** qu'avec sass on peut aussi ajouter des media queries par selecteur.

```scss
// .scss - ex.
.container {
  width: 80%;
  @media (min-width: 40em) {
    width: 50%;
  }
}
```

**TO DO 👉** Essayer vous-mêmes de mettre en place media queries de cette façon.
