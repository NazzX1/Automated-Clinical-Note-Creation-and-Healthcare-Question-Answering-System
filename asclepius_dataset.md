 

*********************
# DATASET INFORMATION
*********************
1. **Title of dataset**: Asclepius-Synthetic-Clinical-Notes

2. **Description**:
    a collection of 158,000 rows of Clinical Note - Question - Answer pairs, generated using GPT-3.5 from PMC-Patients case reports

3. **Recommended Citation**:
   ```bibtex
   @misc{kweon2024publiclyshareableclinicallarge,
      title={Publicly Shareable Clinical Large Language Model Built on Synthetic Clinical Notes}, 
      author={Sunjun Kweon and Junu Kim and Jiyoun Kim and Sujeong Im and Eunbyeol Cho and Seongsu Bae and Jungwoo Oh and Gyubok Lee and Jong Hak Moon and Seng Chan You and Seungjin Baek and Chang Hoon Han and Yoon Bin Jung and Yohan Jo and Edward Choi},
      year={2024},
      eprint={2309.00237},
      archivePrefix={arXiv},
      primaryClass={cs.CL},
      url={https://arxiv.org/abs/2309.00237}, 
}
   

*************************
# DATA ACCESS INFORMATION
*************************

1. **Source** : [Asclepius-Synthetic-Clinical-Notes](https://huggingface.co/datasets/starmpcc/Asclepius-Synthetic-Clinical-Notes)

2. **License** : Creative Commons Attribution 4.0 International (CC BY 4.0)
 

****************************
# METHODS OF DATA COLLECTION
****************************

1. **Methods of Data Collection**
	The dataset is structured in a Clinical Note - Question - Answer format, designed to train and evaluate clinical large language models (LLMs). The data collection process involved two key steps:

   - Synthesis of Synthetic Clinical Notes:
        Synthetic clinical notes were generated using GPT-3.5, based on case reports from PMC-Patients (PubMed Central Patient Case Reports). This step ensured the creation of realistic and diverse clinical narratives.

   - Generation of Instruction-Answer Pairs:
        Using the synthetic clinical notes, 157,000 instruction-answer pairs were generated. These pairs were created to simulate real-world clinical questions and answers



📌 **Variable list**:
    - patient-is : integer
    - note : string
    - question : string
    - answer : string
    - task : string    


    > **_NOTE:_**: the task column is normalized to 8 labels:
       1. Question answering
       2. Abbreviation expansion
       3. Relation extraction
       4. Named Entity recognition
       5. Summarization
       6. Temporal information extraction
       7. Coreference resolution
       8. paraphrasing

