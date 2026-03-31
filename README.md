# An Empirical Study on LLMs-Generated Privacy Notices under the GDPR
This GitHub repo outlines the systematic steps taken to conduct research on popular frontier LLMs, to assess their proficiency in generating GDPR compliant privacy notices

### Prerequisites
#### Access Rights Required
1. Access to Google Colab or Google Colab Pro
2. Access to Google NotebookLM

#### Obtaining LLM API Keys
1. Google Gemini API (Can be obtained via: https://ai.google.dev/gemini-api/docs/api-key)
2. ChatGPT API (Can be obtained via: https://platform.openai.com/api-keys)
3. Claude API (Can be obtained via: https://platform.claude.com/settings/keys)

---

### Steps to Execute 
#### Generate LLM Privacy Notices
1. Clone the repo

2. Create a folder within Google Drive

3. Upload the clone repo to the created folder

4. Open the Folder_Organizer.ipynb script file within Google Colab and change the following {folder_name} values to match the file path of Dataset.csv

* csv_file ="/content/drive/MyDrive/{folder_name}/Datasets/Dataset.csv"
* base_path ="/content/drive/MyDrive/{folder_name}/Datasets"

5. Once changed, run the Folder_Organizer.ipynb script (this will create individual folders for each app listed within the Dataset.csv file). Once completed, you should have 43 new folders, one for each app.

6. Once completed, manually add the "original privacy notices" seen with the folder named "Original Privacy Notices" to the corresponding app folder created in Step 5.

7. Open the Generate_LLM_Privacy_Notices.ipynb script file within Google Colab and change the following {folder_location} values match the file path of Dataset.csv

- dataset_file_path = "/content/drive/MyDrive/{folder_name}/Datasets/Dataset.csv"
- base_dir = "/content/drive/MyDrive/{folder_name}/Datasets" (within functions query_claude(), query_gemini(), query_chatgpt())

8. Get the associated API keys for each of the LLMs (Google Gemini, ChatGPT, Claude), click on the "Secrets" menu item (left side), and store the values as shown below:

Notebook Access | Name        | Value    |
|---|---|---|
|Enable          | chatgpt-key | xxxxxxxx |
|Enable          | claude-key  | xxxxxxxx |
|Enable          | gemini-key  | xxxxxxxx |
   
9. Once changed, run the Generate_LLM_Privacy_Notices.ipynb script (this will create the individual LLM-generated privacy notices for Gemini-2.5-flash, Gemini-2.5-pro, ChatGPT-5, ChatGPT-5.2, Claude-Sonnet-4-5-20250929, Claude-Haiku-4-5-20251001 into each of the 43 app folders).

---

### Steps to Execute 
#### Run Cosine Similarity Data Assessment 
1. Open the Data_Analysis_Sentence_Transformers_Similarity.ipynb script file within Google Colab and change the following {folder_location} values match the file path of Datasets

- folder_path = "/content/drive/MyDrive/{folder_name}/Datasets/**/*.txt"
- directory_path = "/content/drive/MyDrive/{folder_name}/Datasets/"

2. Once changed, run the Data_Analysis_Sentence_Transformers_Similarity.ipynb script (this will create the Sentence Transformer-based similarity scores for each app x llm persona).

---

### Steps to Execute 
#### Conduct Grading Rubric Operation 
1. Open Google's NotebookLM and for a given app, upload the 18 LLM-generated privacy notices to the notebook (don't include the {app_name}_original_privacy_notice.txt)

2. Using the below questions, ask the NotebookLM to answer the following 14 questions:

- Is the identity and the contact details of the controller and, where applicable, of the controller’s representative; mentioned in all 18 sources?
- Is the contact details of the data protection officer, where applicable; mentioned in all 18 sources?
- Is the purposes of the processing for which the personal data are intended as well as the legal basis for the processing; mentioned in all 18 sources?
- Is where the processing is based on point (f) of Article 6(1), the legitimate interests pursued by the controller or by a third party; mentioned in all 18 sources?

- Is the recipients or categories of recipients of the personal data, if any; mentioned in all 18 sources?
- Is where applicable, the fact that the controller intends to transfer personal data to a third country or international organisation and the existence or absence of an adequacy decision by the Commission, or in the case of transfers referred to in Article 46 or 47, or the second subparagraph of Article 49(1), reference to the appropriate or suitable safeguards and the means by which to obtain a copy of them or where they have been made available. mentioned in all 18 sources?

- Is the period for which the personal data will be stored, or if that is not possible, the criteria used to determine that period; mentioned in all 18 sources?
- Is the existence of the right to request from the controller access to and rectification or erasure of personal data or restriction of processing concerning the data subject or to object to processing as well as the right to data portability; mentioned in all 18 sources?

- Is where the processing is based on point (a) of Article 6(1) or point (a) of Article 9(2), the existence of the right to withdraw consent at any time, without affecting the lawfulness of processing based on consent before its withdrawal; mentioned in all 18 sources?
- Is the right to lodge a complaint with a supervisory authority; mentioned in all 18 sources?

- Is whether the provision of personal data is a statutory or contractual requirement, or a requirement necessary to enter into a contract, as well as whether the data subject is obliged to provide the personal data and of the possible consequences of failure to provide such data; mentioned in all 18 sources?

- Is the existence of automated decision-making, including profiling, referred to in Article 22(1) and (4) and, at least in those cases, meaningful information about the logic involved, as well as the significance and the envisaged consequences of such processing for the data subject. mentioned in all 18 sources?

- Is the categories of personal data concerned; mentioned in all 18 sources?
- Is from which source the personal data originate, and if applicable, whether it came from publicly accessible sources; mentioned in all 18 sources?

3. Open the grading_rubic.csv file within Google Sheets and fill out the grades following the rubic.

