#Directives

我们用了 GraphQL 中一种称作**指令**的新特性。一个指令可以附着在字段或者片段包含的字段上，然后以任何服务端期待的方式来改变查询的执行。GraphQL 的核心规范包含两个指令，其必须被任何规范兼容的 GraphQL 服务器实现所支持：

-   `@include(if: Boolean)` 仅在参数为 `true` 时，包含此字段。
-   `@skip(if: Boolean)` 如果参数为 `true`，跳过此字段。

指令在你不得不通过字符串操作来增减查询的字段时解救你。服务端实现也可以定义新的指令来添加新的特性。
```graphql
query Hero($episode: Episode, $withFriends: Boolean!) {
  hero(episode: $episode) {
    name
    friends @include(if: $withFriends) {
      name
    }
  }
}
```
```json
#Variables 
{
  "episode": "JEDI",
  "withFriends": false
}
```