# Hybrid Multi-Agent Procurement Assistant for Automated PO Generation

## 🌟 Project Overview

This project implements a **Hybrid Multi-Agent System** to streamline and automate document-intensive procurement workflows. The goal is to design an integrated framework that can understand unstructured procurement documents (quotations), apply complex business rules, and generate structured Purchase Orders (POs) with reliable Human-in-the-Loop (HIL) oversight.

The system is built on **SAP Business Technology Platform (BTP)** to ensure enterprise-grade security, scalability, and seamless integration with core SAP ERP systems.

## 🎯 Key Objectives

1.  **Architecture Design:** Design a hybrid multi-agent architecture integrating OCR, semantic search, and automated reasoning.
2.  **Data Extraction:** Implement robust Optical Character Recognition (OCR) to extract structured, machine-readable data from unstructured PDF quotations.
3.  **Intelligent Reasoning:** Develop **LLM Agents** capable of interpreting extracted data, validating pricing against catalog data, and autonomously generating the PO structure.
4.  **Integration & Oversight:** Develop a prototype integrated with BTP services (AI Core/Kyma) and a **Flask-based HIL interface** for compliance and auditability.
5.  **Evaluation:** Measure improvements in accuracy, turnaround time, and overall process efficiency using synthetic datasets.

## ⚙️ Architecture

The system follows a microservices architecture orchestrated on BTP's Kyma Runtime, leveraging distinct agents for specific tasks:

| Component | Technology | Role |
| :--- | :--- | :--- |
| **OCR Agent** | Python / Tesseract | Extracts data (Vendor, Items, Pricing) from PDFs and converts to JSON. |
| **Retrieval Agent** | Vector Store (FAISS/HANA) | Uses semantic search (embeddings) to match extracted item names to the vendor catalog. |
| **Reasoning Agent** | Python / LLM (via AI Core) | Applies complex business rules (Price Deviation Function) and validates PO readiness. |
| **Orchestrator** | Kyma/Cloud Foundry | Manages the workflow between agents and handles state and error routing. |
| **UI** | Flask / SAP Fiori | Provides the Human-in-the-Loop (HIL) interface for validation and audit trail. |

## 📁 Repository Structure

* `/ocr`: Code for the OCR model and text extraction logic.
* `/retrieval`: Code for the Vector Store implementation and catalog matching logic.
* `/reasoning`: Code for the LLM-driven pricing validation and PO assembly agents.
* `/ui`: Code for the Human-in-the-Loop (HIL) web interface.
* `/data`: Contains raw and processed data (see Setup).
* `/logs`: Local log files for development/debugging.

### Data Subfolders

* `/data/synthetic_quotes`: **50 synthetic PDF quotations** for testing.
* `/data/vendor_catalogs`: **3–5 CSV catalog files** for item matching.
* `/data/output`: Intermediate JSON files output by the OCR agent.

## 🚀 Setup & Installation

### Prerequisites

* Python 3.9+
* Git
* Access to a private SAP BTP Sub-Account and AI Launchpad Workspace.
* SAP AI Core service instance credentials (via Service Key for local testing).

### Local Setup

1.  **Clone the Repository:**
    ```bash
    git clone [https://github.com/adhithyavb/hybrid-procurement-agent.git](https://github.com/adhithyavb/hybrid-procurement-agent.git)
    cd hybrid-procurement-agent
    ```
2.  **Install Dependencies:** (To be added later when `requirements.txt` is created)
3.  **Configure BTP Access:** Place your BTP Service Keys (e.g., for AI Core) in a secure location and load them as environment variables (e.g., in a `.env` file).

---