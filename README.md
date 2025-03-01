es-wrk
===


[![Build Status](http://img.shields.io/travis/rayyildiz/es-wrk.svg?style=flat-square)](https://travis-ci.org/rayyildiz/es-wrk)
[![Build status](https://ci.appveyor.com/api/projects/status/ak03giji8xyeqco4?svg=true)](https://ci.appveyor.com/project/rayyildiz/es-wrk)
[![Go Report Card](https://goreportcard.com/badge/github.com/rayyildiz/es-wrk)](https://goreportcard.com/report/github.com/rayyildiz/es-wrk)
[![FOSSA Status](https://app.fossa.io/api/projects/git%2Bgithub.com%2Frayyildiz%2Fes-wrk.svg?type=shield)](https://app.fossa.io/projects/git%2Bgithub.com%2Frayyildiz%2Fes-wrk?ref=badge_shield)

ES-WRK is a dummy data generator for [elastic search](https://github.com/elastic/elasticsearch). 


Installation
---

To install this package, you need to install [Go](https://golang.org/dl/) and [setup your Go workspace](https://golang.org/doc/install) on your computer. Then install the library is to run:

```bash
$ go get github.com/rayyildiz/es-wrk
```

Getting Started
---

Define your model as below. Don't forget the use [json tag](https://golang.org/pkg/encoding/json/#Marshal).
```go
type Book struct {
	ID            string `json:"id"`
	ISBN          string `json:"isbn"`
	Title         string `json:"title"`
	Author        string `json:"author"`
	PostDate      string `json:"postDate"`
	CurrentStatus int    `json:"currentStatus"`
	IsPublished   bool   `json:"isPublished"`
}
```

Then start worker as below. `es-wrk` creates random data and insert into the elasticsearch. 

```go
import "github.com/rayyildiz/es-wrk/worker"

wrk, err := worker.NewWorker(elasticURL, elasticUsername, elasticPassword, reflect.TypeOf(Book{}))
if err != nil {
    panic("[ERROR] could not created worker")
}

wrk.Start(20000)
```


TODO
---

- [ ] Nested object
- [ ] Multi worker support

## License
[![FOSSA Status](https://app.fossa.io/api/projects/git%2Bgithub.com%2Frayyildiz%2Fes-wrk.svg?type=large)](https://app.fossa.io/projects/git%2Bgithub.com%2Frayyildiz%2Fes-wrk?ref=badge_large)