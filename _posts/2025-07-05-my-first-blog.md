---
layout: post
title: first blog
date: 2025-07-05 11:59:00-0400
description: my first blog
tags: comments
categories: perspective
disqus_comments: true
related_posts: false
featured: true
mermaid:
  enabled: true
  zoomable: true
code_diff: true
map: true
chart:
  chartjs: true
  echarts: true
  vega_lite: true
tikzjax: true
typograms: true
---
## Why would we need a disease world model?
Every day it has become more and more clear that a LLM based AI system can get really good at diagnosis. 


## What could we do with a disease world model?
What if patients not only received their current medical scans, but also future medical scans, with virtual interventions? Doctors could directly observe the progression of patients' conditions, allowing them to suggest personalised early treatment planning years before serious conditions emerge. Patients could also gain a better understanding of their conditions, facilitating easier communication between patients and doctors. Furthermore, pharmaceutical companies could determine the endpoints of drug trials based on direct visual evidence. Such scenarios might seem far-fetched, but recent progress in world models could offer a solution towards their realization. World models are generative AI models that simulate open-ended, video-based digital worlds, providing unlimited environments for training AI agents and potentially unlocking the pathway to general artificial intelligence. The increasing use of medical imaging across various medical fields has accumulated a vast amount of temporal imaging data, analogous to videos, subsequently making it feasible to adapt world models for healthcare applications. In this perspective paper, we discuss the prospects of world models in healthcare. In particular, we coin the concept of Disease World Model and provide its formal definition. We as well discuss an unified architecture for building such a Disease World Model, based on medical imaging or with patients' meta data. 

## Setup
* We define **synthetic artifacts** $X$, as high-dimensional clinical representations (e.g., medical images, medical images + lab reports) of an individual $i \in \{1, ..., N\}$.
* Let $G$ be a **generative system** that produces a temporal sequence of artifacts $\{X_i^t\}_{t=0}^{t=D_i}$, where $X_i^t$ is the artifact for individual $i$ at time stamp $t$, $D_i$ is the death time point of the individual $i$.
* Let the **real artifacts** of an individual $i \in \{1, ..., N\}$ be $\{Y_i^t\}_{t=S}^{t=E}$, where the real clinical representations are available during the time period between the starting point $t=S$ and the end point $t=E$.
* Let $M$ be a **diagnostic agent** (e.g., human doctors, clinical LLM) that can map the clinical representations ($X$ and $Y$) to diagnosis. The accuracy of the diagnosis is measured by a metric $\mathcal{L}$.

---

## Definition 1: Disease World Model

A generative system $G$ is a **Disease World Model** if its generated artifact sequences $\{X_i^t\}_{t=0}^{t=D_i}$ satisfy the following two properties for all individuals $i$:

1.  **Clinical Reliability:** Each generated artifact $X_i^t$ is *clinically reliable* for all $t$.
2.  **Individual Characterizability:** Each generated artifact sequence $\{X_i^t\}_{t=0}^{t=D_i}$ is *individually characterizable*.

---

## Definition 1.1: Clinical Reliability

An artifact $X_i^t$ is **clinically reliable** if, for a given diagnostic agent $M$ and accuracy metric $\mathcal{L}$, the following conditions hold:

1.  **Diagnostic Verifiability:** The accuracy of a diagnosis derived from the synthetic artifact should be larger than a threshold $\alpha$:

    $L(M(X_i^t)) \ge \alpha, \quad t \in \{S, \dots, E\}$

    In the strictest scenario, we define $\alpha = L(M(Y_i^t)), \quad t \in \{S, \dots, E\}$. In less strict scenarios, experts should determine the threshold $\alpha$. This condition ensures the diagnostic utility of the synthetic artifacts is verifiable.

2.  **Temporal Consistency:** The diagnostic accuracy is a non-decreasing function of time. For any two time points $t_1$ and $t_2$ such that $t_1 < t_2$, we have:

    $L(M(X_i^{t_1})) \le L(M(X_i^{t_2})), \quad t_1 < t_2$

    This condition ensures the diagnostic utility of the synthetic artifacts is reliable.

---


## Definition 1.2: Individual Characterizability

A sequence of artifacts $\{X_i^t\}_{t=0}^{t=D_i}$ is **individually characterizable** if there exists an identification function $I: \mathcal{X} \to \{1, ..., N\}$ (where $\mathcal{X}$ is the space of all possible sequences) that can identify the individual $i$ from their generated sequence with a high probability $\beta$ close to 1.

$\mathbb{P}(I(\{X_i^t\}_{t=0}^{t=D_i}) = i) \ge \beta$

This ensures that the sequence contains a unique signature of the individual's disease progression, preventing the model from generating generic sequences or wrong sequences.

---

## Relevant Works
We briefly review the concept of digital twins and the specific type of digital twins for healthcare. The digital twin concept was born in the field of aerospace engineering, where the researchers started to use ``replica'' to reproduce a physical complex system to replace the real expensive experiments to cut the costs in XX age in the US. This was commonly regarded as the begining of the concept of ``digital twins''. Through time, the concept of ``digital twins'' have gone through continuous evolution and expansion. It has also migrated from the aerospace engineering filed to any other fields that are involved with modelling complex physical systems. Recently, Katsoulakis et al \cite{digital_twin_healthcare_review_npj_Digital_Medicine} provided a definition of a digital twin for healthcare as, ``a virtual representation of a person which allows dynamic simulation of potential treatment strategy, monitoring and prediction of health trajectory, and early intervention and prevention, based on multi-scale modelling of multi-modal data such as clinical, genetic, molecular, environmental, and social factors etc.'' The same authors also identified three essences of a digital twin, including a physical entity, a virtual replica, and a connection between the two. 

Disease World Model is a special case of the digital twin for healthcare. The purpose of this paper is not to replace the concept of the digital twins. Rather, this paper is written to fulfil the details of the broad concept of the healthcare digital twin, so the future researchers can focus on developing the designed computational tools, utilising existing technologies, towards personalised medicine. 

What is lacking in the existing concept of Disease Progression Modelling and how can medical world models help?
Not end to end. It is one-size-for-all, lacking of individulisaing. 