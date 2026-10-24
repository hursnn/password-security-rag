# Password Security RAG with LangChain

For this project, I rebuilt my previous RAG system using LangChain.
I kept the same five password-security documents and the same eight
questions so I could compare the two versions.

The notebook loads the documents, splits them into chunks, stores them
in Chroma, and retrieves information for each question. I connected the
retriever, prompt template, and model step using the pipe operator.

## Files

- `langchain_notebook.ipynb`: My completed notebook with outputs.
- `my_kb/`: The same five documents from my previous project.
- `goldset.json`: Six answerable questions and two unanswerable questions.
- `results_langchain.csv`: My experiment results.
- `ai_framework_kb.md`: The practice document provided for this module.
- `framework_goldset.json`: The questions for the practice document.

## How to Run

Open the notebook in Colab or Jupyter. Put the data files and the
`my_kb` folder in the same working directory. Run the installation cell
first, then run the remaining cells in order.

An API key and GPU are not required. The first run needs internet access
to download the packages and embedding models. I used offline mode,
which shows part of the retrieved text instead of generating an answer.
If nothing is retrieved, it says it does not know.

## Results

For this experiment, I used a chunk size of 500, an overlap of 100,
and k=3. I changed only the score threshold.

| Score threshold | Evidence found / 6 | Refused / 2 |
|---|---:|---:|
| 0.1 | 6 | 0 |
| 0.2 | 6 | 1 |
| 0.3 | 6 | 1 |
| 0.4 | 5 | 2 |
| 0.5 | 4 | 2 |
| 0.6 | 2 | 2 |

A higher threshold helped the system refuse unanswerable questions,
but it also missed some questions that the documents could answer.

I also tested a configuration with the same fixed-character splitting,
embedding function, L2 distance, and k value as my previous project.
It found the evidence for all six answerable questions and refused
both unanswerable questions.

For that comparison, I used the score formula `1 - distance / 2`.
The previous distance threshold of 0.9 becomes a score threshold of 0.55.
This formula applies to this configuration, not every LangChain setup.

My previous results counted a question as found if any chunk was
retrieved. In the matched test, I checked both whether a chunk was
retrieved and whether it contained an evidence phrase.

## One Problem I Found

At a threshold of 0.3, the system retrieved a passage for the question
about the exact number of password breaches worldwide in 2025.
The passage explained password breaches, but it did not include that
number. Its score was 0.3258, so it passed the threshold.

This showed me that a related passage does not always contain the answer.
The offline function still displayed it because the retrieval was not empty.
