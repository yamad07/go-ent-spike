# ent-gql-spike

entの自動生成機能を使ってAPIプラットフォームのプロトタイプを検証するためのレポジトリ。

# サーバーの起動
```shell
go run server.go
```

でGraphQLのサーバーが起動する。[https://localhost:8000](http://localhost:8080/)でGraphiQLにアクセスができるので、そこからQuery及びMutationを投げる。

以下でUserを作成できる。
```graphql
mutation CreateUser {
  createUser(input: {age: 10, name: "tanimura"}) {
    id
    age
  }
}
```

mutationを叩いた後、以下でUserを検索できる。mutationで作成したUserが返って来ればOK
```graphql
query SearchUser {
  users(where: {name: "tanimura"}) {
  	edges {
      node {
        id
        age
        name
      }
    }
	}
}
```
