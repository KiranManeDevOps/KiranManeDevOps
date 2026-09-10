# Kiran Mane

DevOps engineer in Pune, India. Four years, mostly AWS and Kubernetes. Right now that
means running on-premises RKE2 clusters and AWS EKS platforms end to end.

**What that has meant in practice:**

- Built RKE2 Kubernetes clusters on bare metal, 3–7 nodes, from machine provisioning through MetalLB, Traefik, cert-manager, kube-vip, and Calico default-deny NetworkPolicy.
- Moved cluster storage off Rook-Ceph onto TopoLVM once it was clear the hardware — 1 GbE, HDD-backed — was never going to meet Ceph's requirements, then rebuilt the backup story around VolSync/restic and `pg_dumpall` into MinIO to cover what node-local storage gives up.
- Wrote the cluster's monitoring service myself: ~3,800 lines of Python on FastAPI, running 70 Prometheus-backed health checks every 30 seconds with capacity forecasting and alert routing across five channels. No kubeconfig, no pod exec, no extra cluster permissions.
- Migrated live ingress from Nginx Proxy Manager to Traefik, including root-causing and recovering a production outage traced to a config key that is valid in K3s and fatal in RKE2.
- On AWS: one Terraform codebase across dev/qa/uat/prod — EKS with IRSA-scoped service accounts, Graviton Spot node groups behind cluster-autoscaler, HPA and PodDisruptionBudget on every deployment, ECS alongside it, and scheduled off-hours teardown of non-production compute, databases and managed Airflow.

**Tools** Kubernetes · RKE2 · EKS · ECS · Terraform · Helm · Docker · Jenkins · Prometheus · Grafana · SigNoz · Rook-Ceph · TopoLVM · MetalLB · Traefik · cert-manager · Calico · VolSync · MinIO · Python · Bash

Executive PG Certification in Cloud Computing and DevOps, iHub Divya Sampark at IIT Roorkee.

Most of what I build lives in private infrastructure repositories; GitHub is the public slice of it.

📫 [kiranmane0074@gmail.com](mailto:kiranmane0074@gmail.com)
