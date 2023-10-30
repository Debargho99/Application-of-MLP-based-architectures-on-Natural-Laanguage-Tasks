# Exploring-MLP-based-architectures-for-natural-language-tasks

## Introduction
Transformers are the model architectures of choice in the era of
pre-trained language models. While completely Multilayer Perceptron,
or MLP,architectures have showed promise in recent research
in both the vision and language domain, they have not been investigated
utilizing the pre-train-fine-tune approach. Are MLP models
competitive to Transformers in the context of language models
when pre-trained? This study addresses this research subject and
delivers a number of intriguing conclusions. We find that MLPbased
pre-trained models are competitive with their Transformer
counterpart in some cases, albeit with constraints. We conduct experiments
on a throughout an extensive range of datasets/tasks
in the GLUE and SCROLLS benchmarks. Overall, the findings outlined
in this paper makes us optimistic for the utility of alternative
architectures for language tasks.

## Setting up the environment

``` pip install requirments.txt -r ```

## Experiments
### Non Pretrained Setting
Sure! Here are the bullet points:

- Non-pretrained scenario:
  - Use frozen transformer embeddings.
  - Add Attention/MLP blocks on top of them.

- Token size <= 512:
  - Take BERT embeddings.
  - Fine tune the setup for GLUE benchmark tasks.

- Token size > 512:
  - Use Longformer embeddings.
  - Fine tune the setup for QALT and CNLI tasks of the SCROLLS benchmark.

- MLP block configuration:
  - Input dimension, hidden dimension, and output dimension of token mixing block set in the ratio 1:2:1.

- Longformer attention block:
  - 4 heads.
  - Input dimension of 512.

- Sparse attention block:
  - 12 heads.
  - Input dimension of either 1024 or 4096.

- Consistency across experiments:
  - All experiments contain 24 self-attention or MLP blocks.

### Pretrained Setting

Sure! Here are the bullet points:

- Pre-training duration and batch size:
  - Both MLP and Transformer models are pre-trained for 24 hours in steps.
  - Batch size is set to 128.

- Training setup:
  - Identical to the 24-hour BERT introduced by Intel.

- Pre-training objective:
  - Masked Language Modelling (MLM).
  - Goal is to recover randomly masked tokens in a sequence.

- Optimization and learning rate scheduler:
  - Adafactor optimizer.
  - Inverse square root learning rate scheduler.

- Pre-training data:
  - Sequence length < 512: Colossal Cleaned Common Crawl Corpus (C4).
  - Sequence length > 512: Long Document Corpus.

- Pre-training execution:
  - Each pre-training run is performed using Google Cloud TPU services.
  - Runs for approximately 55,000-56,000 training iterations.

