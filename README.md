## Webhook Platform

### Overview 
This platform accepts webhook events via HTTP POST being sent by a service to another service. It stores them in Postgres and guarantees at-least once delivery to registered endpoints. The platform tracks delivery status, retries on failure with backoff mechanisms and retries undeliverable events or requests to a queue. It will ensure that the request is eventually sent to the service thus acting also as a message queue. 

In the case of failures, an incident response agent built with LangGraph will identify the issue and report back using the Loki/Grafana/Promethues/Tempo stack. It will also diagnose the failure and wait for human approval before executing the resolution.

### High level Architecture
#### Infra and Cluster
Hetzner Cloud
Terraform
K3s

#### Core application service
Go service
Postgres

#### Observability
Loki
Grafana
Tempo
Promethues


### Build Phases 
Phase 1: Cluster Infra
Goal: Bring up a self-operated k3s cluster on Hetzner using Terrafor, Cilium and Hubble
- [ ] Provision 3 Hetzner VMs (cx22) via Terraform  
- [ ] Configure private networking and firewall  
- [ ] Create a load balancer with Terraform  
- [ ] Install k3s on the control-plane node  
- [ ] Install Cilium as CNI  
- [ ] Verify the cluster and traffic flows with Hubble

Phase 2: Webhook services and gateway
Phase 3
Phase 4
Phase 5

### Repository Structure
```
webhook-platform/
├── README.md
├── infra/
└── terraform/
```
