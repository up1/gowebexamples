+++
weight = 7
title = "Static Files"
description = "This example will show how to serve static files like CSS or JS from a specific directory using the http.FileServer in the Go programming language."
+++

# [Go Web Examples:](/) Static Files

This example will show how to serve static files like CSSs, JavaScripts or images from a specific directory.

``` go
// static-files.go
package main

import "net/http"

func main() {
	fs := http.FileServer(http.Dir("assets/"))
	http.Handle("/static/", http.StripPrefix("/static/", fs))

	http.ListenAndServe(":8080", nil)
}
```
``` console
$ tree assets/
assets/
└── css
    └── styles.css
```
``` console
$ go run static-files.go

$ curl -s http://localhost:8080/static/css/styles.css
body {
    background-color: black;
}
```
