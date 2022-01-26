GraphQL 对象类型上的每一个字段都可能有零个或者多个参数，例如下面的 `length` 字段：

```graphql
type Starship {
  id: ID!
  name: String!
  length(unit: LengthUnit = METER): Float
}
```

所有参数都是具名的，不像 JavaScript 或者 Python 之类的语言，函数接受一个有序参数列表，而在 GraphQL 中，所有参数必须具名传递。本例中，`length` 字段定义了一个参数，`unit`。

参数可能是必选或者可选的，当一个参数是可选的，我们可以定义一个**默认值** —— 如果 `unit` 参数没有传递，那么它将会被默认设置为 `METER`。