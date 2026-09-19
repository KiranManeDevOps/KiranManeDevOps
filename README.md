# Kiran Mane

DevOps engineer in Pune, India. I run on-premises RKE2 Kubernetes and AWS EKS platforms
end to end — from bare metal and Terraform through storage, backup, security and observability.

## What I've built

**On-prem Kubernetes**
- Built RKE2 clusters on bare metal, 3–7 nodes, from machine provisioning through MetalLB, Traefik, cert-manager, kube-vip and Calico default-deny NetworkPolicy.
- Run both Rook-Ceph and node-local TopoLVM, and pick per cluster: Ceph where the network and drives justify replicated storage, TopoLVM where predictable low latency and a small operational surface matter more — then covered what node-local storage gives up with Velero, VolSync/restic and `pg_dumpall` into MinIO (24-hour RPO).
- Deployed a hybrid PostgreSQL on Kubernetes — durable data and WAL on separate, differently provisioned volumes, and sort/hash scratch on a RAM-backed tablespace — improving query performance by **40–70%** under production load with `fsync` and `synchronous_commit` left on.
- Migrated live ingress from Nginx Proxy Manager to Traefik, including root-causing a production outage traced to a config key that is valid in K3s and fatal in RKE2.

**Disaster recovery & reliability**
- Automated DR failover for a GPU-backed on-prem AI service: detects the failure, scales a standby AWS environment (including on-demand GPU capacity), and switches Route 53 traffic — recovery in minutes, near-zero data loss via continuous replication.
- Automated voice-service monitoring that detects production failures, alerts with context and triggers rolling restarts — MTTR from hours to minutes.
- Root-caused a recurring high-CPU incident in a messaging system and replaced the manual fix with an automated remediation service.

**Observability & AIOps**
- Built an AI-powered SRE investigation platform: give it a symptom and a time window, and it correlates Prometheus, SigNoz/OpenTelemetry traces, logs and Percona PMM into a timeline, tested root-cause hypotheses and a remediation plan, with an LLM (Claude API) narrating the findings.
- Wrote a cluster monitoring service in Python/FastAPI — 70 Prometheus-backed health checks every 30 seconds, capacity forecasting and per-rule alert routing to Slack, Teams, Discord, PagerDuty, email and webhooks, with no extra cluster permissions.

**AWS**
- Migrated a live application across AWS regions and accounts with zero downtime using weighted Route 53 traffic shifting.
- Cut monthly cloud spend by 27% in four months through rightsizing and resource lifecycle policies.
- One Terraform codebase across dev/qa/uat/prod — EKS with IRSA-scoped service accounts, Graviton Spot node groups behind cluster-autoscaler, HPA and PodDisruptionBudget on every deployment, ECS alongside it, and scheduled off-hours teardown of non-production compute, databases and managed Airflow.
- Managed IAM and least-privilege access across 17 AWS accounts; Kubernetes RBAC on EKS (IAM-integrated) and RKE2 (Rancher).

**Security & CI/CD**
- OIDC federation so on-prem workloads assume AWS IAM roles for S3 — no static credentials between environments.
- Removed hardcoded credentials by fetching AWS Secrets Manager values at container startup across EKS and ECS.
- Trivy, ECR scan-on-push and SonarQube in the pipeline; WAF with geo-restriction rules for production apps.
- Jenkins CI/CD across build, test and deploy; GitOps delivery with Helm and Argo CD.

## Featured projects

| Project | What it is |
|---|---|
| [**bare-metal-kubernetes**](https://github.com/KiranManeDevOps/bare-metal-kubernetes) | Two on-premises RKE2 platforms built from bare metal: architecture and build order, the Rook-Ceph vs TopoLVM storage decision, backup/DR, Jenkins as code, and sanitized manifests. |
| [**sre-investigation-platform**](https://github.com/KiranManeDevOps/sre-investigation-platform) | Design of an AI-assisted incident investigation platform: anomaly onset detection, hypotheses that are tested rather than listed, explainable confidence, and blast radius — a deterministic engine computes, the model only narrates. |

## Tools

**Kubernetes** RKE2 · EKS · ECS · Rancher · Helm · Docker<br>
**Networking & storage** MetalLB · Traefik · cert-manager · Calico · Rook-Ceph · TopoLVM · MinIO<br>
**Backup & DR** Velero · VolSync · Route 53 failover<br>
**IaC & delivery** Terraform · CloudFormation · Ansible · Proxmox · Jenkins · Argo CD · AWS CodePipeline<br>
**Observability** Prometheus · Grafana · SigNoz · OpenTelemetry · Percona PMM · CloudWatch · Kubecost<br>
**AWS** EC2 · EKS · ECR · IAM · VPC · S3 · RDS · ElastiCache · OpenSearch · Lambda · SQS · SNS · CloudFront · WAF · Secrets Manager<br>
**Security** Trivy · SonarQube · OIDC federation · Kubernetes RBAC<br>
**Code** Python · Bash · Groovy · Claude API

## Certifications

- Executive PG Certification in Cloud Computing and DevOps — iHub Divya Sampark, IIT Roorkee
- Advanced PG Certificate in AI Engineering on Cloud and AIOps — IIT Roorkee *(in progress)*

Most of what I build lives in private infrastructure repositories; the projects above are the public slice of it.

📫 [kiranmane0074@gmail.com](mailto:kiranmane0074@gmail.com)
