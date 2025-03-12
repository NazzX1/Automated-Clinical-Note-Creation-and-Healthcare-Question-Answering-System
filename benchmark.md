# LLM benchmark for clinical note QA


-------------------------------------------------------------------------------
1. Introduction:
    this benchmark evaluates the performance of LLMs in answering questions based on clinical notes.
    The goal is to assess how well the model can understand and extract relevant information from complex medical texts
-------------------------------------------------------------------------------------------------------------------------

2. Benchmark Overview:

   - **Task** : Question answering on clinical notes
   - **Datasets** :
    custom clinical QA Dataset :  dataset of clinical notes with annotated questions and answers (10 QA_pairs, 3 clinical_notes)
    Asclepius-Synthetic-Clinical-Notes dataset : This dataset is composed with Clinical Note - Question - Answer format to build a clinical LLMs.
    
  
   - **Metrics**:
     - F1-score : Percentage of predictions that match the ground truth exactly.
     - Bleu-score : measure of the precision of n-grams in the model output, against the reference text.
     - Rouge-1 : refers to the overlap of unigrams (each word) between the system and reference summaries.
     - Rouge-2 : refers to the overlap of bigrams between the system and reference summaries.
     - Rouge-L : measures the length of the longest common subsequence (LCS) present in the reference text and the hypothesis text.
     - BERTscore : a metric for evaluating text generation that computes similarity scores based on contextual embeddings from models like BERT, capturing semantic meaning rather than exact word matches

--------------------------------------------------------------------------------------
3. Models details:
   
   **🚩 Baseline Model**:
    - *deepseek-R1*📌 : 
          open-weight large language model (LLM) developed by DeepSeek, optimized for reasoning, code generation, and natural language understanding. It features a transformer-based architecture, supporting multi-turn dialogue, code assistance, and general AI tasks


   **🚩 Evaluated models**:

     - *BioMistral-7B-DARE*📌:
               a merged pretrained language model specifically designed for biomedical and clinical applications. It is created by combining multiple pre-trained models using the DARE TIES (Drop And REscale with TIES merging) method, which enhances the model's performance and efficiency by selectively dropping redundant parameters and rescaling weights.
     
     
     ```sh
               @misc{labrak2024biomistral,
                    title={BioMistral: A Collection of Open-Source Pretrained Large Language Models for Medical Domains}, 
                    author={Yanis Labrak and Adrien Bazoge and Emmanuel Morin and Pierre-Antoine Gourraud and Mickael Rouvier and Richard Dufour},
                    year={2024},
                    eprint={2402.10373},
                    archivePrefix={arXiv},
                    primaryClass={cs.CL}
               }}}

    ```


    - *Bio-Medical-3B-CoT-012025*📌:
               This model is a fine-tuned version of Qwen2.5-3b-Instruct on a custom "BioMedData" dataset (Ne : 600,000+), enhanced with chain-of-thought prompting instructions to introduce advanced reasoning capabilities. It has been specifically optimized for applications in the Healthcare & Lifesciences (HLS) domain.
    ```sh
               @misc{ContactDoctor_Bio-Medical-3B-CoT-012025,
                    author = {ContactDoctor},
                    title = {Bio-Medical-3B-CoT-012025: A High-Performance Biomedical Language Model with Reasoning Capabilities},
                    year = {2025},
                    howpublished = {https://huggingface.co/ContactDoctor/Bio-Medical-3B-CoT-012025},
               }} 
    ```

    - *Apollo2-2B*📌:
                This model is a dense model trained on the [ApolloMoEDataset]("https://huggingface.co/datasets/FreedomIntelligence/ApolloMoEDataset"), a high-quality medical dataset that includes books, papers, encyclopedias, doctor-patient dialogues, exams, websites, and practical guidelines. Specifically designed for healthcare applications, the model is well-suited for tasks such as medical question answering, diagnosis assistance, and patient interaction.
    ```sh
               @misc{ContactDoctor_Bio-Medical-3B-CoT-012025,
                    author = {ContactDoctor},
                    title = {Bio-Medical-3B-CoT-012025: A High-Performance Biomedical Language Model with Reasoning Capabilities},
                    year = {2025},
                    howpublished = {https://huggingface.co/ContactDoctor/Bio-Medical-3B-CoT-012025},
               }}
    ```
    - *BioMedLM*📌:
                is new language model trained exclusively on biomedical abstracts and papers from [The Pile](https://pile.eleuther.ai/)

    ```sh
               @misc{bolton2024biomedlm27bparameterlanguage,
                    title={BioMedLM: A 2.7B Parameter Language Model Trained On Biomedical Text}, 
                    author={Elliot Bolton and Abhinav Venigalla and Michihiro Yasunaga and David Hall and Betty Xiong and Tony Lee and Roxana Daneshjou and Jonathan Frankle and Percy Liang and Michael Carbin and Christopher D. Manning},
                    year={2024},
                    eprint={2403.18421},
                    archivePrefix={arXiv},
                    primaryClass={cs.CL},
                    url={https://arxiv.org/abs/2403.18421}, 
                    }}}
    ```

--------------------------------------------------------------------------------------

4. Results:
   
   ```sh 
    Note : the models are provided with a clinical note and a question then the answers are evaluated against the ground truth annotations
   ```


📌On the custom clinical QA Dataset :

| Model      | nb of parameters      | F1-score | Bleu-score | Rouge-1 | Rouge-2 | Rouge-L | BERTscore | inference_method |
| --------------- | --------------------- |  --------------------- | --------------------- | --------------------- | --------------------- |  --------------------- | --------------------- | --------------------- |
| Deepseek-R1 | 671B | 0.60 | 0.35 | 0.71 | 0.58 | 0.69 | 0.95 | api |
| BioMistral-7B-DARE | 7B | 0.37 | 0.0013 | 0.26 | 0.14 | 0.23 | 0.81 | api |
| Bio-Medical-3B-CoT-012025 | 3B | 0.42 | 0.07 | 0.48 | 0.28 | 0.45 | 0.92 | api |
| Apollo2-2B | 2B | 0.28 | 0.03 | 0.34 | 0.18 | 0.30 | 0.89 | api |
| BioMedLM | 2.7B | 0.06 | 1.7946814451803416e-156 | 0.09 | 0.009 | 0.074 | 0.80 | image |


📌On the Asclepius-Synthetic-Clinical-Notes Dataset : 

| Model      | nb of parameters      | F1-score | Bleu-score | Rouge-1 | Rouge-2 | Rouge-L | BERTscore | inference_method |
| --------------- | --------------------- |  --------------------- | --------------------- | --------------------- | --------------------- |  --------------------- | --------------------- | --------------------- |
| Deepseek-R1 | 671B | -- | -- | -- | -- | -- | -- | api |
| BioMistral-7B-DARE | 7B | 0.37 | 0.21 | 0.42 | 0.28 | 0.34 | 0.83 | api |
| Bio-Medical-3B-CoT-012025 | 3B | 0.26 | 0.08 | 0.40 | 0.22 | 0.29 | 0.88 | api |
| Apollo2-2B | 2B | 0.28 | 0.10 | 0.39 | 0.23 | 0.31 | 0.87 | api |
| BioMedLM | 2.7B | 0.06 | 1.7946814451803416e-156 | 0.09 | 0.009 | 0.074 | 0.80 | image |




- Bio-Medical-3B-CoT-012025 (3B) emerges as the best choice among the smaller models for clinical QA tasks, achieving strong performance on the Custom Clinical QA Dataset (F1-score: 0.42, BERTScore: 0.92) and moderate performance on the Asclepius-Synthetic-Clinical-Notes Dataset (F1-score: 0.26, BERTScore: 0.88). While BioMistral-7B-DARE (7B) performs slightly better on the Asclepius dataset (F1-score: 0.37), its lower performance on the Custom Clinical QA Dataset makes it less consistent. Apollo2-2B (2B) shows moderate results, and BioMedLM (2.7B) is not viable due to poor performance. Therefore, Bio-Medical-3B-CoT-012025 is the recommended model for its balance of performance and efficiency.

--------------------------------------------------------------------------------------
