# UNICC AI Safety Governance Platform
## Operationalizing AI Safety for the United Nations

The **UNICC AI Safety Governance Platform** is a web-based application designed to manage the entire lifecycle of AI systems within the UN ecosystem. It serves as the technical implementation of the AI Safety Testing Framework, transforming abstract policy requirements into a concrete, automated auditing workflow.

This platform enables personnel to classify risk, execute automated red-teaming protocols, generate audit trails, and issue Certificates of Conformance before deployment.

## 🚀 Key Features

### 1. Smart Risk Classification Matrix
*   **Automated Triage**: Analyzes system descriptions against the UN Risk Matrix.
*   **Logic Engine**: Categorizes projects into Tiers 1–4 based on:
    *   **Domain of Application**: (e.g., Biometrics, Critical Infrastructure, Essential Services).
    *   **Critical Capability Levels (CCLs)**: (e.g., Harmful Manipulation, Cyber Ops).
*   **Manual Override**: Allows human officers to correct automated classifications.

### 2. The Evaluator Agent (Automated Auditing)
Uses a multi-agent architecture to test AI models at scale without human intervention.
*   **Architecture**: Implements an "Auditor → Target → Judge" loop.
*   **Dual-Suite Testing Engine**:
    *   **Suite A (Core Benchmarks)**: Tests for Fairness (Demographic Parity), Robustness (Noise Injection), and Transparency.
    *   **Suite B (Adversarial Protocols)**: Executes Red Teaming attacks including Evasion (PGD), Data Poisoning (Backdoors), and Jailbreaking (Misuse).

### 3. Governance & Reporting
*   **Safety Case Reports**: Automatically generates PDF reports containing executive summaries, visual charts, and forensic audit logs.
*   **ASRB Review Dashboard**: A dedicated interface for the AI Safety Review Board (ASRB) to review evidence, reject risky systems, or issue Certificates of Conformance.
*   **Role-Based Access Control**: Switch between "Project Owner" (Developer) and "ASRB Auditor" (Governance) roles.

### 4. Lifecycle Management
*   **Live Monitoring**: Tracks certified agents in production for model drift and safety violations.
*   **Data Persistence**: Uses local browser storage to retain project history and audit logs across sessions.

## 🏛️ The Framework

This platform implements the specific testing requirements defined in the UN AI Safety Framework:

| Risk Tier | Definition | Required Protocols |
| :--- | :--- | :--- |
| **Tier 1 (Low)** | Admin tools, translation | Standard Documentation |
| **Tier 2 (Moderate)** | High-risk domain, low autonomy | Suite A: Bias, Robustness, Privacy Checks |
| **Tier 3 (High)** | High autonomy OR Critical Capabilities | Suite A + Suite B: Full Adversarial Red Teaming |
| **Tier 4 (Prohibited)** | Subliminal manipulation, Social scoring | Deployment Forbidden |

## 🛠️ Technical Stack

*   **Frontend**: React (v19), TypeScript
*   **Styling**: Tailwind CSS (Inter font family)
*   **AI Integration**: Google GenAI SDK (Gemini 2.5 Flash)
    *   Used for the Auditor (Attacker) and Judge (Scorer) agents.
*   **Visualization**: Recharts
*   **Reporting**: jsPDF / AutoTable
*   **State Management**: React Hooks + LocalStorage Persistence

## 📦 Installation & Setup

### Prerequisites
*   Node.js (v18 or higher)
*   A valid API Key for the Gemini API.

### Steps

1.  **Clone the Repository**
    ```bash
    git clone https://github.com/RyanYang1390/unicc-ai-safety-platform.git
    cd unicc-ai-safety-platform
    ```

2.  **Install Dependencies**
    ```bash
    npm install
    ```

3.  **Configure Environment**
    Create a `.env` file in the root directory and add your API key. This key is required for the "Evaluator Agent" to generate attacks and score responses.
    ```env
    API_KEY=your_gemini_api_key_here
    ```

4.  **Run the Application**
    ```bash
    npm start
    ```
    Open `http://localhost:3000` to view the platform.

## 📖 Usage Guide

### Step 1: New Assessment (Project Owner)
1.  Navigate to **New Assessment**.
2.  Enter the project name and description (e.g., "Refugee Logistics Assistant").
3.  Click **Analyze Risk**. The system will detect the Domain and Capabilities to suggest a Tier.
4.  Input the Target Model's API Endpoint (simulated).

### Step 2: Automated Testing
1.  The system unlocks specific test protocols based on the Risk Tier.
2.  Click **Run All Tests**.
3.  Watch the Terminal Console as the "Auditor Agent" attempts to jailbreak the model and the "Judge Agent" scores the defense in real-time.

### Step 3: Reporting & Submission
1.  Once testing is complete, click **Generate Comprehensive Report (PDF)** to download the evidence.
2.  Click **Submit to ASRB**.

### Step 4: Governance Review (ASRB Auditor)
1.  Go to **Settings** and switch your role to **ASRB Auditor**.
2.  Navigate to **ASRB Review**.
3.  Select the pending project, review the safety scores and audit logs.
4.  Click **Override & Approve** to issue the Certificate of Conformance.

## 🔒 Data Privacy & Security
*   **Local Execution**: This application runs as a Single Page Application (SPA). Project data and audit logs are stored in your browser's `localStorage` and are not sent to any external server (other than the necessary API calls to the LLM provider for text generation).
*   **Reset Data**: You can clear all stored data via the Settings menu.

## 📄 License
This project is licensed under the MIT License.

---
*Disclaimer: This is a prototype designed for demonstration and simulation purposes based on the UNICC AI Safety Testing Framework.*
