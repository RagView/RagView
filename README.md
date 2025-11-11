
<img width="2768" height="684" alt="标准色logo白底_画板 1" src="https://github.com/user-attachments/assets/d93a0136-acb1-4ac0-8538-163a905c3912" />

## Why RagView?

As RAG technology continues to evolve, there are now nearly 60 distinct approaches, reflecting a stage of diversity and rapid experimentation. Depending on the scenario, different RAG solutions may yield significantly different outcomes in terms of recall rate, accuracy, and F1 score. Beyond accuracy, enterprises and individual developers must also weigh factors such as computational cost, performance, framework maturity, and scalability. However, there is currently no unified platform that consolidates and compares these RAG technologies. Developers and enterprises are often forced to download open-source code, deploy systems independently, and run manual evaluations—an inefficient and costly process.  
To address this gap, we are building RagView—a benchmarking and selection platform for RAG technologies, designed for both developers and enterprises. RagView provides standardized evaluation metrics, streamlined benchmarking workflows, intuitive visualization tools, and a modular plug-in architecture, enabling users to efficiently compare RAG solutions and select the approach best suited to their specific business needs.  
Today’s teams need a standardized rag evaluation process to compare diverse approaches fairly—using clear rag evaluation metrics (answer accuracy, context precision/recall, cost, and latency) and reproducible benchmarks. RagView centralizes this, so you can run apples-to-apples rag evaluation and pick what actually works for your domain.

## Basic Concepts

### Terminology

- RAG solution: A RAG solution that follows the basic RAG workflow but applies special techniques in various components to improve recall and accuracy. The RAG solutions in RagView currently come from the open-source community; future plans include integrating commercial pipelines and implementing solutions from academic research.
- Document: The original form of knowledge in the RAG system, including text files (PDF, DOCX, TXT) and images (JPG, PNG, BMP). In the current version, only PDF is supported.
- Document Set: A collection of documents. In a RAG evaluation, this is the smallest unit of documents that is referenced.
- Test Set: A set of evaluation data that includes questions, the source text passages (which must be contained in documents of the document set) that a large model used as references to answer the questions, and the standard answers that the model is expected to generate based on those passages. In RAG evaluation, a test set is the smallest unit of test data referenced.
- RAG evaluation Task: Consists of one document set, one test set, and N user-selected RAG solutions; it executes the RAG evaluation and returns the results.A RAG evaluation task computes predefined rag evaluation metrics at both query-level and task-level for consistent, reproducible comparison.
- RAG evaluation count: A unit representing the complete evaluation of one RAG solution. If an evaluation task selects multiple solutions, it consumes multiple counts.

### Functional Metrics

RagView reports core rag evaluation metrics that capture answer quality and retrieval quality: Answer Accuracy, Context Precision, and Context Recall. These rag evaluation signals reveal whether the system surfaces the right passages and uses them faithfully.

- Answer Accuracy: Measures how consistent the generated answer is with the reference answer; higher is better.
- Context Precision: Evaluates how accurate the retrieved relevant segments are for this RAG solution (i.e., the proportion of retrieved content that is actually relevant to the answer, considering ranking); higher is better.
- Context Recall: Measures how comprehensively the relevant segments are retrieved by this RAG solution; higher is better.

### Performance Metrics

For production decisions, efficiency matters. RagView treats latency, token consumption, and resource usage as first-class rag evaluation metrics, enabling cost-aware model and retriever choices.

- Token Consumption: The number of tokens consumed by various LLMs across different stages of the RAG solution (including preprocessing, indexing, retrieval, generation, etc.).
- Time: The time consumed by various components of the RAG solution, including preprocessing, indexing, retrieval, and generation.

## Quick Start

Welcome to RagView.ai .  
In RagView, you can complete a RAG evaluation task quickly with just a few simple steps.

1. Upload Document Set: In Data Management, upload a set of documents to be retrieved during the RAG process. These documents will serve as the knowledge base for retrieval; different RAG solutions may use different chunking and retrieval methods on them.
2. Upload Test Set: In Data Management, upload the test data for evaluation. The test data includes the questions, the original text excerpts (from the document set) that the large model used for reference, and the reference standard answers. The test set should be prepared according to the provided sample file.
3. Launch Evaluation Task: In Evaluation Management, create a rag evaluation task, select the document set and test set, choose solutions, and pick the rag evaluation metrics to compute (e.g., answer accuracy, context precision/recall, latency).
4. View Evaluation Details: In Evaluation Management, after the task completes, click Details to view results. Based on the metrics you care about, select the suitable RAG solution and download the code for that pipeline.

### Register / Login

<img width="1920" height="919" alt="image" src="https://github.com/user-attachments/assets/b87af339-c4d2-43c3-95bc-4c04cbc4ff2b" />


https://www.ragview.ai/login

You can register or log in using Google, GitHub, or email.

### Upload Document Set

<img width="1920" height="919" alt="image-1" src="https://github.com/user-attachments/assets/f5540bfe-17b1-44f0-97b3-200c18c73a03" />


https://www.ragview.ai/components/dataset

- In Data Management, click Create Document Set to create an empty document set for storing documents to be retrieved.
- Click the Upload button to upload one or more documents to the document set.
Note: Files in the example document set cannot be deleted.

### Upload Test Set

<img width="1920" height="919" alt="image-2" src="https://github.com/user-attachments/assets/60561e44-2f61-405d-8110-1e950eb99045" />


- Download the sample test set file (in XLSX or JSON format) and prepare your test set according to the sample.
- Click the Upload button to upload the test set.

### Launch RAG Evaluation Task

<img width="1920" height="919" alt="image-3" src="https://github.com/user-attachments/assets/176a955e-7b79-45ad-b387-9ba7a15a5333" />


https://www.ragview.ai/components/evaluationManagement

1. Create a new evaluation task in Evaluation Management.
2. Enter the task name and description.
3. Select the document set and test set.
4. Select the RAG solutions to be evaluated.

<img width="1920" height="919" alt="image-4" src="https://github.com/user-attachments/assets/2a755830-3843-457b-b856-18b65d903755" />


5. Configure the parameters and evaluation metrics.
6. Click the Submit button to start the evaluation task.

### View Evaluation Details

<img width="1920" height="919" alt="image-8" src="https://github.com/user-attachments/assets/f16797be-797f-414e-968f-c7f0901109b1" />


On the evaluation task page, click Details on a task.

<img width="1920" height="919" alt="image-9" src="https://github.com/user-attachments/assets/47fb0ba9-9c7f-49e0-b830-d4a66a5f4ef4" />


View the metric scores for different tasks.

<img width="1920" height="919" alt="image-7" src="https://github.com/user-attachments/assets/d33f913d-3d8a-4ab6-91bc-987c76706845" />


View the detailed evaluation record for a single query.

<img width="1920" height="919" alt="image-10" src="https://github.com/user-attachments/assets/29aed1e1-985c-4d27-ba8b-3247cca95b46" />


View the detailed computation process for a single metric of a single query.

### Acquire More Evaluation Counts

Each evaluation task consumes one evaluation count per RAG solution selected. A task with multiple solutions will consume multiple counts. You can purchase additional evaluation counts on the purchase page.

## Frequently Asked Questions

1. Is RagView open source?  
Answer: RagView currently has no open source plan, but we aim to cover hardware operating costs with relatively low fees. However, we will open-source our optimized RAG solutions.  
GitHub: https://github.com/RagView/RagView.

2. How does RagView charge?  
Answer: We currently charge per evaluation count. In the future, pricing may align with tokens and runtime—both already tracked as rag evaluation metrics for transparency.

3. Can I automatically generate a test set from a document set?  
Answer: Yes. We plan to add a feature in version 1.1 to automatically generate a test set from the document set. With this feature, you will only need to click and wait for an LLM to generate QA pairs from the documents.

4. What is the format of the test set?  
Answer: The test set should be in XLSX or JSON format. Please refer to the sample file for the exact format.

5. What is the format of the document set?  
Answer: Currently, only PDF format is supported for documents. We plan to add support for image-based documents in future versions.

6. How can I view evaluation results?  
Answer: Go to the Evaluation Management page and open Details to review dashboards and downloadable reports of your rag evaluation metrics—including answer quality, context metrics, and efficiency.

7. How can I view the code for a RAG scheme?  
Answer: Currently, you will need to search for the RAG scheme by name on GitHub. In version 1.1, we will open-source the integrated code and provide a download link directly in the evaluation results.

8. Can RagView be used for commercial purposes?  
Answer: Yes, it can.

9. Can I compare my own RAG with open-source RAGs?  
Answer: We plan to support this in future versions. See our milestone plan (link) for details.

10. Which RAG schemes are already integrated into RagView?  
Answer: We have currently integrated R2R, LangFlow, and DocsGPT. In the future, we plan to add 1–2 new RAG schemes each week, depending on the availability and stability of open-source code. See our roadmap (link) for more details.

11. How can I contact you?  
Answer: You can contact us via email: <EMAIL>ragandview@gmail.com</EMAIL>

## RagView Milestone Plan

### Key Features

- Test Set Auto-Generation: Based on the documents in the document set, use a naive chunking method and an LLM to automatically generate Q&A pairs from each chunk, producing the test set data.
- Custom RAG Integration: Provide an SDK/API for developers to integrate their own RAG solutions into RagView, enabling comparison between their solutions and open-source solutions.
- Evaluation Task Optimization: Support setting up and comparing multiple configurations (different hyperparameters) of the same RAG solution.
- Evaluation Report Generation: Support automatic generation of PDF reports from evaluation results.

### Usability Enhancements

- Email Notifications: Since evaluations are asynchronous and may take minutes to tens of minutes, add email notifications to inform users when evaluation results are ready.
- Result Charting: Generate bar charts, pie charts, radar charts, etc., based on metric scores to facilitate visual comparison.
- Hardware Resource Profiling: Collect statistics on hardware resource usage for different evaluation pipelines, aiding developers in assessing production feasibility.
- Optional Metrics: Make evaluation metrics optional (no longer mandatory), allowing users to select only the metrics they are interested in.

### More RAG solutions

Legend:  
✅ = Integrated | 🚧 = In Progress | ⏳ = Pending Integration  

| No. | Name | GitHub Link | Features | Status |
|-----|------|-------------|----------|--------|
| 0 | Langflow | [langflow-ai/langflow](https://github.com/langflow-ai/langflow) | Build, scale, and deploy RAG and multi-agent AI apps.But we use it to build a naive RAG.  | ✅ |
| 1 | R2R | [SciPhi-AI/R2R](https://github.com/SciPhi-AI/R2R) | SoTA production-grade RAG system with Agentic RAG architecture and RESTful API support. | ✅ |
| 2 | KAG | [OpenSPG/KAG](https://github.com/OpenSPG/KAG) | Retrieval framework combining OpenSPG engine and LLM, using logical forms for guided reasoning; overcomes traditional vector similarity limitations; supports domain-specific QA. | ⏳ |
| 3 | GraphRAG | [microsoft/graphrag](https://github.com/microsoft/graphrag) | Modular graph-based retrieval RAG system from Microsoft. | 🚧 |
| 4 | LightRAG | [HKUDS/LightRAG](https://github.com/HKUDS/LightRAG) | "Simple and Fast Retrieval-Augmented Generation," designed for simplicity and speed. | ✅ |
| 5 | dsRAG | [D-Star-AI/dsRAG](https://github.com/D-Star-AI/dsRAG) | High-performance retrieval engine for unstructured data, suitable for complex queries and dense text. | 🚧 |
| 6 | paper-qa | [Future-House/paper-qa](https://github.com/Future-House/paper-qa) | Scientific literature QA system with citation support and high accuracy. | ⏳ |
| 7 | cognee | [topoteretes/cognee](https://github.com/topoteretes/cognee) | Lightweight memory management for AI agents ("Memory for AI Agents in 5 lines of code"). | ⏳ |
| 8 | trustgraph | [trustgraph-ai/trustgraph](https://github.com/trustgraph-ai/trustgraph) | Next-generation AI product creation platform with context engineering and LLM orchestration; supports API and private deployment. | ⏳ |
| 9 | graphiti | [getzep/graphiti](https://github.com/getzep/graphiti) | Real-time knowledge graph builder for AI agents, supporting enterprise-grade applications. | ⏳ |
| 10 | DocsGPT | [arc53/DocsGPT](https://github.com/arc53/DocsGPT) | Private AI platform supporting Agent building, deep research, document analysis, multi-model support, and API integration. | ✅ |
| 11 | youtu-graphrag | [youtugraph/youtu-graphrag](https://github.com/TencentCloudADP/youtu-graphrag) | Graph-based RAG framework from Tencent Youtu Lab, focusing on knowledge graph construction and reasoning for domain-specific applications. | ⏳ |
| 12 | Kiln | [https://github.com/Kiln-AI/Kiln](https://github.com/Kiln-AI/Kiln) | Desktop app for zero-code fine-tuning, evals, synthetic data, and built-in RAG tools. | ⏳ |
| 13 | Quivr | [https://github.com/QuivrHQ/quivr](https://github.com/QuivrHQ/quivr) |a RAG that is opinionated, fast and efficient so you can focus on your product. | ⏳ |

### More RAG Evaluation Metrics

We will gradually add functionality and performance metrics for RAG evaluation, including:

| **Metric Type**                     | **Metric Name**                              | **Description**                                                                            |
| ----------------------------------- | -------------------------------------------- | ------------------------------------------------------------------------------------------ |
| **Effectiveness / Quality Metrics** | Recall@k                                     | Proportion of queries where the correct answer appears in the top k retrieved documents    |
|                                     | Precision@k                                  | Proportion of relevant documents among the top k retrieved documents                       |
|                                     | MRR (Mean Reciprocal Rank)                   | Average reciprocal rank of the first relevant document                                     |
|                                     | nDCG (Normalized Discounted Cumulative Gain) | Ranking relevance metric that considers the importance of document order                   |
|                                     | Answer Accuracy / F1                         | Match between generated answers and reference answers (Exact Match or F1)                  |
|                                     | ROUGE / BLEU / METEOR                        | Text overlap / language quality metrics                                                    |
|                                     | BERTScore / MoverScore                       | Semantic-based answer matching metrics                                                     |
|                                     | Context Precision                            | Proportion of retrieved documents that actually contribute to the answer                   |
|                                     | Context Recall                               | Proportion of reference answer information covered by retrieved documents                  |
|                                     | Context F1                                   | Combined score of Precision and Recall                                                     |
|                                     | Answer-Context Alignment                     | Whether the answer strictly derives from the retrieved context                             |
|                                     | Overall Score                                | Composite metric, usually a weighted combination of answer quality and context utilization |
| **Efficiency / Cost Metrics**       | Latency                                      | Time required from input to answer generation                                              |
|                                     | Token Consumption                            | Number of tokens consumed during answer generation                                         |
|                                     | Memory Usage                                 | Memory or GPU usage during model execution                                                 |
|                                     | API Cost / Compute Cost                      | Estimated cost of calling the model or retrieval API                                       |
|                                     | Throughput                                   | Number of requests the system can handle per unit time                                     |
|                                     | Scalability                                  | System performance change when data volume or user requests increase                       |

