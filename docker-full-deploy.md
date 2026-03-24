# Download the latest Dependency-Track Docker Compose file
curl -LO https://dependencytrack.org/docker-compose.yml

# Start the stack using Docker Compose (creates the fixed network automatically)
docker compose up -d

# Pull your eol-dt Docker image
docker pull yourdockerhubusername/eol-dt:latest

# Run the eol-dt container in the same network as Dependency-Track
docker run --rm \
    --network dtrack-net \
    -e DT_APIURL="http://apiserver:8080" \
    -e DT_APIKEY="YOUR API KEY" \
    yourdockerhubusername/eol-dt:latest
