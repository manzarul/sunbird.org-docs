---
title: Load Balancer Setup
page_title: Load Balancer Setup
description: Information about how to set up the Load Balancers
keywords: Load Balancers, load, Agent Swarm, Keycloak swarm, Swarm, services, KP-LB Services, DP-LB Services, setup
allowSearch: true
---

## Overview

Load Balancers are required to scale your applications and create a high availability for your services. Balancing the load provides
low latency and high throughput, and scales up to millions of flows for all TCP and UDP applications.

The Load Balancer distributes new inbound flows that arrive on its frontend to backend pool instances, as per rules and health probes that are set. This page provides details to set up the Agent Swarm, Keycloak Swarm, KP-LB services and the DP-LB services 

## Agent Swarm
To setup Agent Swarm, execute the following instructions for each of the mentioned fields: 
- Frontend ip configuration - attach public ip
- Backend pools - attach agent vm's or availability set of agent group
- Health Probes/check - Configure path and port - 80 and 443 (both)
- EX: name: http 
- Protocol: TCP 
- Port: 80 
- Interval: 5 
- Unhealthy threshold: 2
- Load Balancing rules - Frontend-ip-config,Frontend-port,backend-port, Backend-pool and health-probe
- Ex: Frontend-port: 80
- backend-port: 80
> **Note:** Follow similar steps for port 443


## Keycloak Swarm
To setup Keycloak Swarm, execute the following instructions for each of the mentioned fields: 
- Frontend ip configuration - Internal ip by default
- Backend pools - attach keycloak vm or availability set of keycloak group
- Health Probes/check - Configure path and port - 8080
- EX: name: keycloakhealth 
- Protocol: TCP 
- Port: 8080 
- Interval: 5 
- Unhealthy threshold: 2
- Load Balancing rules - Frontend-ip-config,Frontend-port, backend-port, Backend-pool and health-probe
- Ex: Frontend-port: 80
- backend-port: 8080

## KP-LB Services
To setup KP-LB services, execute the following instructions for each of the mentioned fields: 
- Frontend ip configuration - Internal ip by default
- Backend pools - attach vm's of learning and search or availability set for learning and search
- Health Probes/check - Configure path and port - 8080 (for learning) and 9000 (for search)
- EX: name: learninghealth 
- Protocol: http 
- Port: 8080 
- Path: /learning-service/health
- Interval: 5 
- Unhealthy threshold: 2
- Frontend-port: 8080
- Backend-port: 8080

- Name: searchhealth 
- Protocol: http 
- Port: 9000 
- Path: /health 
- Interval: 5 
- Unhealthy threshold: 2
- Load Balancing rules - Frontend-ip-config, Frontend-port, Backend-port, Backend-pool and health-probe
Example: Frontend-port: 9000
Backend-port: 9000

## DP-LB Services (Analytics Api)
To setup DP-LB services, execute the following instructions for each of the mentioned fields: 
- Frontend ip configuration - Internal ip by default
- Backend pools - attach vm's of analytics-api or availability set for analytics-api group
- Health Probes/check - Configure path and port - 9000
- EX: name: analyticshealth 
- Protocol: tcp 
- Port: 9000 
- Interval: 5 
- Unhealthy threshold: 2
- Load Balancing rules - Frontend-ip-config,Frontend-port, backend-port, Backend-pool and health-probe
Example: Frontend-port: 9000
Backend-port: 9000

