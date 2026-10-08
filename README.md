# AI related notebooks
This is a bunch of AI related notebooks I used for some tasks.

## Hungarian LLM evaluation results:

| LLM | en->hu BLEU | Spell error % | HuLU avg | GLUE avg |
| --- | ----------- | ------------- | -------- | -------- |
| MichelRosselli/apertus:70b-instruct-2509-q4_k_m| 0.1478 | 2.7% | 0.627 | ---
| onprem-ai/Apertus-v1.5-8B-FP8 | 0.1376 | 2.1% | 0.640 | 0.722
| gemma-2-27b-it-Q5_K_L.gguf | 0.1364 | 3.3% | 0.727 | 0.799
| google_gemma-3-27b-it-Q5_K_L.gguf | 0.1327 | 3.3% | 0.759 | 0.804
| MichelRosselli/apertus:8b-instruct-2509-q4_k_m | 0.1313 | 2.5% | 0.616 | 0.652
| SambaLingo-Hungarian-Chat-Q5_K_M.gguf | 0.1302 | 1.8% | 0.459 | 0.339
| Qwen3.8-27B-W4A16-AutoRound-fast | 0.1210 | 3.3% | 0.771 | 0.777
| salamandra-7b-instruct.Q6_K.gguf | 0.1157 | 2.9% | 0.487 | 0.588
| gemma4:31b | 0.1152 | 6.2% | 0.789 | 0.834
| Meta-Llama-3.1-70B-Instruct-Q2_K.gguf | 0.1141 | 4.5% | 0.677 | 0.723
| PULI-LlumiX-32K-Instruct-Q4_K_M.gguf | 0.1132 | 2.9% | 0.496 | 0.499
| gemma-2-9b-it-Q6_K_L.gguf | 0.1125 | 3.2% | 0.727 | 0.799
| glm-4.7-flash:q4_K_M | 0.1124 | 2.9% | 0.638 | 0.725
| Mistral-Small-24B-Instruct-2501-Q6_K.gguf | 0.1036 | 5.2% | 0.725 | 0.811
| RedHatAI/gemma-4-26B-A4B-it-FP8-dynamic | 0.0990 | 5.0% | 0.690 | 0.796
| phi-4-Q6_K.gguf | 0.0981 | 3.4% | 0.705 | 0.791
| Llama-3.3-70B-Instruct-Q2_K.gguf | 0.0954 | 9.3% | 0.747 | 0.788
| Mistral-Small-3.2-24B-Instruct-2506-virtuoso | 0.0952 | 7.2% | 0.669 | 0.789
| mixtral-8x7b-instruct-v0.1.Q5_K_M.gguf | 0.0946 | 3.6% | xxx | 0.762
| gpt-oss:20b | 0.0888 | 3.5% | 0.702 | ---
| Meta-Llama-3.1-8B-Instruct-Q6_K_L.gguf | 0.0870 | 3.5% | xxx | 0.740
| Qwen2.5-32B-Instruct-Q4_K_L.gguf | 0.0705 | 8.3% | xxx | 0.811
| Qwen3.5-4B-FP8 | 0.0694 | 4.6% | 0.686 | 0.710
| aya-expanse:32b | 0.0677 | 8.0% | 0.586 | ---
| solar-10.7b-instruct-v1.0.Q6_K.gguf | 0.0673 | 8.0% | xxx | 0.699
| Ministral-8B-Instruct-2410-Q6_K_L.gguf | 0.0672 | 6.8% | xxx | 0.654
| c4ai-command-r-v01.i1-Q4_K_S.gguf | 0.0667 | 6.1% | xxx | 0.704
| gemma-2-2b-it-Q6_K_L.gguf | 0.0619 | 4.5% | xxx | 0.624
| salamandra-2b-instruct_Q6_K.gguf | 0.0600 | 8.6% | xxx | 0.316
| Llama-3.2-3B-Instruct-Q6_K_L.gguf | 0.0534 | 4.1% | xxx | 0.614
| Ministral-3:14b | 0.0519 | 3.2% | 0.702 | --
| Mistral-NeMo-Minitron-8B-Instruct-Q6_K_L.gguf | 0.0497 | 7.9% | xxx | 0.728
| Yi-1.5-34B-Chat-Q4_K_M.gguf | 0.0462 | 12.3% | xxx | 0.809
| llama-2-7b-32k-instruct.Q5_K_M.gguf | 0.0450 | 13.5% | xxx | 0.641
| Phi-3-medium-4k-instruct-Q6_K_L.gguf | 0.0373 | 8.4 | xxx | 0.716
| gpt-35-turbo-instruct | 0.0264 | 8.0% | xxx | ---
| OLMoE-1B-7B-0924-Instruct-Q6_K_L.gguf | 0.0201 | 10.6% | xxx | 0.574
| Phi-3-mini-4k-instruct-q4.gguf | 0.0186 | 11.6% | xxx | 0.659
| DeepSeek-R1-Distill-Qwen-32B-Q4_K_L.gguf | 0.0013 | 55.2% | xxx | 0.816
| falcon-mamba-7b-instruct.Q6_K.gguf | 0.0000 | 54.4% | xxx | ---

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

Note 5:

DeepSeek-R1-Distill-Qwen-32B uses a different output format, first "thinks" then "responds", thus the unmodified en->hu BLEU evaluation also takes into consideration the preceding english "thinking" output, and substantially makes results worse, even though it has the highest GLUE score, and midrange HuLU score (though slightly worse then the original Qwen2.5-32B).

Note 6:

In october 2026, I discovered a bug in HuLU testing while migrating the scripts to use OpenAI endpoints. This invalidates previous measurements on this site, hence the *xxx* value in that column. Remeasurement in progress...

## Files in this repo
- **HUN_Book_scraping.ipynb**: a scraper to download most PDF files and their metadata from OSzK (Országos Széchenyi Könyvtár) MEK (Magyar Elektronikus Könyvtár)
- **HUN_Book_statistics.ipynb**: builds some statistics from the downloaded PDFs in CSV form, to further analyze in Excel
- **eval-GLUE.ipynb**: a simple, locally running Koboldcpp hosted LLM evaluator on the GLUE validation dataset
- **eval-HULU.ipynb**: a simple, locally running Koboldcpp hosted LLM evaluator on the HuLU validation dataset
- **gen-hunglish-testset.ipynb**: Generate hunglish evaluation dataset, for BLEU
- **eval-BLEU-en-hu.ipynb**: a simple, locally running Koboldcpp hosted LLM evaluator on the hunglish-BLEU.json dataset
- **LLM_Eval.xlsx**: the results of some LLM evaluations I run
