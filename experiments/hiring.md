# Bias in Hiring
## Description

We also choose to evaluate the models on the occupation labeling task introduced by \citet{de-arteaga_bias_2019}. This task involves short biographies that specify a person’s occupation, which were scraped from Common Crawl. Mentions of the person’s occupation are removed from the biography, and the remaining text is then used to predict the occupation. \citet{li_prompt_2023} report an accuracy of 85.65% for a bias-mitigated BERT model fine-tuned for the task, the best accuracy of which we are aware. 

## Performance Metric
Classification accuracy. Percent of biographies labeled with the correct occupation. 

## Bias metric
Difference in TPR between men and women. TPR is the percent of biographies labeled with the correct occupation. (TPR is the same as accuracy, just that RW seems to use “TPR Gap” to talk abt bias and “Accuracy” to talk about performance).

## Code/Data
Available [here](https://github.com/isaacOnline/biosbias)

## Training Setup
Text classification. Not sure exactly how to do this with our modeling setup? Should we create a prompt? 


@inproceedings{de-arteaga_bias_2019,
	location = {New York, {NY}, {USA}},
	title = {Bias in Bios: A Case Study of Semantic Representation Bias in a High-Stakes Setting},
	isbn = {978-1-4503-6125-5},
	url = {https://doi.org/10.1145/3287560.3287572},
	doi = {10.1145/3287560.3287572},
	series = {{FAT}* '19},
	abstract = {We present a large-scale study of gender bias in occupation classification, a task where the use of machine learning may lead to negative outcomes on peoples' lives. We analyze the potential allocation harms that can result from semantic representation bias. To do so, we study the impact on occupation classification of including explicit gender indicators—such as first names and pronouns—in different semantic representations of online biographies. Additionally, we quantify the bias that remains when these indicators are "scrubbed," and describe proxy behavior that occurs in the absence of explicit gender indicators. As we demonstrate, differences in true positive rates between genders are correlated with existing gender imbalances in occupations, which may compound these imbalances.},
	pages = {120--128},
	booktitle = {Proceedings of the Conference on Fairness, Accountability, and Transparency},
	publisher = {Association for Computing Machinery},
	author = {De-Arteaga, Maria and Romanov, Alexey and Wallach, Hanna and Chayes, Jennifer and Borgs, Christian and Chouldechova, Alexandra and Geyik, Sahin and Kenthapadi, Krishnaram and Kalai, Adam Tauman},
	date = {2019},
	note = {event-place: Atlanta, {GA}, {USA}},
	keywords = {gender bias, algorithmic fairness, automated hiring, compounding injustices, online recruiting, Supervised learning},
}

@inproceedings{li_prompt_2023,
	location = {Toronto, Canada},
	title = {Prompt Tuning Pushes Farther, Contrastive Learning Pulls Closer: A Two-Stage Approach to Mitigate Social Biases},
	url = {https://aclanthology.org/2023.acl-long.797},
	doi = {10.18653/v1/2023.acl-long.797},
	shorttitle = {Prompt Tuning Pushes Farther, Contrastive Learning Pulls Closer},
	abstract = {As the representation capability of Pre-trained Language Models ({PLMs}) improve, there is growing concern that they will inherit social biases from unprocessed corpora. Most previous debiasing techniques used Counterfactual Data Augmentation ({CDA}) to balance the training corpus. However, {CDA} slightly modifies the original corpus, limiting the representation distance between different demographic groups to a narrow range. As a result, the debiasing model easily fits the differences between counterfactual pairs, which affects its debiasing performance with limited text resources. In this paper, we propose an adversarial training-inspired two-stage debiasing model using Contrastive learning with Continuous Prompt Augmentation (named {CCPA}) to mitigate social biases in {PLMs}' encoding. In the first stage, we propose a data augmentation method based on continuous prompt tuning to push farther the representation distance between sample pairs along different demographic groups. In the second stage, we utilize contrastive learning to pull closer the representation distance between the augmented sample pairs and then fine-tune {PLMs}' parameters to get debiased encoding. Our approach guides the model to achieve stronger debiasing performance by adding difficulty to the training process. Extensive experiments show that {CCPA} outperforms baselines in terms of debiasing performance. Meanwhile, experimental results on the {GLUE} benchmark show that {CCPA} retains the language modeling capability of {PLMs}.},
	eventtitle = {{ACL} 2023},
	pages = {14254--14267},
	booktitle = {Proceedings of the 61st Annual Meeting of the Association for Computational Linguistics (Volume 1: Long Papers)},
	publisher = {Association for Computational Linguistics},
	author = {Li, Yingji and Du, Mengnan and Wang, Xin and Wang, Ying},
	editor = {Rogers, Anna and Boyd-Graber, Jordan and Okazaki, Naoaki},
	urldate = {2023-10-31},
	date = {2023-07},
}
