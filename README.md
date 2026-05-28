# DevOps Society x Elastic London Hack Night

Prerequisites and Instructions for 18th June Hack Night

## Details

## You will need

1. Your laptop!
2. The following software installed on your laptop:
* [Docker](https://docs.docker.com/get-started/get-docker/)
* [Docker Compose](https://docs.docker.com/compose/install/)
* [Claude Code](https://code.claude.com/docs/en/desktop)

## Objective
This is an open challenge to setup your own agents and MCP tools and apps to find and fix issues within a complex application ecosystem. Prizes will be awarded for the most novel 

## Cluster Setup

1. Register for an Elastic trial, via [this link](https://cloud.elastic.co/registration?tech=rtp&pg=global&plcmt=nav&cta=eswt-24503-b)
2. Create a new Serverless Observability project [as per these instructions](https://www.elastic.co/docs/solutions/observability/get-started#create-an-obs-serverless-project)
3. Create Elasticsearch and Kibana API keys [as per these instructions](https://www.elastic.co/docs/deploy-manage/api-keys/elasticsearch-api-keys)

## App Setup

1. Fork and clone the [Elastic OTel demo fork](https://github.com/elastic/opentelemetry-demo).
2. Connect your demo to an Elastic trial cluster by adding your cluster endpoint and key to `.env.override` (see sample below):

```zsh
ELASTIC_OTLP_ENDPOINT="https://my-cluster.ingest.northeurope.azure.elastic.cloud:443"
ELASTIC_OTLP_API_KEY="MyRandomAPIKey"
```

3. Add the OTel processor for Elastic Streams integration:

Processors:

```
processors:
  batch:
  transform/logs-streams:
    log_statements:
      - context: resource
        statements:
          - set(attributes["elasticsearch.index"], "logs.otel")
```



4. Start the demo application:

```
./demo.sh docker

# Alt with Kubernetes
./demo.sh k8s
```

Adding processor to logs pipeline:

```
service:
  pipelines:
    logs:
      exporters:
        - debug
        - otlphttp/elastic
      processors:
        - batch
        - transform/logs-streams
```

## Tools 

### Elastic Observability

1. See the [APM guide](https://www.elastic.co/docs/solutions/observability/apm) for details of available screens
2. Browse the Discover, Service Inventory and Traces screens to see the available data

### Elastic Agent Builder

1. Follow the [getting started](https://www.elastic.co/docs/solutions/observability/get-started#create-an-obs-serverless-project) and chat with your telemetry data using the default agent
2. Create your own agent using [these instructions](https://www.elastic.co/docs/explore-analyze/ai-features/agent-builder/custom-agents)

### Elastic Observability MCP App

*Note: you will need a local Claude Code installation*

1. Download the MCP App [as per these instructions](https://github.com/elastic/example-mcp-app-observability#quick-start), and open the binary file
2. Add the cluster Elasticsearch endpoint and Elasticsearch and Kibana API keys to the MCP app settings, similar to the below screenshot:

<img width="1483" height="1068" alt="Sample cluster details for Elastic Observability MCP app" src="https://github.com/user-attachments/assets/ef4793d0-e264-4530-813b-d5c4d5e47a9b" />

3. Configure permissions for the respective tools
4. Try out the tools to see what information you can find, such as the observe tool


*(Note that the tool `k8s-blast-radius` requires a Kubernetes setup rather than vanilla Docker)*

