# Password Security: A RAG-Based Question Answering System

## Project Overview

This project was developed for IT7075 Applied AI for Cybersecurity at the University of Cincinnati.

The goal is to build a Retrieval-Augmented Generation (RAG) system that answers questions using a custom knowledge base about password security.

## Knowledge Base

The knowledge base contains five Markdown documents covering:

1. Password fundamentals
2. Password managers
3. Multi-factor authentication
4. Phishing and password attacks
5. Password breach response

The documents contain approximately 10,000 characters in total. Their origins are described in `my_kb/SOURCES.md`.

## RAG Implementation

The system uses Python, ChromaDB, and an embedding model to retrieve relevant document chunks.

The workflow includes:

1. Loading the knowledge base
2. Splitting documents into overlapping chunks
3. Storing embeddings in ChromaDB
4. Retrieving relevant chunks using vector similarity
5. Filtering retrieved chunks by distance
6. Returning supporting evidence or refusing unsupported questions

The current custom implementation returns retrieved evidence rather than generating a new answer with an LLM.

## Evaluation

The evaluation dataset contains eight questions:

- Six answerable questions
- Two unanswerable questions

With a maximum distance threshold of 0.9 and k=3, the system achieved:

- Found: 6/6
- Refused: 2/2
- Evidence found: 6/6

These results measure retrieval and evidence coverage, not the accuracy of LLM-generated answers.

## Experiments

Two retrieval parameters were evaluated independently:

- Maximum distance threshold
- Number of retrieved chunks (k)

The distance threshold affected retrieval performance. A threshold of 0.9 achieved the best balance in the tested configurations.

Changing k from 1 to 8 did not change the evaluation scores at a threshold of 0.9.

Detailed results are available in `results.csv`, and the visualization is saved as `figure.png`.

## Project Files

- `rag_notebook.ipynb` — Implementation and experiment outputs
- `my_kb/` — Custom password security knowledge base
- `goldset.json` — Evaluation questions and supporting evidence
- `results.csv` — Experimental results
- `figure.png` — Experiment visualization

## How to Run

1. Open `rag_notebook.ipynb` in Google Colab.
2. Install the required Python packages.
3. Upload the knowledge base files and `goldset.json`.
4. Run the notebook cells in order.
5. Review the retrieval results and evaluation outputs.

## AI Assistance

ChatGPT was used to assist with educational content drafting, Python code development, and debugging. The implementation and experimental results were reviewed during the project.