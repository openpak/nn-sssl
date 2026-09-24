# Next session — nn-sssl

Updated 2026-09-15.

The hackless Wii U path's certificate tool: turns an operator-supplied dump
of `Nintendo CA - G3` into the forged CA + wildcard site cert the Wii U's
post-5.5.5 SSL verifier accepts. It IS a git repo (41 commits, remote
openpak/nn-sssl, no tags) — and it is a tool, not a service: nothing here
builds, tags or deploys.

## Where things stand

- One OpenPak commit (`cb4c93b`, 2026-09-10): the README's OpenPak header —
  what the operator must supply and where each artifact goes. Mechanism
  unchanged from upstream (`patch.js`, Docker, env/CLI options).
- The operator's part, none of it done yet: dump
  `/storage_mlc/sys/title/0005001b/10054000/content/scerts/CACERT_NINTENDO_CA_G3.der`
  from a Wii U, run the script, then serve the wildcard site cert from
  Traefik for the Nintendo names.
- The console half of the route is `nn-sssl-dns` (DNS setting only);
  Aroma consoles use `nn-inkay` instead and need none of this.
- The hackless route end to end has never been exercised on a console.
- Untracked (2026-09-15 docs pass): `CHANGELOG.md`, `docs/`, `prds/` stubs.

## Next steps

1. Decide whether the hackless route gets an operator run this cycle (it
   needs a console that can dump G3) or stays documented-only.
2. If run: mint the pair, install into Traefik, point a stock Wii U's DNS
   at `nn-sssl-dns`, attempt sign-in — that is WU-0 on the hackless route.

## Pointers

- README: the two verifier bugs, env/CLI table, Docker usage
- ../prds/platform-wiiu-prd.md §4 — the two console routes
- ../nn-sssl-dns (DNS half), ../nn-inkay (modded alternative)

## Scratch (research and throwaway work)

Decompiles, Ghidra projects, dumps, exefs/romfs extracts, packet captures,
strace and emulator logs, probe harnesses: put them in
`~/REPOS/Openpak/scratch/<topic>`. That folder is a local mount of the media pool,
outside every repository, so nothing in it is committed. Never use `/tmp` (a
shared 15 GB RAM disk) or elsewhere on `/home` for this. Keys and signing
material never go there. Rule: `docs/playbooks/conventions.md` in the workspace.
