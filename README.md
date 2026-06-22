# PrepForge AI 🚀
> An Open-Source, LLM-Powered Adaptive GRE Quant Mock Platform & SaaS.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Next.js](https://img.shields.io/badge/Next.js-15-%23000000?logo=nextdotjs)](https://nextjs.org/)
[![Node.js](https://img.shields.io/badge/Node.js-20-green?logo=node.js)](https://nodejs.org/)
[![TailwindCSS](https://img.shields.io/badge/TailwindCSS-v4-blue?logo=tailwindcss)](https://tailwindcss.com/)

PrepForge AI disrupts the pricey standardized testing market by offering an open-access, production-grade GRE Quantitative preparation platform. Built with a robust MERN/Next.js architecture and powered by localized LLM prompt-engineering, PrepForge allows students to practice curated mock exams or dynamically synthesize customized, section-specific sub-tests (e.g., Arithmetic, Algebra, Geometry) on demand.

[Explore Live Demo] · [Report Bug] · [Request Feature]

---

## 🌟 Core Features

### 1. Static vs. Dynamic Synthetic Test Engines
* **Curated Benchmarks:** Take standardized, high-fidelity Quant sections curated by administrators to establish a baseline score.
* **On-Demand LLM Generation:** Instantly synthesize dynamic, section-specific quiz modules (e.g., 20 questions focused entirely on Arithmetic or Quantitative Comparison) via deterministic LLM pipelines with structured JSON schemas.

### 2. High-Fidelity Exam Simulation
* **Precise Chrono-Tracking:** A strict section-level countdown timer mirroring actual GRE conditions.
* **Mathematical Precision:** Clean, readable rendering of complex mathematical notations, formulas, and data interpretation graphs using LaTeX.
* **Progressive State Persistence:** Robust local/server-side synchronization ensures that a user's active test state is resilient against accidental browser refreshes.

### 3. Granular Performance Analytics (Premium Layer)
* Comprehensive post-exam dashboards breaking down accuracy by concept, time spent per question, and historical progression curves.

---

## 🏗️ Architecture & System Design

PrepForge AI is designed for optimal decoupling, low-latency rendering, and cost-efficient LLM throughput.

```text
+-----------------------------------+
              |          Frontend Client          |
              |  (Next.js / React / Tailwind)     |
              +-----------------+-----------------+
                                |
                                | HTTPS / REST
                                v
              +-----------------+-----------------+
              |       NestJS API Gateway          |
              |    (Controllers, Guards, DTOs)    |
              +--------+-----------------+--------+
                       |                 |
     +-----------------+ (Prisma Client) +-----------------+
     |                                                     |
     v                                                     v
+--------+------------------+                        +---------+------------------+
|    MongoDB Atlas Cloud    |                        |  Structured LLM Engine     |
| (Users, Static Tests,     |                        | (OpenAI / DeepSeek JSON    |
|  Historical Analytics)    |                        |  Generation Pipeline)      |
+---------------------------+                        +----------------------------+
```
### Backend Design Patterns
* **Modular Architecture:** Fully encapsulated feature modules (`AuthModule`, `TestModule`, `AiModule`, `AnalyticsModule`) adhering to clean-architecture paradigms.
* **Type-Safe Data Access:** Prisma ORM abstraction mapping cleanly to MongoDB collections with explicit TS interfaces.
* **Data Validation:** Strict inbound DTO schema verification via `class-validator` and `class-transformer`.

---

## 🛠️ Tech Stack Specification

* **Framework:** NestJS (v10.x) — A progressive Node.js framework for building efficient, reliable, and scalable server-side applications.
* **Runtime:** Node.js (v20.x LTS)[cite: 1].
* **Database Layer:** MongoDB cloud cluster managed seamlessly via **Prisma ORM**[cite: 1].
* **AI Orchestration:** Native OpenAI SDK / LangChain integration utilizing structured outputs (`response_format: { type: "json_object" }`) to guarantee strict validation of question-and-answer schemas[cite: 1].

---

## 🚀 Getting Started

### Prerequisites
* Node.js (v18.x or v20.x recommended)[cite: 1]
* MongoDB Instance (Local daemon or Atlas Cloud Connection URI)[cite: 1]
* OpenAI API Key (or equivalent LLM provider credentials)[cite: 1]

### Installation & Local Setup

1. **Clone the Repository:**
```bash
   git clone [https://github.com/yourusername/prepforge-ai.git](https://github.com/yourusername/prepforge-ai.git)
   cd prepforge-ai/backend
   ```[cite: 1]

2. **Install Dependencies:**
```bash
   npm install
   ```[cite: 1]

3. **Environment Configuration:**
   Create a `.env` file in the root of your backend directory:
```env
   PORT=5000
   DATABASE_URL="mongodb+srv://<username>:<password>@cluster.mongodb.net/prepforge?retryWrites=true&w=majority"
   JWT_SECRET=your_ultra_secure_jwt_secret
   OPENAI_API_KEY=sk-proj-xxxxxxxxxxxxxxxxxxxxxxxx
   ```[cite: 1]

4. **Initialize Prisma Client:**
   Generate the Prisma client based on the database schema mappings:
```bash
   npx prisma generate
   ```[cite: 1]

5. **Launch the Development Server:**
```bash
   npm run start:dev
