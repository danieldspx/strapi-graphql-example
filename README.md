
# Reproducing the bug

    npm install
    npm run develop
Open the GraphQL playground at `http://localhost:1337/graphql`

We have the following relationships:
Pages `hasMany` Sections
Sections `hasMany` Articles

So if we query something like:

```
query {
  pages {
    sections {
      articles {
        description
      }
    }
  }
}
```
Since this is a 3 level nested query, this will give us the following error:

> Your filters contain a field 'undefined' that doesn't appear on your
> model definition nor it's relations

A workaround is to change the relationship from `hasMany` to `manyToMany` but this is not the ideal scenario, although it solves our problem temporarily.
