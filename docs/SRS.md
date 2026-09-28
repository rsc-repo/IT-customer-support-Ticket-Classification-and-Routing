# Software Requirements Specification (SRS)
IT customer support ticket Classifier & Routing 

### 1. System Overview
The **Smart Civic Issue Classifier & Routing Engine** automatically ingests citizen-reported non-emergency complaints, classifies them into relevant municipal departments using a fine-tuned DistilBERT transformer model, determines SLA priority levels, and routes tickets to appropriate department dashboards.


### 2. Functional Requirements

#### FR-1: Data Ingestion & Preprocessing
- **FR-1.1:** System shall ingest raw complaint text submitted via web interface or API.
- **FR-1.2:** System shall clean text by stripping whitespace and removing sensitive PII patterns (e.g., phone numbers, addresses) using regex filters.
- **FR-1.3:** Text shall be tokenized using `DistilBertTokenizerFast` capped at a maximum length of 128 tokens.

#### FR-2: Department Classification
- **FR-2.1:** System shall classify complaints into 5 core municipal categories:
  - *Roads & Potholes*
  - *Garbage & Sanitation*
  - *Street Lighting*
  - *Water Supply & Drainage*
  - *Public Transport & Traffic*
- **FR-2.2:** System shall return top-3 predicted categories alongside probability confidence scores.

#### FR-3: Priority & SLA Routing Logic
- **FR-3.1:** System shall dynamically assign priority levels (`Urgent`, `High`, `Normal`) based on critical keyphrase triggers (e.g., *burst*, *cave-in*, *down*, *leakage*) and probability thresholds ($>0.85$).
- **FR-3.2:** System shall map categorized complaints to dedicated municipal department queues.

#### FR-4: Admin Interface & Visualization
- **FR-4.1:** System shall provide an interactive Gradio web app for real-time ticket submission, prediction display, and priority tagging.


### 3. Non-Functional Requirements
- **Latency:** Single ticket inference time shall be less than $300\text{ ms}$ on standard T4 GPU acceleration.
- **Usability:** System shall be fully executable inside Google Colab environment with zero external server dependencies.
- **Maintainability:** Code structure shall adhere to PEP-8 standards with clear modular functions.




