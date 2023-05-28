# Python-Code-Generator

https://github.com/AvishakeAdhikary/Python-Code-Generator/assets/32614982/f86b2cbd-2e44-45ff-b432-43a1cc0e8e19

## Introduction
This is a Python code for generating code snippets using the pre-trained language model from Salesforce called CodeGPT. This code uses the Hugging Face Transformers library, which provides an easy-to-use interface to access the pre-trained models.

## Installation
To use this code, you need to have the `transformers` library installed in your Python environment. You can install it using the following command:

!pip install transformers

## Usage
1. First, you need to import the necessary libraries and load the pre-trained model and tokenizer using the following code:

from transformers import AutoModelForCausalLM, AutoTokenizer
import torch

checkpoint = "Salesforce/codegen2-1B"
device = "cuda" if torch.cuda.is_available() else "cpu"

tokenizer = AutoTokenizer.from_pretrained(checkpoint)
model = AutoModelForCausalLM.from_pretrained(checkpoint, trust_remote_code=True, revision="main")

2. Then, you can prompt the user to input a prompt for the code snippet using the following code:
```
prompt = str(input("Enter your prompt: "))
```


3. Next, you can encode the prompt using the tokenizer and generate the code snippet using the pre-trained model using the following code:
```
input_ids = tokenizer(prompt, return_tensors="pt").input_ids
generated_ids = model.generate(input_ids, max_length=1024)
```
4. Finally, you can decode the generated code snippet using the tokenizer and print it to the console using the following code:
```
print(tokenizer.decode(generated_ids[0], skip_special_tokens=True))
```
## Model
This code uses the pre-trained model from Salesforce called CodeGPT. The model is a transformer-based language model that has been trained on a large corpus of code from various programming languages. The model can generate code snippets given a prompt or a description of the desired functionality.

![image](https://github.com/AvishakeAdhikary/Python-Code-Generator/assets/32614982/57818749-8754-448e-a291-1f89c2f1d741)

## Acknowledgements
This code is based on the Hugging Face Transformers library and the pre-trained model from Salesforce called CodeGPT.
