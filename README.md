# lemonfiber-caddy

The image of the proxy in a [lemonfiber](https://github.com/lemonfiber/lemonfiber) stack:
Caddy, rebuilt without the file capability Caddy's own image carries on its binary, so
it starts with no added kernel capability. It listens on 8080 and 8443, which the stack publishes as 80 and 443, and serves the household's names.

This repository builds `ghcr.io/lemonfiber/caddy`. You do not run it yourself:
[`plugin-caddy`](https://github.com/lemonfiber/plugin-caddy) runs it as the upstream its
adapter speaks lemonfiber's `proxy.front` contract for, and pins it by digest.

## What is here

| Path | What it is |
| --- | --- |
| `Dockerfile` | The image, from Caddy's own pinned by digest |
| `config/caddy/Caddyfile` | The configuration the image starts with |

## How it is published

Every commit on `main` builds `linux/amd64` and `linux/arm64` under one index,
tagged `main-<commit>`, and moves `plugin-caddy`'s pin to it on a pull request there.
The release train never tags this repository: `plugin-caddy`'s release pins the image
its `main` holds. The specification has the details:
[`30-repos/lemonfiber-caddy.md`](https://github.com/lemonfiber/spec/blob/main/30-repos/lemonfiber-caddy.md).

## Contributing and security

Read the [contributing guide](https://github.com/lemonfiber/spec/blob/main/50-governance/contributing.md)
before opening a pull request. Report a vulnerability as the
[security policy](https://github.com/lemonfiber/.github/blob/main/SECURITY.md)
describes, not in a public issue.

## Licence

[Hippocratic License 3.0](LICENSE).
