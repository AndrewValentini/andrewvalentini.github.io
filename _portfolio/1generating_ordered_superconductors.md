---
title: "Diffusion-Based Discovery of Ordered Superconductors"
excerpt: "Abstract: To address the disconnect between novel computational predictions and experimental realization in AI-driven superconductor discovery pipelines, we fine-tune a diffusion foundation model on 7,183 superconductors labeled with crystallographic disorder probability and superconducting critical temperature, and employ classifier-free guidance to steer sampling towards ordered and high-temperature superconductors. We demonstrate that this model exhibits a 2.05x improvement in the ability to generate ordered structures with respect to an unguided baseline, from 31.80% to 65.13%, in addition to a 4.16x improvement in the median superconducting critical temperature of generated materials, from a median Tc of 0.99K to 4.13K. Structures generated from this fine-tuned model are then screened through a multi-stage pipeline which employs machine learning and density functional theory calculations to assess disorder probability, thermodynamic stability, and superconducting properties, with selected structures advancing to experimental synthesis."
collection: portfolio
author_profile: true
share: true
navigation: false
preview_image: /files/1D_kde_double_guidance_slide2.png
preview_alt: "Density plots of critical temperature and disorder probability for the training data, Tc-guided samples, and Tc and disorder-guided samples"
preview_caption: "Distributions of superconducting critical temperature (left) and disorder probability (right) for the training data and for structures generated with T<sub>c</sub> guidance alone and with joint T<sub>c</sub> &amp; disorder guidance."
---

My poster is linked <a href='/files/posters/Diffusion_Based_Discovery_of_Ordered_Superconductors_Poster.pdf'>here</a>

<figure>
    <a href="/files/guided_diffusion_full.png"><img src="/files/guided_diffusion_full.png" alt="Diagram of the base neural network with two adapter modules, one for each conditioning variable, whose summed outputs feed into every hidden layer" /></a>
    <figcaption class="image-caption">Network architecture for conditioning on two properties at once. Each conditioning variable (c<sub>i</sub>, c<sub>j</sub>), here superconducting critical temperature and disorder probability, gets its own adapter module: the variable is embedded (g<sub>i</sub>), passed through a small adapter network f<sub>adapter,i</sub>, and projected by a mix-in layer f<sub>mixin,i</sub>. The outputs of the two adapter modules are summed and injected into every hidden layer H<sup>(1)</sup>, …, H<sup>(L)</sup> of the pretrained diffusion network, so a single fine-tuned model can be steered toward both properties simultaneously. Click the figure to view it at full size.</figcaption>
</figure>

<figure>
    <img src="/files/1D_kde_double_guidance_slide2.png" alt="Density plots of critical temperature and disorder probability for the training data, Tc-guided samples, and Tc and disorder-guided samples" />
    <figcaption class="image-caption">Distributions of superconducting critical temperature (left) and disorder probability (right) for the training data and for structures generated with T<sub>c</sub> guidance alone and with joint T<sub>c</sub> &amp; disorder guidance.</figcaption>
</figure>

<figure>
    <a href="/files/workflow_light_nontrans.png"><img src="/files/workflow_light_nontrans.png" alt="Flowchart of the screening pipeline: training and generation stages, then machine-learned interatomic potential screening stages, then DFT screening stages, ending in final candidates" /></a>
    <figcaption class="image-caption">Screening pipeline from generated structures to final candidates. A DiffCSP model trained on the Alexandria database is fine-tuned with adapter modules on a superconductivity database and sampled with classifier-free guidance on T<sub>c</sub> and disorder (green). Generated structures are first screened with machine-learned interatomic potentials (blue). Structures are kept if they are structurally valid with a predicted disorder probability d ≤ 20%. They are then relaxed with UMA, deduplicated and checked for novelty, and kept only if they are thermodynamically stable (E<sub>hull</sub> ≲ 0, E<sub>formation</sub> ≲ 0), metallic (band gap ≈ 0), predicted to have T<sub>c</sub> ≥ 5 K, and dynamically stable. The remaining structures are re-relaxed and re-checked with density functional theory (red) for dynamical stability and T<sub>c</sub> ≥ 5 K, giving the final candidates passed to experimental collaborators for synthesis. Click the figure to view it at full size.</figcaption>
</figure>
