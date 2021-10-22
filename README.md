# Differential Diagnosis Dialogue Dataset Automatic Creation Instructions

In this project, we build a T5 model that take some symptoms as input and output a patient sentence or a doctor question.

T5 is an encoder-decoder model pre-trained on a multi-task mixture of unsupervised and supervised tasks and for which each task is converted into a text-to-text format. 

The data we used for the training was from [medDG](https://github.com/lwgkzl/MedDG), a Chinese medical dialogue dataset that collects conversations between physicians and patients and marks the symptoms of each conversation. We first translated it into English and collected the symptoms and corresponding sentences for the training.

We divide the data into doctor and patient, and use these two data to generate a doctor's conversation and a patient's conversation respectively. Each data point is: some symptoms (input), and a question or sentence (label). For example input: diarrhea, nausea. Output: I feel a little nauseous, a little diarrhea, and a little chest tightness, is it related to pneumonia? For example, input : stomachache, output: Hello! Is it a pain in the abdomen or breasts ?

In order for T5 to work well, a different prefix is needed for the input corresponding to each task, e.g., for translation: translate English to German: …, for summarization: summarize: …. In this task, we treat dialogue generation as summarization problem, so we used "summarize:" as prefix to the input data. In the future we will try to experiment with different prefixes to see if the results can be better.
