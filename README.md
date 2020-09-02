你好！
很冒昧用这样的方式来和你沟通，如有打扰请忽略我的提交哈。我是光年实验室（gnlab.com）的HR，在招Golang开发工程师，我们是一个技术型团队，技术氛围非常好。全职和兼职都可以，不过最好是全职，工作地点杭州。
我们公司是做流量增长的，Golang负责开发SAAS平台的应用，我们做的很多应用是全新的，工作非常有挑战也很有意思，是国内很多大厂的顾问。
如果有兴趣的话加我微信：13515810775  ，也可以访问 https://gnlab.com/，联系客服转发给HR。
<img src="docs/guide/.vuepress/public/super-graph.png" width="250" />

### Build web products faster. Secure high performance GraphQL

[![GoDoc](https://img.shields.io/badge/godoc-reference-5272B4.svg)](https://pkg.go.dev/github.com/dosco/super-graph/core?tab=doc)
![Apache 2.0](https://img.shields.io/github/license/dosco/super-graph.svg?style=flat-square)
![Docker build](https://img.shields.io/docker/cloud/build/dosco/super-graph.svg?style=flat-square)
![Cloud native](https://img.shields.io/badge/cloud--native-enabled-blue.svg?style=flat-squareg)
[![Discord Chat](https://img.shields.io/discord/628796009539043348.svg)](https://discord.gg/6pSWCTZ)  

## What's Super Graph?

Designed to 100x your developer productivity. Super Graph will instantly and without you writing code provide you a high performance GraphQL API for Postgres DB. GraphQL queries are compiled into a single fast SQL query. Super Graph is a GO library and a service, use it in your own code or run it as a seperate service.

## Using it as a service

```console
git clone https://github.com/dosco/super-graph 
cd ./super-graph
make install

super-graph new <app_name>
```

## Using it in your own code

```golang
package main

import (
  "database/sql"
  "fmt"
  "time"
  "github.com/dosco/super-graph/core"
  _ "github.com/jackc/pgx/v4/stdlib"
)

func main() {
  db, err := sql.Open("pgx", "postgres://postgrs:@localhost:5432/example_db")
  if err != nil {
    log.Fatalf(err)
  }

  conf, err := core.ReadInConfig("./config/dev.yml")
  if err != nil {
    log.Fatalf(err)
  }

  sg, err = core.NewSuperGraph(conf, db)
  if err != nil {
    log.Fatalf(err)
  }

  query := `
    query {
      posts {
      id
      title
    }
  }`

  res, err := sg.GraphQL(context.Background(), query, nil)
  if err != nil {
    log.Fatalf(err)
  }

  fmt.Println(string(res.Data))
}
```

## About Super Graph

After working on several products through my career I find that we spend way too much time on building API backends. Most APIs also require constant updating, this costs real time and money.
            
It's always the same thing, figure out what the UI needs then build an endpoint for it. Most API code involves struggling with an ORM to query a database and mangle the data into a shape that the UI expects to see.

I didn't want to write this code anymore, I wanted the computer to do it. Enter GraphQL, to me it sounded great, but it still required me to write all the same database query code.

Having worked with compilers before I saw this as a compiler problem. Why not build a compiler that converts GraphQL to highly efficient SQL.

This compiler is what sits at the heart of Super Graph with layers of useful functionality around it like authentication, remote joins, rails integration, database migrations and everything else needed for you to build production ready apps with it.

## Features

- Complex nested queries and mutations
- Auto learns database tables and relationships
- Role and Attribute based access control
- Opaque cursor based efficient pagination
- Full text search and aggregations
- JWT tokens supported (Auth0, etc)
- Join database queries with remote REST APIs
- Also works with existing Ruby-On-Rails apps
- Rails authentication supported (Redis, Memcache, Cookie)
- A simple config file
- High performance GO codebase
- Tiny docker image and low memory requirements
- Fuzz tested for security
- Database migrations tool
- Database seeding tool
- Works with Postgres and YugabyteDB


## Documentation

[supergraph.dev](https://supergraph.dev)

## Contact me

I'm happy to help you deploy Super Graph so feel free to reach out over
Twitter or Discord.

[twitter/dosco](https://twitter.com/dosco)

[chat/super-graph](https://discord.gg/6pSWCTZ)

## License

[Apache Public License 2.0](https://opensource.org/licenses/Apache-2.0)

Copyright (c) 2019-present Vikram Rangnekar


