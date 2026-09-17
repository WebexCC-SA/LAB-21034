---
#icon: material/folder-open-outline
icon: material/server-network
---

## Integrate MCP Server Overview

**MCP (Model Context Protocol)** is a standardized framework for exchanging contextual information between AI models and external systems. By connecting an MCP server to your Webex AI Agent, you can expose pre-built tools — such as pharmacy lookups and order status checks — without rebuilding the same logic in every voice flow.

### Why Use MCP?

- **Reuse fulfillment logic** across multiple AI agents
- **Connect to external tools** with minimal flow configuration
- **Scale integrations** by adding tools on the server rather than in each flow

### Tools in This Lab

The MCP server deployed for Cisco Event Health includes:

1. **Check pharmacy and clinic locations** — addresses stored on the MCP server
2. **Check medication order status** — queries the order API by order ID

### Call Flow

Attendee asks a question → Webex AI Agent → MCP Server tool → External API or data source → Response returned to the agent → Attendee receives the answer.

---

Proceed to the guide below to register the Agentic App, enable it in Collaboration Control Hub, and connect MCP tools to your AI agent.
