# Wii U SSSL Server

OpenPak's Wii U SSSL Server.

| | |
| --- | --- |
| Network | Wii U |
| Role | Forges a CA and a wildcard site certificate that the Wii U's post-5.5.5 SSL verifier accepts, from a Nintendo CA - G3 dump |
| Depends on | Nintendo CA - G3 dump (operator-supplied, not in this repository) |
| Used by | Traefik (serves the site certificate for the Nintendo names) |
| Image | `sssl` (local build from the `Dockerfile`) |
| Based on | [Pretendo `SSSL`](https://github.com/PretendoNetwork/SSSL) (GPL-3.0) |
| Licence | GPL-3.0 |

## What it produces

| File | What |
| --- | --- |
| `forged-ca.pem` | Patched copy of Nintendo CA - G3 with a new key |
| `forged-ca-private-key.pem` | Private key for the forged CA |
| `ssl-cert.pem` | Site certificate for `-cn` (default `*`), signed by the forged CA |
| `ssl-cert-private-key.pem` | Private key for the site certificate |
| `csr.csr` | Certificate signing request for the site key |
| `cert-chain.pem` | Site certificate followed by the forged CA |

## Run

```sh
npm i
node patch      # reads SSSL_* environment variables; or: node patch -i
```

## Docs

- [Protocol](docs/protocol.md)
- [Evidence](docs/evidence.md)
- [Deploy](docs/deploy.md)
- [Notes](docs/notes.md)
- [Upstream README](docs/upstream.md)
- [Docs index](docs/README.md)

## Licence

GPL-3.0. See [LICENSE](LICENSE).
