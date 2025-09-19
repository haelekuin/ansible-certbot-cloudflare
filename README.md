# ansible-certbot-cloudflare

A example playbook to use [certbot-dns-cloudflare](https://certbot-dns-cloudflare.readthedocs.io/en/stable/) and [geerlingguy.certbot](https://github.com/geerlingguy/ansible-role-certbot) to roll out certificates.

This would be redundant if [this PR](https://github.com/geerlingguy/ansible-role-certbot/pull/237) gets merged.

### Instructions

1. Follow the [instructions](https://certbot-dns-cloudflare.readthedocs.io/en/stable/#credentials) on how to create a Cloudflare API key.
2. Define the `certbot_cloudflare_api_token` and `certbot_admin_email` variable.
3. On your host, define your certbot domain variables looking something like this
```yaml
certbot_certs:
  - name: "hostofdoom.meow.com"
    domains:
      - "hostofdoom.meow.com"
```

I set `--dns-cloudflare-propagation-seconds 60` because it would sometimes fail. You can play around with lowering it if you don't like waiting.
