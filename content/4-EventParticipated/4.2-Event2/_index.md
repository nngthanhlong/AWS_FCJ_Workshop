---
title: "Event 2"
weight: 1
chapter: false
pre: " <b> 4.2. </b> "
---

# Summary: "Generative AI with Amazon Bedrock"
**Time:** 08:30 – 15/11/2025

---

## Purpose of the Event

- Provide foundational knowledge about Generative AI and highlight differences compared to traditional Machine Learning approaches.
- Introduce Amazon Bedrock service in detail along with supported Foundation Models.
- Present the RAG (Retrieval Augmented Generation) technical process to build smarter, more accurate AI applications and reduce hallucination phenomena.
- Overview the ecosystem of specialized AI services on AWS and how they integrate with Bedrock.

---

## Speakers List

- **Lam Tuan Kiet** - Sr DevOps Engineer, FPT Software.
- **Danh Hoang Hieu Nghi** - AI Engineer, Renova Cloud.
- **Dinh Le Hoang Anh** - Cloud Engineer Trainee, First Cloud AI Journey.

---

## Event Highlights

### Transition: From Traditional ML to Foundation Models

- **Traditional Machine Learning models** operate in a "one model – one task" fashion, requiring large amounts of labeled data and complex training and deployment processes.

- **Foundation Models (FM)** are trained on massive amounts of unlabeled data, providing better generalization and applicability to various tasks such as text generation, summarization, question-answering, and chatbots.

---

### AWS AI Ecosystem

- **Amazon Bedrock** is a hub for advanced models from AI21, Anthropic, Cohere, Meta, Stability AI, and Amazon's own models.

- Beyond FMs, AWS provides a series of Specialized AI Services – ready-to-use services without needing self-training:

  - **Amazon Rekognition**: Image and video recognition and analysis.
  - **Amazon Translate**: Real-time language translation.
  - **Amazon Textract**: Extract structured data from scanned documents.
  - **Amazon Transcribe**: Convert audio to text.
  - **Amazon Polly**: Convert text to speech.
  - **Amazon Comprehend**: Sentiment analysis, topic detection, keyword extraction.
  - **Amazon Kendra**: Natural language search within enterprise documents.
  - **Amazon Lookout**: Detect anomalies in industrial systems.
  - **Amazon Personalize**: Build real-time recommendation systems.

---

### Prompting Technique: Chain of Thought (CoT)

- Comparison between **Standard Prompting** (asking and getting a direct answer) and **Chain-of-Thought Prompting**.
- CoT encourages the model to **think out loud**, breaking down problems into multiple reasoning steps. This approach is particularly effective for complex logical problems and often yields more accurate and consistent results compared to direct question answering.

---

### RAG (Retrieval Augmented Generation)

- **The Problem**: LLMs are often limited by their training data (not continuously updated) and sometimes produce hallucinations.
- **The Solution**: Combine LLMs with an external Knowledge Base retrieval layer. The model retrieves relevant information and uses it to construct answers – rather than relying solely on memorized knowledge.
- **Data Ingestion Process**:
  1. Collect new data and divide it into chunks.
  2. Pass each chunk through an Embeddings model (e.g., Amazon Titan Text Embeddings V2.0) to convert to vectors.
  3. Store these vectors in a Vector Store (OpenSearch Serverless, Pinecone, Redis, etc.).
- **RetrieveAndGenerate API**: Handles the entire pipeline: receives user input → creates embedding for the query → queries Vector Store → injects context into prompt → calls LLM to generate final answer.

---

## Learning Outcomes

### About AI and Cloud

- Better understand when to use specialized AI services – suitable for quick and specific tasks – versus when to use Generative AI or Bedrock for creative problems or high customization needs. Understand RAG thinking, which focuses more on data organization and providing proper context rather than just calling an LLM API.

### Technical Architecture

- Better understand how an AI system works end-to-end. Not just "call the model to generate an answer," but the system requires many data preparation and information organization steps before AI can answer accurately.

- RAG architecture is broken down into clear steps: data collection → chunking → storage in search repository → retrieval of relevant information → feeding into the model for answering. This step-by-step approach makes management and scaling easier as data grows.

---

## Application to Work

- **Standardize unstructured data**: Use Textract and Bedrock Agents to automate extraction of information from forms, invoices, and scanned documents, minimizing manual work.

- **Support decision-making**: Apply generative models to automatically summarize reports, highlight key metrics, and suggest actions based on current data.

---

## Event Experience

Attending the workshop was very valuable, providing me a comprehensive view of AI and how to use it optimally and reasonably. The game section was also very helpful in reinforcing the knowledge learned during the workshop.

### Networking and Exchange

- The workshop created opportunities for direct discussions with speakers, helping me understand more about AI usage and some new AI tools. After each presentation, I had access to the speakers' LinkedIn profiles to continue learning afterward.

### Key Takeaways

- Attending the workshop gave me a clearer perspective on how to apply AI effectively. I realized that RAG is an important component for AI to provide accurate answers based on enterprise-internal data.

- Additionally, I was impressed by AWS's comprehensive ecosystem — from storage, models, to orchestration tools — making building a real AI application much easier and more feasible.

