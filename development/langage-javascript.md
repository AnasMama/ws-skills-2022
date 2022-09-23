# Langage Javascript

> ❌ A travailler

> ✔️ Auto validation par l'étudiant

## 🎓 J'ai compris et je peux expliquer

- les `structures` de base du langage ✔️
- les normes `ecmascript` ✔️
- l'utilisation de l'`asynchrone` ✔️
- les spécifités du mot-clef `this` ✔️

## 💻 Je code en Javascript

### Un exemple de code commenté ❌ / ✔️

```javascript
const noAccent = (str: string) => {
// Variable regroupant tous les accents possibles en fonction de la lettre
  const accent = [
    /[\300-\306]/g,
    /[\340-\346]/g, // A, a
    /[\310-\313]/g,
    /[\350-\353]/g, // E, e
    /[\314-\317]/g,
    /[\354-\357]/g, // I, i
    /[\322-\330]/g,
    /[\362-\370]/g, // O, o
    /[\331-\334]/g,
    /[\371-\374]/g, // U, u
    /[\321]/g,
    /[\361]/g, // N, n
    /[\307]/g,
    /[\347]/g, // C, c
  ];
  // Lettres sans accent  
  const noaccent = ["A", "a", "E", "e", "I", "i", "O", "o", "U", "u", "N", "n", "C", "c"];
  // Pour chaque lettre de notre string, si elle appartient au tableau accent, on la remplace par son équivalence sans accent
  for (let i = 0; i < accent.length; i++) {
    str = str.replace(accent[i], noaccent[i]);
  }
  // On return la réponse en minuscule
  return str.toLowerCase();
};
```

### Utilisation dans un projet ✔️

[lien github](...)https://github.com/AnasMama/frontend-whats-the-movie.git

Description : J'ai utilisé cette algorithme pour la soumission des réponses d'un joueur. 

### J'ai utilisé ce langage en production ✔️

[lien du projet][(...)](https://github.com/AnasMama/lyrics-guesser-backend.git)

Description : Ce projet est un backend réalisé en TypeScript avec express suivant le modèle MVC. Le paradigme de programmation de ce backend est la programmation orienté objet. 

### J'ai utilisé ce langage en environement professionnel ✔️

Description : Je travaille actuellement avec le framework Svelte.

## 🌐 J'utilise des ressources
https://www.freecodecamp.org/news/search/?query=react
https://javascript.plainenglish.io/
https://developer.mozilla.org/fr/docs/Web/JavaScript

### Titre

- lien
- description

## 🚧 Je franchis les obstacles

### Point de blocage ✔️

Description:

Plan d'action : (à valider par le formateur)

- action 1 ❌ / ✔️
- action 2 ❌ / ✔️
- ...

Résolution :

## 📽️ J'en fais la démonstration

- J'ai ecrit un [tutoriel](...) ❌ / ✔️
- J'ai fait une [présentation](...) ❌ / ✔️

