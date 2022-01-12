#Mutations
REST 中，任何请求都可能最后导致一些服务端副作用，但是约定上建议不要使用 `GET` 请求来修改数据。GraphQL 也是类似 —— 技术上而言，任何查询都可以被实现为导致数据写入。然而，建一个约定来规范任何导致写入的操作都应该显式通过变更（mutation）来发送。
```graphql
mutation CreateReviewForEpisode($ep: Episode!, $review: ReviewInput!) {
  createReview(episode: $ep, review: $review) {
    stars
    commentary
  }
}

```
```json
# VARIABLES
{
  "ep": "JEDI",
  "review": {
    "stars": 5,
    "commentary": "This is a great movie!"
  }
}
```
```json
{
  "data": {
    "createReview": {
      "stars": 5,
      "commentary": "This is a great movie!"
    }
  }
}
```
注意 `createReview` 字段如何返回了新建的 review 的 `stars` 和 `commentary` 字段。这在变更已有数据时特别有用，例如，当一个字段自增的时候，我们可以在一个请求中变更并查询这个字段的新值。

你也可能注意到，这个例子中，我们传递的 `review` 变量并非标量。它是一个**输入对象类型**，一种特殊的对象类型，可以作为参数传递。你可以在 Schema 页面上了解到更多关于输入类型的信息。

##### 变更中的多个字段（Multiple fields in mutations）

一个变更也能包含多个字段，一如查询。查询和变更之间名称之外的一个重要区别是：

**查询字段时，是并行执行，而变更字段时，是线性执行，一个接着一个。**

这意味着如果我们一个请求中发送了两个 `incrementCredits` 变更，第一个保证在第二个之前执行，以确保我们不会出现竞态。