### command to sign the cert using public ca
Steps below will use public letsencrypt CA to sign the certificate

```bash
sudo apt install certbot
mkdir logs config
certbot certonly --manual --work-dir . --logs-dir ./logs --config-dir ./config
# answer prompts. generates the fullchain.pem and privatekey.pem files under ./config/live/s1.youmayneedthis.com/

# convert to pfx
openssl pkcs12 -export -out letsencrypt.s1.youmayneedthis.com.pfx -inkey ./config/live/s1.youmayneedthis.com/privkey.pem -in ./config/live/s1.youmayneedthis.com/fullchain.pem
```
