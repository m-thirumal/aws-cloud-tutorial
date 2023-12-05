# SES (Simple Mail Service)

1. Go to SES service and create `Identity`.

2. Verify Domain with `Route 53` or any other service provider

```
_amazonses.example.com                 TXT
xxxxx._domainkey.example.com           TXT
xxxx._domainkey.example.com            CNAME              dkim.amazonses.com
xxxx._domainkey.example.com            CNAME              dkim.amazonses.com
```

3. Configuration set to track Email (send, delivered, bounce, Open, Click, etc)

