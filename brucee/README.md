note for bruce 2026.06.16

https://github.com/2cld/netstack/tree/docs/wan/cloudflare
is repo for
https//netstack.org/docs/wan/cloudflare/

and you found a bug in my cloudflare route, I had my dev going to https sb http so trafik <-> cf cert fail

github keeps the public stuff, private stuff is in https://gitea.cat9.me
I think you can just go register... I did have cf filter on an monthly cert auth, but I have not tested in awhile

---
from wip (my local ai I use)

---
It's infra routing (Cloudflare → traefik → container), not an nspwa code problem. The nspwa app itself is healthy — it's the traffic never reaching it. This belongs on the docker-compose repo (where traefik config lives) or netstack (where the pattern is documented).

Let me put it on the docker-compose repo since that's where the traefik config and certs live:

Filed: [docker-compose#1](https://gitea.cat9.me/nsadmin/docker-compose/issues/1) — `nspwa.cat9.me 502: traefik serving default cert instead of ACME cert`

Full diagnosis included with 3 fix options. This is a `cat9-ops` task (infra overhead). You can tackle it as part of today's HWPC block if it's blocking your work, or schedule a separate `cat9-ops` block for it. The nspwa app itself is fine — it's just the cert/tunnel plumbing.
