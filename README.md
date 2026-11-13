# ZeroGuard AI

**AI-Powered SOC Automation & Zero Trust Security on Microsoft Azure**

ZeroGuard AI is a cybersecurity project that combines Zero Trust principles with a multi-agent AI-based Security Operations Center (SOC). It aims to help detect, investigate, enrich, and respond to security incidents through an automated workflow.

The project was developed as a Proof of Application (PFA) and deployed on Microsoft Azure.

## Project Overview

Traditional SOC operations often require analysts to manually correlate security events, investigate suspicious activity, enrich threat intelligence, and prepare incident reports.

ZeroGuard AI explores how specialized AI agents can automate parts of this workflow while integrating identity security, network monitoring, threat intelligence, and automated response.

## Architecture

The solution follows a distributed, microservices-based architecture composed of:

- **Multi-agent orchestrator:** Coordinates the seven main SOC agents.
- **Grafana VM:** Hosts Grafana dashboards and the FastAPI incident API.
- **Honeypot VM:** Hosts Cowrie and a dedicated FastAPI API for honeypot statistics.
- **Microsoft Entra ID:** Provides identity and authentication security.
- **Azure OpenAI:** Generates AI-assisted incident analysis and reports.
- **Azure Network Security Groups:** Supports network-level response actions.

### Main SOC Agents

| Agent | Responsibility |
|---|---|
| Identity Agent | Analyzes identity-related security events |
| Network Agent | Analyzes network information and suspicious IPs |
| Threat Intelligence Agent | Enriches indicators using AbuseIPDB and VirusTotal |
| Compliance Agent | Evaluates security and compliance considerations |
| SOAR Agent | Coordinates response actions, including NSG rules and Telegram alerts |
| Forensics Agent | Builds incident timelines and maps attack techniques |
| Audit Agent | Uses GPT-4o to generate incident reports |

An additional **Honeypot Agent** analyzes Cowrie activity and attack statistics.

## Technology Stack

| Category | Technologies |
|---|---|
| Cloud | Microsoft Azure |
| Identity | Microsoft Entra ID |
| AI | Azure OpenAI, GPT-4o |
| Backend | Python, FastAPI |
| Visualization | Grafana |
| Honeypot | Cowrie |
| Threat Intelligence | AbuseIPDB, VirusTotal |
| Notifications | Telegram Bot API |
| Security | Azure NSG, Zero Trust |
| Attack Simulation | Kali Linux |
| Framework | MITRE ATT&CK |

## Security Scenarios Tested

The project report documents several security scenarios:

- Password spraying against Microsoft Entra ID.
- Device Code OAuth phishing simulation.
- Detection of suspicious authentication activity.
- Enrichment of suspicious IP addresses using threat intelligence services.
- Automated incident notification through Telegram.
- Network-level response through Azure NSG.
- SSH attack capture and analysis using Cowrie.

The Device Code scenario was limited to generating the OAuth device code; token exploitation was deliberately excluded from the test.

## Reported Results

The following figures are taken from the project's validation results:

| Metric | Reported result |
|---|---:|
| Main SOC agents | 7 |
| Additional honeypot agent | 1 |
| Complete agent execution | 29.06 seconds |
| Honeypot attack events captured | Over 1,000 |
| MITRE ATT&CK techniques covered | 8 |
| Mean Time to Detect (MTTD) | Approximately 29 seconds |
| Mean Time to Respond (MTTR) | Approximately 8 seconds |

These are project-reported test results, not independent production benchmarks.

## Repository Contents

This repository is intended to contain:

- Technical documentation and architecture.
- Agent descriptions and workflow.
- Deployment and configuration documentation.
- Test scenarios and results.
- Selected screenshots and project evidence.

**Note:** The original Python source files are currently unavailable. This repository therefore documents the project and its reported implementation; it does not currently provide a complete runnable implementation.

## Security Notice

This project uses cloud services and external APIs. Never commit:

- Azure OpenAI API keys.
- AbuseIPDB or VirusTotal API keys.
- Telegram bot tokens.
- Private keys, certificates, or credentials.
- Sensitive tenant information or infrastructure details.

Use environment variables and a `.env.example` file containing placeholders for configuration.

## Project Context

Developed as a cybersecurity engineering PFA at EMSI, Morocco.

**Project:** ZeroGuard AI  
**Focus:** Cloud Security, Zero Trust, AI-driven SOC Automation, Threat Intelligence and Incident Response.
