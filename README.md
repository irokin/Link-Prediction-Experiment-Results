### Link Prediction Problem: Experiment Results on Benchmark Datasets

In this thread I have collected recently published and well-aged approaches for knowledge graph completion (link prediction) problems. The included methods can be roughly divided into groups: Rule-based Methods, Embedding Methods, Graph Neural Network Methods and Hybird Methods (relational reinforcement learning, differentiable reasoning, etc.). Experiments results are collected from original and follow-up papers, and best effort has been attempted to assure results of the same method are carried out with similar configurations, but do expect results under different settings being put around each other.

#### Type Markers: 
- **E** as embedding methods
- **R** as rule-based methods
- **NN** as graph neural nets
- Hybird Methods:
  - **E+NN** 
  - **R+NN**
  - **R+E** 
  - **R+E+NN** 
  - **R+RL** : Rule + reinforcement learning

Approach Format: 
- (Approach Type)-(Method Name)-(Published Year)-(Reference Index) 

#### Datasets
- Large
  - FB15K
  - FB15K-237
  - NELL-995
  - WN18
  - WN18RR
  - YAGO3-10
  - YAGO37
- Small/Medium
  - Kinship
  - UMLS
  - Citeseer
  - Cora
  - Pubmed
  - UWCSE

#### Experiments Results

> Mean Rank (MR)
> 

|Approach|NELL-995|FB15K|FB15K-237|WN18|WN18RR|Kinship|UMLS
|--|--|--|--|--|--|--|--|
|**E**-TransE-2013-[9]|2100|-|323|-|2300|6.8|-|
|**E**-DistMult-2015-[6]|4213|-|512|-|7000|5.26|-|
|**E**-ANALOGY-2017-[8]|-|-|-|-|-|-|-|
|**E**-SimpleE-2018-[1]|-|-|-|-|-|-|-|
|**E**-ConvE-2018-[2]|3560|64|245|504|4464|2.03|-
|**E**-ComplEx-N3-2018-[3]|4600|-|546|-|7882|2.48|-|
|**E**-CrossE-2019-[7]|-|-|-|-|-|-|-|
|**E**-Rotate-2019-[23]|-|**40**|**177**|**254**|2923|-|-
|**R**-Node+LinkFeat-2015-[17]|-|-|-|-|-|-|-|
|**R**-AMIE-2015-[10]|-|-|-|-|-|-|-|
|**R**-Gaifman-2016-[24]|-|75|-|298|-|-|-
|**R**-RuleN-2018-[11]|-|-|-|-|-|-|-|
|**R**-RUGE-2018-[13]|-|-|-|-|-|-|-|
|**R**-AnyBURL-2019-[12]|-|-|-|-|-|-|-|
|**R+E**-RLvLR-2018-[15]|-|-|-|-|-|-|-|
|**NN**-R-GCN-2017-[5]|-|-|-|-|-|-|-|
|**E+NN**-R-GCN+\-2018-[4]|7600|-|600|-|6700|25.92|-|
|**E+NN**-ConvKB-2018-[16]|**600**|-|216|-|**1295**|3.3|-
|**E+NN**-AttentionE-2019-[18]|965|-|210|-|1940|**1.94**|-
|**R+NN**-Neural LP-2017-[14]|-|-|-|-|-|-|-|
|**R+NN**-NTP lambda-2017-[20]|-|-|-|-|-|-|-|
|**R+NN**-DRUM-2019-[22]|-|-|-|-|-|-|-|
|**R+RL**-MINERVA-2018-[19]|-|-|-|-|-|-|-|
|**R+RL**-Multi-Hop-2018-[21]|-|-|-|-|-|-|-|

> Filter Mean Reciprocal Rank (Filter MRR) 
> 

The filtered MRR is concerned about the problem that when evaluating embedding methods, positive instances are used to generate negative instances (or testing sets) by corrupting its head and tail, however, in raw MRR, there is no guarantee that the generated instances never overlap with existing positive insatnces, thus introduce unfairness to the evaluation. Filter MRR simply remove any generated instances that are known as positive facts. This problem won't appear in the rule-based methods (or question-answering systems), so the MRR evaluation on rule-based methods is filter MRR by default.

|Approach|NELL-995|FB15K|FB15K-237|WN18|WN18RR|Kinship|UMLS
|--|--|--|--|--|--|--|--|
|**E**-TransE-2013[9]|0.401|0.38|0.294|0.455|0.226|0.068|-
|**E**-DistMult-2015-[6]|0.485|0.639|0.281|0.813|0.444|0.516|0.878
|**E**-ANALOGY-2017-[8]|-|0.725|0.219|0.942|-|-|-
|**E**-SimpleE-2018-[1]|-|0.727|-|0.942|-|-|-|
|**E**-ConvE-2018-[2]|0.491|0.745|0.316|0.942|0.46|0.833|0.797
|**E**-ComplEx-N3-2018-[3]|0.482|**0.86**|0.37|**0.95**|**0.48**|0.823|0.838|
|**E**-CrossE-2019-[7]|-|0.728|0.299|0.83|-|-|-
|**E**-Rotate-2019-[23]|-|0.799|0.338|0.949|0.476|-|-
|**R**-Node+LinkFeat-2015-[17]|-|0.821|0.237|0.94|-|-|-
|**R**-AMIE-2015[10]|-|-|-|-|-|-|-|
|**R**-Gaifman-2016-[24]|-|-|-|-|-|-|-
|**R**-RuleN-2018-[11]|-|-|-|-|-|-|-|
|**R**-RUGE-2018-[13]|-|0.768|-|-|-|-|-
|**R**-AnyBURL-2019-[12]|-|0.83|0.31|**0.95**|**0.48**|-|-|
|**R+E**-RLvLR-2018-[15]|-|-|0.24|-|-|-|-
|**NN**-R-GCN-2017-[5]|-|0.651|0.248|0.814|-|-|-
|**E+NN**-R-GCN+\-2018-[4]|-|0.696|0.249|0.819|-|-|-|
|**E+NN**-ConvKB-2018-[16]|0.43|-|0.396|-|0.248|0.033|-
|**E+NN**-AttentionE-2019-[18]|0.530|-|**0.518**|-|0.44|**0.904**|-
|**R+NN**-Neural LP-2017-[14]|-|0.76|0.24|0.94|-|0.619|0.778
|**R+NN**-NTP lambda-2017-[20]|-|-|-|-|-|0.793|0.912
|**R+NN**-DRUM-2019-[22]|-|-|0.343|-|**0.486**|0.61|0.81
|**R+RL**-MINERVA-2018-[19]|0.725|-|0.293|-|0.448|0.720|0.825
|**R+RL**-Multi-Hop-2018-[21]|**0.727**|-|0.407|-|0.472|0.878|**0.94**

> Hits@1 
> 

|Approach|NELL-995|FB15K|FB15K-237|WN18|WN18RR|Kinship|UMLS
|--|--|--|--|--|--|--|--|
|**E**-TransE-2013[9]|0.344|0.231|0.198|0.089|0.0427|0.009|-
|**E**-DistMult-2015-[6]|0.401|0.522|0.199|0.701|0.412|0.367|**0.916**
|**E**-ANALOGY-2017-[8]|-|0.646|0.131|0.939|-|-|-
|**E**-SimpleE-2018-[1]|-|0.660|-|0.939|-|-|-
|**E**-ConvE-2018-[2]|0.403|0.67|0.239|0.935|0.39|0.738|0.894|
|**E**-ComplEx-N3-2018-[3]|0.399|0.599|0.132|0.936|0.409|0.733|0.823|
|**E**-CrossE-2019-[7]|-|0.634|0.211|0.741|-|-|-
|**E**-Rotate-2019-[23]|-|0.75|0.241|0.944|0.428|-|-|
|**R**-Node+LinkFeat-2015-[17]|-|-|-|-|-|-|-|
|**R**-AMIE-2015[10]|-|0.647|0.174|0.872|0.358|-|-
|**R**-Gaifman-2016-[24]|-|0.692|-|0.767|-|-|-|
|**R**-RuleN-2018-[11]|-|0.772|0.182|0.945|0.427|-|-
|**R**-RUGE-2018-[13]|-|0.703|-|-|-|-|-
|**R**-AnyBURL-2019-[12]|-|**0.808**|0.233|**0.946**|**0.446**|-|-
|**R+E**-RLvLR-2018-[15]|-|-|-|-|-|-|-|
|**NN**-R-GCN-2017-[5]|-|0.541|0.153|0.686|-|-|-
|**E+NN**-R-GCN+\-2018-[4]|-|0.601|0.151|0.697|-|-|-
|**E+NN**-ConvKB-2018-[16]|0.37|-|0.198|-|0.0562|0.4362|-|
|**E+NN**-AttentionE-2019-[18]|0.447|-|0.46|-|0.361|**0.859**|-
|**R+NN**-Neural LP-2017-[14]|-|-|0.166|-|0.376|0.475|0.643|
|**R+NN**-NTP lambda-2017-[20]|-|-|-|-|-|0.759|0.843|
|**R+NN**-DRUM-2019-[22]|-|-|0.255|-|0.425|0.46|0.67
|**R+RL**-MINERVA-2018-[19]|**0.663**|-|0.217|-|0.413|0.605|0.728
|**R+RL**-Multi-Hop-2018-[21]|0.656|-|**0.329**|-|0.437|0.811|0.902

> Hits@3
> 

|Approach|NELL-995|FB15K|FB15K-237|WN18|WN18RR|Kinship|UMLS
|--|--|--|--|--|--|--|--|
|**E**-TransE-2013[9]|0.472|0.472|0.376|0.823|0.441|0.643|-
|**E**-DistMult-2015-[6]|0.524|0.718|0.301|0.921|0.47|0.581|0.967
|**E**-ANALOGY-2017-[8]|-|0.785|0.240|0.944|-|-|-|
|**E**-SimpleE-2018-[1]|-|0.773|-|0.944|-|-|-
|**E**-ConvE-2018-[2]|0.531|0.801|0.35|0.947|0.43|0.917|0.964|
|**E**-ComplEx-N3-2018-[3]|0.528|0.759|0.244|0.945|0.469|0.899|0.962|
|**E**-CrossE-2019-[7]|-|0.802|0.331|0.931|-|-|-
|**E**-Rotate-2019-[23]|-|**0.83**|0.375|**0.952**|0.492|-|-|
|**R**-Node+LinkFeat-2015-[17]|-|-|-|-|-|-|-|
|**R**-AMIE-2015[10]|-|-|-|-|-|-|-|
|**R**-Gaifman-2016-[24]|-|-|-|-|-|-|-
|**R**-RuleN-2018-[11]|-|-|-|-|-|-|-|
|**R**-RUGE-2018-[13]|-|0.815|-|-|-|-|-
|**R**-AnyBURL-2019-[12]|-|-|-|-|-|-|-|
|**R+E**-RLvLR-2018-[15]|-|-|-|-|-|-|-|
|**NN**-R-GCN-2017-[5]|-|0.736|0.258|0.928|-|-|-
|**E+NN**-R-GCN+\-2018-[4]|0.126|0.760|0.264|0.929|0.137|0.088|-
|**E+NN**-ConvKB-2018-[16]|0.47|-|0.324|-|0.445|0.755|-|
|**E+NN**-AttentionE-2019-[18]|0.564|-|**0.54**|-|0.483|**0.941**|-
|**R+NN**-Neural LP-2017-[14]|-|-|0.248|-|0.468|0.707|0.869|
|**R+NN**-NTP lambda-2017-[20]|-|-|-|-|-|0.798|**0.983**
|**R+NN**-DRUM-2019-[22]|-|-|0.378|-|**0.513**|0.71|0.94
|**R+RL**-MINERVA-2018-[19]|**0.773**|-|0.329|-|0.456|0.812|0.9|
|**R+RL**-Multi-Hop-2018-[21]|-|-|-|-|-|-|-|

> Hits@10
> 

|Approach|NELL-995|FB15K|FB15K-237|WN18|WN18RR|Kinship|UMLS
|--|--|--|--|--|--|--|--|
|**E**-TransE-2013[9]|0.501|0.539|0.465|0.909|0.501|0.841|-
|**E**-DistMult-2015-[6]|0.61|0.814|0.408|0.943|0.49|0.867|0.992
|**E**-ANALOGY-2017-[8]|-|0.854|0.405|0.947|-|-|-
|**E**-SimpleE-2018-[1]|-|0.838|-|0.947|-|-|-
|**E**-ConvE-2018-[2]|0.613|0.873|0.491|0.955|0.48|0.9814|0.992|
|**E**-ComplEx-N3-2018-[3]|0.606|0.91|0.56|0.96|0.57|0.9711|0.995
|**E**-CrossE-2019-[7]|-|-|0.474|-|-|-|-
|**E**-Rotate-2019-[23]|-|0.884|0.533|0.959|0.571|-|-|
|**R**-Node+LinkFeat-2015-[17]|-|0.87|0.36|0.943|-|-|-
|**R**-AMIE-2015[10]|-|0.858|0.409|0.948|0.388|-|-
|**R**-Gaifman-2016-[24]|-|0.842|-|0.939|-|-|-|-
|**R**-RuleN-2018-[11]|-|0.87|0.42|0.958|0.536|-|-
|**R**-RUGE-2018-[13]|-|0.865|-|-|-|-|-|
|**R**-AnyBURL-2019-[12]|-|**0.89**|0.486|0.959|0.555|-|-
|**R+E**-RLvLR-2018-[15]|-|-|0.393|-|-|-|-
|**NN**-R-GCN-2017-[5]|-|0.825|0.414|0.955|-|-|-|
|**E+NN**-R-GCN+\-2018-[4]|0.188|0.842|0.417|**0.964**|0.08|0.239|-|
|**E+NN**-ConvKB-2018-[16]|0.545|-|0.517|-|0.525|0.953|-
|**E+NN**-AttentionE-2019-[18]|0.695|-|**0.626**|-|0.581|0.98|-|
|**R+NN**-Neural LP-2017-[14]|-|0.837|0.362|0.945|**0.657**|0.912|0.962
|**R+NN**-NTP lambda-2017-[20]|-|-|-|-|-|0.878|**1.0**
|**R+NN**-DRUM-2019-[22]|-|-|0.516|-|0.586|0.92|0.98
|**R+RL**-MINERVA-2018-[19]|0.831|-|0.456|-|0.513|0.924|0.968
|**R+RL**-Multi-Hop-2018-[21]|**0.844**|-|0.564|-|0.542|**0.982**|0.992

### References
[1] Kazemi, S. M., & Poole, D. (2018). SimplE Embedding for Link Prediction in Knowledge Graphs. NIPS, 1–12.

[2] Dettmers, T., Minervini, P., Stenetorp, P., & Riedel, S. (2018). Convolutional 2D Knowledge Graph Embeddings. AAAI, 1811–1818.

[3] Lacroix, T., Usunier, N., & Obozinski, G. (2018). Canonical Tensor Decomposition for Knowledge Base Completion. ICML.

[4] Schlichtkrull, M., Kipf, T. N., Bloem, P., Titov, I., & Welling, M. (2018). Modeling Relational Data with Graph Convolutional Networks. ESWC, 593–607.

[5] Kipf, T. N., & Welling, M. (2017). Semi-Supervised Classification with Graph Convolutional Networks. ICLR, 1–14. Retrieved from http://arxiv.org/abs/1609.02907

[6] Yang, B., Yih, W., He, X., Gao, J., & Deng, L. (2015). Embedding entities and relations for learning and inference in knowledge bases. ICLR, 1–13.

[7] Zhang, W., Paudel, B., Zhang, W., Bernstein, A., & Chen, H. (2019). Interaction Embeddings for Prediction and Explanation in Knowledge Graphs. WSDM.

[8] Liu, H., Wu, Y., & Yang, Y. (2017). Analogical Inference for Multi-relational Embeddings. ICML.

[9] Bordes, A., Usunier, N., Weston, J., & Yakhnenko, O. (2013). Translating Embeddings for Modeling Multi-Relational Data. NIPS, 2787–2795. https://doi.org/10.1007/s13398-014-0173-7.2

[10] Galárraga, L., Teflioudi, C., Hose, K., & Suchanek, F. M. (2015). Fast rule mining in ontological knowledge bases with AMIE+. VLDB Journal, 24(6), 707–730. https://doi.org/10.1007/s00778-015-0394-1

[11] Meilicke, C., Fink, M., Wang, Y., Ruffinelli, D., Gemulla, R., & Stuckenschmidt, H. (2018). Fine-grained evaluation of rule- and embedding-based systems for knowledge graph completion. ISWC, 3–20. https://doi.org/10.1007/978-3-030-00671-6_1

[12] Meilicke, C., Chekol, M. W., Ruffinelli, D., & Stuckenschmidt, H. (2019). Anytime Bottom-Up Rule Learning for Knowledge Graph Completion. IJCAI, 3137–3143.

[13] Guo, S., Wang, Q., Wang, L., Wang, B., & Guo, L. (2018). Knowledge Graph Embedding with Iterative Guidance from Soft Rules. AAAI, 4816–4823.

[14] Yang, F., & Cohen, W. W. (2017). Differentiable Learning of Logical Rules for Knowledge Base Reasoning. NIPS.

[15] Omran, P. G., Wang, K., & Wang, Z. (2018). Scalable rule learning via learning representation. IJCAI, 2149–2155.

[16] Nguyen, D. Q., Nguyen, T. D., Nguyen, D. Q., & Phung, D. (2018). A Novel Embedding Model for Knowledge Base Completion. NAACL.

[17] Toutanova, K., & Chen, D. (2015). Observed versus latent features for knowledge base and text inference. Proceedings of the 3rd Workshop on Continuous Vector Space Models and Their Compositionality, 57–66. https://doi.org/10.18653/v1/w15-4007

[18] Nathani, D., Chauhan, J., Sharma, C., & Kaul, M. (2019). Learning Attention-based Embeddings for Relation Prediction in Knowledge Graphs. ACL. Retrieved from http://arxiv.org/abs/1906.01195

[19] Das, R., Dhuliawala, S., Zaheer, M., Vilnis, L., Durugkar, I., Krishnamurthy, A., … Mccallum, A. (2018). Go for a walk and arrive at the answer: Reasoning over paths in knowledge bases using reinforcement learning. ICLR.

[20] Rocktäschel, T., & Riedel, S. (2017). End-to-End Differentiable Proving. NIPS. Retrieved from http://arxiv.org/abs/1705.11040

[21] Lin, X. V., Richard, S., & Caiming, X. (2018). Multi-Hop Knowledge Graph Reasoning with Reward Shaping. ACL, 3243–3253.

[22] Sadeghian, A., Armandpour, M., Ding, P., & Wang, D. Z. (2019). DRUM: End-To-End Differentiable Rule Mining On Knowledge Graphs. NIPS, 1–13. Retrieved from http://arxiv.org/abs/1911.00055

[23] Sun, Z., Deng, Z., Nie, J., & Tang, J. (2019). Rotate: Knowledge graph embedding by relational rotation in complex space. ICLR, 1–18.

[24] Niepert, M. (2016). Discriminative gaifman models. NIPS, 3413–3421.

### Planned Addition

[25] Zhu, Y., Liu, H., Wu, Z., Song, Y., & Zhang, T. (2019). Representation Learning with Ordered Relation Paths for Knowledge Graph Completion. EMNLP.
