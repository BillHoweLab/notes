# Medical Debt Information Extraction

## Description

Hospitals routinely pass unpaid bills to collection agencies, sidestepping laws that require offering financial services to low-income patients.  
The extent of the problem is not known, because the only source of infomoration that spans multiple hospitals and multiple collection agencies is the courts themselves.

Court cases are public record, but are largely inaccessible due to procedural, technical, and policy restrictions.  

Once obtained, they have inconsistent structure, layout, format, content, and language, complicating information extraction.

Deep learning and generative AI provide some support for the extraction problem.  

Layout-based models (LBMs) associate each OCR token with (x,y) coordinates to expose positioning information to the model, improving performance for semi-structured forms and documents.

- **Many-shot Token Classifier (LBMC)**: One method using LBMs is to label each OCR token with the desired information (defendant name, address, judgment amount, etc.) and train a token 
classifier to recognize all relevant tokens, then post-process them into a coherent result (e.g., assemble several tokens tagged as "address" into a coherent address.) This approach can require significant labeling work for fine-tuning, however.  

- **Few-shot Layout Q&A (LBMQ)**: Another method using LBMs is to simpley provide a few examples of the correct "span" that includes the answer and use Q&A interfaces. 
For example, we can ask "Given input XXX, the address is YYY.  What is the address for XXX2?"  
This approach requires less labeled data and less post-processing but may offer worse performance.  Any LBM-based method is dependent on OCR, which are not very reliable, especially with handwritten notes that can appear on cases.

- **LLM Q&A (LLMQ)**: LLMs / generative models can potentially answer these questions with no pre- or post-processing and zero shots: 
Provide the entire pdf file and pose the question "What is the defendant's address?"  Few-shot variants of this approach are also feasible.


## Questions

1. If LLMs work for this problem, can smaller models work just as well?  We need long context windows.
2. Do LBMs work for these problems
3. Even though the data is public, it is sensitive.  Can we redact identifying information to make use of this dataset for research?


## Design

We have ~7 tasks: identiy whther the case is medical debt, then extract: 
- defendant name
- defendant address
- amount of suit
- principal amount
- judgment amount
- name of provider

We have 1200 cases from Thurston county.

Of these, we have hand-labeled the token span covering the 7 tasks for 138 medical debt cases, and we have another 100 cases that are known to be not medical debt as negative examples.

For each case there may be multiple pdfs and each pdf may include multiple pages.  
For LBMC, we can classify tokens regardless of which pdf or page they are on. 
For LBMQ, we provide a fixed page where the desired information is typically found.   
For LLMQ, we provide the pdf in which the answer is expected to be found, but need not specify the page.

## Results

Initial results show high accuracy for some tasks, confounded by situations where the answer cannot be found on the provided input.

We are emphasizing the LLM approach, in which case we will try a smaller model.



