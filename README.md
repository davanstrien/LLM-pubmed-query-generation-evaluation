# PubMed Query Generation Evaluation

This repository contains code and data for evaluating the performance of various language models in assisting with the generation of PubMed search queries. The evaluation is conducted on a set of 9 representative prompts that a user might pass to a model to help generate an advanced search query.

## Language Models Evaluated
The following language models are currently being evaluated:

- anthropic/claude-3-opus
- openai/gpt-4-0314
- databricks/dbrx-instruct
- cohere/command-r-plus
- mistralai/mixtral-8x7b-instruct
- mistralai/mistral-7b-instruct:free

This selection includes both open-source and closed models.

## Evaluation Metrics
For each prompt, the generated query is passed to the PubMed API, and the initial search results are parsed to provide a crude sense of query performance. The evaluation metrics include:

- The number of search results returned by PubMed (note: more results do not necessarily indicate a better query, as overly broad queries can return too many results)
- "Quoted Phrases Not Found Count": the number of terms in the search query not recognized as valid MeSH terms or keywords by PubMed, serving as a rough proxy for model "hallucination"
- Whether the search query generated by the model caused an error when passed to the PubMed API (Failed)  
- Whether the search query required basic regex processing to be valid for the PubMed API (Regex)

Please note that this evaluation does not closely assess the relevance of the retrieved articles, but rather provides a general indication of query performance.

## Results Summary
Here is a summary table of the search result counts for each model across the 9 test prompts:

| search_idx | anthropic/claude-3-opus | cohere/command-r-plus | databricks/dbrx-instruct | mistralai/mistral-7b-instruct:free | mistralai/mixtral-8x7b-instruct | openai/gpt-4-0314 |
|------------:|--------------------------:|------------------------:|---------------------------:|-------------------------------------:|----------------------------------:|--------------------:|
| 0          | 280                      | 454985                 | 0                         | 326                                 | 189                              | 24                 |
| 1          | 1078                     | 498                    | 2                         | 0                                   | 2200                             | 1531               |
| 2          | 222                      | 71                     | 0                         | 0                                   | 0                                | 195                |
| 3          | 276                      | 0                      | 0                         | 0                                   | 0                                | 1                  |
| 4          | 1788                     | 0                      | 0                         | 0                                   | 1063                             | 101                |
| 5          | 2803                     | 696                    | 0                         | 0                                   | 49                               | 1292               |
| 6          | 116                      | 0                      | 0                         | 0                                   | 0                                | 86                 |
| 7          | 4731                     | 4364                   | 0                         | 0                                   | 1903                             | 382                |
| 8          | 1525                     | 14562                  | 1332                      | 21750                               | 0                                | 11239              |

## Usage
A Jupyter notebook demonstrating how to run this evaluation on your own will be shared in the future. Please stay tuned for updates.