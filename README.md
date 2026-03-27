# Dependency-Track End-of-Life SBOM Integration
Integration for Dependency-Track that fetches and reports EoL info for your software bill of materials poject dependencies. Monitors and assigns EoL state as vulnerabilities to the components. Uses endoflife.date dataset by default; supports custom datasets. Early PoC / experimental.

![EOL DependencyTrack](https://raw.githubusercontent.com/Chriz76/endoflife-dependencytrack/main/main.png)

This repository provides the integration as:

- Binaries for Linux and Windows: Best if you have an already running Dependency-Track installation
- Docker image: Quick start setup for Dependency-Track and the endoflife.date integration in docker. Can also be used with existing Dependency-Track docker setups.

---

## Binary Releases

Precompiled binaries are available under **GitHub Releases**.

Supported platforms:

- linux-x64
- win-x64

Example:

./myservice --port 8080


---

## Quick Start (Docker)

Run the service using Docker:

docker run -p Chriz76/deptrack-eol:latest

---

## Docker Image

Image:

myorg/myservice

Tags:

- latest
- v0.1

Pull image:

docker pull myorg/myservice:latest

---

## Configuration

Environment variables:

| Variable | Description | Default |
|---------|-------------|--------|
| PORT | HTTP port | 8080 |
| LOG_LEVEL | Logging level | info |

Example:

docker run -p 8080:8080 \
-e LOG_LEVEL=debug \
myorg/myservice:latest

---

## License

EOL-DT is free to use under the terms of the [LICENSE](LICENSE).  
It is provided as-is, without warranty or liability. See LICENSE for details.

## Telemetry & Privacy

EOL-DT may send usage and error data.  
For full details, including what data is collected and how to disable telemetry, see [PRIVACY.md](PRIVACY.md).
