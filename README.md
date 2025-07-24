# AWS Fault Injection Service (FIS) MCP Server

This MCP server provides tools for working with AWS Fault Injection Service (FIS), allowing users to create, manage, and execute fault injection experiments.

## Overview

AWS Fault Injection Service (FIS) is a managed service that enables you to perform fault injection experiments on your AWS workloads. This MCP server provides capabilities to interact with FIS, making it easier to create and manage chaos engineering experiments.

## Features

- List and retrieve experiment templates
- Create and delete experiment templates
- Start and stop experiments
- List available action types
- Generate example templates

## Installation

1. Clone the repository:
```bash
git clone https://github.com/RadiumGu/AWS-FIS-MCP.git
cd AWS-FIS-MCP
```

2. Install `uv` from [Astral](https://docs.astral.sh/uv/getting-started/installation/) or the [GitHub README](https://github.com/astral-sh/uv#installation)

3. Install Python using `uv python install 3.10`

4. Set up a virtual environment:
```bash
uv venv
source .venv/bin/activate
uv pip install -e .
```

5. Run the MCP server:
```bash
uv run aws_fis_mcp/server.py
```

6. Connect to your MCP server with Amazon Q Developer CLI:
```json
"aws_fis_mcp": {
    "autoApprove": [],
    "disabled": false,
    "command": "uv",
    "args": [
        "--directory",
        "/home/ec2-user/mcp-servers/fis-mcp",
        "run",
        "aws_fis_mcp/server.py"
    ],
    "env": {
        "MCP_TRANSPORT": "stdio",
        "AWS_PROFILE": "default",
        "AWS_REGION": "us-east-2"
    },
    "transportType": "stdio"
}
```

Alternatively, you can use the provided `mcp_config.json` file as a reference for your MCP configuration.

## Available Tools

### Experiment Templates
- `list_experiment_templates`: List all AWS FIS experiment templates
- `get_experiment_template`: Get detailed information about a specific template
- `create_experiment_template`: Create a new experiment template
- `delete_experiment_template`: Delete an experiment template

### Experiments
- `list_experiments`: List all AWS FIS experiments
- `get_experiment`: Get detailed information about a specific experiment
- `start_experiment`: Start a new experiment based on a template
- `stop_experiment`: Stop a running experiment

### Action Types
- `list_action_types`: List all available AWS FIS action types
- `generate_template_example`: Generate an example template for a given target and action type

## Example Usage

Once connected to Amazon Q with the MCP server running, you can use commands like:

```
List all my FIS experiment templates in us-west-2
```

```
Start an experiment using template exp-12345abcde in us-east-1
```

```
Generate an example template for stopping EC2 instances
```

## Requirements

- Python 3.10+
- boto3
- AWS credentials configured with appropriate permissions for FIS

## License

This project is licensed under the MIT License - see the LICENSE file for details.