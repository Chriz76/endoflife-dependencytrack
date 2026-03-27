# Dependency-Track End-of-Life SBOM Integration
Integration for Dependency-Track that fetches and reports EoL info for your software bill of materials project dependencies. Monitors and assigns EoL state as vulnerabilities to the components. Uses endoflife.date dataset by default; supports custom datasets. Early PoC / experimental.

![EOL DependencyTrack](https://raw.githubusercontent.com/Chriz76/endoflife-dependencytrack/main/main.png)

The integration is provided as:

- **Binaries for [Linux](https://github.com/Chriz76/endoflife-dependencytrack/releases/download/v0.1.0-alpha/eol-dt-linux-x64.tar.gz) and [Windows](https://github.com/Chriz76/endoflife-dependencytrack/releases/download/v0.1.0-alpha/eol-dt-win-x64.zip)**: Best if you already have a running Dependency-Track installation
- **Docker image**: Install Dependency-Track and the endoflife.date integration in docker

---

## Dependency-Track API-Key

The eol integration uses the Dependency-Track API. You can create an API key in the [Web UI](http://localhost:8080/):

![API Key](https://raw.githubusercontent.com/Chriz76/endoflife-dependencytrack/main/apikey.png)

## Quick Start (Existing Dependency-Track Installation)

### Linux
```bash
# Download the latest binary
curl -LO https://github.com/Chriz76/endoflife-dependencytrack/releases/download/v0.1.0-alpha/eol-dt-linux-x64.tar.gz

# Extract the archive
tar -xzvf eol-dt-linux-x64.tar.gz

# Make it executable
chmod +x eol-dt

# Run it
./eol-dt --apikey YOUR_DEPENDENCY_TRACK_API_KEY

```

### Windows
- Download the [latest Windows binary](https://github.com/Chriz76/endoflife-dependencytrack/releases/download/v0.1.0-alpha/eol-dt-win-x64.zip) 
- Unzip it
- Run it with your api key
```cmd
eol-dt --apikey YOUR_DEPENDENCY_TRACK_API_KEY
```

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

## Usage

```bash
Usage: eol-dt [options]

Options:
  --help, -h           Show this help message and exit
  --apikey <key>       Set the DependencyTrack API key
  --apiurl <url>       Set the DependencyTrack API base URL
                       (default: http://localhost:8081/api/)
  --eoldata <source>   Set the End of Life data source URL
                       (default: https://endoflife.date/api/v1/products/full)
                       or a local path
  --telemetry <on|off> Enable or disable telemetry (default: on)
  --loglevel <0-5>     Set verbosity level
                       (0 = trace, 5 = critical, default: 2)
```
## Configuration via Environment Variables

All CLI options can also be set via environment variables prefixed with DT_:

| Option         | Environment Variable  | Default                                           |
|----------------|--------------------|--------------------------------------------------|
| `--apikey`     | `DT_APIKEY`        | — (required if not in config)                   |
| `--apiurl`     | `DT_APIURL`        | `http://localhost:8081/api/`                     |
| `--eoldata`    | `DT_EOLDATA`       | `https://endoflife.date/api/v1/products/full`   |
| `--telemetry`  | `DT_TELEMETRY`     | `on`                                             |
| `--loglevel`   | `DT_LOGLEVEL`      | `2`                                              |
---

## License

EOL-DT is free to use under the terms of the [LICENSE](LICENSE).  
It is provided as-is, without warranty or liability. See LICENSE for details.

## Telemetry & Privacy

EOL-DT may send usage and error data.  
For full details, including what data is collected and how to disable telemetry, see [PRIVACY.md](PRIVACY.md).
