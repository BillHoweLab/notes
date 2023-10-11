# Graph Merging

## Questions

Are we able to use LLMs to resolve synonyms graph conflicts? 

## Description

We have two representations of a graph with the same semnatic meaning (e.g., refer to the same area/object/relation), and they have some structral conflicts (e.g., missing/extra edges) or contecxtual conflicts (e.g., missing/extra attributes). The goal is to merge the two conflicted representations, and output the correct/ideal graph. One real world application example is that we have different annotations of the sidewalks (e.g., google map v.s. OSM), which might conflict with each other.

Recent works have shown promising results using LLMs on graph representations of data. This project aims to exploit the capabilities of LLMs in addressing the graph conflicts issue.

## Design

The proposed LLM methods are:

- Simply input two conflicted graphs into LLM and ask it to output a new one.
- Input two conflicted graph into LLM, together with the heuristic rules about how to merge the two graphs , and ask it to out a new graph. This scenario mimics the real world approach where human correctors follow the rules to merge the graphs. Rules are great because they set the standards, but following them is time consuming and hard to scale. But if we can use LLM to represent this procedure, maintain similar performances, and also reduce the amount of human labor, that would be amazing.
- On top of 2, where we use GPT3.5/4 directly without any future learning, we could fine-tune LLMs for our task.
- For 1 and 2, we dont need any node attributes yet. We could incorporate node attributes and use LLM to generate graph embeddings (similar to my current approach). But with LLM, we can embed textual attributes, which might be very helpful.

## Results
