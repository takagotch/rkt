### rkt
---
https://github.com/rkt/rkt

```go
package main

import (
  "log"
  "net/http"
)

func main() {
  http.HandleFunc("/", func(w http.ResponseWriter, r *http.Request) {
    log.Printf("request from %v\n", r.RemoteAddr)
    w.Write([]byte("hello\n"))
  })
  log.Fatal(http.ListenAndServe(":5000", nil))
}
```

```
CGO_ENABLED=0 go build -ldflags '-extldflags "-static"'

go build -compiler gccgo -gccgoflags '-static'

file hello
ldd hello

rkt --insecure-options=image run hello-0.0.1-linux-amd64.aci
rkt list
curl 172.16.28.2:5000
```

```
```


