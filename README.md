# MessagePack encoding for Golang

[![Build Status](https://travis-ci.org/vmihailenco/msgpack.svg)](https://travis-ci.org/vmihailenco/msgpack)
[![PkgGoDev](https://pkg.go.dev/badge/github.com/vmihailenco/msgpack/v5)](https://pkg.go.dev/github.com/vmihailenco/msgpack/v5)
[![Documentation](https://img.shields.io/badge/pg-documentation-informational)](https://msgpack.uptrace.dev/)
[![Chat](https://discordapp.com/api/guilds/752070105847955518/widget.png)](https://discord.gg/rWtp5Aj)

> :heart: [**Uptrace.dev** - distributed traces, logs, and errors in one place](https://uptrace.dev)

- Join [Discord](https://discord.gg/rWtp5Aj) to ask questions.
- [Documentation](https://msgpack.uptrace.dev)
- [Reference](https://pkg.go.dev/github.com/vmihailenco/msgpack/v5)
- [Examples](https://pkg.go.dev/github.com/vmihailenco/msgpack/v5#pkg-examples)

## Features

- Primitives, arrays, maps, structs, time.Time and interface{}.
- Appengine \*datastore.Key and datastore.Cursor.
- [CustomEncoder](https://pkg.go.dev/github.com/vmihailenco/msgpack/v5#example-CustomEncoder)/CustomDecoder
  interfaces for custom encoding.
- [Extensions](https://pkg.go.dev/github.com/vmihailenco/msgpack/v5#example-RegisterExt) to encode
  type information.
- Renaming fields via `msgpack:"my_field_name"` and alias via `msgpack:"alias:another_name"`.
- Omitting individual empty fields via `msgpack:",omitempty"` tag or all
  [empty fields in a struct](https://pkg.go.dev/github.com/vmihailenco/msgpack/v5#example-Marshal--OmitEmpty).
- [Map keys sorting](https://pkg.go.dev/github.com/vmihailenco/msgpack/v5#Encoder.SortMapKeys).
- Encoding/decoding all
  [structs as arrays](https://pkg.go.dev/github.com/vmihailenco/msgpack/v5#Encoder.UseArrayForStructs)
  or
  [individual structs](https://pkg.go.dev/github.com/vmihailenco/msgpack/v5#example-Marshal--AsArray).
- [Encoder.UseJSONTag](https://pkg.go.dev/github.com/vmihailenco/msgpack/v5#Encoder.UseJSONTag) with
  [Decoder.UseJSONTag](https://pkg.go.dev/github.com/vmihailenco/msgpack/v5#Decoder.UseJSONTag) can
  turn msgpack into drop-in replacement for JSON.
- Simple but very fast and efficient
  [queries](https://pkg.go.dev/github.com/vmihailenco/msgpack/v5#example-Decoder-Query).

API docs: https://pkg.go.dev/github.com/vmihailenco/msgpack/v5. Examples:
https://pkg.go.dev/github.com/vmihailenco/msgpack/v5#pkg-examples.

## Installation

This project uses [Go Modules](https://github.com/golang/go/wiki/Modules) and semantic import
versioning since v4:

```shell
go mod init github.com/my/repo
go get github.com/vmihailenco/msgpack/v5
```

## Quickstart

```go
import "github.com/vmihailenco/msgpack/v5"

func ExampleMarshal() {
    type Item struct {
        Foo string
    }

    b, err := msgpack.Marshal(&Item{Foo: "bar"})
    if err != nil {
        panic(err)
    }

    var item Item
    err = msgpack.Unmarshal(b, &item)
    if err != nil {
        panic(err)
    }
    fmt.Println(item.Foo)
    // Output: bar
}
```

## See also

- [Fast and flexible HTTP router](https://github.com/vmihailenco/treemux)
- [Golang PostgreSQL ORM](https://github.com/go-pg/pg)
- [Golang message task queue](https://github.com/vmihailenco/taskq)
