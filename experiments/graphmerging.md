# Graph Conflation

## Description

Motivated by the TDEI project, we seek a method that can take two small graphs that describe the same real-world environment (e.g., an intersection where edges are sidewalks and/or roadways)
and to produce a merged graph that corrects errors.  The applciation is that we may have conflicting information from multiple sources, and developing a list of heuristics to manage the merging is error-prone and time consuming.
We instead aim to provide training examples and learn a function.

Nodes and edges may have attributes, and these should be merged as well.  In particular, the geometry should be reconciled.

We are considering contrastive graph learning models for attributed graphs.

# Design

For LLMs, we consider whether they can reason about graph isomorphisms and find that the LLMs make mistakes even in trivial examples.

## Prompt
Are the following two graphs isomorphic? 

graph 1: 
strict graph  {
1;
2;
3;
4;
1 -- 2;
1 -- 3;
2 -- 4;
}

graph 2: 
strict graph  {
1;
2;
3;
4;
3 -- 1;
3 -- 2;
1 -- 4;
}

## Response

Let's analyze the given graphs:

Graph 1:

Node 1 is connected to Nodes 2 and 3.
Node 2 is connected to Nodes 1 and 4.
Node 3 is connected to Node 1.
Node 4 is connected to Node 2.
Graph 2:

Node 1 is connected to Nodes 3 and 4.
Node 2 is connected to Node 3.
Node 3 is connected to Nodes 1 and 2.
Node 4 is connected to Node 1.
Upon inspection, the two graphs are indeed isomorphic. To see this, one can map the nodes as follows:

Node 1 in Graph 1 → Node 3 in Graph 2
Node 2 in Graph 1 → Node 4 in Graph 2
Node 3 in Graph 1 → Node 1 in Graph 2
Node 4 in Graph 1 → Node 2 in Graph 2

This mapping preserves the adjacency relationship between nodes, and thus, the two graphs are isomorphic.

## Prompt

I don't think your isomorphism is correct.  
Graph 2 has an edge from 1 to 4.  But in your mapping, that would mean there would need to be an edge from 3 to 2, which there is not

## Response
