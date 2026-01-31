# **Weeks 5–6 — Module 3: Secure AI Data Pipelines & Training Environments**

This is Module 3 of 5 of the [12-week Security Architect Program](https://github.com/epatter1/AI_Data_Security_Architect_Program/blob/main/12_week_overview.md)

### Focus areas
* #### Build secure ingestion pipelines (Kinesis, Event Hub, Pub/Sub)
* #### Implement encryption for AI workloads (KMS, Key Vault, Cloud KMS)
* #### Demonstrate federated learning with secure aggregation
* #### Add data poisoning detection to training workflows

#### Deliverables:
* Secure AI Data Pipeline Repo + Training Environment Security Playbook: [Link to walkthrough](https://github.com/epatter1/Secure_AI_Data_Pipelines_and_Training_Environments/blob/main/Secure_AI_Data_Pipelines_and_Training_Environments_walkthrough.md)

---

## **Technologies, Frameworks & Cloud Services Used**

### 🧠 **AI/ML, Federated Learning & Data Integrity**

<a href="PyTorch">
  <img src="https://img.shields.io/badge/PyTorch-EE4C2C?logo=pytorch&logoColor=white" />
</a>
<a href="TensorFlow">
  <img src="https://img.shields.io/badge/TensorFlow-FF6F00?logo=tensorflow&logoColor=white" />
</a>
<a href="Flower">
  <img src="https://img.shields.io/badge/Federated_Learning-Flower-4B0082" />
</a>
<a href="Opacus">
  <img src="https://img.shields.io/badge/Secure_Aggregation-DP/FL-6A5ACD" />
</a>
<a href="ART">
  <img src="https://img.shields.io/badge/Data_Poisoning-Detection-005C5C" />
</a>

---

### 🔐 **Security, Encryption & Governance**

<a href="KMS">
  <img src="https://img.shields.io/badge/AWS-KMS-232F3E?logo=amazonaws&logoColor=white" />
</a>
<a href="KeyVault">
  <img src="https://img.shields.io/badge/Azure-Key_Vault-0078D4?logo=microsoftazure&logoColor=white" />
</a>
<a href="CloudKMS">
  <img src="https://img.shields.io/badge/GCP-Cloud_KMS-4285F4?logo=googlecloud&logoColor=white" />
</a>
<a href="MITRE-ATLAS">
  <img src="https://img.shields.io/badge/MITRE-ATLAS-blue" />
</a>
<a href="OWASP-LLM-Top-10">
  <img src="https://img.shields.io/badge/OWASP-Top_10_for_LLMs-000000?logo=owasp&logoColor=white" />
</a>
<a href="STRIDE">
  <img src="https://img.shields.io/badge/Threat_Modeling-STRIDE-purple" />
</a>

---

## ☁️ **Cloud Platforms**

### **AWS**

<a href="AWS">
  <img src="https://img.shields.io/badge/AWS-232F3E?logo=amazonaws&logoColor=white" />
</a>
<a href="Kinesis">
  <img src="https://img.shields.io/badge/Kinesis-FF9900?logo=amazonaws&logoColor=white" />
</a>
<a href="S3">
  <img src="https://img.shields.io/badge/S3-569A31?logo=amazons3&logoColor=white" />
</a>

---

### **Azure**

<a href="Azure">
  <img src="https://img.shields.io/badge/Azure-0078D4?logo=microsoftazure&logoColor=white" />
</a>
<a href="EventHub">
  <img src="https://img.shields.io/badge/Event_Hub-0089D6?logo=microsoftazure&logoColor=white" />
</a>
<a href="KeyVault">
  <img src="https://img.shields.io/badge/Key_Vault-0078D4?logo=microsoftazure&logoColor=white" />
</a>

---

### **GCP**

<a href="GCP">
  <img src="https://img.shields.io/badge/GCP-4285F4?logo=googlecloud&logoColor=white" />
</a>
<a href="PubSub">
  <img src="https://img.shields.io/badge/Pub/Sub-4285F4?logo=googlecloud&logoColor=white" />
</a>
<a href="CloudKMS">
  <img src="https://img.shields.io/badge/Cloud_KMS-4285F4?logo=googlecloud&logoColor=white" />
</a>

---

## 🛠️ **DevOps, Infrastructure & Tooling**

<a href="Python">
  <img src="https://img.shields.io/badge/Python-3776AB?logo=python&logoColor=white" />
</a>
<a href="Docker">
  <img src="https://img.shields.io/badge/Docker-2496ED?logo=docker&logoColor=white" />
</a>
<a href="Terraform">
  <img src="https://img.shields.io/badge/Terraform-844FBA?logo=terraform&logoColor=white" />
</a>
<a href="MLflow">
  <img src="https://img.shields.io/badge/MLflow-0194E2" />
</a>

---

## 📊 **Documentation & Visualization**

<a href="Markdown">
  <img src="https://img.shields.io/badge/Markdown-000000?logo=markdown&logoColor=white" />
</a>
<a href="Architecture-Diagrams">
  <img src="https://img.shields.io/badge/Architecture_Diagrams-4285F4" />
</a>
<a href="Playbooks">
  <img src="https://img.shields.io/badge/Training_Environment-Security_Playbook-green" />
</a>
<a href="Dashboards">
  <img src="https://img.shields.io/badge/Data_Integrity-Dashboard-6A5ACD" />
</a>

---

# **WEEK 5 — Secure Data Ingestion + Encryption Foundations**

### **1. Set Up the Secure Pipeline Structure**
```
module3-secure-ai-data-pipelines/
    ingestion/
    encryption/
    federated-learning/
    poisoning-detection/
    diagrams/
    docs/
```

---

### **2. Build Secure Ingestion Pipelines**
Folder: `ingestion/`

Includes:
- AWS Kinesis → S3 secure stream  
- Azure Event Hub → ADLS ingestion  
- GCP Pub/Sub → BigQuery pipeline  

Security controls:
- Private endpoints  
- IAM roles / RBAC  
- Schema validation  
- Input sanitization  

---

### **3. Implement Encryption for AI Workloads**
Folder: `encryption/`

You will:
- Encrypt data at rest (KMS, Key Vault, Cloud KMS)  
- Encrypt data in transit (TLS 1.2+)  
- Use envelope encryption for training artifacts  
- Rotate keys + enforce least privilege  

---

### **4. Create Initial Secure Pipeline Architecture Diagram**
Diagram: `diagrams/week5_secure_pipeline_architecture.md`

```
┌──────────────────────────────┐
│     Ingestion Layer          │
│ Kinesis / EventHub / PubSub  │
└──────────────────────────────┘
              │
              ▼
┌──────────────────────────────┐
│   Encryption (KMS / KV / CKMS)│
└──────────────────────────────┘
              │
              ▼
┌──────────────────────────────┐
│  Secure Storage (S3/ADLS/GCS)│
└──────────────────────────────┘
```

---

# **WEEK 6 — Federated Learning + Data Poisoning Detection**

### **1. Implement Federated Learning with Secure Aggregation**
Folder: `federated-learning/`

Includes:
- Flower or TensorFlow Federated  
- Secure aggregation protocol  
- Client-side DP  
- Model update validation  

---

### **2. Add Data Poisoning Detection**
Folder: `poisoning-detection/`

Techniques:
- Activation clustering  
- Loss-based anomaly detection  
- Gradient similarity checks  
- Outlier filtering  

Outputs:
- Poisoning risk score  
- Flagged samples  
- Recommended mitigations  

---

### **3. Add Case Studies + Documentation**
Folder: `docs/case_studies/`

Examples:
- Kinesis ingestion poisoning attempt  
- Azure Key Vault key rotation failure scenario  
- Federated learning client poisoning case  

---

### **4. Create the Training Environment Security Playbook**
File: `docs/training_environment_security_playbook.md`

Sections:
- Secure ingestion patterns  
- Encryption best practices  
- Federated learning security  
- Poisoning detection workflows  
- Cloud-specific controls  
- Governance mapping (NIST AI RMF, ISO 42001)  

---

## **End of Weeks 5–6 Deliverables**

### ✅ **Secure AI Data Pipeline Repository**
Includes:
- Secure ingestion pipelines  
- Encryption examples  
- Federated learning with secure aggregation  
- Data poisoning detection  
- Architecture diagrams  
- Case studies  

### ✅ **Training Environment Security Playbook**
A polished, enterprise-ready guide for securing AI data flows and distributed training environments.
