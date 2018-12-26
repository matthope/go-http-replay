# go-http-replay

## Synopsis

Replay HTTP response or fetch from the remote:

```go
import (
	"net/http"
	"testing"

	httpreplay "github.com/aereal/go-http-replay"
)

func Test_http_lib(t *testing.T) {
	httpClient := &http.Client{
		Transport: httpreplay.NewReplayOrRoundTripper("./testdata"),
	}
	// httpClient will behave like the client that created from NewReplayRoundTripper but DO actual request if local cache is missing.
}
```

Only replay HTTP response from cache:

```go
import (
	"net/http"
	"testing"

	httpreplay "github.com/aereal/go-http-replay"
)

func Test_http_lib(t *testing.T) {
	httpClient := &http.Client{
		Transport: httpreplay.NewReplayRoundTripper("./testdata"),
	}
	// httpClient will not do actual request to remote sites but returns the response from local cache files.
}
```

## Author

- aereal