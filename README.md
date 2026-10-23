# Awesome-ML-Pipelines-Orchestration

# Top ML Pipelines & Orchestration Tools Ecosystem

**Curated List of SaaS Products & Open-Source GitHub Projects**  
*Focused on Multi-Backend Compute Coordination, Dynamic Workflows & Data Scientist Ergonomics*  
**Last updated: March 2026**

This repository tracks notable **SaaS platforms** and **open-source projects** for **ML Pipelines & Orchestration**. These tools coordinate the work of machine learning — scheduling training jobs across compute backends, managing dependencies, and handing off to model registries and serving infrastructure — without stitching together a dozen disconnected scripts.

**Examples** include Kubeflow Pipelines, Flyte, Metaflow, Apache Airflow, Dagster, Prefect, AWS SageMaker Pipelines, Azure ML Pipelines, Google Vertex AI Pipelines, and Databricks Workflows (the category leaders).

**Open-source emphasis**: This section is heavily expanded with every major active project for self-hosting, Kubernetes-native execution, and transparent pipeline definitions — ideal for ML platform teams supporting multiple model teams across heterogeneous compute backends.

Contributions welcome! Open a PR to add/update entries. Keep descriptions factual and link to official sites.

## Table of Contents
- [SaaS/Hosted Platforms](#saas-hosted-platforms)
- [Open-Source GitHub Projects](#open-source-github-projects)
- [How to Contribute](#how-to-contribute)
- [Disclaimer](#disclaimer)

## SaaS/Hosted Platforms

- **AWS SageMaker Pipelines** — **The most-mentioned MLOps platform in job listings for 2026** . **Full lifecycle coverage**: Pipelines, Studio, Model Registry, Endpoints, Model Monitor, Feature Store, and Clarify, all integrated with IAM, S3, VPC, and CloudWatch . **Strong foundation model story** via Bedrock and JumpStart, with mature governance through model cards, lineage tracking, and approval workflows for regulated industries . **The catch**: "twenty products in a trench coat" — figuring out which piece to use is its own learning curve, and costs add up fast if endpoint usage isn't monitored . **Best for AWS-native organizations of any size**, especially enterprises with compliance requirements .

- **Google Vertex AI Pipelines** — **KFP v2 OSS compatible**, giving teams portability between open-source Kubeflow Pipelines and managed GCP execution . **Gemini-first** with first-party access to Google's foundation models . **AutoML genuinely works** for tabular, vision, and text tasks without deep ML expertise . **The catch**: less mature than SageMaker on some governance and compliance fronts, and it locks you into GCP . **Best for GCP-native organizations** and teams building GenAI products on Gemini .

- **Azure Machine Learning Pipelines** — **MLflow native**, with broad compliance certifications (ISO, SOC, HIPAA, GDPR) and responsible AI dashboards for fairness, interpretability, and transparency . **Deep Azure DevOps integration** enables CI/CD extensions into continuous training and monitoring . **The catch**: workflows are optimized for Microsoft services, reducing cross-cloud portability . **Best for Microsoft-committed enterprises** .

- **Databricks Workflows** — **The Lakehouse architecture unifying data engineering and ML pipelines** through the medallion schema . **Delta Lake** manages dataset versioning and lineage, while **MLflow** provides experiment tracking, artifact logging, and model registry . **Databricks Asset Bundles and Terraform provider** express infrastructure as code for jobs, serving endpoints, and feature pipelines . **Best for organizations wanting one platform for data and ML** with reproducible feedback loops across data, model, and deployment pipelines .

## Open-Source GitHub Projects

- **Kubeflow Pipelines** — **The Kubernetes-native ML pipeline platform** — Apache 2.0 licensed, **14,500+ GitHub stars** . **KFP orchestrates end-to-end workflows** with APIs, SDKs, and REST API for CI/CD integration . **The installation requires Kubernetes expertise** — a master node needs 4 vCPU and 16 GB RAM . **KFP components are defined as Docker containers or DSL-decorated functions**, which forces packaging files and dependencies into images . **Deployment options**: standalone dev flavor for experiments, community distribution for production with RBAC and multi-tenancy, or Kubernetes Native API mode storing pipeline definitions as Custom Resources for GitOps workflows . **PostgreSQL is only supported for development** — production KFP uses MySQL-backed deployment because of a known concurrency limitation in MLMD's PostgreSQL backend . **The hard limit**: broad but operationally heavy — Kubernetes expertise is non-negotiable . **Best for organizations already standardized on Kubernetes** wanting end-to-end ML pipelines with a path to managed execution via Vertex AI Pipelines .

- **Flyte** — **The strongly typed, Kubernetes-native orchestrator built for reproducibility** — Apache 2.0 licensed . **Strongly typed interfaces validate data at every step** using Flyte types, catching errors before runtime . **Immutability** ensures reproducibility by preventing changes to execution state . **Data lineage** tracks movement and transformation throughout the workflow lifecycle . **Map tasks** enable parallel execution with minimal configuration . **Multi-tenancy** lets multiple users share the same platform while maintaining distinct data and configurations . **Dynamic workflows** can change and evolve as needed, with branching based on static or dynamic data . **Intra-task checkpointing** and **cache outputs** via `cache=True` . **GPU acceleration** and **spot/preemptible instance scheduling** via `interruptible=True` . **Flyte 2** (March 2026) adds **self-healing workflows** that recover from infrastructure-caused failures (OOM, container pre-emption) using infrastructure-as-context, with a local TUI for debugging and a Devbox for local development . **Best for teams wanting strong typing and reproducibility** on Kubernetes, especially those needing dynamic workflows and multi-tenancy .

- **Metaflow** — **The Python-loving data scientist's pipeline tool**, originally developed at Netflix to boost productivity across classical statistics and deep learning . **Python DSL** lets a scientist describe a workflow as decorated Python steps, and Metaflow handles versioning, scheduling, and resource provisioning . **The `spin` command** (Metaflow 2.19) executes a single `@step` with state carried over from the parent step, enabling notebook-like iterative development without losing production readiness . **Built-in configuration management** and **custom decorators** for domain-specific abstractions . **Scales horizontally and vertically** with task and data parallelism, supporting Ray, MPI, and Torch Distributed . **Deployment targets**: AWS Batch, Titus, Kubernetes, and now **Kubeflow Pipelines** via the Metaflow-Kubeflow integration (some features like conditional/recursive steps not yet supported) . **The hard limit**: AWS-first heritage — other clouds work but with more configuration . **Best for data scientists wanting to stay focused on modeling** rather than infrastructure, especially in Python-first teams .

- **Apache Airflow** — **The enterprise veteran with the largest ecosystem of ML compute backend integrations** — Apache 2.0 licensed, **3,000+ contributors** and **20M+ downloads/month** . **Provider packages include first-class integrations with SageMaker, Vertex AI, Databricks, MLflow, Weights & Biases, Hugging Face, and Kubernetes execution backends** . **Deferrable operators** keep long-running training jobs from consuming worker slots while waiting for completion . **Multi-cloud deployment** supports teams training on different clouds, and **KubernetesPodOperator** gives full control over GPU requests and node affinity . **The catch**: **high learning curve and DevOps difficulty** — it's a general-purpose orchestrator, not ML-specific . **Best for ML platform teams supporting multiple model teams across multiple compute backends** with governance and lineage requirements .

- **Dagster** — **The asset-centric orchestrator for ML/AI pipelines** — Apache 2.0 licensed . **Asset-based design** maps cleanly to ML asset pipelines (datasets, features, trained models), with **best data lineage** for visualizing dependencies across the pipeline . **Type system catches errors before runtime**, and **built-in testing** makes unit testing pipelines easy . **Integrations with MLflow, Weights & Biases, and major ML compute backends** . **Best for RAG pipelines, embedding generation, and ML feature engineering** where asset-state-centric thinking matches the work . **Note**: Prefect has announced an agreement to acquire Dagster Labs (transaction not yet closed), with continuity commitments for now .

- **Prefect** — **The developer-friendly general-purpose orchestrator** — Apache 2.0 licensed, **17,700+ GitHub stars** . **Decorator-style `@flow` and `@task`** wrap ML training and inference logic with **low-to-medium learning curve** . **Prefect Cloud provides managed orchestration**, while the hybrid model lets execution happen in customer infrastructure via outbound-only workers . **Best for small ML teams** wanting simpler setup than Airflow .

### Additional Strong Open-Source Options

- **TFX (TensorFlow Extended)** — Production ML platform that runs on multiple orchestrators (Apache Beam, Apache Airflow, Kubeflow Pipelines, Vertex AI Pipelines), meaning a single TFX pipeline definition can move between local development, on-premise Kubernetes, and managed cloud execution . Best for teams wanting orchestrator portability.
- **Valohai** — Open-core MLOps platform with pipeline orchestration and experiment tracking. **Best for teams wanting a managed-or-self-hosted hybrid** with strong pipeline visualization.
- **ClearML** — Apache-2.0 licensed platform bundling experiment tracking with task orchestration, agent-based scheduling, and automatic logging of code state, dependency hashes, and random seeds — the most convenient out-of-the-box reproducibility coverage among open-source platforms . Best for teams managing multi-GPU distributed training wanting tracking, pipeline scheduling, and agent management from one tool.

**Frameworks for building custom systems**: Combine **Kubeflow Pipelines** for Kubernetes-native pipeline orchestration with KFP v2 portability to Vertex AI, **Flyte** for strongly typed reproducible workflows with self-healing execution and multi-tenancy, **Metaflow** for Python-native data scientist workflows with notebook-like `spin` iteration, **Dagster** for asset-centric ML pipelines with strong lineage, **Apache Airflow** for multi-backend compute coordination with the broadest integration ecosystem, and **Prefect** for simpler Python-native orchestration — to build an ML pipeline stack tailored to your team's DevOps capacity, compute backends, and governance requirements.

## How to Contribute

1. Fork the repo.
2. Add/edit entries in `README.md` (follow existing format).
3. Include: name, link, 1–2 sentence description, and whether it's SaaS or open-source.
4. Submit PR with a short explanation.

Star the repo if you find it useful!

## Disclaimer

- This is a **community-curated** list — not exhaustive and not an endorsement.
- ML pipeline orchestration tools differ significantly in abstraction level, Kubernetes dependency, and data scientist ergonomics. **Kubeflow Pipelines is powerful but operationally heavy** — it requires Kubernetes expertise and a master node with 4 vCPU and 16 GB RAM, and production deployments use MySQL because of a known PostgreSQL concurrency limitation in MLMD . **Flyte's strong typing catches errors before runtime** but requires learning its type system and Kubernetes deployment model . **Metaflow has the easiest DevOps experience** for Python data scientists, but its AWS heritage means other clouds require more configuration, and the Kubeflow integration doesn't yet support conditional/recursive steps . **Apache Airflow has the broadest ML integration ecosystem** but a high learning curve; **Dagster is asset-centric** with better lineage but a smaller integration ecosystem; **Prefect is simpler** for small teams . **Prefect has announced an agreement to acquire Dagster Labs** (transaction not yet closed) — factor vendor continuity into roadmap decisions . **Cloud-managed pipelines (SageMaker, Vertex, Azure ML) eliminate operational burden** at the cost of cloud lock-in .
- Self-hosted open-source solutions require proper Kubernetes cluster configuration (for Kubeflow and Flyte), database backend management (MySQL for production KFP), and someone on the team who owns the infrastructure — "free" self-hosted still has a headcount cost.

---

**Made for ML platform engineers and data scientists orchestrating pipelines across heterogeneous compute backends.**
Let's make ML pipelines and orchestration more open, reproducible, and compute-aware.
