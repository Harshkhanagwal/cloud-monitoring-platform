# Project Overview – Cloud Infrastructure Monitoring & Incident Management Platform

## 1. Overview – What is this project?

We are building a centralized Cloud Infrastructure Monitoring and Incident Management Platform that will help users monitor Linux servers, identify infrastructure problems, investigate incidents, and manage services from a single dashboard.

The platform will continuously collect server performance metrics, monitor running applications and Docker containers, and detect abnormal conditions such as high CPU usage, memory exhaustion, disk space issues, application failures, or server downtime.

When an issue is detected, the platform will automatically generate an incident, collect relevant system information, and use Generative AI to analyze the problem, identify possible root causes, and suggest troubleshooting steps.

The primary objective is to simplify infrastructure monitoring and incident investigation while reducing the manual effort required from system administrators and operations teams.

## 2. Issues We Are Going to Handle

The platform will focus on identifying and managing the following infrastructure and operational issues:

A. Server Resource Issues

- High CPU utilization or unexpected CPU spikes.
- Excessive RAM consumption and memory exhaustion.
- Low disk space or disk utilization reaching critical levels.
- Unusual network traffic or connectivity issues.
- High system load and performance degradation.

B. Server Availability Issues

- Linux server becoming unreachable.
- Unexpected server downtime.
- Monitoring agent becoming unavailable.
- Server performance becoming unstable.

C. Application Issues

- Application or backend service crashing.
- Application becoming unresponsive.
- Unexpected process termination.
- Application errors and abnormal behavior.

D. Docker Container Issues

- Docker container unexpectedly stopping.
- Container becoming unhealthy.
- Excessive CPU or memory consumption by a container.
- Application running inside a container becoming unavailable.

E. Operational Issues

- Repeated infrastructure failures.
- Recurring performance problems.
- Difficulty identifying the cause of an incident.
- Lack of centralized visibility into server health and operational issues.

## 3. Basic Approach – What Happens When an Issue Occurs?

Let's understand the complete workflow using an example of a server experiencing a sudden CPU spike.

## Incident handling workflow

1. Issue Detection
    
    The monitoring agent continuously collects server metrics. It detects that CPU utilization has reached 95%.
    
2. Data Collection
    
    The agent collects relevant information, such as CPU usage, memory utilization, running processes, system logs and application status.
    
3. Backend Processing
    
    The agent sends the collected information to our FastAPI backend, where the incoming data is validated and processed.
    
4. Incident Generation
    
    The monitoring engine checks the configured thresholds and generates an incident because CPU utilization has exceeded the permitted limit.
    
5. Investigation
    
    The system gathers additional information relevant to the incident, such as resource consumption by individual processes and recent application logs.
    
6. AI-Powered Analysis
    
    Generative AI analyzes the collected information, identifies possible reasons behind the CPU spike, and prepares troubleshooting recommendations.
    
7. Dashboard Notification
    
    The incident and its diagnostic report are displayed on the React dashboard with severity, affected server, issue details and recommendations.
    
8. Resolution
    
    The administrator reviews the findings, performs the required corrective action, and marks the incident as resolved after verification.
    

This same approach will be used for other issues, including memory exhaustion, disk space problems, stopped containers, application failures and server downtime.

## 4. How Generative AI Will Help

Generative AI will act as an intelligent diagnostic assistant within our platform.

Traditional monitoring can tell us that something is wrong. Generative AI will help us understand why it might be happening and what we should investigate next.

Its responsibilities will include:

- Metric Analysis: Analyze CPU, RAM, disk and network utilization to understand abnormal resource consumption.
- Log Analysis: Examine relevant system and application logs to identify errors and unusual events.
- Root Cause Investigation: Correlate available metrics, process information and logs to identify potential causes of an incident.
- Troubleshooting Recommendations: Suggest practical steps that administrators can follow to investigate and resolve problems.
- Incident Summarization: Generate easy-to-understand summaries explaining what happened, when it happened and which server was affected.
- Recurring Issue Analysis: Help identify patterns in repeated incidents and suggest areas requiring further investigation.

Example:

AI Diagnostic Report

Critical

Incident: High CPU utilization – Server 01

Detected issue

CPU utilization reached 95% and remained above the configured threshold.

Possible cause

A background process is consuming excessive CPU resources.

Recommended investigation

1. Identify the top CPU-consuming processes.
2. Inspect the process and its parent application.
3. Review recent application logs.
4. Investigate whether the behavior is expected.

Suggested next step

Investigate the process responsible for the abnormal CPU consumption before taking corrective action.

Illustrative AI output, not an actual diagnosis.

We will use LangChain for LLM integration and LangGraph for structured, multi-step diagnostic workflows.

Initially, AI will only provide analysis and recommendations. Actual corrective actions will remain under administrator control.

## 5. Technology Stack and Its Responsibilities

| Technology | Purpose |
| --- | --- |
| React.js | Build the centralized monitoring and incident management dashboard. |
| Python | Develop the monitoring agent and backend functionality. |
| FastAPI | Build REST APIs, receive monitoring data and manage incidents. |
| MongoDB | Store server information, metrics, incidents and diagnostic reports. |
| Linux (Kali VM) | Simulate the cloud-hosted Linux servers for initial development and testing. |
| Docker | Containerize our demo application and monitoring agent so they can run on the Linux VM. |
| LangChain | Integrate LLMs and process AI diagnostic requests. |
| LangGraph | Build multi-step AI investigation workflows. |
| AWS EC2 | Host our infrastructure when we move beyond local testing. |
| Git & GitHub | Source control and team collaboration. |

Important clarification about Docker:

Docker will not be used to containerize our entire development platform initially.

We will use it specifically for:

- Creating a demo application container to simulate a deployed cloud application.
- Creating a monitoring agent container that runs on Linux and monitors the relevant environment.
- Simulating application and container failures for testing.

Our React frontend, FastAPI backend and MongoDB will run on the main development machine initially.

## 6. Initial Infrastructure and Hosting Environment

For the initial development stage, we will use a Kali Linux Virtual Machine as our local cloud hosting environment.

The purpose is to simulate a real Linux server environment without immediately requiring paid cloud infrastructure.

Our setup will look like this:

!image.png

Once the local implementation is stable, we will move the demo application and monitoring workloads to AWS EC2 and connect them to the same centralized platform.

## 7. Final Project Objective

Our ultimate goal is to develop a platform that brings together:

1. Centralized Linux infrastructure monitoring.
2. Docker container monitoring.
3. Automated infrastructure issue detection.
4. Incident creation and lifecycle management.
5. AI-powered incident investigation and troubleshooting.
6. Centralized infrastructure visibility through a web dashboard.
7. Future support for monitoring remotely hosted AWS infrastructure.

In simple terms: We are building a platform that detects infrastructure problems, gathers the information needed to investigate them, uses Generative AI to help explain what went wrong, and provides administrators with a centralized place to manage and resolve those incidents.

[](https://app.notion.com/p/41648fb978d1802fb6deec9eed6a6da3?pvs=21)