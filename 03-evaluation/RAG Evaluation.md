# RAG Evaluation

| **Evaluation Level**      | **What is Measured**                                                 | **Ground Truth Needed**                                                            |
| ------------------------- | -------------------------------------------------------------------- | ---------------------------------------------------------------------------------- |
| **Retrieval** (only)      | Did we fetch the right docs?                                         | **Ground truth relevance labels** (which docs/passages are relevant to each query) |
| **Generation** (only)     | Did the LLM produce a correct answer?                                | **Ground truth answers** (gold reference responses)                                |
| **Full RAG** (end-to-end) | Did the system answer correctly, considering retrieval + generation? | Both: relevance judgments **and** gold answers                                     |

## Methods for Data Generation

1. **Human Annotators/Domain Experts**: Highest quality, but time-consuming. Experts manually label relevant query-document pairs.
2. **LLMs for Synthetic Generation**: An LLM generates user questions from FAQ records; the original FAQ is the relevant document for these questions.
3. other methos, like User Interaction Logs

## Retrieval Evaluation: Metrics

Retrieval evaluation is central to RAG. It requires a ground truth dataset and treats retrieval as a **ranking problem**.

#### Common Metrics

1. **Hit Rate (a form of Recall)**
   
   - Did any relevant doc appear in the top-k results?
   
   - Binary per query, averaged over dataset.

2. **Mean Reciprocal Rank (MRR)**
   
   - Measures how early the first relevant document appears.
   
   - Formula: `MRR = avg(1/rank_of_first_relevant)`.

## Offline (Generation) Evaluation

Offline methods allow evaluation **before deployment**.

#### Embedding Similarity

One approach is to compare the **ground-truth answer** with the **LLM-generated answer** using embeddings + cosine similarity.

#### LLM-as-Judge

LLMs themselves can act as evaluators.

- **Idea**: Prompt the LLM to grade or compare answers.

- **Evaluation modes**:
  
  1. **With reference answer** → compares generated vs. ground truth.
  
  2. **Without reference** → evaluates directly the generated answer to the query.

## Broader LLM Evaluation & Monitoring

LLM apps need **ongoing evaluation**, both offline and online.

- **Offline** (pre-deployment): Hit-rate, MRR, cosine similarity, LLM judge.

- **Online** (post-deployment): A/B testing, user feedback, production monitoring.
