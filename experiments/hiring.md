# Bias in Hiring

## Questions

1. Can small finetuned models perform competitvely against GPT-4 at identifying a person's career based on their biography?
2. Can these models do so while achieving less bias?
3. How does altering the gender/career joint distribution of the finetuning set affect performance and bias?

## Description

See [here](https://github.com/BillHoweLab/notes/blob/main/Howe_Microsoft_Accelerate_Foundation_Models_Research_Proposal.docx) for 
more details. 

## Design

- Use subsets of [biobias](https://github.com/microsoft/biosbias)  with different distributions of gender and jobs to train models
- Measure their TPR at identifying people of different careers, as well as the differences in TPR between people who use male pronouns and those who use female pronouns
- Can compare to [HybridHiring](https://www.microsoft.com/en-us/research/publication/investigations-of-performance-and-bias-in-human-ai-teamwork-in-hiring/) if we want to benchmark against humans

## Results

- Measurement of ChatGPT on HybridHiring discused [here](https://github.com/BillHoweLab/notes/blob/main/2023-10-11%20Hiring%20Updates.pdf)
