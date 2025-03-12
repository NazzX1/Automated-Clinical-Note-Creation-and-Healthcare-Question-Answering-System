 

*********************
# DATASET INFORMATION
*********************
1. **Title of dataset**: The MTS-Dialog dataset

2. **Description**:
    it's a collection of 1.7k short doctor-patient conversations and corresponding clinical notes

3. **Recommended Citation**:
   ```bibtex
   @inproceedings{ben-abacha-etal-2023-empirical,
    title = "An Empirical Study of Clinical Note Generation from Doctor-Patient Encounters",
    title     = {An Empirical Study of Clinical Note Generation from Doctor-Patient Encounters},
    author    = {Asma Ben Abacha and Wen-wai Yim and Yadan Fan and Thomas Lin},
    booktitle = {Proceedings of the 17th Conference of the European Chapter of the Association for Computational Linguistics},
    year      = {2023},
    pages     = {2291--2302},
    address   = {Dubrovnik, Croatia},
    publisher = {Association for Computational Linguistics},
    url       = {https://aclanthology.org/2023.eacl-main.168/},
    doi       = {10.18653/v1/2023.eacl-main.168}
}
   

*************************
# DATA ACCESS INFORMATION
*************************

1. **Source** : [MTS-DIALOG](https://github.com/abachaa/MTS-Dialog)

2. **License** : Creative Commons Attribution 4.0 International (CC BY 4.0)
 

****************************
# METHODS OF DATA COLLECTION
****************************

1. **Methods of Data Collection**:
	The MTS-DIALOG dataset was created by generating simulated doctor-patient conversations from publicly available clinical notes. These clinical notes were sourced from the [Mtsamples collection](https://www.mtsamples.com/), a public repository of de-identified medical notes (South et al., 2014; Moramarco et al., 2022a). The selected notes cover the six most frequent note types and specialties in the collection, including:
        - General Medicine
        - SOAP (Subjective, Objective, Assessment, Plan)
        - Neurology
        - Orthopedic
        - Dermatology
        - Allergy/Immunology

2. **Quality assurance procedures**:
	The quality of the MTS-DIALOG dataset is ensured through a three-stage process:
        **Annotator Selection**: Only candidates with medical training (e.g., former medical scribes) were hired as annotators.
        **Training and Feedback**: Annotators received one-on-one periodic feedback during the initial stages from an experienced trainer.
        **Independent Validation**: The entire dataset was independently validated using a rubric grading system to ensure accuracy and consistency

************************
# SUMMARY OF DATA FILES
************************

1. **List of data files**
	📌 Filename: MTS-Dialog-TestSet-1-MEDIQA-Chat-2023.csv
	- Description: 
                Official test set used in the MEDIQA-Chat 2023 challenge (Task A : Section Header Topic Classification)

	📌 Filename: MTS-Dialog-TestSet-2-MEDIQA-Sum-2023.csv
	- Description: 
                Official test set used in the MEDIQA-Sum 2023 challenge (Task A & Task B : Section Header Topic Classification & Short Dialogue2Note Summarization)

	📌 Filename: MTS-Dialog-TrainingSet.csv
	- Description:
                The training set consists of 1,201 pairs of conversations and associated summaries.

	📌 Filename: ValidationSet.csv
	- Description:
                The validation set consists of 100 pairs of conversations and their summaries

📌 **Variable list**:
    - id : integer
    - section_header : string
    - section_text : string
    - dialogue : string  


    > **_NOTE:_**: the section headers are normalized to 20 labels:
       1. genhx [HISTORY of PRESENT ILLNESS]
       2. pastmedicalhx [PAST MEDICAL HISTORY]
       3. cc [CHIEF COMPLAINT]
       4. pastsurgical [PAST SURGICAL HISTORY]
       5. allergy
       6. ros [REVIEW OF SYSTEMS]
       7. medications
       8. assessment
       9. exam
       10. diagnosis
       11. disposition
       12. plan
       13. edcourse [EMERGENCY DEPARTMENT COURSE]
       14. immunizations
       15. imaging
       16. gynhx [GYNECOLOGIC HISTORY]
       17. procedures
       18. other_history
       19. labs

