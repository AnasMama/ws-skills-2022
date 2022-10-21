# TypeScript

> ❌ A travailler

> ✔️ Auto validation par l'étudiant

## 🎓 J'ai compris et je peux expliquer

- l'intéret de TypeScript dans l'IDE ✔️ Debug plus simple.
- les types de bases ✔️ 
- comment et pourquoi étendre une interface ✔️ Récupérer des propriétés d'une interface pour les utiliser sur une autre.
- les classes et les decorators ✔️ Décorateur : Affecte la classe qui le suit afin de lui ajouter des opérations. 

## 💻 J'utilise

### Un exemple personnel commenté ✔️
// Interface d'un message
interface Message {
  author: string;
  sentAt: string;
  message: string;
}

// Extension de l'interface Message avec la propriété unread en plus
interface MessageWithUnread extends Message {
  unread: boolean;
}

// Interface des activités entrées
interface Activities { lastActivityDatetime: string, messages: Message[] }

const activities: Activities = {
    lastActivityDatetime: '2020-11-09T10:11:32.093Z', // JSON datetime/ISO8601
    messages: [
        { author: 'Thibault', sentAt: '2020-11-07T11:11:32.093Z', message: "Hello there" },
        { author: 'Joseph', sentAt: '2020-11-08T10:15:32.093Z', message: "Hi!" },
        { author: 'Thibault', sentAt: '2020-11-08T21:13:43.093Z', message: "What's up?" },
        { author: 'Thibault', sentAt: '2020-11-09T11:11:22.093Z', message: "Heoh" },
        { author: 'Joseph', sentAt: '2020-11-10T14:15:32.093Z', message: "Yeah sorry" },
        { author: 'Joseph', sentAt: '2020-11-10T10:23:32.093Z', message: "Hi" },
        { author: 'Thibault', sentAt: '2020-11-05T18:12:32.093Z', message: "Welcome in the new channel" },
    ]
   }

// Fonction qui nous permet de trier les messages en fonction de leur propriété sentAt (le plus ancien en premier) et les modifier en ajoutant une propriété "non lu" (booléen signifiant que l'utilisateur actuel n'a pas lu ce message) basé sur le lastActivityDatetime saisir.
function displayMessage({
  lastActivityDatetime,
  messages,
}: Activities): MessageWithUnread[] {
  return messages.map((message) => {
    const unread = message.sentAt <= lastActivityDatetime ? false : true;
    return { ...message, unread: unread };
  }).sort((prev, next) => {
    if (prev.sentAt < next.sentAt) return -1
    if (prev.sentAt > next.sentAt) return 1
    return 0;
  });
};

console.log(displayMessage(activities))
//[
//     {
//         "author": "Thibault",
//         "sentAt": "2020-11-05T18:12:32.093Z",
//         "message": "Welcome in the new channel",
//         "unread": false
//     },
//     {
//         "author": "Thibault",
//         "sentAt": "2020-11-07T11:11:32.093Z",
//         "message": "Hello there",
//         "unread": false
//     },
//     {
//         "author": "Joseph",
//         "sentAt": "2020-11-08T10:15:32.093Z",
//         "message": "Hi!",
//         "unread": false
//     },
//     {
//         "author": "Thibault",
//         "sentAt": "2020-11-08T21:13:43.093Z",
//         "message": "What's up?",
//         "unread": false
//     },
//     {
//         "author": "Thibault",
//         "sentAt": "2020-11-09T11:11:22.093Z",
//         "message": "Heoh",
//         "unread": true
//     },
//     {
//         "author": "Joseph",
//         "sentAt": "2020-11-10T10:23:32.093Z",
//         "message": "Hi",
//         "unread": true
//     },
//     {
//         "author": "Joseph",
//         "sentAt": "2020-11-10T14:15:32.093Z",
//         "message": "Yeah sorry",
//         "unread": true
//     }
// ]

### Utilisation dans un projet ✔️

[lien github]https://github.com/AnasMama/lyrics-guesser-backend.git

Description : Backend réalisé avec typescript et express.

### Utilisation en production si applicable ✔️

[lien du projet](...)

Description :

### Utilisation en environement professionnel ✔️

Description : En entreprise, j'utilise typescript avec svelte.

## 🌐 J'utilise des ressources

### Titre

- lien
- https://www.typescriptlang.org/
- description
- Doc officielle de typescript.

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
