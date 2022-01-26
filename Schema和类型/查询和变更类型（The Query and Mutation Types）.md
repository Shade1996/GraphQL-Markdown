一个 schema 内有两个特殊类型：
```graphql
schema {
  query: Query
  mutation: Mutation
}
```
每一个 GraphQL 服务都有一个 `query` 类型，可能有一个 `mutation` 类型。这两个类型和常规对象类型无差，但是它们之所以特殊，是因为它们定义了每一个 GraphQL 查询的**入口**。
```graphql
type Query {
  hero(episode: Episode): Character
  droid(id: ID!): Droid
}
```
