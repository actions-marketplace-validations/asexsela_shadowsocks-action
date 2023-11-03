# Shadowsocks Connect via Outline

A GitHub Action to seamlessly connect to a Shadowsocks server using the Outline platform.

## Params

- `ip` -> IP address (required)
- `port` -> Port address (required)
- `password` -> IP address (required)
- `encrypt_method` -> IP address (default: chacha20-ietf-poly1305)

## Get `encrypt_method` and `password` from Outline URI

```shell
# Outline URI
# ss://<encrypted-data>@<ip>:<port>/?outline=1

echo "<encrypted-data>" | base64 --decode

# Output:
# <encrypt_method>:<password>
```

## Usage

```yaml
name: Test Shadow Socks

on:
  workflow_dispatch:

jobs:
  test:
    runs-on: ubuntu-latest
    permissions:
      contents: read
      
    steps:
      - name: Checkout repository
        uses: actions/checkout@v4

      - name: Shadowsocks Connect via Outline
        uses: asexsela/shadowsocks-action@v1
        with:
            ip: ${{ secrets.SHADOWSOCKS_IP }}
            port: ${{ secrets.SHADOWSOCKS_PORT }}
            password: ${{ secrets.SHADOWSOCKS_PASSWORD }}
```
