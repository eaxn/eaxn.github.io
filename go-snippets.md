# Snippets (Go)

## HTTP GET Request with custom user agent

```go
package main

import (
	"io"
	"net/http"
	"os"
)

func main() {
	agent := "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/103.0.0.0 Safari/537.36" // your custom user agent
	client := http.Client{} // the http client
	url := "http://jann.dev"
	req, err := http.NewRequest("GET", url, nil)
	if err != nil {
		panic(err) // you can use log.Fatalln instead
	}
    req.Header.Set("User-Agent", agent)
	resp, err := client.Do(req)
	if err != nil {
		panic(err)
	}
	f, err := os.Create("page.html") // create a new file for the output file
	if err != nil {
		panic(err)
	}
	// save the body to example.html
	_, err = io.Copy(f, resp.Body)
	if err != nil {
		panic(err)
	}
}
```
