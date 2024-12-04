# Chatbot
Transfer learnt model built on a pretrained LLM such as GPT-2
| **Task**                                     | **Comments**                                                                                          | **Status**      | **Individual Responsible** |
|----------------------------------------------|------------------------------------------------------------------------------------------------------|-----------------|----------------------------|
| **Preprocessing**                            | Handle emojis and punctuations POS tagging,Tokenization, padding, and dataset creation for GPT-2 fine-tuning.                                    | Done            | Ramandeep             |
| **Training**                                 | Three epochs of fine-tuning GPT-2 with proper optimizer.  | Done            | Akash             |
| **Evaluation (ROUGE-L, BERT Scores)**        | ROUGE-L and BERT scores computed for validation set predictions against ground truth responses.       | Done            | Akash            |
| **Interpretation using LIME**                | Placeholder steps for LIME text explanations.                                     | Not applicable         | Akash             |
| **1st round of tuning** | Fine-tuned learning rate from 5e-5 to 1e-4 for better model stability. | Done            | Ramandeep             |
| **2nd round of tuning** | Adjusted training loop for augmented dataset to enhance training diversity.                          | Done            | Akash             |
| **Final AUC Value**             | Achieved AUC value of 1.0 shows Strong distinguishability.                               | Done            | Ramandeep             |
| **Next Steps Recommendations**               | Evaluate on larger datasets, analyze model outputs, experiment with hyperparameters, integrate LIME/SHAP, use user feedback. | Done         | Akash & Ramandeep               |
