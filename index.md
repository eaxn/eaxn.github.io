# Code Snippets

## HTTP GET Request with custom user agent

### Go

    ```go
    package main

    import (
        "net/http"
        "io"
    )

    func main() {
        agent := "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/103.0.0.0 Safari/537.36" // your custom user agent
        client := http.Client{} // the http client
        url := "http://jann.dev"
        req, err := http.NewRequest("GET", url, nil)
        if err != nil {
            panic(err) // you can use log.Fatalln instead
        }
        resp, err := client.Do(req)
        if err != nil {
            panic(err)
        }
        f, err := os.Create() // create a new file for the output file
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
### Java
