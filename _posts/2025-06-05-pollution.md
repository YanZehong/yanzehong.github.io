---
layout: post
title: "Mitigating GenAI-powered Evidence Pollution for Out-of-Context Multimodal Misinformation Detection"
published: true
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

<div class="img-div-any-width" markdown="0">
  <image src="/images/dart/intro.jpeg" width="310" height="350" />
</div>


<blockquote class='subtle'>
  arXiv, 2025 / <a href="https://arxiv.org/pdf/2501.14728">PDF</a> / <a href="https://yanzehong.github.io/pollutino/">Project Page</a> / <a href="https://github.com/YanZehong/GenAI-Evidence-Pollution">Code</a> / <a href="https://github.com/YanZehong/GenAI-Evidence-Pollution/tree/main/data">Data</a>
</blockquote>


<p align="justify">
We investigate how  polluted evidence affects the performance of existing OOC detectors, revealing a performance degradation of more than 9 percentage points. We further propose two strategies, cross-modal evidence reranking and cross-modal claim-evidence reasoning, to address the challenges posed by polluted evidence.
</p>
<!--more-->





## Abstract
<p align="justify">
  While large generative artificial intelligence (GenAI) models have achieved significant success, they also raise growing concerns about online information security due to their potential misuse for generating deceptive content. Out-of-context (OOC) multimodal misinformation detection, which often retrieves Web evidence to identify the repurposing of images in false contexts, faces the issue of reasoning over GenAI-polluted evidence to derive accurate predictions. Existing works simulate GenAI-powered pollution at the claim level with stylistic rewriting to conceal linguistic cues, and ignore  evidence-level pollution for such information-seeking applications. In this work, we investigate how  polluted evidence affects the performance of existing OOC detectors, revealing a performance degradation of more than 9 percentage points. We propose two strategies, cross-modal evidence reranking and cross-modal claim-evidence reasoning, to address the challenges posed by polluted evidence. Extensive experiments  on two benchmark datasets show that these strategies can effectively enhance the robustness of existing out-of-context detectors amidst polluted evidence.
</p>

## Introduction
<p align="justify">
<ul>
<li> Existing studies has predominantly examined the GenAI-posed threats at the \textit{claim level}. Recent works on evidence-level threats have focused on  textual pollution within fixed, highly structured evidence corpora like Wikipedia pages. However, this narrow focus results in a considerable gap for multimodal misinformation detectors in the real-world  where evidence retrieved from the web are typically unstructured, noisy and polluted. </li>  
<li> We construct a large diverse collection of  multimodal evidence to simulate the challenges posed by GenAI-based pollution for OOC misinformation detectors. </li>  
<li> We propose cross-modal evidence reranking and cross-modal claim-evidence reasoning to significantly enhance the robustness of OOC detectors against evidence pollution. </li>  
</ul>
</p>


## Framework

<div class="img-div-any-width" markdown="0">
  <image src="/images/dart/framework.jpeg" width="500" height="570"/>
</div>

<p align="justify">

The proposed DART framework consists of four key modules: 

<ul>
<li> <b>Sentence Encoding Block</b> transforms the document into individual sentences and generate representations for sentence-aspect combination.</li>  

<li> <b>Global Context Interaction Block</b> models interactions among sentences and generate context-aware representations that capture aspect-specific information across long-range dependencies.</li>  

<li> <b>Aspect Aggregation Block</b> performs local and global attentive pooling to obtain the document representation.</li>  

<li> <b>Sentiment Classification Block</b> With the document representation obtained, this block leverages a two-layered Multilayer Perceptron (MLP) to predict the sentiment for  the aspect.</li>  

</ul>
</p>


## Dataset 

<div class="img-div-any-width" markdown="0">
  <image src="/images/dart/dataset.jpeg"/>
</div>

## Comparative Study

### Performance in TripAdvisor and BeerAdvocate
<p align="center">
<div class="img-div-any-width" markdown="0">
  <image src="/images/dart/result-2.png" width="350" height="200"/>
</div>
<div class="img-div-any-width" markdown="0">
  <image src="/images/dart/result-3.png" width="400" height="300"/>
</div>
</p>


### Performance in SocialNews
<div class="img-div-any-width" markdown="0">
  <image src="/images/dart/result-1.png"/>
</div>

<div class="img-div-any-width" markdown="0">
  <image src="/images/dart/result.jpeg"/>
</div>


<blockquote class='subtle'>
  <b>Note</b>
  <ul>
    <li>DART surpasses others in overall accuracy and excels in five key aspects, particularly in the digital-online and health aspects.</li>  
    <li>DART shows superior performance as document length increases.</li>
  </ul>
</blockquote>



## Application to Trust and Polarity Prediction

<div class="img-div-any-width" markdown="0">
  <image src="/images/dart/result-5.png" width="500" height="550"/>
</div>

<blockquote class='subtle'>
  <b>Note</b>
  <ul>
    <li>DART gives the best performance in three key aspects and is competitive with GPT4-zeroshot for the Dependability aspect, due to the fewer number of documents with this aspect.</li>  
  </ul>
</blockquote>



## Ablation

<div class="img-div-any-width" markdown="0">
  <image src="/images/dart/result-4.png" width="500" height="200"/>
</div>


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
