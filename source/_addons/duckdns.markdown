---
layout: page
title: "DuckDNS"
description: "Automatically update your Duck DNS IP address with integrated HTTPS support via Let's Encrypt."
date: 2017-04-30 13:28
sidebar: true
comments: false
sharing: true
footer: true
featured: true
---

[Duck DNS](https://duckdns.org/) is a free service which will point a DNS (sub domains of duckdns.org) to an IP of your choice. This add-on includes support for Let's Encrypt and will automatically create and renew your certificates.

```json
{
  "lets_encrypt": {
    "accept_terms": true
  },
  "token": "sdfj-2131023-dslfjsd-12321",
  "domains": ["my-domain.duckdns.org"]
}
```

Configuration variables:

- **token** (*Required*): Your Duck DNS API key.
- **domains** (*Required*): A list of domains to update DNS.
- **seconds** (*Optional*): Seconds between updates to Duck DNS.
- **lets_encrypt.accept_terms** (*Optional*): If you accept the [Let's Encrypt Subscriber Agreement][le], it will generate & update Let's Enrypt certificates for your DuckDNS domain.

[le]: https://letsencrypt.org/repository/

## {% linkable_title Home Assistant configuration %}

Use the following configuration in Home Assistant to use the generated certificate:

```yaml
http:
  base_url: https://my-domain.duckdns.org:8123
  ssl_certificate: /ssl/fullchain.pem
  ssl_key: /ssl/privkey.pem
```

If you use a other port as `8123` or a SSL proxy, change the port number.

## {% linkable_title Router configuration %}

You'll need to forward the port you listed in your configuration (8123 in the example above) on your router to your Home Assistant system. You can find guides on how to do this on [Port Forward](https://portforward.com/) - noting that you'll only need to forward the TCP port.
