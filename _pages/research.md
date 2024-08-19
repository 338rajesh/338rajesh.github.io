---
layout: page
title: Research
permalink: /research/
nav: true
---

- [**Composite materials RVE Generation**](#composite-materials-rve-generation)
- [**Influence of fibre cross-sectional profile on multi-physical properties of composite material**](#influence-of-fibre-cross-sectional-profile-on-multi-physical-properties-of-composite-material)
- [**A deep learning model to predict properties of composite material**](#a-deep-learning-model-to-predict-properties-of-composite-material)
- [**Inverse design of porous structures using generative adversarial networks**](#inverse-design-of-porous-structures-using-generative-adversarial-networks)
- [**Design of twin screw compressor rotor profiles using generative adversarial networks**](#design-of-twin-screw-compressor-rotor-profiles-using-generative-adversarial-networks)

----

### **Composite materials RVE Generation**

A computationally efficient algorithm is developed to generate virtual Representative Volume Element (RVE) of the composite materials, that can handle arbitrary inclusion geometries and higher inclusion volume fraction. 
Generating RVEs with arbitrary inclusion shapes, involves a non-trivial problem of finding the overlap between non-circular or non-spherical geometries. To simplify this problem, we resort to divide-and-rule philosophy where the geometry of interest is represented as a union of circles or spheres as shown in below.

<p align="center">
  <img width="800" src="https://ars.els-cdn.com/content/image/1-s2.0-S0263822322003452-gr3_lrg.jpg">
  <br><br> Union of n-Spheres representation of various inclusion shapes, which converts the overlap detection between a pair of non-circular/non-spherical inclusion shapes to the overlap detection between two groups of circles or spheres. 
</p>
<!-- 
I have <ins>*developed an universal-overlap detection and removal scheme*</ins> between arbitrary shapes is developed, as a part of generating RVEs with arbitrary inclusion shapes. In this part of work, I have learnt and used used geometry skills, in addition to the statistical analysis and micro-mechanical aspects. -->

It starts with random initialisation of inclusions in the RVE domain while allowing overlaps. Then, a constrained optimisation problem is defined with the magnitude of overlap as the cost to be minimised. I have used non-monotone spectral projection gradient (NMSPG) algorithm to solve the this problem, for which I have derived the gradient of the cost to gain the computational efficiency. In the following the flow-chart of the procedure, along with a generated RVE containing non-circular shapes.

<p align="center">
  <img width="800" src="https://ars.els-cdn.com/content/image/1-s2.0-S0263822322003452-gr1_lrg.jpg">
  <br><br> Flowchart of the steps involved in RVE generation and a sample RVE with different inclusion shapes. RVE with different shapes is generated to show the capability of the algorithm. 
</p>

<p align="center">
  <img width="800" src="https://ars.els-cdn.com/content/image/1-s2.0-S0263822322003452-gr4_lrg.jpg">
  <br><br> Sample RVEs with various inclusion shapes, generated using this algorithm. 
</p>

For more details,  see the related publications:
+ [A computationally efficient approach for generating RVEs of various inclusion/fibre shapes](https://doi.org/10.1016/j.compstruct.2022.115560)

<br>
<hr style="border:2px solid gray">
<br>

### **Influence of fibre cross-sectional profile on multi-physical properties of composite material**

There was a consensus in literature that composite material properties increase with increase in the perimeter of the fibre cross-section. It was speculated that this phenomenon is due to increase in fibre-matrix interface that leads to better load distribution to stiffer constituents from the matrix. Though we have observed such phenomenon at higher perimeters, we have observed a abnormal drop behaviour at lower perimeter increments as shown below. Physically, it means increasing fibre matrix at lower $$\beta$$ values while the monotonically increasing fibre influence is observed after a certain shape factor $$\beta$$. And, this phenomenon is observed across the fibre cross-sectional shapes and across different physics (thermal, mechanical and piezo-electrical).

<p align="center">
  <img width="800" src="https://ars.els-cdn.com/content/image/1-s2.0-S0263822323006670-gr3_lrg.jpg">
</p>
Among the various physical properties, here we show the variation of elastic properties with shape factor, $$\beta$$. Note that the property drops briefly at lower $$\beta$$, but a monotonic increase at higher $$\beta$$. On a side note, with a stiffer matrix a complete opposite behaviour is noticed where a slight rise followed by a monotonic decrease at higher $$\beta$$.

<br>
For this purpose, we have considered five different non-circular shapes as shown below. A non-dimensional parameter $$\beta$$, defined as the ratio of the perimeter $$P$$ of the respective shape perimeter to that of the circle containing equivalent area $$A$$, is used to compare across the shapes.

$$\beta = \frac{P}{\sqrt{4 \pi A}} \in [0, 1]$$

<p align="center">
  <img width="800" src="https://ars.els-cdn.com/content/image/1-s2.0-S0263822323006670-gr1_lrg.jpg">
</p>
 The summary of shapes used in the cross-sectional influence study. For each shape, a parameter $$\delta$$, perimeter and area are defined. On the right hand side of each shape, RVEs containing inclusions with extreme $$\delta$$ values are shown.

Effective material properties are evaluated using the computationally efficient homogenisation tool is developed in Julia language. It is based on a mathematically rigorous Variational Asymptotic Method and FEA based homogenisation tool along with my fellow PhD student A. Phaneendra, at NMCAD laboratory, IISc Bengaluru.

For more details,  see the related publications:
+ [Influence of fibre cross-section profile on the multi-physical properties of uni-directional composites](https://doi.org/10.1016/j.compstruct.2023.117321)


<br>
<hr style="border:2px solid gray">
<br>

### **A deep learning model to predict properties of composite material**

Massive data sets are developed using the RVE generation algorithm and homogenisation tool. Then, a generalised surrogate deep learning CNN model is developed for predicting thermal and thermo-mechanical properties of fibre reinforced composites, with *fibre volume fractions and material systems spanning end-to-end practical range*. In the following image, we show the characteristics of the data set used for training the CNN model. These data sets are made available to the community on [Zenodo](https://doi.org/10.5281/zenodo.8035643) and [Kaggle](https://www.kaggle.com/datasets/rajeshnakka/elastic-properties-of-fibre-reinforced-composites).

<p align="center">
  <img width="800" src="https://media.springernature.com/full/springer-static/image/art%3A10.1038%2Fs41598-023-34823-3/MediaObjects/41598_2023_34823_Fig2_HTML.png?as=webp">
</p>
Summary of the target values (or effective elastic properties) with respect to fibre volume fraction and fibre-matrix elastic moduli contrast, used for training the material property informed CNN model.

Though there were deep learning based models to predict properties from microstructure images, there was no efficient mechanism to learn material information. The previous models were able to map the structural features with the effective properties. Hence, in this work, we develop a simple mechanism is proposed based on the linear interpolation, to encode the constituent properties in the microstructure image. 

<p align="center">
  <img width="600" src="https://media.springernature.com/full/springer-static/image/art%3A10.1038%2Fs41598-023-34823-3/MediaObjects/41598_2023_34823_Fig4_HTML.png?as=webp">
  <br>
</p>
A schematic representation of the material property encoding in a two-phase material. In (b) an encoded array is shown for a property with 10 units for matrix and 400 units for fibre, that is applicable for a system with properties in the range of [1, 500] units.

For more details,  see the related publications:
+ [A generalised deep learning-based surrogate model for homogenisation utilising material property encoding and physics-based bounds](https://www.nature.com/articles/s41598-023-34823-3)

<br>
<hr style="border:2px solid gray">
<br>


### **Inverse design of porous structures using generative adversarial networks** [WIP]

A conditional GAN is developed to generate porous structures for a specified elastic and thermal conduction properties. 


![Sample Porous Structures](/assets/img/porous_structures.png) 


<p align="center">A sample set of porous structures used for training the GAN model.</p>

<br>
<hr style="border:2px solid gray">
<br>

### **Design of twin screw compressor rotor profiles using generative adversarial networks** [WIP]

Twin screw compressors are widely in the industry for pressurising the gases. I have developed a GAN model that can produce the similar but different profiles from that of the training set profiles. This project is funded and guided by centre for compressor technology at City, University of London.

<p align="center">
  <img width="460" height="400" src="/assets/img/gan-generated-profile.png">
</p>

<p align="center">
A sample GAN generated profiles
</p>

<br>
<hr style="border:2px solid gray">
<br>
