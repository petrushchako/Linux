# `curl`

## Description:
`curl` is a command-line tool used to transfer data from or to a server, supporting multiple protocols such as HTTP, HTTPS, FTP, SCP, and more. It is often used for web requests and downloading/uploading files. `curl` is a powerful tool for developers to interact with APIs and servers.

## Syntax:
`curl [options] [URL]`

## Options:
- `-O, --remote-name`: Save the output to a file using the remote server’s filename.
- `-o, --output <file>`: Write output to `<file>` instead of stdout.
- `-L, --location`: Follow redirects.
- `-I, --head`: Fetch only the headers.
- `-X, --request <command>`: Specify the HTTP method to use (e.g., GET, POST, PUT, DELETE).
- `-d, --data <data>`: Send specified data in a POST request to the server.
- `-H, --header <header>`: Pass custom header(s) to the server (e.g., authentication tokens).
- `-u, --user <user:password>`: Use basic HTTP authentication.
- `-v, --verbose`: Provide detailed information about the request.
- `-k, --insecure`: Ignore SSL certificate warnings.
- `-T, --upload-file <file>`: Upload a file to the server.
- `-F, --form <name=content>`: Submit form data with the request.
- `-s, --silent`: Run in silent mode (no output or progress).

## Protocols Supported:
- HTTP, HTTPS
- FTP, FTPS
- SCP, SFTP
- LDAP, IMAP, POP3, SMTP
- SMB, TELNET, TFTP

## Example:
1. To download a file from a URL and save it as its original name:

    `curl -O https://example.com/file.txt`

2. To send data in a POST request:

    `curl -d "username=user&password=pass" https://example.com/login`

3. To upload a file via FTP:

    `curl -T uploadfile.txt ftp://ftp.example.com/`

4. To retrieve only the HTTP headers of a page:

    `curl -I https://example.com`

5. To send a GET request with a custom header:

    `curl -H "Authorization: Bearer token" https://api.example.com/data`

## Usage:
1. Define the URL or server address to interact with.
2. Choose the appropriate options for the task (download, upload, POST data, etc.).
3. Optionally use options like `-v` for detailed output or `-o` to specify output file names.
4. Run the `curl` command and observe the response from the server or save it to a file.

## Notes:
- `curl` is commonly used for testing API endpoints, downloading files, and making HTTP requests directly from the command line.
- When using `-d` for POST requests, remember that `curl` defaults to a `POST` request. For other methods like PUT or DELETE, use the `-X` option.
- `curl` can handle complex tasks like multipart file uploads and custom HTTP headers, making it ideal for API interaction.
- Always consider security when using options like `-k` (insecure SSL), especially for production environments.



<br><br><br>


## 21 curl exercises
These exercises are about understanding how to make different kinds of HTTP requests with curl. They’re a little repetitive on purpose. They exercise basically everything I do with curl.

To keep it simple, we’re going to make a lot of our requests to the same website: `https://httpbin.org`. httpbin is a service that accepts HTTP requests and then tells you what request you made.

1. Request `https://httpbin.org`
    ```sh
    curl https://httpbin.org
    ```

2. Request `https://httpbin.org/anything`. httpbin.org/anything will look at the request you made, parse it, and echo back to you what you requested. curl’s default is to make a `GET` request.
    ```sh
    curl https://httpbin.org/anything
    ```
    
3. Make a `POST` request to `https://httpbin.org/anything`
    ```sh
    curl -X POST https://httpbin.org/anything
    ```
    
4. Make a `GET` request to `https://httpbin.org/anything`, but this time add some query parameters (set `value=panda`).
    ```sh
    curl -X POST https://httpbin.org/anything -d "value=panda"
    ```
    > While curl automatically chooses `POST` when `-d` is used, it's good practice to include it explicitly.
    
5. Request google’s `robots.txt` file (`www.google.com/robots.txt`)
    ```sh
    curl -O https://www.google.com/robots.txt
    ```
    
6. Make a `GET` request to `https://httpbin.org/anything` and set the header `User-Agent: elephant`.
    ```sh
    curl https://httpbin.org/anything -H "User-Agent: elephant"
    # curl https://httpbin.org/anything -H "User-Agent: elephant" -H "Authorization: Bearer token"
    ```
    
7. Make a `DELETE` request to `https://httpbin.org/anything`
    ```sh
    curl -X DELETE https://httpbin.org/anything
    ```
    
8. Request `https://httpbin.org/anything` and also **get the response headers**
    ```sh
    curl https://httpbin.org/anything --include
    curl https://httpbin.org/anything -i
    ```
    
9. Make a `POST` request to `https://httpbin.org/anything` with the JSON body `{"value": "panda"}`
    ```sh
    curl -X POST https://httpbin.org/anything --json '{"value":"panda"}'
    ```
    
10. Make the same `POST` request as the previous exercise, but set the `Content-Type` header to `application/json` (because `POST` requests need to have a content type that matches their body).<br>Look at the json field in the response to see the difference from the previous one.
    ```sh
    curl -X POST https://httpbin.org/anything -H "Content-Type: application/json" -d '{"value":"panda"}'
    ```
    
11. Make a `GET` request to `https://httpbin.org/anything` and set the header `Accept-Encoding: gzip` (what happens? why?)
    ```sh
    curl https://httpbin.org/anything -H "Accept-Encoding: gzip"
    ```
    > This makes a `GET` request to `https://httpbin.org/anything` and sets the `Accept-Encoding: gzip` header, which asks the server to compress the response using `gzip`. If the server supports it, you'll get a gzipped response, which you can decompress if needed.<br>To see the raw response, you can add the `--verbose` (`-v`) flag    


12. Put a bunch of a JSON in a file and then make a `POST` request to `https://httpbin.org/anything` with the **JSON in that file as the body**
    ```sh
    curl -X POST https://httpbin.org/anything -H "Content-Type: application/json" -d @file.json
    ```
    
13. Make a request to `https://httpbin.org/image` and set the header `Accept: image/png`.<br>Save the output to a PNG file and open the file in an image viewer. Try the same thing with different Accept: headers.
    ```sh
    curl -X GET https://httpbin.org/image -H "Accept: image/png" -o img.png
    ```
    
14. Make a `PUT` request to `https://httpbin.org/anything`
    ```sh
    curl -X PUT https://httpbin.org/anything
    # curl -X PUT https://httpbin.org/anything -d "some data"
    ```
    
15. Request `https://httpbin.org/image/jpeg`, save it to a file, and open that file in your image editor.
    ```sh
    curl -o img.jpeg https://httpbin.org/image/jpeg
    ```
    
16. Request `https://www.twitter.com`.<br>You’ll get an empty response. Get curl to show you the response headers too, and try to figure out why the response was empty.
    - **Request**
        ```sh
        curl -i https://www.twitter.com
        ```
    
    - **Response**
        ```sh
        perf: 7402827104
        location: https://twitter.com/
        cache-control: no-cache, no-store, max-age=0
        content-length: 0
        x-transaction-id: 8eb68999658fc76e
        x-response-time: 1
        x-connection-hash: 074814dad34f5c7e5ccd6e69cd0d72fb54e2185cec888cf7ba304b65c5d83213
        date: Fri, 04 Oct 2024 11:57:52 GMT
        server: tsa_b
        ```

    - **Explanation**
        - **perf: 7402827104** - This may represent performance metrics specific to Twitter's backend.
        - **location: https://twitter.com/** - This indicates the URL being accessed, which is the homepage of Twitter.
        - **cache-control: no-cache, no-store, max-age=0** - This header indicates that the response should not be cached.
        - **content-length: 0** - This indicates that there is no content in the response body (which is common for redirect responses).
        - **x-transaction-id: 8eb68999658fc76e** - A unique identifier for the transaction, useful for debugging.
        - **x-response-time: 1** - This indicates that the response time was 1 millisecond.
        - **x-connection-hash: 074814dad34f5c7e5ccd6e69cd0d72fb54e2185cec888cf7ba304b65c5d83213** - This may be a hash for the connection, possibly for load balancing or routing purposes.
        - **date: Fri, 04 Oct 2024 11:57:52 GMT** - The date and time when the response was generated.
        - **server: tsa_b** - This indicates the type of server handling the request, in this case, a specific Twitter server.


17. Make any request to `https://httpbin.org/anything` and just set some nonsense headers (like `panda: elephant`)
    ```sh
    curl https://httpbin.org/anything -H "panda:elephant"
    ```
    
18. Request `https://httpbin.org/status/404` and `https://httpbin.org/status/200`.<br>Request them again and get curl to show the response headers.
    ```sh
    curl https://httpbin.org/status/404 -i
    curl https://httpbin.org/status/200 -i
    ```
    
19. Request `https://httpbin.org/anything` and set a `username` and `password` (with `-u username:password`)
    ```sh
    curl https://httpbin.org/anything -u userValue:passValue -i
    ```
    
20. Download the Twitter homepage (`https://twitter.com`) in Spanish by setting the `Accept-Language: es-ES` header.
    ```sh
    curl -o twitter.html https://x.com -H "Accept-Language: es-ES"
    # curl -s -H 'Accept-Language: es'  -XGET "http://www.google.com" -o google.html
    ```

21. Make a request to the Stripe API with curl. (see `https://stripe.com/docs/development` for how, they give you a test API key). Try making exactly the same request to `https://httpbin.org/anything`.
    
    - **Request**:
        ```sh
        curl https://api.stripe.com/v1/charges -u sk_test_zzPhAh8sZkhmI4JDtzTNnhGl:
        # The colon prevents curl from asking for a password.
        ```
    - **Explanation**:
        - `https://api.stripe.com/v1/charges` : This is the URL for the Stripe API endpoint to create a charge.
        - `-u sk_test_zzPhAh8sZkhmI4JDtzTNnhGl:` : This option is for basic authentication. It includes your test API key (replace this with your actual test API key). **The colon at the end is necessary to indicate that there is no password**.
