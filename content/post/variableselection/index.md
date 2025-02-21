---
title: 'SelDel: Graph-based way for variable selection' 
date: '2024-11-04'

# Is this an unpublished draft?
draft: false

tags:
  - graph theory
  - vairable selection

categories:
  - research
---

## Context
During my work/study program at Crédit Agricole Centre France[^1], I developed **appetency scores**. This method is part Customer Relationship Managment (CRM) strategy by finally associating to each client an "appency mark" (typically between 0 and 100) to an offer or a product. During the score creation process I needed to select variables, partly in order to reduce computation complexity. However, bank databases are widely too large and complex so I could not reasonably select these variables by hand. A scientific barrier indeed identified.

## Selection Deletion
The main goal is to select variables that contains pure informations. So if two variables are *too* correlated, we should choose only one of them.

Indeed, we begin by computing Spearman correlation [^2] matrix. Then we create a *highly correlated* variable graph. Each node represents a variable and each edge represents a *high correlation* that explains the non-oriented property of this graph. Also the term *highly correlated* should be understood as a threshhold chosen by the DataMiner. The algorithm is named *SeDe* for **Selection-Deletion** because it is iterative. First, we **select** the least degree node and find among its adjacent node, the one that has the greatest degree. Then we **delete** this particular node. Edges that were connected to the deleted node will be deleted too. Then, the algorithm iterate these two steps.

Intuitively, high correlation deletion between variables will be propagated through the graph.


{{% callout note %}}
To be continued with an example and algorithm formalization
{{% /callout %}}




[^1]: Because of a confidential clause, I cannot go into methods' details.
[^2] : Spearman C. (1904). "The proof and measurement of association between two things". American Journal of Psychology. 15 (1): 72–101. doi:10.2307/1412159. JSTOR 1412159.