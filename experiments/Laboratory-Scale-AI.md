# Toward Laboratory-Scale AI

It's the age of the mono-model. OpenAI, Google, and Anthropic have conquered the language model landscape, offering a product more powerful than
anything achievable by academic and public interest companies.

...Or have they? A leaked Google memo stoked excitement (and concerns) in declaring that Big Tech may have "no moat" - no true competitive advantage - 
as technologies like low-rank adaptation, quantization, and knowledge distillation have enabled small players to build highly performant customized models
on mid-range LLMs like Llama-7b, often at very low cost (a few hundred dollars).

With this project, the Howe lab looks to put these promising initial results with "Laboratory-Scale" language models on firm empirical footing 
by evaluating large, closed models against small, open alternatives, focusing specifically on academic and public interest settings which have 
strong incentives to remain independent of corporate infrastructure.

## Questions

1. Can open models running on consumer-grade hardware compete with large, closed models like ChatGPT?
2. What techniques work best to even the playing field? (Quantization, LoRA, Prompt Optimization, Teacher-Student Distillation)
3. Are smaller models tolerably efficient at inference time in comparison to large closed models?
4. Does there exist a disparity with regard to task-relevant fairness metrics between large closed models and small open models?

## Description

We want to understand whether small, open Laboratory-Scale Language Models (LSLMs?) can compete with large, closed Large Language Models (LLMs), especially on
tasks of public or academic interest where the use of transparent, fair, and/or privacy-preserving methods are worth a few percentage points of task performance.

## Research Design

We will evaluate ~3-7 small, open models against ~3-7 large, closed models. Evaluations will concern 1) performance on tasks of public
or academic interest and 2) fairness in task-relevant settings.

### Model Selection

Open models should be:

1. Mountable (and trainable) on either a consumer-grade 16GB T4 GPU (scenario 1) or a 40GB A100 GPU (scenario 2), with or without quantization.
2. Previously instruction-tuned or chat-tuned to allow more direct comparison with large models and to minimize adaptation costs.
3. Open source or available with one of the following licenses...

Candidate open models:

1. Meta LLAMA-2-Chat 7B
2. Mistral-7B-Instruct
3. Hugging Face H4-Zephyr
4. LMSYS Vicuna
5. Google Flan-T5
6. LAION-AI OpenAssistant
7. TII Falcon

Closed models should be:

1. Widely ~~hyped~~ used
2. What else?

Candidate closed models:

1. OpenAI GPT-3.5-Turbo
2. OpenAI GPT-4
3. Google Bard/Palm
4. Anthropic Claude
5. Cohere Coral

### Performance task selection

Performance tasks should be:

1. Publicly available with an open, easily accessible dataset and established metrics.
2. Of interest to governmental, non-profit, or academic organizations that may prefer not to rely on closed, pay-per-token models.
3. Accomplishable within the architectural constraints of a smaller model (e.g., article-length summarization would qualify, but book-length summarization would not).

Candidate performance tasks:

1. Fact-Checking: FreshQA
2. Text Summarization: CNN DailyNews
3. Hybrid Hiring

### Fairness task selection

Fairness tasks should be:

1. Connected to the real-world use of the model (not solely intrinsic).
2. Publicly available with a dataset and evaluation metrics, or at least well-described enough to be reconstructed.

Candidate fairness tasks:

1. Name-nationality bias (Text Summarization)
2. Differential TPR in occupation prediction (Hybrid Hiring)

### Evaluation Settings

Models can be assessed in the following settings:

1. Zero-shot
    - With CoT prompting
    - With prompt compilation
2. Fine-tuned
    - With low-rank adaptation
3. Distillation
    - With small open models learning from large closed models

Fine-tuning and distillation have a maximum budget of $25 per adaptation and a maximum carbon budget of...

Closed models will likely be assessed only in the zero-shot setting, though we can fine-tune some of them if we decide that is
worthwhile as a point of comparison.

## Results

We can report results from open and closed models on the selected tasks in markdown tables.

------------------------------------------------------------------------------------
| Zero-Shot Results by Task                                                        |
------------------------------------------------------------------------------------
| Task                   || Llama-2-Chat | Mistral-7B | Vicuna || GPT-3.5T | GPT-4 |
------------------------------------------------------------------------------------
| FreshQA Fact-Checking  ||              |            |        ||          |       |
| CNN Text Summarization ||              |            |        ||          |       |
| Hybrid Hiring          ||              |            |        ||          |       |
------------------------------------------------------------------------------------

------------------------------------------------------------------------------------
| Fine-Tuned Results by Task                                                       |
------------------------------------------------------------------------------------
| Task                   || Llama-2-Chat | Mistral-7B | Vicuna || GPT-3.5T | GPT-4 |
------------------------------------------------------------------------------------
| FreshQA Fact-Checking  ||              |            |        ||          |       |
| CNN Text Summarization ||              |            |        ||          |       |
| Hybrid Hiring          ||              |            |        ||          |       |
------------------------------------------------------------------------------------

## Overleaf Draft

Draft to be linked after adding some of the basics. We can shoot for ACM FAccT (end of January 2024) or AIES (mid-March 2024).

## Relevant Reading

1. We Have No Moat (leaked Google memo)
2. Llama, Alpaca, Vicuna papers
3. LoRA, qLoRA
4. Substack

(to be linked)

## Ideas

Drop 'em here!

Interview study? Would be interesting to hear how government, academia, etc. think about large vs. small models.