Here is the implementation of creating a simple server:
```go
package server

type Server {
  host string
  port int
}

func New(host string, port int) *Server {
  return &Server{host, port}
}

func (s *Server) Start() error {
  // todo
}
```
And here's how client will use this package
```go
package main

import (
  "log"
  
  "github.com/acme/pkg/server"
)

func main() {
  svr := server.New("localhost", 1234)
  if err := svr.Start(); err != nil {
    log.Fatal(err)
  }
}
```

However the provided code is couldn't be extended and there will be problems with adding new features to the package since it would lead to errors in the implementation if we change exported function's parameters or return types.

So the functional options pattern becomes a solution here:
```go
package server

type Server {
  host string
  port int
  timeout time.Duration
  maxConn int
}

func New(options ...func(*Server)) *Server {
  svr := &Server{}
  for _, o := range options {
    o(svr)
  }
  return svr
}

func (s *Server) Start() error {
  // todo
}

func WithHost(host string) func(*Server) {
  return func(s *Server) {
    s.host = host
  }
}

func WithPort(port int) func(*Server) {
  return func(s *Server) {
    s.port = port
  }
}

func WithTimeout(timeout time.Duration) func(*Server) {
  return func(s *Server) {
    s.timeout = timeout
  }
}

func WithMaxConn(maxConn int) func(*Server) {
  return func(s *Server) {
    s.maxConn = maxConn
  }
}
```

And Client will use it like this:
```go
package main

import (
  "log"
  
  "github.com/acme/pkg/server"
)

func main() {
  svr := server.New(
    server.WithHost("localhost"),
    server.WithPort(8080),
    server.WithTimeout(time.Minute),
    server.WithMaxConn(120),
  )
  if err := svr.Start(); err != nil {
    log.Fatal(err)
  }
}
```

