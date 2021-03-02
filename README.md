Forked from [HybridGroup](https://github.com/hybridgroup/mjpeg)

# How to use
- Initialise standard Echo server as [per](https://echo.labstack.com/cookbook/hello-world).
- Define a Echo HTTP GET route.
- Pass new `StreamToEcho` func as the handler.

# Code Example
```
package main

import (
	"github.com/GaryMcBay/mjpeg"
	"github.com/labstack/echo"
)

func main() {

	e := echo.New()
	stream := mjpeg.NewStream()

	e.GET("/capture", stream.StreamToEcho)

	// Start server
	e.Logger.Fatal(e.Start(":8080"))
}

```