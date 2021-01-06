# Letsencrypt wildcard with HAProxy and Arvan Cloud

Command: 
```bash
certbot certonly  --manual --preferred-challenges=dns --manual-auth-hook ./authenticator.sh --manual-cleanup-hook ./cleanup.sh  --deploy-hook ./deploy.sh  -d *.example.com -d example.com
```

Check  Certificate’s Expiration Date:
```bash
echo | openssl s_client -connect example.com:443 -servername example.com 2>/dev/null | openssl x509 -noout -dates
```

Check  Certificate’s Expiration Date of Certification File:
```bash
openssl x509 -noout -dates -in cert.pem
```

Cron:
```bash
10 0 * * * certbot renew
```
