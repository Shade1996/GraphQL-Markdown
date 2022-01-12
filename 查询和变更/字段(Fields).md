#Fields
查询和其结果拥有几乎一样的结构。这是 GraphQL 最重要的特性，因为这样一来，你就总是能得到你想要的数据，而服务器也准确地知道客户端请求的字段。
```graphql
{
  hero {
    name
    # 查询可以有备注！
    friends {
      name
    }
  }
}
```
```json
{
  "data": {
    "hero": {
      "name": "R2-D2",
      "friends": [
        {
          "name": "Luke Skywalker"
        },
        {
          "name": "Han Solo"
        },
        {
          "name": "Leia Organa"
        }
      ]
    }
  }
}
```