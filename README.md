# Log

## Logentries

Go (golang) client library for logging to https://logentries.com/ via TLS.  Compatible with http://golang.org/pkg/log/#Logger

* Uses a buffered chan to avoid blocking the application.  Will drop log messages if the chan is full.

Example usage:

```
package main

import (
	"github.com/GeoNet/log/logentries"
	"log"
	"time"
)

func init() {
	logentries.Init(LOGENTRIES_TOKEN)
}

func main() {
	for {
		log.Print("Hello Logentries.")
		time.Sleep(time.Duration(5) * time.Second)
	}
}
```
