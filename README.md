<!-- ===== HEADER ===== -->
<a href="#">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=0:0b1e3f,100:2a5298&height=200&section=header&text=Amirmahdi%20Golahmar&fontSize=48&fontColor=ffffff&animation=fadeIn&fontAlignY=35&desc=Backend%20%26%20Platform%20Engineer%20%7C%20Computer%20Engineering%20Student&descSize=18&descAlignY=55" width="100%"/>
</a>

<!-- ===== TYPING ANIMATION ===== -->
<div align="center">

[![Typing SVG](https://readme-typing-svg.demolab.com?font=Fira+Code&weight=600&size=26&duration=3500&pause=900&color=2E67F8&center=true&vCenter=true&width=700&lines=Backend+%26+Platform+Engineer;Kubernetes+%E2%80%A2+Docker+%E2%80%A2+Observability;Building+AI+agents+with+MCP;Django+%26+DRF+Specialist;Computer+Engineering+%40+AUT+(Polytechnic+Tehran))](https://git.io/typing-svg)

<img src="https://komarev.com/ghpvc/?username=AmirmahdiGolahmar&color=2E67F8&style=flat&label=Profile+Views" alt="profile views"/>

</div>

---

## 🧠 About Me

- 🎓 **Computer Engineering** student at **Amirkabir University of Technology** (Polytechnic Tehran) — GPA **4.00/4.00**
- 💻 **Backend engineer** building scalable systems with **Django**, **DRF**, **Celery** and **PostgreSQL**
- ☸️ Now working across the stack below the app too: **Kubernetes**, **Docker**, **CI/CD** and **observability** (Prometheus, VictoriaMetrics, Grafana)
- 🤖 Building **AI agents for operations**: a read-only **Kubernetes root-cause-analysis agent** built on **MCP**, hooks and skills
- 🛡️ Into **security** and CTFs: web exploitation, container escapes and Kubernetes attack paths
- 🔬 Also work with **Computer Vision** and **Deep Learning** (YOLO, OpenCV, PyTorch) and **Data Analysis**
- 🚀 Interested in **research lab**
- 📫 Reach me: **amirmahdigolahmar@gmail.com** · **amir.golahmar@aut.ac.ir**

---

## 🛠 Tech Stack

**Backend & APIs**
<p>
  <img src="https://skillicons.dev/icons?i=python,django,graphql,fastapi,react" />
  <img src="https://img.shields.io/badge/Celery-37814A?style=for-the-badge&logo=celery&logoColor=white" />
  <img src="https://img.shields.io/badge/Gunicorn-499848?style=for-the-badge&logo=gunicorn&logoColor=white" />
</p>

**Cloud Native & DevOps**
<p>
  <img src="https://skillicons.dev/icons?i=kubernetes,docker,githubactions,nginx,linux,bash,git" />
  <img src="https://img.shields.io/badge/Traefik-24A1C1?style=for-the-badge&logo=traefikproxy&logoColor=white" />
  <img src="https://img.shields.io/badge/GHCR-181717?style=for-the-badge&logo=github&logoColor=white" />
</p>

**Observability**
<p>
  <img src="https://skillicons.dev/icons?i=prometheus,grafana" />
  <img src="https://img.shields.io/badge/VictoriaMetrics-621773?style=for-the-badge&logo=victoriametrics&logoColor=white" />
</p>

**AI Agents & LLM Tooling**
<p>
  <img src="https://img.shields.io/badge/MCP-Model_Context_Protocol-000000?style=for-the-badge" />
  <img src="https://img.shields.io/badge/Claude_Code-D97757?style=for-the-badge&logo=claude&logoColor=white" />
  <img src="https://img.shields.io/badge/Agent_Hooks_%26_Skills-2E67F8?style=for-the-badge" />
</p>

**Databases**
<p>
  <img src="https://skillicons.dev/icons?i=postgres,redis,sqlite" />
</p>

**Languages & AI / Data**
<p>
  <img src="https://skillicons.dev/icons?i=c,java,pytorch,opencv" />
  <img src="https://img.shields.io/badge/Ultralytics_YOLO-111F68?style=for-the-badge&logo=yolo&logoColor=white" />
  <img src="https://img.shields.io/badge/pandas-150458?style=for-the-badge&logo=pandas&logoColor=white" />
  <img src="https://img.shields.io/badge/NumPy-013243?style=for-the-badge&logo=numpy&logoColor=white" />
</p>

> **Also:** OOP · Data Structures · Algorithms · Relational Database Design · Django ORM · Kubernetes RBAC · Container Networking · Machine Learning · Deep Learning · Linear Algebra, Probability & Statistics

---

## 🚀 Featured Projects

### ☸️ Kubernetes App Platform — [`k8s-api`](https://github.com/AmirmahdiGolahmar/k8s-api) + [`k8s-api-frontend`](https://github.com/AmirmahdiGolahmar/k8s-api-frontend) · [🌐 live](https://golahmar.osdl.ir)

A self-service platform that turns "give me an nginx in a namespace" into a two-click operation instead of a `kubectl apply`.

- Register a cluster's kubeconfig, then create **namespaces** and **apps** (Deployment + Service) from a web UI or REST API
- Ownership and per-user access control on clusters, namespaces and apps
- **Pod file backups** on demand or on a cron schedule with **Celery + Celery Beat**
- Own **observability stack**: `/metrics` via django-prometheus, scraped by **VictoriaMetrics**, dashboards in **Grafana**
- Shipped with **GitHub Actions → GHCR**, deployed with raw manifests behind a **Traefik** Ingress

`Django` · `DRF` · `kubernetes-client` · `Celery` · `Redis` · `React` · `Ant Design` · `Docker` · `Kubernetes` · `VictoriaMetrics` · `Grafana`

### 🤖 Kubernetes RCA Agent — [`rca-k8s`](https://github.com/AmirmahdiGolahmar/rca-k8s)

An AI agent that finds the **root cause** of broken workloads in a Kubernetes namespace, built safe by design: it can look at everything and change nothing.

```mermaid
flowchart LR
    U["👤 incident<br/>question"] --> A["Claude Code agent<br/>+ k8s-rca skill"]
    A -->|"Bash (kubectl)"| PRE["PreToolUse hook<br/>blocks mutating verbs"]
    A --> MCP["kubernetes-mcp-server<br/>--read-only"]
    PRE --> K8S[("Kubernetes API<br/>RBAC: read-only SA")]
    MCP --> K8S
    K8S --> POST["PostToolUse hook<br/>redacts secrets"]
    POST --> A
    A -.->|"large logs"| SUB["log-summarizer<br/>subagent"]
    A --> OUT["ROOT CAUSE · EVIDENCE<br/>CONFIDENCE · PATCH"]
```

- **Defense in depth:** RBAC-scoped read-only ServiceAccount, read-only MCP tool surface, a hook that blocks `kubectl apply/delete/exec/...`, and a hook that redacts secrets from every tool output
- **Fixed diagnostic order** enforced by a skill (pods → events → describe → logs → YAML → endpoints) before any hypothesis
- **Failure-injection testbed** with reproducible scenarios: missing env var, label mismatch, renamed ConfigMap key, NetworkPolicy blocking the DB, failing readiness probe, broken DNS
- Unit tests for the hooks and the MCP handshake

`Claude Code` · `MCP` · `Hooks` · `Skills` · `Subagents` · `Kubernetes RBAC` · `Python`

### 🛡️ Ham CTF Write-ups — [`hamctf-writeups`](https://github.com/AmirmahdiGolahmar/hamctf-writeups/tree/add-AmirmahdiGolahmar-writeups/AmirmahdiGolahmar)

11 flags solved end to end, from web bugs to full host compromise, each with a reproducible PoC and a single `extract.sh` that replays them all:

`Docker layer forensics` → `API schema exposure` → `path traversal` → `broken access control` → `JWT alg confusion` → `command injection` → `SSRF into the cluster network` → `ServiceAccount token leak` → `privileged pod + hostPath escape` → `Docker socket escape to the host`

### 🚗 ZipDepth as a YOLO26n Backbone — [`zipdepth_yolo26n`](https://github.com/AmirmahdiGolahmar/zipdepth_yolo26n)

Research experiment: *can features learned for monocular depth estimation replace a detection backbone?* Swapped YOLO26n's backbone for the depth-pretrained ZipDepth encoder with channel adapters, fine-tuned on **KITTI**, and ran controlled ablations (adapter depth, neck/head init, longer training).

- Best ZipDepth variant reached **0.531** vs **0.602** mAP50-95 for the original, at 3.4× the parameters
- Deeper adapters helped most; depth pretraining gave **no** advantage on small, distant objects
- Full write-up with per-class AP, confusion matrices and PCA feature maps

`PyTorch` · `Ultralytics` · `KITTI` · `Colab T4`

### 📦 Earlier work

| Project | Description | Stack |
|---|---|---|
| **Dynamic Form Management** | Scalable backend for dynamic workflow & form management with GraphQL APIs, async pipelines (Celery/Redis), and production deploy (Gunicorn/Nginx) | Django · DRF · Graphene · PostgreSQL · Docker |
| [**Iranian_HEIS**](https://github.com/AmirmahdiGolahmar/Iranian_HEIS) | National household income/expenditure analysis with clustering (K-Means) & data visualization | pandas · NumPy · scikit-learn |
| [**Plate Recognition**](https://github.com/ZeinabMoayeri/Plate_recognition) | Iranian license-plate detection pipeline with image preprocessing & bounding-box extraction | Python · OpenCV · Pillow |

---

## 📊 GitHub Stats

<div align="center">

<img height="165" src="https://github-readme-stats.vercel.app/api?username=AmirmahdiGolahmar&show_icons=true&theme=tokyonight&hide_border=true" />
<img height="165" src="https://github-readme-stats.vercel.app/api/top-langs/?username=AmirmahdiGolahmar&layout=compact&theme=tokyonight&hide_border=true&langs_count=8" />

<img src="https://streak-stats.demolab.com?user=AmirmahdiGolahmar&theme=tokyonight&hide_border=true" />

<img src="https://github-profile-trophy.vercel.app/?username=AmirmahdiGolahmar&theme=tokyonight&no-frame=true&row=1&column=7&margin-w=8" />

</div>

---

## 🌐 Connect With Me

<div align="center">

<a href="mailto:amirmahdigolahmar@gmail.com"><img src="https://img.shields.io/badge/Email-D14836?style=for-the-badge&logo=gmail&logoColor=white" /></a>
<a href="https://github.com/AmirmahdiGolahmar"><img src="https://img.shields.io/badge/GitHub-100000?style=for-the-badge&logo=github&logoColor=white" /></a>
<a href="https://www.linkedin.com/in/amirmahdigolahmar"><img src="https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white" /></a>

</div>

<!-- ===== FOOTER ===== -->
<img src="https://capsule-render.vercel.app/api?type=waving&color=0:2a5298,100:0b1e3f&height=120&section=footer" width="100%"/>
