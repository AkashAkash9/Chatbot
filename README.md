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


## Features
- **Fine-tuning**: Leverages the `transformers` library to train the GPT-2 model on the custom conversation dataset.
- **Evaluation**: Computes and displays performance metrics such as ROUGE-L Score, BERT Score, and AUC, and generates ROC curves.
- **Model Interpretability**: Placeholder for integrating interpretability tools for explaining model decisions.
- **Custom Tokenization**: Handles input tokenization with padding and truncation to fit a specific maximum length for efficient model processing.
- **Deployment**: Interactive web app using Streamlit for real-time model testing.

## Data Preparation
The dataset should be in CSV format (`processed_data.csv`) and must have the following columns:
- **`human`**: Contains the human-side of the conversation.
- **`gpt`**: Contains the GPT-generated responses.

Ensure that the CSV file is placed in the `data/` directory for the scripts to access it.

## Usage Instructions

### Training the Model
The training script fine-tunes a pre-trained GPT-2 model using the provided dataset. The training process involves specifying hyperparameters such as learning rate, batch size, and the number of epochs. This step is crucial for adapting the pre-trained model to the specific nature of the conversation data.

### Evaluating the Model
The evaluation script computes key performance metrics:
- **ROUGE-L Score**: Measures the fluency and overlap of n-grams between generated text and reference responses.
- **BERT Score**: Assesses the semantic similarity between generated responses and ground truths using BERT embeddings.
- **AUC & ROC Curve**: Evaluates the binary classification performance of the model. The AUC score is a measure of how well the model distinguishes between human and GPT responses.
### Output 

0	human	gpt
0	1	ive been feeling so sad and overwhelmed lately...	hey there im here to listen and support you it...
1	2	i recently got a promotion at work which i tho...	i can understand how it can be overwhelming wh...
2	3	well the workload has increased significantly ...	it sounds like youre dealing with a lot of pre...
3	4	ive been trying to prioritize my tasks and del...	its great to hear that youre already implement...
4	5	youre right i havent really opened up about my...	its completely normal to feel that way but rem...

Embedding(50258, 768)

Epoch 1/3: 100%|██████████| 13/13 [01:58<00:00,  9.11s/it]
Epoch 1 Loss: 11.1060
Epoch 2/3: 100%|██████████| 13/13 [01:39<00:00,  7.64s/it]
Epoch 2 Loss: 9.6153
Epoch 3/3: 100%|██████████| 13/13 [01:38<00:00,  7.60s/it]
Epoch 3 Loss: 8.3855

Generated Responses: ['Human: i have a few close friends who have always been there for me maybe its time i lean on them more GPT: its wonderful that you have a support system already in place remember that its okay to ask for help and lean on those who care about you to help you navigate your way through this difficult time.\n\nRAW Paste Data\n\nHello everyone! I am here to talk about my experiences with my friends and family and how they have been able to support me through this difficult time. I am', 'Human: ill definitely make a conscious effort to reach out when i need support it just feels nice knowing that im not alone in this GPT: youre never alone in this journey its important to regularly check in with yourself and your emotions are there any selfcare practices you enjoy or would like to explore to help you navigate this conflict.\n\nRAW Paste Data\n\nDear Reader, As you can imagine, more people are reading The Jerusalem Post than ever before. Nevertheless, traditional business models are no longer sustainable and high-quality publications, like ours, are being forced to look', 'Human: ive always found solace in art maybe i can start painting again and use it as an outlet for my emotions GPT: that sounds like a fantastic idea art therapy can be a powerful tool for selfexpression and emotional healing it can help you connect with your feelings on a deeper level than just your emotions.\n\nAdvertisements', "Human: thank you for your guidance and support i really appreciate it GPT: youre welcome remember healing takes time so be patient with yourself im here for you every step of the way feel free to reach out whenever you need to talk about anything you can about this or any other topic you feel like you can help us understand what you're up against i hope you can find a way to help us understand what you're up against i hope you can find a way to help us understand", 'Human: im feeling extremely upset today its so hard to trust in myself GPT: im here for you can you tell me more about whats causing you to feel upset and why its difficult to trust yourself? i dont know how you feel about me but its been a while since i have been here im glad you are here to help you understand whats going on im glad you are here to help you understand whats going on im glad you are here to help', 'Human: i constantly doubt my abilities and feel like im never good enough its hard to have confidence in my decisions when im afraid of making mistakes GPT: it sounds like selfesteem is a major issue for you can you recall any specific experiences or moments that have contributed to this lack of trust in yourself and your abilities?\n\nReply · Report Post', 'Human: well in school i always compared myself to others and felt like i couldnt measure up i was often criticized by teachers and classmates and that made me doubt my own worth GPT: im sorry to hear that you went through such challenging experiences its understandable how those experiences would have a lasting impact on your selfesteem can you remember any instances when you did feel confident in yourself or your abilities?\n\nAnonymous 05/12/15 (Tue) 07:33:49 AM No. 95958 >>95958\n\nI remember feeling like i was a burden to myself and my friends and my coworkers and my', 'Human: there were a few times when i achieved something i had worked really hard for like getting a good grade on a project or receiving praise for my talent but those moments were fleeting and the doubt quickly crept back in GPT: its essential to acknowledge your accomplishments and the moments when you do feel capable im curious how do you see yourself in comparison to others who have been through similar experiences?\n\nI feel like I have been through a lot of challenges and setbacks but I feel like I have been able to overcome them without feeling overwhelmed by them. I feel like I have been able to express myself through', 'Human: i often feel like everyone else has it all together and im the only one struggling i tend to think that im inherently flawed which makes it hard to trust my own abilities GPT: remember everyone has their own struggles and insecurities even if they might not show it its important to realize that you have unique strengths and talents that make you who you are have you ever tried reframing your negative thoughts about yourself and its important to remember that you have been through a lot and you can tell its not always easy to find your way around its important to remember that you have been through a lot and you can tell its not always easy to find your way around its', 'Human: ive tried but its challenging to shift my perspective it feels natural to be selfcritical and find flaws in everything i do GPT: changing thought patterns takes time and practice have you considered engaging in activities that boost your selfesteem such as pursuing hobbies or setting achievable goals?\n\nI have been doing this for a while now and its been a great experience. I have been able to understand myself better and understand my emotions and emotions have been a great help to me understand myself better and understand my emotions have been a', 'Human: i guess ive never really tried those things im afraid of failure and worry that even if i try i wont succeed GPT: its understandable to feel apprehensive but remember that selfesteem is built through experience and overcoming challenges taking small steps and celebrating even the smallest victories can help you build confidence whats one small goal youd like to accomplish?\n\nReply · Report Post', 'Human: i suppose i could start by dedicating some time each day to a hobby i enjoy like painting maybe if i focus on something i love it will help boost my selfesteem GPT: thats a wonderful idea engaging in activities that bring you joy and allow for selfexpression can have a tremendous impact on your selfesteem remember to be kind to yourself throughout this process and celebrate each step forward no matter how small or insignificant it may seem.']
Ground Truths: ['Human: i have a few close friends who have always been there for me maybe its time i lean on them more GPT: its wonderful that you have a support system already in place remember that its okay to ask for help and lean on those who care about you', 'Human: ill definitely make a conscious effort to reach out when i need support it just feels nice knowing that im not alone in this GPT: youre never alone in this journey its important to regularly check in with yourself and your emotions are there any selfcare practices you enjoy or would like to explore to help you navigate this conflict', 'Human: ive always found solace in art maybe i can start painting again and use it as an outlet for my emotions GPT: that sounds like a fantastic idea art therapy can be a powerful tool for selfexpression and emotional healing it can help you connect with your feelings on a deeper level', 'Human: thank you for your guidance and support i really appreciate it GPT: youre welcome remember healing takes time so be patient with yourself im here for you every step of the way feel free to reach out whenever you need to talk', 'Human: im feeling extremely upset today its so hard to trust in myself GPT: im here for you can you tell me more about whats causing you to feel upset and why its difficult to trust yourself', 'Human: i constantly doubt my abilities and feel like im never good enough its hard to have confidence in my decisions when im afraid of making mistakes GPT: it sounds like selfesteem is a major issue for you can you recall any specific experiences or moments that have contributed to this lack of trust in yourself', 'Human: well in school i always compared myself to others and felt like i couldnt measure up i was often criticized by teachers and classmates and that made me doubt my own worth GPT: im sorry to hear that you went through such challenging experiences its understandable how those experiences would have a lasting impact on your selfesteem can you remember any instances when you did feel confident in yourself', 'Human: there were a few times when i achieved something i had worked really hard for like getting a good grade on a project or receiving praise for my talent but those moments were fleeting and the doubt quickly crept back in GPT: its essential to acknowledge your accomplishments and the moments when you do feel capable im curious how do you see yourself in comparison to others', 'Human: i often feel like everyone else has it all together and im the only one struggling i tend to think that im inherently flawed which makes it hard to trust my own abilities GPT: remember everyone has their own struggles and insecurities even if they might not show it its important to realize that you have unique strengths and talents that make you who you are have you ever tried reframing your negative thoughts about yourself', 'Human: ive tried but its challenging to shift my perspective it feels natural to be selfcritical and find flaws in everything i do GPT: changing thought patterns takes time and practice have you considered engaging in activities that boost your selfesteem such as pursuing hobbies or setting achievable goals', 'Human: i guess ive never really tried those things im afraid of failure and worry that even if i try i wont succeed GPT: its understandable to feel apprehensive but remember that selfesteem is built through experience and overcoming challenges taking small steps and celebrating even the smallest victories can help you build confidence whats one small goal youd like to accomplish', 'Human: i suppose i could start by dedicating some time each day to a hobby i enjoy like painting maybe if i focus on something i love it will help boost my selfesteem GPT: thats a wonderful idea engaging in activities that bring you joy and allow for selfexpression can have a tremendous impact on your selfesteem remember to be kind to yourself throughout this process and celebrate each step forward no matter how small']
ROUGE-L: 0.7967323161792907
BERT Score: [0.838638961315155, 0.8232792615890503, 0.9712232351303101, 0.7971480488777161, 0.8147158026695251, 0.9561942219734192, 0.8509508967399597, 0.8607290983200073, 0.8783012628555298, 0.8457299470901489, 0.9734296798706055, 0.9757768511772156]

### First Round of Tuning
Epoch 1/3: 100%|██████████| 13/13 [02:05<00:00,  9.67s/it]
Epoch 1 Loss: 6.3317
Epoch 2/3: 100%|██████████| 13/13 [01:38<00:00,  7.57s/it]
Epoch 2 Loss: 3.9096
Epoch 3/3: 100%|██████████| 13/13 [01:38<00:00,  7.61s/it]
Epoch 3 Loss: 1.5481

ROUGE-L: 0.7967323161792907
BERT Score: [0.838638961315155, 0.8232792615890503, 0.9712232351303101, 0.7971480488777161, 0.8147158026695251, 0.9561942219734192, 0.8509508967399597, 0.8607290983200073, 0.8783012628555298, 0.8457299470901489, 0.9734296798706055, 0.9757768511772156]

### Second Round of Tuning
Epoch 1/3: 100%|██████████| 14/14 [02:37<00:00, 11.23s/it]
Epoch 1 Loss: 0.5878
Epoch 2/3: 100%|██████████| 14/14 [02:11<00:00,  9.36s/it]
Epoch 2 Loss: 0.4380
Epoch 3/3: 100%|██████████| 14/14 [01:48<00:00,  7.72s/it]
Epoch 3 Loss: 0.3695

ROUGE-L: 0.7772292973259689
BERT Score (F1): [0.8855832815170288, 0.9565747380256653, 0.9999998807907104, 0.9118945598602295, 0.8849402666091919, 0.9001768827438354, 0.7956093549728394, 0.8433223366737366, 0.8383560180664062, 0.7773559093475342, 0.8929117918014526, 0.7789052128791809]

### AUC Score: 1.0000


### Generating Responses
The response generation script allows users to input a prompt and obtain a continuation generated by the fine-tuned GPT-2 model. This helps in testing the model's ability to handle different conversational contexts.

### Interpretability
A placeholder script for integrating interpretability tools like LIME or SHAP is available. These tools can provide insights into the model's decision-making process, helping users understand which parts of the input influence the model's output the most.

### Deployment with Streamlit
The model is deployed as an interactive web app using Streamlit. This allows users to enter prompts and receive real-time responses from the fine-tuned model. To run the app locally:
1. Created app.py
2. Run the Streamlit app script by executing:
   streamlit run app.py

