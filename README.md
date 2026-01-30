# AI Agent Swarm Spike

This repository contains an experimental spike investigating how agentic frameworks can be used to manage a swarm of AI agents working together to accomplish complex tasks.

## Prequisites

- [Python](https://docs.python.org/3/using/index.html) `>= 3.13.7` - We recommend using [uv](https://docs.astral.sh/uv/getting-started/installation/) to manage your Python environment.
- [pipx](https://pipxproject.github.io/pipx/installation/)
- [uv](https://docs.astral.sh/uv/getting-started/installation/)
- [Amazon Bedrock Access](https://aws.amazon.com/bedrock/) - Ensure you have either IAM user credentials or a [Bedrock API Key](https://docs.aws.amazon.com/bedrock/latest/userguide/api-keys-use.html) with appropriate permissions.
- [Docker](https://docs.docker.com/get-docker/) - Optional if you want to run the OpenTelemetry Collector for tracing.

## Setup

### Python Environment

Please install python `>= 3.13.7` and `pipx` in your environment. This project uses [uv](https://github.com/astral-sh/uv) to manage the environment and dependencies.

```python
# install uv via pipx
pipx install uv

# sync dependencies
uv sync
```

### Environment Variables

This project uses a `.env` file stored in the `./notebooks` directory to manage environment variables. An example `.env.example` file is provided. Please copy this file to `./notebooks/.env` and fill in the required values.

```bash
cp notebooks/.env.example notebooks/.env
```

Below is a description of the environment variables:

| Variable                    | Required | Default               | Description                                      |
|-----------------------------|----------|-----------------------|--------------------------------------------------|
| `AWS_REGION`                | Yes      | `eu-west-2`           | AWS region where Bedrock is hosted              |
| `AWS_BEARER_TOKEN_BEDROCK`  | Yes      | None                  | Bearer token for accessing Amazon Bedrock       |
| `OTEL_EXPORTER_OTLP_ENDPOINT` | No     | None                  | OpenTelemetry endpoint for exporting traces     |

For Amazon Bedrock, you can also set up your AWS credentials using the standard AWS environment variables (`AWS_ACCESS_KEY_ID` and `AWS_SECRET_ACCESS_KEY`). However, we recommend that you use the `AWS_BEARER_TOKEN_BEDROCK` for simplicity.

### OpenTelemetry (Optional)
If you want to enable tracing, you can run an OpenTelemetry Collector using Docker. We recommend using [otel-tui](https://github.com/ymtdzzz/otel-tui) to store and visualise traces.

You can run the otel-tui Docker container with the following command:
```bash
docker run --rm -it -p 4318:4318 --name otel-tui ymtdzzz/otel-tui:latest
```

Make sure to set `OTEL_EXPORTER_OTLP_ENDPOINT` in your `.env` file to enable tracing.

## Notebooks

The experiments are contained within Jupyter notebooks located in the `notebooks/` directory. There are two main categories of notebooks:
* Scrapers - Notebooks that scrape and prepare data for analysis.
* Swarms - Notebooks that demonstrate multi-agent AI swarms analyzing the prepared data.

Further documentation is provided within each notebook and in the [Experiment Writeup](experiment-writeup.md).
