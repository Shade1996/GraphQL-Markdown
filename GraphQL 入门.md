##### GraphQL 是一个用于 API 的查询语言，是一个使用基于类型系统来执行查询的服务端运行时（类型系统由你的数据定义）。GraphQL 并没有和任何特定数据库或者存储引擎绑定，而是依靠你现有的代码和数据支撑。

```graphql
type Query {

 me: User

}

type User {

 id: ID

 name: String

}
```
```graphql
{

 me {

 name

 }

}
```
```json
{

 "me": {

 "name": "Luke Skywalker"

 }

}
```
[[查询和变更]]
[[Schema和类型]]
