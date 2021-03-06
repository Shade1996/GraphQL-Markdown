##### 对象类型和字段（Object Types and Fields）

```graphql
type Character {
  name: String!
  appearsIn: [Episode!]!
}
```

-   `Character` 是一个 **GraphQL 对象类型**，表示其是一个拥有一些字段的类型。你的 schema 中的大多数类型都会是对象类型。
-   `name` 和 `appearsIn` 是 `Character` 类型上的**字段**。这意味着在一个操作 `Character` 类型的 GraphQL 查询中的任何部分，都只能出现 `name` 和 `appearsIn` 字段。
-   `String` 是内置的**标量**类型之一 —— 标量类型是解析到单个标量对象的类型，无法在查询中对它进行次级选择。后面我们将细述标量类型。
-   `String!` 表示这个字段是**非空的**，GraphQL 服务保证当你查询这个字段后总会给你返回一个值。在类型语言里面，我们用一个感叹号来表示这个特性。
-   `[Episode!]!` 表示一个 `Episode` **数组**。因为它也是**非空的**，所以当你查询 `appearsIn` 字段的时候，你也总能得到一个数组（零个或者多个元素）。且由于 `Episode!` 也是**非空的**，你总是可以预期到数组中的每个项目都是一个 `Episode` 对象。

现在你知道一个 GraphQL 对象类型看上去是怎样，也知道如何阅读基础的 GraphQL 类型语言了。