# T5 Text Summarizer

A Python notebook companion for a prototype that condenses longer text into a shorter summary. It uses the pretrained `t5-small` model through Hugging Face Transformers and presents a text input and output in Gradio.

[Open the Google Colab notebook](https://colab.research.google.com/drive/16eq4xWrxKD2qtFc09EMAewZbTVjjxcPj?usp=sharing) · [Read the source snapshot](https://github.com/vivekar217220-del/AI_Projects/blob/main/Text_Summarizer)

![Preview of the text summarizer interface](https://github.com/user-attachments/assets/ff1ce676-6747-44db-bbe2-0a83e2731487)

## How it works

1. The user enters a passage in the Gradio text field.
2. The summarizer prefixes the input with `summarize: ` so the text-to-text model receives the intended task.
3. The T5 tokenizer converts the input to a PyTorch tensor and truncates it at the configured input limit.
4. The model generates a new sequence with beam search.
5. The tokenizer decodes the generated sequence, skipping special tokens, and Gradio displays the summary.

| Source setting | Value |
| --- | --- |
| Model | `t5-small` |
| Input limit in the tokenizer call | 1,024 tokens with truncation enabled |
| Generation bounds | `min_length=40` and `max_length=150` |
| Beam search | Four beams, length penalty of 2.0, early stopping enabled |

The numeric settings govern token sequences. The number of words displayed varies with the text and tokenizer.

## Try the notebook

1. Open the Colab link at the top of this page and connect a Python runtime.
2. Follow the notebook sections for dependencies, pretrained model loading, the summarization function, and the Gradio interface.
3. Submit a short article or study note and compare the summary with the original.

For a quick qualitative check, start with a passage that includes a topic, a fact, and a result. Check whether the summary keeps those details and avoids changing numbers or inventing information. Repeat with a longer passage to see where truncation matters.

## Repository scope

This repository contains the notebook link and interface preview. The implementation snapshot lives in [AI Projects](https://github.com/vivekar217220-del/AI_Projects/blob/main/Text_Summarizer). The prototype demonstrates pretrained model inference and a simple UI. Review generated summaries against the source, especially when using text close to the input limit.
