# Entity Matching


## Description
The task is entity matching, with the idea that this will help in the property transfer/voting record linkage in my housing project. There’s a lot of work in entity matching so we have some flexibility in how we carry out the task.

We could use either a dataset introduced by others, or a dataset I’ve created for my housing project. The custom dataset consists of two tables derived from public records from Mecklenburg County, North Carolina. The first contains 15,532 names and addresses from a subset of the county’s property transfer documents (specifically those documents that involve instant buying real estate companies and that occurred before ~January of 2023). The second table consists of 2,003,414 names and address from the county’s voter records. The join is based on name and address. 

The main issues with this dataset are that 1) There are no ground truth labels currently, and 2) Others haven’t used it, so we’d have to measure performance of other methods ourselves. 

An alternative would be using a dataset that’s previously been used in entity matching (or entity resolution even). Examples of this might be [DBPedia](https://github.com/ZJU-DAILY/LargeEA), or a dataset like DBLP-ACM or Magellan that’s included in the [Machamp](https://arxiv.org/pdf/2106.08455.pdf) benchmark.

Worth noting that others have performed [prompt tuning for Entity Matching on RoBERTa-base](https://doi.org/10.14778/3565816.3565836), so we’ll want to think about how our work complements theirs. 

## Performance Metric
F1 (related to pairs in test set that are labeled correctly as either matches or non matches; Could also use accuracy, tpr, tnr, etc.) Others show a variety of metrics, including F1 \cite{wang_promptem_2022,yao_entity_2022}.

## Bias metric: 
If we use the housing dataset, or another dataset that could be labeled for race/gender: bias@k, e.g. in FairER: Entity Resolution With Fairness Constraints (acm.org)


## Code/Data
Tables are available [here](https://drive.google.com/drive/folders/1TnIBZ0JTmaql3AUPKWK52fMzFVCucCbX?usp=sharing). I still need to make entity-pairs that will be used for training (we also need to get ground truth).

## Training Setup
Text classification. Not sure exactly how to do this with our modeling setup? Should we create a prompt?

@article{wang_promptem_2022,
	title = {{PromptEM}: Prompt-Tuning for Low-Resource Generalized Entity Matching},
	volume = {16},
	issn = {2150-8097},
	url = {https://doi.org/10.14778/3565816.3565836},
	doi = {10.14778/3565816.3565836},
	abstract = {Entity Matching ({EM}), which aims to identify whether two entity records from two relational tables refer to the same real-world entity, is one of the fundamental problems in data management. Traditional {EM} assumes that two tables are homogeneous with the aligned schema, while it is common that entity records of different formats (e.g., relational, semi-structured, or textual types) involve in practical scenarios. It is not practical to unify their schemas due to the different formats. To support {EM} on format-different entity records, Generalized Entity Matching ({GEM}) has been proposed and gained much attention recently. To do {GEM}, existing methods typically perform in a supervised learning way, which relies on a large amount of high-quality labeled examples. However, the labeling process is extremely labor-intensive, and frustrates the use of {GEM}. Low-resource {GEM}, i.e., {GEM} that only requires a small number of labeled examples, becomes an urgent need. To this end, this paper, for the first time, focuses on the low-resource {GEM} and proposes a novel low-resource {GEM} method, termed as {PromptEM}. {PromptEM} has addressed three challenging issues (i.e., designing {GEM}-specific prompt-tuning, improving pseudo-labels quality, and running efficient self-training) in low-resource {GEM}. Extensive experimental results on eight real benchmarks demonstrate the superiority of {PromptEM} in terms of effectiveness and efficiency.},
	pages = {369--378},
	number = {2},
	journaltitle = {Proc. {VLDB} Endow.},
	author = {Wang, Pengfei and Zeng, Xiaocan and Chen, Lu and Ye, Fan and Mao, Yuren and Zhu, Junhao and Gao, Yunjun},
	date = {2022-10},
	note = {Publisher: {VLDB} Endowment},
	file = {Full Text:/Users/is28/Zotero/storage/M5SU2SEC/Wang et al. - 2022 - PromptEM Prompt-Tuning for Low-Resource Generaliz.pdf:application/pdf},
}

@inproceedings{yao_entity_2022,
	location = {New York, {NY}, {USA}},
	title = {Entity Resolution with Hierarchical Graph Attention Networks},
	isbn = {978-1-4503-9249-5},
	url = {https://doi.org/10.1145/3514221.3517872},
	doi = {10.1145/3514221.3517872},
	abstract = {Entity Resolution ({ER}) links entities that refer to the same real-world entity from different sources. Existing work usually takes pairs of entities as input and judges those pairs independently. However, there is often interdependence between different pairs of {ER} decisions, e.g., the entities from the same data source are usually semantically related to each other. Furthermore, current {ER} approaches are mainly based on attribute similarity comparison, but ignore interdependence between attributes. To address the limits of existing methods, we propose {HierGAT}, a new method for {ER} based on a Hierarchical Graph Attention Transformer Network, which can model and exploit the interdependence between different {ER} decisions. The benefit of our method comes from: 1) The graph attention network model for joint {ER} decisions; 2) The graph-attention capability to identify the discriminative words from attributes and find the most discriminative attributes. Furthermore, we propose to learn contextual embeddings to enrich word embeddings for better performance. The experimental results on publicly available benchmark datasets show that {HierGAT} outperforms {DeepMatcher} by up to 32.5\% of F1 score and up to 8.7\% of F1 score compared with Ditto.},
	pages = {429--442},
	booktitle = {Proceedings of the 2022 International Conference on Management of Data},
	publisher = {Association for Computing Machinery},
	author = {Yao, Dezhong and Gu, Yuhong and Cong, Gao and Jin, Hai and Lv, Xinqiao},
	date = {2022},
	note = {Series Title: {SIGMOD} '22},
	keywords = {collective entity linking, entity resolution, graph attention networks, hierarchical heterogeneous graph},
	file = {PDF:/Users/is28/Zotero/storage/7WK4HQA4/3514221.3517872.pdf:application/pdf},
}
