# `openssl`

### Prerequisites
Make sure you have OpenSSL installed:

```bash
openssl version
```

If not installed:
- **macOS**: `brew install openssl`
- **Ubuntu**: `sudo apt install openssl`
- **Windows (WSL)**: `sudo apt install openssl`

<br><br><br>

## 1. Create a Private Key
```bash
openssl genpkey -algorithm RSA -out private.key -aes256
```
- `-algorithm RSA`: Choose RSA algorithm.
- `-aes256`: Encrypt the key with AES-256.
- `private.key`: Output file for the private key.

<br><br><br>

## 2. Generate a Certificate Signing Request (CSR)
```bash
openssl req -new -key private.key -out request.csr
```

You’ll be prompted to enter:
- Country (e.g. US)
- State
- Organization Name
- Common Name (e.g. `example.com`)
- Email

<br><br><br>

## 3. Create a Self-Signed Certificate (for local/testing use)
```bash
openssl req -x509 -key private.key -in request.csr -out certificate.crt -days 365
```
- `-x509`: Generates a self-signed certificate.
- `-days 365`: Valid for 1 year.

<br><br><br>

## 4. Act as Your Own Certificate Authority (CA)
### 4.1 Generate a Root CA Key and Certificate
```bash
openssl genpkey -algorithm RSA -out rootCA.key
openssl req -x509 -new -key rootCA.key -out rootCA.crt -days 3650 -subj "/CN=MyRootCA"
```

### 4.2 Sign a CSR with Your CA to Issue a Cert
```bash
openssl x509 -req -in request.csr -CA rootCA.crt -CAkey rootCA.key -CAcreateserial -out signed.crt -days 365
```
- `-CAcreateserial`: Creates a serial number file.

<br><br><br>

## 5. Verify a Certificate
```bash
openssl x509 -in signed.crt -text -noout
```

<br><br><br>

## 6. Convert Certificate Formats
### PEM to DER (binary)
```bash
openssl x509 -in certificate.crt -outform der -out certificate.der
```

### DER to PEM
```bash
openssl x509 -in certificate.der -inform der -out certificate.crt
```

<br><br><br>

## 7. Bundle Certificate with Private Key (for use in services)
```bash
cat certificate.crt private.key > bundle.pem
```

<br><br><br>

## 8. Test Certificate with a Local Server (Optional)
Start a local HTTPS server with the certificate:
```bash
openssl s_server -key private.key -cert certificate.crt -port 8443
```
Then open `https://localhost:8443` in your browser.

<br><br><br>

## Cleanup Tips
To remove test files:
```bash
rm private.key request.csr certificate.crt rootCA.* signed.crt
```
