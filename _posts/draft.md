---
layout: post
title: Disease worlds models are essential for personalised medicine [Work in progress]
date: 2025-07-05 11:59:00-0400
description: first blog
tags: comments
categories: perspective
disqus_comments: false
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
mathjax: true
---

## Why are world models exciting in general?
Evolution is a verified method that can create intelligence. To follow the evolution path to create a digital intelligent being, we need three essences: scalable learning algorithms, computing hardware, a dynamic and interactive environment that constantly generates new training data. And eveything else is just bitter lessons. However, the last essence is the most challenging yet the most ignored research topic of the community. Luckily, recent progresses in world models and AI agents have started to attract more and more interests to this difficult problem. 

## How can world models benefit medicine?
World models might not only be the data engine to power the future general AI systems, but also a great tool to realise personalised medicine. For example, the disease world models should be able to: 1) perform virtual screening to save patients from a preventative perspective; 2) generate virtual personal disease progression trajectories for optimal treatment planning; 3) simulate virtual interventions for helping develop new drugs and planning surgical procedures. 

## Are the current LLM already world models for personalised medicine?
Every day it has become more evident that current LLMs will one day be as good as human doctors at making diagnoses, if enough clinical representations are embedded and given to the LLMs. However, personalised medicine is far beyond making a diagnosis. Unfortunately, I do not think that the current LLM systems or their future versions are designed for accurate personalised medicine. This is because they can only access sparse and partial clinical representations, rather than looking holistically at the whole picture at both the individual and population levels. For example, there is no real evidence that LLM can do reasoning for disease progression modelling.

## How do we know if we have built a world model for personalised medicine? Looking for correct especailly unexpected emerging properties from the generated artifacts.
A world model should have caputured an unravel level of details of the physical worlds that the generated artifacts must contain emerging physical properties that are also correct in physical world and critically significant for clinical purposes. Therefore, towards developing a world model of a disease, the "testing metrics" should be the artifacts themselves. We need to monitor and look for the emering properties of the generated medical artifacts. Once the generated medical artifacts satisfy conditions to understand and cure a disease, the system that generates those medical artifacts is a disease world model. 

## What medical artifacts should we generate?
In history, the emergence of visual intelligence directly led to the Cambrian Explosion in 541 millions years ago. In advancing medicine, medical imaging has also been playing a pivotal role in diagnosis, drug developments and surgery guidance. We should learn from evolution and keep imaging as a centre in the development of world models for diseases. 

## Contents of this blog:
From the perspective focusing on the emerging properties of the generated medical artifacts, this blog will first lay out the definitions of a Disease World Model, which provides a few future research directions and opportunities. Some early use cases with promising results on lung fibrosis will later be discussed.

**Invites for collaborators** This is a work in progress, so please feel free to contact me if you find a typo, a mistake, or would like to discuss or collaborate. [xumoucheng28@gmail.com](mailto:xumoucheng28@gmail.com).

<img src="/assets/img/blog_disease_world_models/dwm_vs_llms.png" alt="Disease World Models vs LLMs" width="100%" style="max-width: 800px; height: auto;">

_Figure 1: Comparison between Disease World Models and Large Language Models in AI driven healthcare. LLMs can do diagnosis but Disease World Models can do more, even personalised medicine._

<!-- ## What could we do with a disease world model?
What if patients not only received their current medical scans, but also future medical scans, with virtual interventions? Doctors could directly observe the progression of patients' conditions, allowing them to suggest personalised early treatment planning years before serious conditions emerge. Patients could also gain a better understanding of their conditions, facilitating easier communication between patients and doctors. Furthermore, pharmaceutical companies could determine the endpoints of drug trials based on direct visual evidence. Such scenarios might seem far-fetched, but recent progress in world models could offer a solution towards their realization. World models are generative AI models that simulate open-ended, video-based digital worlds, providing unlimited environments for training AI agents and potentially unlocking the pathway to general artificial intelligence. The increasing use of medical imaging across various medical fields has accumulated a vast amount of temporal imaging data, analogous to videos, subsequently making it feasible to adapt world models for healthcare applications. In this perspective paper, we discuss the prospects of world models in healthcare. In particular, we coin the concept of Disease World Model and provide its formal definition. We as well discuss an unified architecture for building such a Disease World Model, based on medical imaging or with patients' meta data.  -->

## Setup for Disease World Model

Before we dive into the formal definitions, we need to define a few terms:

- $X$: synthetic artifacts, as high-dimensional clinical representations (e.g., medical images, medical images + lab reports) of an individual $i \in \{1, ..., N\}$.
- $G$: a generative system that produces a temporal sequence of artifacts $\{X_i^t\}_{t=0}^{t=E_i}$, where $X_i^t$ is the artifact for individual $i$ at time stamp $t$, $E_i$ is the end point (death time point) of the individual $i$.
- $Y$: real artifacts of an individual $i \in \{1, ..., N\}$ be $\{Y_i^t\}_{t=S}^{t=E}$, where the real clinical representations are available during the time period between the starting point $t=S$ and the end point $t=E$.
- $M$: a diagnostic agent (e.g., human doctors, clinical LLM) that can map the clinical representations ($X$ and $Y$) to diagnosis. The accuracy of the diagnosis is measured by a metric $\mathcal{L}$.
- $I$: an identification function to recognise the identities of all sequences of the medical artifacts.
- $f_d$: a mapping function that can transform the generated artifact $X$ into another interpretable data format $d$.
- $\mathcal{I}$: a virtual intervention.

---

## Definition 1: Disease World Model

A generative system $G$ is a **Disease World Model** if its generated artifact sequences $\{X_i^t\}_{t=0}^{t=E_i}$ satisfy the following properties for all individuals $i$.

1. **Clinical Comprehensiveness:** Each generated artifact $X_i^t$ should contain the complete comprehensive clinical representation of the patient that it can be converted into any data format that is interpretable to human doctors.
2. **Clinical Reliability:** Each generated artifact $X_i^t$ is _clinically reliable_ for all $t$.
3. **Interventional Validity:** Each generated artifact sequence under a virtual intervention is realistic and reliable.
4. **Individual Characterisability:** Each generated artifact sequence $\{X_i^t\}_{t=0}^{t=E_i}$ is _individually characterisable_.

---

## Definition 1.1: Clinical Comprehensiveness

An artifact $X_i^t$ is considered _clinically comprehensive_ if it satisfies two conditions:

1. **Comprehensive Representation:** The artifact must encode the complete clinical state of the patient at a given time, rather than a single data modality. Such a comprehensive clinical representation can be seen as the _Clinical_ _Platonic_ _Representation_ of the patient.
2. **Functional Convertibility:** If the artifact is _clinically comprehensive_, it must contain the _Clinical_ _Platonic_ _Representation_ of the patient. Therefore, there must exist a set of mapping functions $\{f_d\}$ capable of converting the artifact $X_i^t$ into any clinically relevant target format $d$ (e.g., medical image, text report, lab reports) that is interpretable by human doctors. Each function performs the transformation $X^t_{i^d} = f_d(X_i^t)$. This ensures that a lot of the existing clinical workflows in the physical world can still be applied on the generated artifacts. It also ensures that the generated artifacts can be directly evaluated for their correctness.

---

## Definition 1.2: Clinical Reliability

An artifact $X_i^t$ is **clinically reliable** if, for a given diagnostic agent $M$ and accuracy metric $\mathcal{L}$, the following conditions hold:

1.  **Diagnostic Verifiability:** The accuracy of a diagnosis derived from the synthetic artifact should be larger than a threshold $\alpha$:

    $L(M(X_i^t)) \ge \alpha, \quad t \in \{S, \dots, E\}$

    In the strictest scenario, the diagnostic accuracy from the synthetic artifact should be at least as good as the real artifacts, more formally, we can define $\alpha \ge L(M(Y_i^t)), \quad t \in \{S, \dots, E\}$. In less strict scenarios, a threshold $\alpha$ needs to be determined to be clinically accetable. This condition ensures the diagnostic utility of the synthetic artifacts is useable and verifiable.

2.  **Temporal Consistency:** The diagnostic accuracy is a non-decreasing function of time. For any two time points $t_1$ and $t_2$ such that $t_1 < t_2$, we have:

    $L(M(X_i^{t_1})) \le L(M(X_i^{t_2})), \quad t_1 < t_2$

    Commonly, existing ML models struggle with predicting a time point that is too far away from now on. This condition ensures the diagnostic utility of the synthetic artifacts is reliable, even for future unseen timepoints.

---

## Definition 1.3: Interventional Validity

Let $\mathcal{I}$ be a virtual interaction (e.g., administering a drug, performing surgery, changing of the time) applied at time $t_{\mathcal{I}}$. The generative system $G$ has _interventional validity_ if it can generate a reliable counterfactual sequence that satisfies the following conditions:

1. **Counterfactual Plausibility**: The generated post-intervention trajectory $\{ X_i^t \mid \mathcal{I} \}$ is clinically plausible and consistent with established medical knowledge regarding the effects of intervention $\mathcal{I}$. This ensures that the interactions injected from the physical world have meaningful consequences to the artifacts. One of the simplest interactions can be the change of time, to see the artifacts at different arbitrary time points.
2. **Post-Intervention Reliability**: Each artifact $X_i^t \mid \mathcal{I}$ generated after the intervention (i.e., for $t \geq t_{\mathcal{I}}$) remains _clinically reliable_ as defined in Definition 1.2. This ensures that the effectiveness of the virtual clinical interactions can be trusted and directly assessed for drug developments and personal treatment planning.

---

## Definition 1.4: Individual Characterisability

A sequence of artifacts $\{X_i^t\}_{t=0}^{t=E_i}$ is _individually_ _characterisable_ to ensure that the sequence contains a unique signature of the individual's disease progression, if it satisfies the following conditions:

1. **Identifiability:** There exists an identification function $I$ that can identify the individual $i$ from their generated sequence with a high probability $\beta$ close to 1.

   $\mathbb{P}(I(\{X_i^t\}_{t=0}^{t=E_i}) = i) \ge \beta$

   An example of such an ientification function $I$ is an unsupervised contrastive clustering algorithm at a very granular level.

2. **Endpoint Fidelity:** The generated trajectory for an individual must terminate at a clinically plausible endpoint. When the ground-truth time of death, $E_i^*$, is available for comparison, the sequence's simulated time of death, $E_i$, must align with it within a predefined, clinically acceptable margin $\delta_E$.

   $E_i - E_i^* \le \delta_E$

   This ensures the model accurately captures the overall duration and prognostic outcome of the individual's specific disease progression pattern.

---

## How to train such a Disease World Model

To be updated

<img src="/assets/img/blog_disease_world_models/dwm_training.png" alt="Training" width="100%" style="max-width: 800px; height: auto;">

_Figure 2: A proposal for the training strategy of a disease world model._

## An early attempted use case that is applied to lung fibrosis disease progression modelling

**4D-VQGAN**: We built an AI model called 4D VQ-GAN for disease progression modelling of the lung fibrosis disease that satisfies the clinical reliability condition of a disease world model. In the context of the disease progression, we can adapt temporal medical imaging as the environments, on the analogy as using the videos as environments in physical world models. As a proof of concept, our early attempt only focus on only one interactive action with the virtual progression trajectories, which is the time. The technical details of this preliminary study can be found in the published conference paper: [4D VQGAN](https://openreview.net/forum?id=tU3IpPQCEc&noteId=tU3IpPQCEc). Given two 3D CT scans of an Idiopathic Pulmonary Fibrosis patient at irregular time points, 4D VQ-GAN can generate synthetic 3D images at any desired time point, effectively modelling a virtual continuous disease progression trajectory for each individual. More importantly, we found that biomarkers derived from the generated CT volumes exhibit a strong clinical correlation with survival outcome, partially satisfying the clinical reliability condition as defined above, thereby highlighting the potential of 4D VQ-GAN for personalized treatment planning and more personalised medicine tasks.

![synthetic scans gif](/assets/img/publication_preview/side_by_side_1200_border.gif)

_Figure 3: An example of generated synthetic imaging medical artifacts sequence compared against the real sequence. Note that the real scans only contain scans at time point year 0, year2, year 3.5, but the generated scans have more time points at year 0, year 1.5, year 2, year 3.5, year 5.5._

<img src="/assets/img/publication_preview/4dvqgan_example.png" alt="synthetic scans detailed" width="100%" style="max-width: 800px; height: auto;">

_Figure 4: Highlighted key visual features of lung fibrosis in generated imaging artifacts. A zoomed region of the left lower lobe (yellow box) in the real and generated CT scans show comparable amounts of architectural distortion, patterned ground glass opacification and reticulation, all hallmarks of lung fibrosis. The availability of our scans are not uniform across time and across patients, the model is trained on scans at irregular time points_

**Verifiable Clinical Reliability**: We explore our model’s clinical utility using a survival analysis based approach to mimic the clinical workflows. Radiologists track prognostic imaging biomarkers in IPF over time to assess disease progression. Though we lack comprehensive visual scores for all cases, we propose a method that mirrors clinical workflows, including selecting key prognostic biomarkers, analyzing their longitudinal changes, and comparing their prognostic value in synthesized vs. real scans. These extracted imaging biomarkers, along with the covariates, are input into the Cox model to assess their prognostic value in the test dataset. This analysis evaluates the consistency of biomarker trajectories between real and synthetic scans, and explores the potential utility of synthetic scans in tracking changes over time. As shown in the below results, it is very interesting to see that the generated CT images can yield survival outcomes that are sometimes even more accurate than those derived from the real images. However, these results may be overestimated due to the limited sample size.

<img src="/assets/img/blog_disease_world_models/survival_outcomes.png" alt="survival outcome" width="100%" style="max-width: 800px; height: auto;">

_Figure 5: For the cross-sectional imaging biomarker, the C-index using the generated third scans is 0.943. In comparison, using biomarkers derived from real CT scans for survival prediction yields a slightly lower C-index of 0.914.
Next, we compute the longitudinal biomarker by evaluating the change in these top five
significant biomarkers over the course of one year, both for real and generated CT scans.
By inputting these longitudinal biomarkers along with covariates into the Cox model, we
obtain C-indices of 1.0 for both real and generated CT scans._

Although the existing 4D VQ-GAN is a step towards the disease world model with promising results, further study is still required to verify if the 4D VQ-GAN also satisfies the clinical reliability condition due to the lack of time and computational resources.

## References:

1. [Genie: Generative Interactive Environments](https://icml.cc/virtual/2024/oral/35508) ICML 2024
2. [Open-Endedness is Essential for Artificial Superhuman Intelligence](https://proceedings.mlr.press/v235/hughes24a.html) ICML 2024
3. [4D-VQ-GAN: A World Model for Synthesizing Medical Scans at Any Time Point for Personalized Disease Progression Modeling of Idiopathic Pulmonary Fibrosis](https://openreview.net/forum?id=tU3IpPQCEc&noteId=tU3IpPQCEc) MIDL 2025
4. [The Platonic Representation Hypothesis](https://phillipi.github.io/prh/) ICML 2024

<!-- ## Some Relevant Works
We briefly review the concept of digital twins and the specific type of digital twins for healthcare. The digital twin concept was born in the field of aerospace engineering, where the researchers started to use ``replica'' to reproduce a physical complex system to replace the real expensive experiments to cut the costs in XX age in the US. This was commonly regarded as the begining of the concept of ``digital twins''. Through time, the concept of ``digital twins'' have gone through continuous evolution and expansion. It has also migrated from the aerospace engineering filed to any other fields that are involved with modelling complex physical systems. Recently, Katsoulakis et al \cite{digital_twin_healthcare_review_npj_Digital_Medicine} provided a definition of a digital twin for healthcare as, ``a virtual representation of a person which allows dynamic simulation of potential treatment strategy, monitoring and prediction of health trajectory, and early intervention and prevention, based on multi-scale modelling of multi-modal data such as clinical, genetic, molecular, environmental, and social factors etc.'' The same authors also identified three essences of a digital twin, including a physical entity, a virtual replica, and a connection between the two.

Disease World Model is a special case of the digital twin for healthcare. The purpose of this paper is not to replace the concept of the digital twins. Rather, this paper is written to fulfil the details of the broad concept of the healthcare digital twin, so the future researchers can focus on developing the designed computational tools, utilising existing technologies, towards personalised medicine.

What is lacking in the existing concept of Disease Progression Modelling and how can medical world models help?
Not end to end. It is one-size-for-all, lacking of individulisaing.  -->
