# Titre de la compétence

> ❌ A travailler

> ✔️ Auto validation par l'étudiant

## 🎓 J'ai compris et je peux expliquer

- l'état (_state_) pour contrôler l'affichage d'un composant ✔️
- les composants enfants et les _props_ qu'on leur passe ✔️
- le déclenchement d'instructions en fonction des actions de l'utilisateur ✔️
- le déclenchement d'instructions en fonction de l'étape du cycle de vie du composant ou du changement de valeur de ses props  ✔️
- l'usage d'un reducer (_useReducer_) pour gérer un état composé dans un composant  ✔️
- l'état stocké dans un composant avec un _context provider_ et accessible dans ses descendants via `useContext` ✔️

## 💻 J'utilise

### Un exemple personnel commenté ✔️

// Création du context qui contiendra l'état de cartList et ses méthodes de changement d'état                  
const CartContext = createContext(null);

// Valeur initiale de cartList
const initialCart = products.map((fruit) => ({ ...fruit, quantity: 0 }));

// Création du reducer. En fonction du type de l'action, on return un état différent.
const reducer = (state = initialValue, action) => {
  const { fruit } = action.payload;
  switch (action.type) {
    case "add":
      const addedCart = state.map((el) =>
        el.name === fruit.name ? { ...el, quantity: el.quantity + 1 } : el
      );
      return addedCart;
    case "remove":
      const removedCart = state.map((el) => {
        if (el.name === fruit.name && el.quantity > 0) {
          return { ...el, quantity: el.quantity - 1 };
        }
        return el;
      });
      return removedCart;
    default:
      return state;
  }
};

const CartProvider = ({ children }) => {
// Déclaration du useReducer pour cartList. Son état actuel est cartList. Sa méthode de changement est dispatch.                         
  const [cartList, dispatch] = useReducer(reducer, initialCart);

  return (
  // On détermine à quelle composant fournir le context. Children symbolise les composants enfants qui pourront l'utiliser
    <CartContext.Provider value={{ cartList, dispatch }}>
      {children}
    </CartContext.Provider>
  );
};

### Utilisation dans un projet ❌ / ✔️

[lien github](...)

Description :

### Utilisation en production si applicable❌ / ✔️

[lien du projet](https://github.com/AnasMama/useReducer-workshop.git)

Description : Je l'ai mise en place pour un atelier à réaliser par des étudiants. Il s'agit de la gestion d'un panier avec useReducer et useContext comme on pourait en trouver sur un site d'e-commerce. La branche useReducer correspond au code complet.

### Utilisation en environement professionnel ❌ / ✔️

Description :

## 🌐 J'utilise des ressources

### Titre

- lien https://fr.reactjs.org/
- description Documentation officielle de la librairie React.

## 🚧 Je franchis les obstacles

### Point de blocage ❌ / ✔️

Description:

Plan d'action : (à valider par le formateur)

- action 1 ❌ / ✔️
- action 2 ❌ / ✔️
- ...

Résolution :

## 📽️ J'en fais la démonstration

- J'ai ecrit un [tutoriel](...) ❌ / ✔️
- J'ai fait une [présentation](...) ❌ / ✔️
