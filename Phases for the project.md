# Phases for the Project

---

#### **Phase 1: Problem Understanding and Planning**
- **Objective**: Predict the **protein-coding potential** of RNA isoforms from sequence data.
- **Deliverable**: A well-defined plan with clear objectives, pipeline design, and expected outcomes.
- **Tasks**:
  1. Understand the FASTA data structure (sequence ID, sequences).
  2. Define labels: Protein-coding (`1`) vs Non-coding (`0`).
  3. Identify preprocessing, feature engineering, and modeling needs.

---

#### **Phase 2: Local Development**
- **Objective**: Build a scalable and error-free preprocessing and modeling pipeline on a local machine.
- **Deliverable**: A functional pipeline that preprocesses FASTA files, extracts features, and trains a baseline model.
- **Tasks**:
  1. **Preprocessing**:
     - Parse sequences and IDs from FASTA.
     - Filter invalid or incomplete sequences.
     - Tokenize sequences into k-mers for downstream processing.
  2. **Feature Engineering**:
     - Extract sequence features like GC content, sequence length, and k-mer embeddings.
  3. **Model Training**:
     - Train a baseline classification model (e.g., logistic regression, random forest).
     - Evaluate the model with metrics like accuracy, F1 score, and AUROC.

---

#### **Phase 3: Azure Data Factory (ADF) for Orchestration**
- **Objective**: Automate data ingestion, preprocessing, and triggering workflows.
- **Deliverable**: An ADF pipeline to fetch, preprocess, and store transformed data.
- **Tasks**:
  1. Use ADF to pull raw FASTA data from Azure Blob Storage.
  2. Trigger preprocessing scripts in Databricks notebooks.
  3. Save processed data into Azure Data Lake.

---

#### **Phase 4: Azure Databricks for Data Processing**
- **Objective**: Scale the preprocessing and feature engineering pipeline for large datasets.
- **Deliverable**: Databricks notebooks that process sequences in parallel using Spark.
- **Tasks**:
  1. Parse FASTA data and generate k-mers for feature extraction.
  2. Apply advanced feature engineering techniques like embeddings or sequence transformations.
  3. Output clean, feature-rich datasets to Azure Data Lake.

---

#### **Phase 5: Model Development and Training**
- **Objective**: Train and evaluate a robust model to classify isoforms.
- **Deliverable**: A trained, serialized model stored in Azure ML Model Registry.
- **Tasks**:
  1. Use Azure ML for distributed training with hyperparameter tuning.
  2. Experiment with deep learning models like `RNA-BERT` or custom CNNs for sequence classification.
  3. Store the trained model in the registry for deployment.

---

#### **Phase 6: Deployment and Scalability**
- **Objective**: Deploy the model as a real-time API.
- **Deliverable**: A scalable AKS-based API for protein-coding prediction.
- **Tasks**:
  1. Containerize the model using Docker and push it to Azure Container Registry (ACR).
  2. Deploy the containerized model to AKS and expose endpoints for inference.
  3. Set up autoscaling in AKS to handle varying workloads.

---

#### **Phase 7: Monitoring and Governance**
- **Objective**: Ensure robust monitoring and compliance for the pipeline.
- **Deliverable**: Integrated monitoring dashboards and data lineage reports.
- **Tasks**:
  1. Use Prometheus and Grafana to monitor API performance (latency, throughput, errors).
  2. Integrate Azure Purview to track data lineage and maintain metadata for compliance.
