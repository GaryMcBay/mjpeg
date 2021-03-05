Forked from [HybridGroup](https://github.com/hybridgroup/mjpeg)

# Changes
- Adds support for streaming an MJPEG http response to Echo web server.
- Added new func `StreamToEcho`.
- `StreamToEcho` implements echo.Context to set header to image/jpeg content-type.
- Writes mjpeg buffer to an Echo-type response and streams to http.

# How to use
- Initialise standard Echo server as [per](https://echo.labstack.com/cookbook/hello-world).
- Define a Echo HTTP GET route.
- Pass new `StreamToEcho` func as the handler.

# Code Example
```go
package main

import (
	"github.com/GaryMcBay/mjpeg"
	"github.com/labstack/echo"
)

func main() {

	e := echo.New()
	stream := mjpeg.NewStream()

	e.GET("/capture", stream.StreamToEcho)
	// Pass your jpegBuffer frames using stream.UpdateJPEG(<your-buffer>)

	// Start server
	e.Logger.Fatal(e.Start(":8080"))

}

```
