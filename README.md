# psd2-extension
psd2-extension is a Burp Suite extension that signs requests to the Redsys PSD2 API.
It calculates the required values and adds the following headers automatically to Repeater requests (or matching Host requests):
- X-Request-ID
- Digest
- Signature
- TPP-Signature-Certificate

You can also configure static headers (PSU-IP-Address, TPP-Redirect-URI, TPP-Redirect-Preferred, Authorization).

## Features
- New Burp tab to configure:
  - Private key and certificate paths
  - Static header values
  - Host header filter
  - Enable/disable switch
  - Enable/disable overwrite Redsys headers.
    - True --> Overwrite headers
    - False --> Add headers (may duplicate headers)

## Installation

1. Download the extension (.py).
2. In burp: Extensions -> Extensions settings > Python Envionment > Add Jython 2.7 standalone JAR file.
3. In Burp: Extensions -> Add extension > Type = "python".
4. Select "psd2-extension.py" and load it.
5. Configure it in the psd2-extension tab.

## Example in Repeter

Before:
```
POST /payments
Host: api.redsys.example.com
...
```

After:
```
POST /payments
Host: api.redsys.example.com
X-Request-ID: ...
Digest: ...
Signature: ...
TPP-Signature-Certificate: ...
PSU-IP-Address: ...
TPP-Redirect-URI: ...
TPP-Redirect-Preferred: ...
Authorization: ...
...
```
