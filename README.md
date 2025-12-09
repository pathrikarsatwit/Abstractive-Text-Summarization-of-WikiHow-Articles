# Abstractive-Text-Summarization-of-WikiHow-Articles
Test Summarization Using T5 Small Model
1. NLP Final Project: Abstractive Text Summarization with T5-small

    1. This repository contains an end-to-end abstractive text summarization system built using a fine-tuned T5-small model. The model summarizes long passages into concise, coherent outputs and is trained on article–summary pairs. The final fine-tuned model is publicly available on the HuggingFace Hub under the name Sakshi-1234/NLPFinal, allowing users to run inference without retraining.

    This README explains the project, provides an example summarization, and outlines clear steps for replicating the entire pipeline.

2. Project Overview

    1. The project uses the T5-small model, a text-to-text transformer architecture well suited for summarization tasks. The dataset was preprocessed by cleaning the text and adding the prefix “summarize:” to each input document. After tokenization, the model was fine-tuned for 2 epochs on an NVIDIA A100 GPU. Training took approximately 1 hour and 23 minutes.

    Once trained, the model and tokenizer were saved and uploaded to HuggingFace so that others can use the summarization model directly.

3. Features

    1. Fully reproducible dataset preparation
    2. Tokenization pipeline for T5-small
    3. Fine-tuning with the HuggingFace Trainer
    4. Inference pipeline with post-processing
    5. Publicly hosted model
    6. Example summarization output

4. Example Summarization

    1. Input Text:
        "Tempeh isn’t always easy to find in grocery stores, but if you have a health food store or a natural foods store in your area you’ll find it in the refrigerated section, close to the tofu. If you prefer not to buy commercially made tempeh, you can make your own. The process is time consuming, but you’ll be able to rest assured that your tempeh contains only natural ingredients."

    2. Generated Summary:
        "Tempeh can be found in natural food stores near tofu, or you can make it at home, though the process takes time. Homemade tempeh ensures the use of only natural ingredients."

5. Evaluation Overview

    1. ROUGE-1 achieved the strongest performance, capturing the core keywords in the summaries. ROUGE-2 and ROUGE-L scores were moderate, which is expected for abstractive summarization where generated phrasing often differs from reference summaries. Overall, the model performs reliably for producing coherent, high-level summaries of unseen text.

6. How to Replicate This Project
    Below are the full steps required to reproduce the entire workflow. However, because the final fine-tuned model is already uploaded to HuggingFace under Sakshi-1234/NLPFinal, users who only want to run inference may skip all training steps and start directly from Step 7.
    Prepare the Environment

    1. Install all required Python libraries (Transformers, Datasets, Evaluate, Torch).
        1. Set up GPU access if you plan to retrain the model.

    2. Load and Inspect the Dataset
        1. Use a dataset containing article–summary pairs.
        2. Check the structure and clean unwanted characters or spacing.

    3. Preprocess and Tokenize the Dataset
        1. Add the “summarize:” prefix to inputs.
        2. Tokenize both articles and summaries.
        3. Pad or truncate to fixed maximum lengths.

    4. Select and Initialize the Model
        1. Load the T5-small architecture and its tokenizer.
        2. Configure prefix, max length, and truncation rules.
        
    5. Configure the Training Pipeline
        1. Define training hyperparameters such as epochs, batch size, learning rate, and evaluation strategy.
        2. Mixed precision may be enabled for faster training.

    6. (Optional) Train the Model
        1. Training is not required because the fine-tuned model is already available publicly.
        2. If you choose to retrain:
            1. training on an A100 GPU took 1 hour and 23 minutes.
            2. After training, save both model and tokenizer.
    
    7. Load the Pretrained Fine-Tuned Model
        1. Most users will start here.
        2. Load the model from the HuggingFace Hub: Sakshi-1234/NLPFinal
        3. This allows running summaries immediately without repeating preprocessing or training.
        
    8. Build and Run the Inference Pipeline
        1. Tokenize new text with the same settings as training.
        2. Generate summaries using the model.
        3. Apply post-processing such as whitespace normalization.
        
    9. Evaluate the Summaries (Optional)
        1. If reproducing the evaluation, compute ROUGE metrics by comparing generated summaries with reference ones.
    
    10. Use the Model for Any New Input
