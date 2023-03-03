# GraphQL

> ❌ A travailler

> ✔️ Auto validation par l'étudiant

## 🎓 J'ai compris et je peux expliquer

- la différence entre REST et GraphQL ✔️
REST est une architecture d'API basée sur HTTP tandis que GraphQL est une technologie de requête et de manipulation de données.
- les besoins auxquels répond GraphQL ✔️
GraphQL permet aux clients de demander exactement les données dont ils ont besoin.
- la définition d'un schéma ✔️
Un schéma est une représentation structurée des types de données et des relations entre eux dans une API GraphQL.
- Query ✔️
C'est une requête GraphQL qui permet de récupérer des données à partir d'une API GraphQL.
- Mutation ✔️
C'est une opération de modification de données dans une API GraphQL, telle que la création, la mise à jour ou la suppression de données.
- Subscription ✔️
C'est une opération qui permet de recevoir des mises à jour en temps réel à partir d'une API GraphQL.

## 💻 J'utilise

### Un exemple personnel commenté ✔️

```javascript
// Requête de type Query qui récupère les données d'un blog en fonction de son slug.
export const GET_ONE_BLOG = gql`
  query GetBlog($slug: String!) {
    getBlog(slug: $slug) {
      id
      name
      description
      template
      slug
  }
`
// Requête de type Mutation qui crée un nouveau blog en envoyant les données de description, de nom et de modèle.
export const CREATE_BLOG = gql`
  mutation Mutation($description: String!, $name: String!, $template: Float!) {
    createBlog(description: $description, name: $name, template: $template) {
      name
      id
      slug
    }
  }
`
```
```javascript
export class BlogResolver {
  // Cette fonction permet de récupérer un blog en fournissant son slug
  @Query(() => Blog)
  async getBlog(@Arg('slug') slug: string): Promise<Blog> {
    try {
      // On cherche un blog qui a le même slug que celui fourni en argument
      const blog = await dataSource.manager.findOneOrFail(Blog, {
        where: {
          slug,
        }
      })
      // Si on trouve un blog correspondant, on le renvoie
      return blog
    } catch (error) {
      // Si une erreur survient, on la log et on renvoie une erreur générique
      console.error(error)
      throw new Error('Something went wrong')
    }
  }
  
  // Cette fonction permet de créer un nouveau blog
  @Authorized()
  @Mutation(() => Blog)
  async createBlog(
    @Ctx() context: { userFromToken: { userId: string; email: string } },
    @Arg('name') name: string,
    @Arg('description') description: string,
    @Arg('template', { nullable: true }) template?: number
  ): Promise<Blog> {
    try {
      // On récupère l'utilisateur à partir du token d'authentification
      const {
        userFromToken: { userId },
      } = context
      const user = await dataSource.manager.findOneOrFail(User, {
        where: { id: userId },
        relations: { blogs: true },
      })
      // On crée un nouveau blog avec les informations fournies en arguments
      const newBlog = new Blog()
      newBlog.name = name
      // On génère un slug unique pour le nouveau blog à partir de son nom
      const baseSlug = slugify(name, slugifyOptions)
      let newSlug = baseSlug
      let i = 0
      let blogExists = true
      // Tant qu'un blog existe déjà avec ce slug, on ajoute un suffixe numérique pour avoir un slug unique
      while (blogExists) {
        const dataSlug = await dataSource.manager.findOne(Blog, {
          where: { slug: newSlug },
        })
        if (dataSlug != null) {
          i++
          newSlug = `${baseSlug}_${i}`
        } else {
          blogExists = false
        }
      }
      newBlog.slug = newSlug
      newBlog.description = description
      newBlog.user = user
      newBlog.template = template ?? 1
      // On sauvegarde le nouveau blog dans la base de données
      const newBlogFromDb = await dataSource.manager.save(newBlog)
      // On met à jour la liste des blogs de l'utilisateur avec le nouveau blog créé
      if (user.blogs !== undefined && user.blogs.length > 0) {
        user.blogs = [...user.blogs, newBlogFromDb]
      } else {
        user.blogs = [newBlogFromDb]
      }
      // On sauvegarde également les modifications apportées à l'utilisateur
      await dataSource.manager.save(user)
      // On renvoie le nouveau blog créé
      return newBlogFromDb
    } catch (error) {
      // Si une erreur survient, on la log et on renvoie une erreur générique
      console.log(error)
      throw new Error('Something went wrong')
    }
  }
}
```

### Utilisation dans un projet ❌ / ✔️

[lien github](...)

Description :

### Utilisation en production si applicable❌ / ✔️

[lien du projet](...)

Description :

### Utilisation en environement professionnel ❌ / ✔️

Description :

## 🌐 J'utilise des ressources

### Titre

- lien
- description

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
