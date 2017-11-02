# issue-1095
example for https://github.com/graphcool/framework/issues/1095

## Instructions

https://api.graph.cool/simple/v1/cj9ijnp421xj90124j6f09gyo

Note these work:

```graphql
query a {
  allPosts {
    id
    title
  }
}

query b {
  allUsers {
    name
  }
}
```

And these show permission errors as expected:

```graphql
query c {
  allUsers {
    id # permission error as expected
  }
}

query d {
  allPosts {
    id # data is returned
    title # data is returned
    author {
      id # permission error as expected
      name # data is returend
    }
  }
}
```

according to this permission in `graphcool.yml`:

```yml
permissions:
  - operation: User.read
    fields: [name]
```
