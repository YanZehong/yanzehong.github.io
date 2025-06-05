---
layout: post
title: "Mitigating GenAI-powered Evidence Pollution for Out-of-Context Multimodal Misinformation Detection"
published: false
---

<p align="center">
  <strong>Zehong Yan<sup style="font-size: 70%;vertical-align: super;">1</sup>, Peng Qi<sup style="font-size: 70%;vertical-align: super;">1</sup>, Wynne Hsu<sup style="font-size: 70%;vertical-align: super;">1</sup>, Mong Li Lee<sup style="font-size: 70%;vertical-align: super;">1</sup></strong>
  <br>
  <sup style="font-size: 70%;vertical-align: super;">1</sup>NUS Centre for Trusted Internet & Community, National University of Singapore
</p>

<p align="center">
  <a href="https://arxiv.org/abs/2501.14728"> 
    <img src="https://img.shields.io/badge/paper-B31B1B?logo=arXiv&labelColor=grey" />
  </a> 
  <a href="https://github.com/YanZehong/GenAI-Evidence-Pollution"> 
    <img src="https://img.shields.io/badge/Code-181717?logo=github&labelColor=grey" />
  </a> 
</p>

<p align="center">
<div class="img-div-any-width" markdown="0">
  <image src="/images/pollution/Fig-4-framework.jpeg"/>
</div>
</p>


<blockquote class='subtle'>
  arXiv, 2025 / <a href="https://arxiv.org/pdf/2501.14728">PDF</a> / <a href="https://yanzehong.github.io/pollutino/">Project Page</a> / <a href="https://github.com/YanZehong/GenAI-Evidence-Pollution">Code</a> / <a href="https://github.com/YanZehong/GenAI-Evidence-Pollution/tree/main/data">Data</a>
</blockquote>


<p align="justify">
We investigate how  polluted evidence affects the performance of existing OOC detectors, revealing a performance degradation of more than 9 percentage points. We further propose two strategies, <em>cross-modal evidence reranking</em> and <em>cross-modal claim-evidence reasoning</em>, to address the challenges posed by polluted evidence.
</p>
<!--more-->





## Abstract
<p align="justify">
  While large generative artificial intelligence (GenAI) models have achieved significant success, they also raise growing concerns about online information security due to their potential misuse for generating deceptive content. Out-of-context (OOC) multimodal misinformation detection, which often retrieves Web evidence to identify the repurposing of images in false contexts, faces the issue of reasoning over GenAI-polluted evidence to derive accurate predictions. Existing works simulate GenAI-powered pollution at the claim level with stylistic rewriting to conceal linguistic cues, and ignore  evidence-level pollution for such information-seeking applications. In this work, we investigate how  polluted evidence affects the performance of existing OOC detectors, revealing a performance degradation of more than 9 percentage points. We propose two strategies, cross-modal evidence reranking and cross-modal claim-evidence reasoning, to address the challenges posed by polluted evidence. Extensive experiments  on two benchmark datasets show that these strategies can effectively enhance the robustness of existing out-of-context detectors amidst polluted evidence.
</p>

## Introduction
<p align="center">
<div class="img-div-any-width" markdown="0">
  <image src="/images/pollution/Fig-1-intro_example_taylor_two_col_1_true.jpeg" width="500" height="200"/>
</div>
<div class="img-div-any-width" markdown="0">
  <image src="/images/pollution/Fig-1-intro_example_taylor_two_col_2_true.jpeg" width="500" height="200"/>
</div>
</p>
    
<p align="justify">
<ul>
<li> Existing studies has predominantly examined the GenAI-posed threats at the <em>claim level</em>. Recent works on <em>evidence-level</em> threats have focused on  textual pollution within fixed, highly structured evidence corpora like Wikipedia pages. However, this narrow focus results in a considerable gap for multimodal misinformation detectors in the real-world  where evidence retrieved from the web are typically unstructured, noisy and polluted. </li>  
<li> We construct a large diverse collection of  multimodal evidence to simulate the challenges posed by GenAI-based pollution for OOC misinformation detectors. </li>  
<li> We propose cross-modal evidence reranking and cross-modal claim-evidence reasoning to significantly enhance the robustness of OOC detectors against evidence pollution. </li>  
</ul>
</p>

## Evidence Pollution with GenAI
<p align="center">
<div class="img-div-any-width" markdown="0">
  <image src="/images/pollution/Fig-2-pipeline.png"/>
</div>
</p>

### Example
<div class="img-div-any-width" markdown="0">
  <image src="/images/pollution/Fig-3-generation_example_two_col.png"/>
</div>

## Proposed Strategies
<p align="center">
<div class="img-div-any-width" markdown="0">
  <image src="/images/pollution/strategies.png" width="400" height="600"/>
</div>
</p>

<p align="justify">

OOC detectors  assess the information authenticity and the consistency between text and associated images.  However, the sophistication of LLMs introduces a new layer of complexity  as it generates convincing polluted evidence that is not easily detected as LLM-generated content. We demonstrate this by evaluating the Vicuna-13B model, an open-source detector, on a dataset comprising of 10,000 pieces of textual evidence, evenly split between human-written and LLM-generated texts. The model  achieves only a 41.3% accuracy in identifying LLM-generated content.
This motivates us to develop two strategies, cross-modal evidence reranking and cross-modal claim-evidence reasoning, to enhance the robustness of  OOC detectors.
</p>


## Dataset 
<p align="center">
<div class="img-div-any-width" markdown="0">
  <image src="/images/pollution/table_data.png"/>
</div>
</p>

## Performance Study

### Effect of Evidence Pollution on OOC Detectors
<p align="center">
<div class="img-div-any-width" markdown="0">
  <image src="/images/pollution/table_pollution.png"/>
</div>
</p>

We observe that: 
1) The combination of polluted text and image  poses a significant threat to
OOC detectors. 
Specifically, the accuracy of all 
detectors drop by more than 9 percentage points, revealing the vulnerabilities of existing OOC detectors against generated multimodal pollution. 
2) Textual pollution has a greater impact than  visual pollution, indicating that existing OOC detectors are more dependent on textual information.
This modality bias may stem from the fact that textual evidence often provides more semantics such as relationships between entities compared to images. 
3) Detection of false claims 
in the presence of 
with polluted evidence proves to be more challenging than true claims.
Specifically, CCN experiences a significant drop of 35.67 points in the F1 score for false claims on 
the VERITE dataset, highlighting the difficulties in reasoning with contradictory evidence.


### Effect of Proposed Strategies
<p align="center">
<div class="img-div-any-width" markdown="0">
  <image src="/images/pollution/table_strategy.png"/>
</div>
</p>

We see that:
1) The combination of both strategies yields the best results, increasing the overall accuracy to 88.82% (+12.40) and 75.44% (+11.15) for SNIFFER on the NewsCLIPpings and VERITE dataset respectively.
This indicates that the two strategies complement each other, enhancing the model's robustness against multimodal pollution. Further, the strategies can  be generalized to the real-world VERITE dataset to mitigate GenAI-based evidence pollution.
2) Incorporating cross-modal evidence re-ranking significantly boosts performance. The overall accuracy of SNIFFER increases to 87.68%, marking an improvement of 11.26%, on the NewsCLIPpings dataset. This strategy also enhances the detection of true and false claims 
 to 87.74% (+10.27) and 87.62% (+12.31), respectively. The results suggest that re-ranking evidence and focusing on the top relevant evidence  greatly aids in reconciling discrepancies introduced by multimodal pollution. 
3) Similar to  cross-modal reranking, cross-modal claim-evidence reasoning module also shows substantial gains, particularly in the detection of true claims. 


### Performance comparison of different strategie
<div class="img-div-any-width" markdown="0">
  <image src="/images/pollution/table_comparison.png"/>
</div>

The extra detector approach involves adding an auxiliary classifier to filter out the generated evidence, the vigilant prompting approach introduces hints at the presence of false evidence in the prompt, and the reader ensemble approach combines multiple judgments based on different evidence by voting. 
SNIFFER, equipped with our proposed solution, achieves the highest performance across two datasets, with significant improvements of 12.40% on NewsCLIPpings and 13.41% on VERITE,
demonstrating its superiority in the presence of polluted evidence.
Notably, our approaches can be easily integrated into existing OOC detection frameworks, such as CCN and RED-DOT, whereas the prompting-based and voting-based approaches are restricted to LLM-based detectors.




## Case Study

<p align="center">
<div class="img-div-any-width" markdown="0">
  <image src="/images/pollution/case.png"/>
</div>
</p>


## BibTeX
If you found this work helpful for your research, please cite it as following:

```
@article{yan2025mitigating,
  title={Mitigating GenAI-powered Evidence Pollution for Out-of-Context Multimodal Misinformation Detection},
  author={Yan, Zehong and Qi, Peng and Hsu, Wynne and Lee, Mong Li},
  journal={arXiv preprint arXiv:2501.14728},
  year={2025}
}
```


<footer class="footer">
  <p>
    This website is adapted from <a href="https://github.com/nerfies/nerfies.github.io">Nerfies</a> and <a hred="https://pengqi.site/Sniffer/">Sniffer</a>. Thanks for the great work.
  </p>
</footer>
