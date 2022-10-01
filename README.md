# InstructCode

> Improving Code Quality through Fine-Tuning Code Generation Models using Reinforcement Learning

This works explores a method to steer a code generation model to produce Python code with higher code quality and and less bugs. For this, we make use of a novel technique to fine-tune the code generation model [CodeParrot](https://huggingface.co/codeparrot) using Reinforcement Learning.

## How it works

The fine-tuning works as follows: The model receives a coding question in natural language, similar to the kind one might find on a Stack Overflow post, and is tasked to produce a code snippet that solves this problem. To reward high quality and correct code snippets, we use a BERT classifier to analyze the quality of the produced code snippet, and use the classifier outputs as reward signals for the reinforcement learning training which is performed using the PPO algorithm.

![Sketch of fine-tuning workflow](https://github.com/JohannesHa/InstructCode/blob/master/media/sketch-of-the-workflow.png?raw=true)

## Project Setup

- The report of the project can be found as the file `summary.pdf` in this folder.

- The trainings code for the model that will be referred to as the "Reward Model" in the report can be found in this folder as a notebook file called `fine-tune-bert-code-quality-classifcation-model.ipynb`

- The trainings code for fine-tuning the CodeParrot code generation model using reinforcement learning can be found in this folder as a notebook file called `fine-tune-code-generation-model-using-reinforcement-learning.ipynb`

For running both notebook files, I recommend loading them into Google Colab and activating GPU support. 

- The StaQC data that is needed for running both notebook files can be found via the following Google drive link: https://drive.google.com/drive/folders/1iZevo7TgNXjukTh-AfuRxe_vUZ8WnVzy?usp=sharing

- The weights for both models (the reward model + the optimized CodeParrot code generation model) can also be found as a zipped file via the provided Google drive link. 
- For demo purposes, you can interact directly with the uploaded version of the model through the Hosted inference API on the HuggingFace Hub via the following link:
    - https://huggingface.co/Johannes/distilbert-base-uncased-finetuned-code-snippet-quality-scoring


## Acknowledgements
A huge thank you to Leandro von Werra for creating the two libraries/models this project is building upon (The [trl library](https://github.com/lvwerra/trl) + [the CodeParrot models](https://huggingface.co/blog/codeparrot)). I really appreciate your open-source work!