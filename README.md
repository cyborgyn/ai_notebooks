# AI related notebooks
This is a bunch of AI related notebooks I used for some tasks.

## Hungarian LLM evaluation results:

| LLM | en->hu BLEU | Spell error % | HuLU avg | GLUE avg |
| --- | ----------- | ------------- | -------- | -------- |
| gemma-2-27b-it-Q5_K_L.gguf | 0.1364 | 3.3% | 0.478 | 0.799
| SambaLingo-Hungarian-Chat-Q5_K_M.gguf | 0.1302 | 1.8% | 0.415 | 0.339
| salamandra-7b-instruct.Q6_K.gguf | 0.1157 | 2.9% | 0.437 | 0.588
| Meta-Llama-3.1-70B-Instruct-Q2_K.gguf | 0.1141 | 4.5% | 0.452 | 0.723
| PULI-LlumiX-32K-Instruct-Q4_K_M.gguf | 0.1132 | 2.9% | 0.426 | 0.499
| gemma-2-9b-it-Q6_K_L.gguf | 0.1125 | 3.2% | 0.495 | 0.799
| mixtral-8x7b-instruct-v0.1.Q5_K_M.gguf | 0.0946 | 3.6% | 0.450 | 0.762
| Meta-Llama-3.1-8B-Instruct-Q6_K_L.gguf | 0.0870 | 3.5% | 0.447 | 0.740
| Qwen2.5-32B-Instruct-Q4_K_L.gguf | 0.0705 | 8.3% | 0.456 | 0.811
| solar-10.7b-instruct-v1.0.Q6_K.gguf | 0.0673 | 8.0% | 0.478 | 0.699
| Ministral-8B-Instruct-2410-Q6_K_L.gguf | 0.0672 | 6.8% | 0.416 | 0.654
| c4ai-command-r-v01.i1-Q4_K_S.gguf | 0.0667 | 6.1% | 0.436 | 0.704
| gemma-2-2b-it-Q6_K_L.gguf | 0.0619 | 4.5% | 0.426 | 0.624
| salamandra-2b-instruct_Q6_K.gguf | 0.0600 | 8.6% | 0.425 | 0.316
| Llama-3.2-3B-Instruct-Q6_K_L.gguf | 0.0534 | 4.1% | 0.419 | 0.614
| Mistral-NeMo-Minitron-8B-Instruct-Q6_K_L.gguf | 0.0497 | 7.9% | 0.432 | 0.728
| Yi-1.5-34B-Chat-Q4_K_M.gguf | 0.0462 | 12.3% | 0.439 | 0.809
| llama-2-7b-32k-instruct.Q5_K_M.gguf | 0.0450 | 13.5% | 0.412 | 0.641
| Phi-3-medium-4k-instruct-Q6_K_L.gguf | 0.0373 | 8.4 | 0.024 | 0.716
| gpt-35-turbo-instruct | 0.0264 | 8.0% | 0.480 | ---
| Phi-3-mini-4k-instruct-q4.gguf | 0.0186 | 11.6% | 0.405 | 0.659
| falcon-mamba-7b-instruct.Q6_K.gguf | 0.0000 | 54.4% | 0.365 | ---

Notes 1:
- HuLU: Hungarian text comprehension tests
- GLUE: English text comprehension tests
- en->hu BLEU: English to Hungarian translation tests, evaluated with BLEU scoring + hunspell to check spelling errors.

Note 2:

SambaLingo-Hungarian-Chat is further trained of llama-2-7b. It translates much better to hungarian (0.1302,1.8% vs 0.0450,13.5%), however HuLU almost didn't change (improved negligable 0.415 vs 0.412), and GLUE score became catastrophic (0.339 vs 0.641). Most probably, what we can observe here, is catastrophic forgetting.

Note 3:

falcon-mamba-7b was so bad, it practically output gibberish. It's spell error is only 54%, because the other 46% were numbers. It's also very slow, and had very high request error rate for classification tasks, so I stopped mid running the GLUE eval process.

Note 4:

Even though gpt-35-turbo-instruct has a high HULU score (one of the highest), it's translation and hungarian spelling capabilities are very bad.

## Files in this repo
- **HUN_Book_scraping.ipynb**: a scraper to download most PDF files and their metadata from OSzK (Országos Széchenyi Könyvtár) MEK (Magyar Elektronikus Könyvtár)
- **HUN_Book_statistics.ipynb**: builds some statistics from the downloaded PDFs in CSV form, to further analyze in Excel
- **eval-GLUE.ipynb**: a simple, locally running Koboldcpp hosted LLM evaluator on the GLUE validation dataset
- **eval-HULU.ipynb**: a simple, locally running Koboldcpp hosted LLM evaluator on the HuLU validation dataset
- **gen-hunglish-testset.ipynb**: Generate hunglish evaluation dataset, for BLEU
- **eval-BLEU-en-hu.ipynb**: a simple, locally running Koboldcpp hosted LLM evaluator on the hunglish-BLEU.json dataset
- **LLM_Eval.xlsx**: the results of some LLM evaluations I run
