# Log

## Logentries

Go (golang) client library for logging to https://logentries.com/ via TLS.  Compatible with http://golang.org/pkg/log/#Logger

* Uses a buffered chan to avoid blocking the application.  Will write to std err if the chan is full.
* To block on write to Logentries set the env var LOGENTRIES_BLOCKING=true

Example usage:

If the environment variable `LOGENTRIES_TOKEN` is set before init() begins then simply import for side effects to log to Logentries:

```
import (
	_ "github.com/GeoNet/log/logentries"
)
```

`logentries.Init("LOGENTRIES_TOKEN")` can be called if needed:

```
package main

import (
	"github.com/GeoNet/log/logentries"
	"log"
	"time"
)

func init() {
	logentries.Init("LOGENTRIES_TOKEN")
}

func main() {
	for {
		log.Print("Hello Logentries.")
		time.Sleep(time.Duration(5) * time.Second)
	}
}
```
