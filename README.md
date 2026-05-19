# DevOps Society x Elastic London Hack Night

Prerequisites and Instructions for 18th June Hack Night

## Details

## You will need

1. Your laptop!
2. The following software installed on your laptop:
* [Docker](https://docs.docker.com/get-started/get-docker/)
* [Docker Compose](https://docs.docker.com/compose/install/)
* [Claude Code](https://code.claude.com/docs/en/desktop)

## Setup

1. Clone (or fork first) the [Elastic OTel demo fork](https://github.com/elastic/opentelemetry-demo).
2. Register for an Elastic trial, via [this link](https://cloud.elastic.co/registration?tech=rtp&pg=global&plcmt=nav&cta=eswt-24503-b)
3. Create a new Serverless Observability project [as per these instructions](https://www.elastic.co/docs/solutions/observability/get-started#create-an-obs-serverless-project)
4. Connect your demo to an Elastic trial cluster [as per the README steps](https://github.com/elastic/opentelemetry-demo#docker).
5. Start the demo application

## Tools 

### Elastic Observability

1. See the [APM guide](https://www.elastic.co/docs/solutions/observability/apm) for details of available screens
2. Browse the Discover, Service Inventory and Traces screens to see the available data
3. Create Elasticsearch and Kibana API keys [as per these instructions](https://www.elastic.co/docs/deploy-manage/api-keys/elasticsearch-api-keys)

### Elastic Agent Builder

1. Follow the [getting started](https://www.elastic.co/docs/solutions/observability/get-started#create-an-obs-serverless-project) and chat with your telemetry data using the default agent
2. Create your own agent using [these instructions](https://www.elastic.co/docs/explore-analyze/ai-features/agent-builder/custom-agents)

### Elastic Observability MCP App

*Note: you will need a local Claude Code installation*

1. Download the MCP App [as per these instructions](https://github.com/elastic/example-mcp-app-observability#quick-start), and open the binary file
2. Add the cluster Elasticsearch endpoint and API keys to the MCP app settings
3. Add the respective skills
4. Try out the skills to see what information you can find

