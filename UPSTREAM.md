# Upstream

| | |
| --- | --- |
| Project | OWASP VulnerableApp |
| Repository | https://github.com/SasanLabs/VulnerableApp |
| Version | 2.1.0 |
| Commit | 668ab14704b63d286bc73f5ec302885a5f192c2e |
| Licence | Apache-2.0 |

`build/web/app/` is that commit, unchanged, without its Git history. Upstream builds its image with
Jib and ships no Dockerfile for the application, so `build/web/Dockerfile` builds the Spring Boot
jar with Gradle 8.5 (the wrapper's version) and runs it on upstream's base image recipe
(`app/Dockerfile.base`: eclipse-temurin:17-jre plus ping). Dependency versions are pinned in
upstream's `build.gradle`. To update, replace `build/web/app/` with a newer release, then change
this table.
