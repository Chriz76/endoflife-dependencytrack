# Dependency-Track End-of-Life SBOM Integration
Integration for Dependency-Track that fetches and reports EoL info for your software bill of materials project dependencies. Monitors and assigns EoL state as vulnerabilities to the components. Uses endoflife.date dataset by default; supports custom datasets. Early PoC / experimental.

![EOL DependencyTrack](https://raw.githubusercontent.com/Chriz76/endoflife-dependencytrack/main/main.png)

The integration is provided as:

- **Binaries for Linux and Windows**: Best if you already have a running Dependency-Track installation
- **Docker image**: Install Dependency-Track and the endoflife.date integration in docker.

---

## Dependency-Track API-Key

The eol integration uses the Dependency-Track API. You can create an API key in the [Web UI](http://localhost:8080/):

![API Key](https://raw.githubusercontent.com/Chriz76/endoflife-dependencytrack/main/apikey.png)

## Binary Releases



Precompiled binaries are available under **GitHub Releases**.

Supported platforms:

- linux-x64
- win-x64

Example:

./myservice --port 8080


---

## Quick Start (Docker)

```bash
# Downloads the latest Docker Compose file
curl -LO https://raw.githubusercontent.com/Chriz76/endoflife-dependencytrack/main/docker-compose.yml

# Starts the Dependency-Track stack using Docker Compose
docker compose up -d

# Run the endoflife.date integration (replace with your API-Key):
docker run --rm --network dtrack-net -e DT_APIURL="http://apiserver:8080/api/" -e DT_APIKEY="YOUR_DEPENDENCY_TRACK_API_KEY" dependencytrackaddons/eol-dependencytrack:latest

```
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
