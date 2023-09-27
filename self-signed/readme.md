### command to create self-signed certificate

```bash
# create root CA cert
openssl req -x509 \
            -sha256 -days 356 \
            -nodes \
            -newkey rsa:2048 \
            -subj "/CN=youmayneedthis.com/C=IN/L=Hyderabad" \
            -keyout rootCA.key -out rootCA.crt 

# create cert
openssl x509 -req \
    -in ../server.csr \
    -out server.crt \
    -CA rootCA.crt -CAkey rootCA.key -CAcreateserial \
    -days 365 \
    -sha256 -extfile cert.conf

# convert to pfx
openssl pkcs12 -export -out s1.youmayneedthis.com.pfx -inkey ../pk.key -in server.crt -certfile rootCA.crt
```
