# EOL-DT Telemetry & Privacy

EOL-DT may collect **anonymous usage and error data** to help improve the software. This includes:

- Exceptions and error messages
- OS and runtime version
- Module usage statistics
- Non-personal identifiers

## Web Server Logs / IP Addresses

When telemetry is sent to our server, the server **may automatically log your IP address**.  
This is standard for any web request and is used for server operations, not linked to any user identity.  

No other personal data (name, email, system user, etc.) is collected.

## How to Opt-Out

Telemetry can be disabled at runtime by setting one of the following:

### Environment Variables

```bash
# Linux / macOS
export DT_TELEMETRY=off

# Windows CMD
set DT_TELEMETRY=off

# Windows PowerShell
$env:DT_TELEMETRY="off"
