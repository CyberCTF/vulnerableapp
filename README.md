# OWASP VulnerableApp

[OWASP VulnerableApp](https://github.com/SasanLabs/VulnerableApp) by Karan Preet Singh Sasan and
the SasanLabs contributors: a modular, deliberately vulnerable Spring Boot application with
levelled vulnerabilities (injection, XSS, XXE, SSRF, JWT, path traversal, file upload and more),
built for learning and for benchmarking security scanners. This repository runs it with
[Isoloom](https://www.isoloom.com): [`isoloom.yml`](isoloom.yml) describes the machine, and the
upstream source in [`build/web/app/`](build/web/app) builds from source with
[`build/web/Dockerfile`](build/web/Dockerfile).

| Machine | Service |
| --- | --- |
| web | VulnerableApp (legacy UI and REST API) on port 9090, under `/VulnerableApp` |

Upstream's full Docker stack adds a modern UI (VulnerableApp-facade), JSP and PHP modules and an
optional LLM module, each a separate upstream project published only as an image. They are not
included: this lab is the main application, built from its source.

## Run it

```bash
isoloom generate
isoloom up docker
```

Then open http://localhost:9090/VulnerableApp/. The same spec runs as Docker on a local VM
(`docker-vm`), on a cloud VM (`cloud-docker`) or on Kubernetes. Lab guide:
[VulnerableApp documentation](https://github.com/SasanLabs/VulnerableApp/tree/master/docs).

Upstream version and commit: [UPSTREAM.md](UPSTREAM.md).

## Licence

Apache-2.0, as VulnerableApp ([LICENSE](LICENSE)). This application is deliberately vulnerable:
keep it isolated.
