#Variables
GraphQL 拥有一级方法将动态值提取到查询之外，然后作为分离的字典传进去。这些动态值即称为**变量**。

使用变量之前，我们得做三件事：

1.  使用 `$variableName` 替代查询中的静态值。
2.  声明 `$variableName` 为查询接受的变量之一。
3.  将 `variableName: value` 通过传输专用（通常是 JSON）的分离的变量字典中。

全部做完之后就像这个样子：`
```graphql
# { "graphiql": true, "variables": { "episode": JEDI } }
query HeroNameAndFriends($episode: Episode) {
  hero(episode: $episode) {
    name
    friends {
      name
    }
  }
}

```

##### 变量定义（Variable definitions）
变量定义看上去像是上述查询中的 `($episode: Episode)`。其工作方式跟类型语言中函数的参数定义一样。它以列出所有变量，变量前缀必须为 `$`，后跟其类型，本例中为 `Episode`。

##### 默认变量（Default variables）
```graphql
query HeroNameAndFriends($episode: Episode = "JEDI") {

 hero(episode: $episode) {
  name
  friends {
    name
	}
 }
}
```