# aiosplunkbase

A simple async API client for interacting with Splunk's Splunkbase service.

## Installation

You can install aiosplunkbase using pip:

```bash
pip install aiosplunkbase
```

## Features

- Asynchronous API client for Splunkbase
- App information retrieval (releases, Splunk version compatibility, etc)
- App downloading

## Usage Examples

### Usage

```python
from aiosplunkbase import SBClient
from pprint import pprint

async def main():
    # Initialize the client
    async with SBClient(username="your_username", password="your_password") as client:
        # Login to Splunkbase
        await client.login()
        
        # Get app information
        app_info = await client.get_app_info("Splunk_TA_aws")
        pprint(app_info)

        # Get latest compatible release for specific Splunk version
        latest_version = await client.get_app_latest_version(
            "Splunk_TA_aws",
            splunk_version="9.0.0",
            is_cloud=False
        )
        pprint(latest_version)

        # Download an app
        async for chunk in client.download_app("Splunk_TA_aws"):
            # Process chunks as needed
            pass
```

## License

MIT License