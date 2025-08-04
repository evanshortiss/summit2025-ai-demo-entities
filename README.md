# AI-Powered Customer Service Platform - Backstage Catalog

This directory contains Backstage entity definitions for the AI-Powered Customer Service Platform, a comprehensive microservices architecture that leverages AI technologies for intelligent customer support.

## Architecture Overview

The platform consists of 10 microservices organized around a central message routing system using Apache Kafka and AI-powered processing with OpenAI and LangChain4j.

### System Components

- **Domain**: `customer-service` - Customer Service Operations
- **System**: `ai-customer-service-platform` - Main system containing all components
- **Resources**: Shared infrastructure (Kafka, PostgreSQL, OpenAI, Milvus)
- **Services**: 10 microservices handling different aspects of customer service
- **APIs**: REST and MCP APIs for external integration

## Services

### Core Services
- **router-ai**: Intelligent message classification and routing
- **moderation**: AI-powered content moderation
- **structured-output**: Information extraction from unstructured text

### Domain-Specific AI Assistants
- **support-ai**: AI support assistant with knowledge base
- **finance-ai**: AI finance assistant with MCP integration
- **website-ai**: AI website assistant

### Data & API Services
- **customer-data**: Customer data management
- **finance-api**: Financial records REST API
- **document-embedding**: Document embedding and vector storage
- **website-mcp**: MCP server for website operations

## Technology Stack

- **Framework**: Quarkus (Java)
- **Messaging**: Apache Kafka
- **Databases**: PostgreSQL, Milvus (Vector DB)
- **AI/ML**: OpenAI, LangChain4j
- **Protocols**: REST, MCP (Model Context Protocol)

## Message Flow

1. Messages enter through the **moderation** service for content filtering
2. **structured-output** extracts key information
3. **router-ai** classifies and routes messages to appropriate teams
4. Specialized AI assistants (**support-ai**, **finance-ai**, **website-ai**) handle domain-specific queries
5. Supporting services (**customer-data**, **finance-api**, **document-embedding**) provide data and context

## Team Ownership

- **platform-team**: Core routing and system infrastructure
- **ai-team**: AI processing services (document-embedding, structured-output)
- **support-team**: Support AI assistant
- **finance-team**: Finance services (AI and API)
- **website-team**: Website services (AI and MCP)
- **customer-team**: Customer data management
- **safety-team**: Content moderation

## Usage

To import this catalog into Backstage:

1. Add the location to your Backstage instance:
   ```yaml
   # In your Backstage app-config.yaml
   catalog:
     locations:
       - type: url
         target: https://github.com/summit2025-ai-demo/backstage-catalog-info/blob/main/catalog-info.yaml
   ```

2. Or use the Backstage UI to register the location:
   - Navigate to "Create" > "Register Existing Component"
   - Enter the URL to `catalog-info.yaml`

## File Structure

```
backstage-catalog-info/
├── catalog-info.yaml          # Main location entity
├── domain.yaml               # Customer service domain
├── system.yaml               # Main platform system
├── resources.yaml            # Shared infrastructure
├── apis.yaml                 # API definitions
├── services/                 # Individual service definitions
│   ├── customer-data.yaml
│   ├── document-embedding.yaml
│   ├── finance-ai.yaml
│   ├── finance-api.yaml
│   ├── moderation.yaml
│   ├── router-ai.yaml
│   ├── structured-output.yaml
│   ├── support-ai.yaml
│   ├── website-ai.yaml
│   └── website-mcp.yaml
└── README.md                 # This file
```

## Dependencies

Each service defines its dependencies on:
- Shared resources (Kafka, databases, external APIs)
- Other components (e.g., AI services depending on MCP servers)

The dependency graph helps visualize the service interactions and data flow through the platform. 