# 🛡️ **Week 5–6: Secure AI Data Pipelines & Training Environments — Complete Walkthrough**

## 📋 Overview

End‑to‑end secure data flows for AI workloads across AWS, Azure, and GCP.  
You will build ingestion pipelines, encryption layers, federated learning with secure aggregation, and data poisoning detection.

**Week 5–6 Goals:**  
- ✅ Build secure ingestion pipelines (Kinesis, Event Hub, Pub/Sub)  
- ✅ Implement encryption for AI workloads (KMS, Key Vault, Cloud KMS)  
- ✅ Demonstrate federated learning with secure aggregation  
- ✅ Add data poisoning detection to training workflows  
- ✅ Produce Training Environment Security Playbook  

**Time:** 8–12 hours  
**Prerequisites:** Python 3.9+, basic cloud knowledge, Module 1 baseline model  

**Next Module:** Model Monitoring + AI Guardrails (Module 4)

---

# 🚀 **Step-by-Step Implementation**

---

## **Step 1: Project Setup (15 minutes)**

```bash
# Create project structure
mkdir module3-secure-ai-data-pipelines
cd module3-secure-ai-data-pipelines

# Create directory structure
mkdir -p ingestion/aws
mkdir -p ingestion/azure
mkdir -p ingestion/gcp
mkdir -p encryption
mkdir -p federated-learning
mkdir -p poisoning-detection
mkdir -p diagrams
mkdir -p docs/case_studies
mkdir -p data
mkdir -p models

# Initialize Python environment
python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate

# Create requirements.txt
cat > requirements.txt << 'EOF'
# Core ML
torch>=2.0.0
tensorflow>=2.13.0
numpy>=1.24.0
pandas>=2.0.0

# Federated Learning
flwr>=1.7.0
tensorflow-federated>=0.72.0

# Data Poisoning Detection
scikit-learn>=1.3.0
art>=1.14.0

# Cloud SDKs
boto3>=1.28.0
azure-eventhub>=5.11.0
google-cloud-pubsub>=2.18.0
google-cloud-storage>=2.14.0

# Encryption
cryptography>=41.0.0

# Utilities
pyyaml>=6.0
matplotlib>=3.7.0
seaborn>=0.12.0
EOF

pip install -r requirements.txt
```

**Verify installation:**

```bash
python -c "import flwr, boto3, art; print('✓ All libraries installed')"
```

---

# **WEEK 5 — Secure Data Ingestion + Encryption Foundations**

---

## **Step 2: Build Secure Ingestion Pipelines (60–90 minutes)**

### Folder:  
`ingestion/`

You will build **three ingestion pipelines**, each with cloud‑native security controls.

---

### **A. AWS Kinesis → S3 Secure Stream**  
File: `ingestion/aws/kinesis_ingest.py`

Includes:
- Kinesis Data Stream  
- IAM least privilege  
- Server‑side encryption (SSE‑KMS)  
- VPC endpoint for private ingestion  

Example snippet:

```python
import boto3
kinesis = boto3.client("kinesis")
response = kinesis.put_record(
    StreamName="secure-stream",
    Data=b"sample payload",
    PartitionKey="key1"
)
```

---

### **B. Azure Event Hub → ADLS Secure Ingestion**  
File: `ingestion/azure/eventhub_ingest.py`

Security controls:
- Managed Identity  
- Private Link  
- Key Vault for connection secrets  

---

### **C. GCP Pub/Sub → BigQuery Pipeline**  
File: `ingestion/gcp/pubsub_ingest.py`

Security controls:
- CMEK encryption  
- VPC‑SC  
- IAM service accounts  

---

## **Step 3: Implement Encryption for AI Workloads (45 minutes)**

### Folder:  
`encryption/`

You will implement:
- Encryption at rest  
- Encryption in transit  
- Envelope encryption for training artifacts  
- Key rotation  

---

### **A. AWS KMS Example**

```python
import boto3
kms = boto3.client("kms")
ciphertext = kms.encrypt(
    KeyId="alias/my-key",
    Plaintext=b"training batch"
)["CiphertextBlob"]
```

---

### **B. Azure Key Vault Example**

Use Key Vault to store:
- Data encryption keys  
- Model signing keys  

---

### **C. GCP Cloud KMS Example**

```python
from google.cloud import kms
client = kms.KeyManagementServiceClient()
```

---

## **Step 4: Create Secure Pipeline Architecture Diagram (10 minutes)**

File:  
`diagrams/week5_secure_pipeline_architecture.md`

```
┌──────────────────────────────────────────┐
│      Ingestion Layer                     │
│ Kinesis / EventHub / PubSub              │
└──────────────────────────────────────────┘
                    │
                    ▼
┌──────────────────────────────────────────┐
│   Encryption Layer (KMS / KV / CKMS)     │
└──────────────────────────────────────────┘
                    │
                    ▼
┌──────────────────────────────────────────┐
│ Secure Storage (S3 / ADLS / GCS)         │
└──────────────────────────────────────────┘
```

---

# **WEEK 6 — Federated Learning + Data Poisoning Detection**

---

## **Step 5: Implement Federated Learning with Secure Aggregation (60–90 minutes)**

### Folder:  
`federated-learning/`

You will build:
- A Flower‑based federated learning system  
- Secure aggregation protocol  
- Client‑side DP  

---

### **A. Basic FL Client**

```python
import flwr as fl

class FLClient(fl.client.NumPyClient):
    def get_parameters(self, config):
        return model.get_weights()
```

---

### **B. Secure Aggregation**

Add:
- Differential privacy noise  
- Gradient clipping  
- Encrypted model updates  

---

### **C. Federated Training Run**

```python
fl.server.start_server(
    server_address="0.0.0.0:8080",
    config=fl.server.ServerConfig(num_rounds=3)
)
```

---

## **Step 6: Add Data Poisoning Detection (45–60 minutes)**

### Folder:  
`poisoning-detection/`

You will implement:
- Activation clustering  
- Loss‑based anomaly detection  
- Gradient similarity checks  

---

### **A. Activation Clustering Example**

```python
from sklearn.cluster import KMeans
clusters = KMeans(n_clusters=2).fit(activations)
```

Outputs:
- Poisoning risk score  
- Flagged samples  
- Recommended mitigations  

---

## **Step 7: Add Case Studies + Documentation (30 minutes)**

Folder:  
`docs/case_studies/`

Examples:
- Kinesis ingestion poisoning attempt  
- Azure Key Vault key rotation failure  
- Federated learning client poisoning  

Each case study includes:
- Attack vector  
- Detection method  
- Mitigation  
- Cloud implications  

---

## **Step 8: Create Training Environment Security Playbook (30 minutes)**

File:  
`docs/training_environment_security_playbook.md`

Sections:
- Secure ingestion patterns  
- Encryption best practices  
- Federated learning security  
- Poisoning detection workflows  
- Cloud-specific controls  
- Governance mapping (NIST AI RMF, ISO 42001)  

---

# 🎉 **End of Weeks 5–6 Deliverables**

### ✅ **Secure AI Data Pipeline Repository**
Includes:
- Secure ingestion pipelines  
- Encryption examples  
- Federated learning with secure aggregation  
- Data poisoning detection  
- Architecture diagrams  
- Case studies  

### ✅ **Training Environment Security Playbook**
Enterprise‑ready documentation for securing AI data flows and distributed training environments.
