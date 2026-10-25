# Deploy: nn-sssl

Fork of Pretendo's SSSL, unchanged in mechanism. It forges a CA the Wii U's post-5.5.5
verifier accepts from a dump of `Nintendo CA - G3` (which an operator must supply; it is not
in this repository) and mints a wildcard site certificate. Point the console's DNS at
[`nn-sssl-dns`](../../nn-sssl-dns) and serve that certificate from Traefik for the Nintendo
names, and an unmodded Wii U reaches OpenPak's `nn-account` and friends. Consoles running
Aroma use [`nn-inkay`](../../../clients/nn-inkay) instead and need none of this.
