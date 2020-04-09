# Hetzner DNS Authenticator certbot plugin


This certbot plugin automates the process of
completing a dns-01 challenge by creating, and
subsequently removing, TXT records using the Hetzner DNS API.

## Install

There is no pypi distribution yet. You can install this plugin via pip directly from this repo though:

```
pip install -e 
```

## Usage

To start using DNS authentication for the Hetzner DNS API, pass the following arguments on certbot's command line:

============================================================= ==============================================
``--authenticator certbot-dns-hetzner:dns-hetzner``          select the authenticator plugin (Required)

``--certbot-dns-hetzner:dns-hetzner-credentials``             Hetzner DNS API credentials INI file. (Required)
============================================================= ==============================================

## Credentials


From the hetzner DNS control panel at https://dns.hetzner.com go to "API Tokens" and add a personal access token.

An example ``credentials.ini`` file:

.. code-block:: ini
    certbot_dns_hetzner:dns_hetzner_api_token = nohnah4zoo9Kiejee9aGh0thoopee2sa

## Examples

.. code-block:: bash
   :caption: To acquire a certificate for ``example.com``
   certbot certonly \\
     --authenticator certbot-dns-hetzner:dns-hetzner \\
     --certbot-dns-hetzner:dns-hetzner-credentials /path/to/my/hetzner.ini \\
     -d example.com
.. code-block:: bash
   :caption: To acquire a certificate for ``*.example.com``
   certbot certonly \\
     --authenticator certbot-dns-hetzner:dns-hetzner \\
     --certbot-dns-hetzner:dns-hetzner-credentials /path/to/my/hetzner.ini \\
     -d '*.example.com'
     
## Thanks to

Of course certbot, which examples and documentation I used to implement this plugin. And to https://github.com/m42e/certbot-dns-ispconfig which served as an excellent example and README template as well.
