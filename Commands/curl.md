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
    curl 
    ```
    
12. Put a bunch of a JSON in a file and then make a `POST` request to `https://httpbin.org/anything` with the **JSON in that file as the body**
    ```sh
    curl 
    ```
    
13. Make a request to `https://httpbin.org/image` and set the header `Accept: image/png`.<br>Save the output to a PNG file and open the file in an image viewer. Try the same thing with different Accept: headers.
    ```sh
    curl 
    ```
    
14. Make a `PUT` request to `https://httpbin.org/anything`
    ```sh
    curl 
    ```
    
15. Request `https://httpbin.org/image/jpeg`, save it to a file, and open that file in your image editor.
    ```sh
    curl 
    ```
    
16. Request `https://www.twitter.com`.<br>You’ll get an empty response. Get curl to show you the response headers too, and try to figure out why the response was empty.
    ```sh
    curl 
    ```
    
17. Make any request to `https://httpbin.org/anything` and just set some nonsense headers (like `panda: elephant`)
    ```sh
    curl 
    ```
    
18. Request `https://httpbin.org/status/404` and `https://httpbin.org/status/200`.<br>Request them again and get curl to show the response headers.
    ```sh
    curl 
    ```
    
19. Request `https://httpbin.org/anything` and set a `username` and `password` (with `-u username:password`)
    ```sh
    curl 
    ```
    
20. Download the Twitter homepage (`https://twitter.com`) in Spanish by setting the `Accept-Language: es-ES` header.
    ```sh
    curl 
    ```
