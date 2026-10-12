RAG Evaluation Pipeline & Parameter Optimization:
An automated evaluation framework designed to analyze how different chunking strategies, overlap sizes, and top-$K$ retrieval parameters impact large language model (LLM) generation quality and hallucination rates in Retrieval-Augmented Generation (RAG) systems.

Project Overview:
Retrieval-Augmented Generation (RAG) systems enhance Large Language Models by integrating external knowledge bases. However, system performance depends heavily on modular design choices. This project implements an end-to-end evaluation pipeline to systematically benchmark 80 distinct parameter configurations across domain-specific research questions.

Key Components:
Module 2 (Retrieval Pipeline): Ingests clean research papers, applies configurable chunking and window overlap, and performs vector retrieval using similarity scores.
Module 3 (LLM Generation): Feeds retrieved context into Qwen/Qwen2.5-3B-Instruct under greedy decoding (temperature=0.0) to generate answers, comparing RAG outputs against standalone LLM responses (No-RAG).
Module 4 (Evaluation & Benchmarking): Scores answer quality and hallucination rates across 80 configurations and 30 test queries.

Summary of Results
   
Method	Mean Answer Quality	Hallucination Rate
LLM Only (No-RAG)	0.60	0.00%
RAG + LLM (Average across 80 Configs)	1.53	0.38%
Top Configuration (CFG_032)	1.73	0.00%


Repository Structure: 
rag-evaluation-pipeline/
│
├── Module_2_Retrieval_Pipeline.ipynb     # Document chunking, indexing, and vector retrieval
├── Module_3_LLM_Generation.ipynb        # Qwen-2.5 generation and baseline comparison
├── module_4_code.ipynb                  # Automated evaluation and metric scoring
│
├── all_papers_sections_clean.csv        # Cleaned corpus of source research papers
├── evaluation_questions - module1_query_set.csv # Benchmark query set
├── module_2_retrieval_results.csv       # Retrieval outputs across configurations
├── module_3_generation_results.csv      # LLM generation outputs (RAG vs No-RAG)
├── module_4_configuration_summary.csv   # Aggregated performance per configuration
└── README.md                            # Project documentation

Experimental Parameters Tested:
Chunk Sizes: [250, 500, 750, 1000, 1500]
Overlap Sizes: [0, 50, 100, 200]
Top-$K$ Values: [1, 3, 5, 10]
Total Configurations Evaluated: 80   
Evaluation Dataset: 30 Domain-Specific Queries
