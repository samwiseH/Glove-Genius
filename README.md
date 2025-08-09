# Glove Genius: AI-Powered Product Advisor for Sales Teams

## 📘 Project Overview

**Glove Genius** is a web-based application designed to support sales representatives at Superior Glove Works in recommending appropriate hand safety products to customers. The application uses artificial intelligence to analyze customer needs and suggest the most suitable gloves or sleeves based on workplace conditions, safety requirements, and real-time stock levels.

This project addresses two key business challenges:
- Reducing the complexity and inconsistency in manual product matching
- Assisting sales reps in finding alternative recommendations when preferred items are low in stock

The AI-powered system ensures our salespeople can deliver high-quality recommendations with speed, accuracy, and reliability.

---

## 🧩 Use Case & Workflow

Sales reps regularly consult with customers to understand their work environments and hazards—such as electrical risk, extreme temperatures, or sharp instruments. Based on this, they suggest gloves or sleeves that match safety and performance needs (e.g., dexterity, cut resistance, fire resistance).

### Current Workflow Challenges:
- Manual catalog lookup can be time-consuming and inconsistent
- Stock shortages make substitutions difficult and error-prone
- New products or updates from ERP systems may not be immediately accessible

### AI-Enhanced Workflow:
1. Sales rep enters customer conditions via a web interface
2. The AI model, using RAG, searches internal product knowledge and stock levels
3. It suggests:
   - The most appropriate product
   - Alternatives if stock is low or unavailable
   - Justifications based on product attributes (e.g., ANSI cut level, heat resistance)

---

## 🤖 AI Features to Be Implemented

| Feature                    | Description                                                                 |
|---------------------------|-----------------------------------------------------------------------------|
| **Prompt Engineering**     | Tailored prompts to surface high-relevance suggestions using ChatGPT-4o     |
| **Structured Outputs**     | Presenting responses in tables with product names, SKUs, attributes, and reasoning |
| **RAG & Vector DB**        | Context retrieval from product metadata, safety data, and ERP inventory using Pinecone + LangChain |
| **Evaluation Framework**   | Ensures suggestions align with sales logic and safety expectations          |
| **Observability Tools**    | LangSmith will log prompts, responses, and analytics for expert review and correctness, especially for top accounts |

---

## 🛠 Technical Approach

- **Frontend**: React-based user interface
- **Backend**: Node.js server handling API communication and LLM orchestration
- **LLM Provider**: OpenAI GPT-4o (existing enterprise license)
- **RAG Framework**: LangChain to power the retrieval layer
- **Vector Database**: Pinecone for product and safety data embeddings
- **ERP Integration**: Daily ingestion of product and stock data via API
- **Observability**: LangSmith for tracing, logging, and analytics

---

## 💬 Example Prompts & Expected Outputs

### 🔹 Prompt 1 – Industry-Specific Needs
> "My customer works in food processing and needs a glove that is cut-resistant, offers high dexterity, and complies with food safety regulations. What should I recommend?"

### ✅ Expected Output
- **Primary Recommendation**: TenActiv™ S18TAXGFN
- **Attributes**: Cut Level A6, CFIA compliant, foam nitrile palm, high dexterity
- **Justification**: This glove is engineered for food-safe environments with a high cut rating (A6), a CFIA-compliant shell, and fine 18-gauge knit for maximum dexterity and tactile control.
- **Alternatives**: 
-    *TenActiv™ STAGFN – Lower cut level (A4) for less extreme conditions
-    *Emerald CX™ ECX18G – Also CFIA-approved with steel-reinforced fibers

---

### 🔹 Prompt 2 – Hazard-Based Search
> "The client is an electrical contractor dealing with high-voltage environments. They want a glove that is arc flash rated and flexible enough for detailed work."

### ✅ Expected Output
- **Primary Recommendation**: Endura® 378GKTFG
- **Attributes**: Arc flash rated, goat-grain leather, foam nitrile palm, high dexterity
- **Justification**: Combines arc flash protection with a supple goat-grain leather shell, providing excellent control for precision tasks while meeting electrical hazard safety standards.
- **Alternatives**:
-    *Endura® 378GOBKL – Higher durability but less finger flexibility
-    *Endura® 378KGTVB – Impact-resistant with Kevlar lining for rugged environments

---

### 🔹 Prompt 3 – Stock-Sensitive Scenario
> "A construction customer needs a durable glove for heavy-duty abrasion tasks, but the Endura 378GTX is low in stock. What are good alternatives?"

### ✅ Expected Output (Structured Table)

| Product Name      | SKU       | Key Attributes                        | In Stock |
|------------------|-----------|----------------------------------------|----------|
| Endura® 378GXTVB | 378GXTVB  | Kevlar-lined, abrasion-resistant       | ✅ Yes   |
| Endura® 378GCXVB | 378GCXVB  | Cowgrain leather, impact protection    | ⚠️ Limited |
| TenActiv™ STXAGT | STXAGT    | Knit shell, high dexterity, abrasion   | ✅ Yes   |

---

## 📈 Evaluation Strategy
•	Use of automated evaluation frameworks (e.g., LangChain evaluators or custom metrics) to compare AI recommendations against expert rules and historical rep suggestions
•	Feedback collection from sales reps via inline ratings and comments
•	Flagging logic to prevent AI from recommending items that are below minimum viable stock levels

---

## 🔎 Observability Plan
-•	All prompts and outputs will be logged with metadata (rep ID, customer type, product suggested)
-•	LangSmith will be used for:
-  o	Prompt tracing and debugging
-  o	Usage analytics
-  o	Monitoring model drift and performance over time
-•	Priority reviews for suggestions made to top-tier accounts
-•	Alerting system to catch invalid outputs (e.g., no substitutions found, inaccurate hazard matching)

