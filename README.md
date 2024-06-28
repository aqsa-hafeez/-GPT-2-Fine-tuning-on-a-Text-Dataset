# -GPT-2-Fine-tuning-on-a-Text-Dataset

# 1. Installation and Imports:

It starts by installing required libraries like transformers and accelerate using !pip install.
Then, it imports necessary libraries for working with datasets, transformers, training, and text generation.

# 2. Device Detection:

It checks if a GPU is available and assigns the device ("cuda") for training if present, otherwise defaults to CPU.

# 3. Loading Dataset:

It opens a text file (/content/drive/MyDrive/Datasets/custom_dataset.txt) containing your training text data.
Creates a Dataset object from the loaded text lines.
To avoid memory issues, it reduces the dataset size by selecting a maximum of 1000 examples using select function.

# 4. Tokenization:

It loads the pre-trained GPT-2 tokenizer.
Sets the padding token to the end-of-sentence token (EOS) for GPT-2.
Defines a function tokenize_function that applies the tokenizer to each text example with padding and truncation (limiting text length).
It uses map function to apply the tokenization function to the entire dataset in batches.

# 5. Data Collator:

A DataCollatorForLanguageModeling is created using the tokenizer for handling batched data during training.

# 6. Model Loading:

The pre-trained GPT-2 model is loaded and transferred to the designated device (CPU or GPU).

# 7. Training Arguments:

Training arguments are set using TrainingArguments:
Output directory for storing training results.
Overwrites existing files in the output directory.
Number of training epochs (set to 1 for demonstration).
Training batch size per device (reduced to 1 for demonstration).
Model checkpoints are saved every 10,000 steps with a maximum of 2 saved checkpoints.
Logging directory for training logs.

# 8. Trainer Initialization:

A Trainer object is initialized with the model, training arguments, training dataset, and data collator.

# 9. Training:

The train method of the trainer is called to start the fine-tuning process on your custom dataset.

# 10. Saving the Model:

After training, the fine-tuned model and tokenizer are saved to the specified directories (./fine-tuned-gpt2).

# 11. Text Generation:

The text-generation pipeline is loaded from the Transformers library using the fine-tuned model and tokenizer.
A prompt ("Once upon a time") is provided for text generation.
The pipeline generates text with a maximum length of 100 characters and returns one generated sequence.
Finally, the generated text is printed.
