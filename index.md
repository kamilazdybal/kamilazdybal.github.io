---
title: Science Doc(k)s
layout: default
---
<head>
<meta name="google-site-verification" content="pPaEg0Fsm_rm7Cdrm7nUz6Qb_mBsRWhOyPflWYtzYmo" />
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.min.css">
</head>

<style>
img {
    border: 1px solid #ddd;
    border-radius: 4px;  
    padding: 5px;
    width: 150px;
}

{
    box-sizing: border-box;
}

.column {
    float: left;
    width: 20%;
    padding: 0px;
}

.row::after {
    content: "";
    clear: both;
    display: table;
}
</style>

<div id="badges">
  <a href="https://www.linkedin.com/in/kamila-zdybal/">
    <img src="https://img.shields.io/badge/LinkedIn-blue?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn Badge" style="width:125px; border:0px" height=40px/>
  </a>  
  <a href="https://scholar.google.com/citations?user=EI_up1gAAAAJ&hl=en&oi=ao">
    <img src="https://img.shields.io/badge/GoogleScholar-critical?style=for-the-badge&logo=googlescholar&logoColor=white" alt="GoogleScholar Badge" style="width:175px; border:0px" height=40/>
  </a>
  <a href="https://www.researchgate.net/profile/Kamila-Zdybal">
    <img src="https://img.shields.io/badge/ResearchGate-lightseagreen?style=for-the-badge&logo=researchgate&logoColor=white" alt="ResearchGate Badge"  style="width:165px; border:0px" height=40/>
  </a>
  <a href="https://orcid.org/0000-0002-3952-3824">
    <img src="https://img.shields.io/badge/orcid-green?style=for-the-badge&logo=orcid&logoColor=white" alt="ORCID Badge" style="width:95px; border:0px" height=40/>
  </a>
  <a href="https://github.com/kamilazdybal/">
  <img src="https://img.shields.io/badge/GitHub-black?style=for-the-badge&logo=github&logoColor=white" alt="GitHub Badge" style="width:105px; border:0px" height=40/>
</a>
  <a href="https://twitter.com/kamilazdybal">
    <img src="https://img.shields.io/badge/Twitter-dodgerblue?style=for-the-badge&logo=twitter&logoColor=white" alt="Twitter Badge" style="width:115px; border:0px" height=40/>
  </a>
</div>

<h4><span class="fa fa-file-pdf-o"></span><a href="https://github.com/kamilazdybal/kamilazdybal.github.io/raw/main/CV-kamila-zdybal.pdf" target="_blank"> Download my CV</a></h4>

<ul id="intro"></ul>

### **Hi, I'm Kamila, welcome to my personal website!**

Hi, I'm Kamila Zdybał and I'm currently a 4th year PhD student at Université libre de Bruxelles.
This website is a collection of tutorials, articles, coding projects and study notes that are the product of most of my passion that I have for life, Universe and everything else. Many of the materials gathered here are related to my research work and I have hopes that by sharing them you might find pursuing science fascinating! Some of my research interests (which typically spice the materials you will find here) are: dimensionality reduction, reduced-order modeling, low-dimensional manifolds methods, fluid dynamics, reacting flows and multicomponent mass transport. I have a dream that the PDFs will now enrich your journey through learning and experimenting!

When it comes to learning, I believe in the quote of Einstein: *you do not really understand something unless you can explain it to your grandmother*. My aim is to implement that level of understanding into the documents I write (although many times I will assume certain prerequisites that your grandmother should have!). Of course, if you wish to profit from the materials presented here, you will need to incorporate them in your journey. I have hopes that you will find doing science fascinating, rewarding and inspiring!

If you like these materials and you'd like to support me, you can [**buy me a coffee**](https://www.buymeacoffee.com/kamilazdybal)! 🚀

Feel free to drop me a line at: **`kamilazdybal at gmail dot com`**.

<img src="https://github.com/kamilazdybal/kamilazdybal.github.io/blob/main/_posts/kamila.jpg?raw=true" alt="about-me" style="width:300px">

-----------------------

<ul id="2022-vki-ulb-cup"></ul>

# Advancing reacting flow simulations with data-driven models

The use of machine learning algorithms to predict behaviors of complex systems is booming. However, the key to an effective use of machine learning tools in multi-physics problems, including combustion, is to couple them to physical and computer models. The performance of these tools is enhanced if all the prior knowledge and the physical constraints are embodied. In other words, the scientific method must be adapted to bring machine learning into the picture, and make the best use of the massive amount of data we have produced, thanks to the advances in numerical computing. The present chapter reviews some of the open opportunities for the application of data-driven reduced-order modeling of combustion systems. We provide examples of feature extraction in turbulent combustion data, empirical low-dimensional manifold (ELDM) identification, classification, regression, and reduced-order modeling.

<sup>K. Zdybał, G. D'Alessio, G. Aversano, M. R. Malik, A. Coussement, J. C. Sutherland, A. Parente, *Advancing reacting flow simulations with data-driven models*, In M. A. Mendez, A. Ianiro, B. R. Noack,  S. L. Brunton, editors, *Data-Driven Fluid Dynamics: Combining First Principles and Machine Learning*, Cambridge University Press, 2022</sup>

<div class="row">
  <div class="column">
    <a><img src="https://github.com/kamilazdybal/kamilazdybal.github.io/raw/main/_posts/flame.png" alt="CUP-book-chapter" style="width:150px"></a>
  </div>
  <div class="column">
    <h4><span class="fa fa-file-pdf-o"></span><a href="https://www.datadrivenfluidmechanics.com/download/book/DataDrivenFluidMechanicsBook_TableofContent.pdf" target="_blank"> Book chapter</a></h4>
    <h4><span class="fa fa-file-pdf-o"></span><a href="https://www.cambridge.org/core/books/datadriven-fluid-mechanics/0327A1A43F7C67EE88BB13743FD9DC8D" target="_blank"> Entire book</a></h4>
  </div>
</div>

<ul id="cost-function"></ul>

# Cost function for low-dimensional manifold topology assessment

In reduced-order modeling, complex systems that exhibit high state-space dimensionality are described and evolved using a small number of parameters. These parameters can be obtained in a data-driven way, where a high-dimensional dataset is projected onto a lower-dimensional basis. A complex system is then restricted to states on a low-dimensional manifold where it can be efficiently modeled. While this approach brings computational benefits, obtaining a good quality of the manifold topology becomes a crucial aspect when models, such as nonlinear regression, are built on top of the manifold. Here, we present a quantitative metric for characterizing manifold topologies. Our metric pays attention to non-uniqueness and spatial gradients in physical quantities of interest, and can be applied to manifolds of arbitrary dimensionality. Using the metric as a cost function in optimization algorithms, we show that optimized low-dimensional projections can be found. We delineate a few applications of the cost function to datasets representing argon plasma, reacting flows and atmospheric pollutant dispersion. We demonstrate how the cost function can assess various dimensionality reduction and manifold learning techniques as well as data preprocessing strategies in their capacity to yield quality low-dimensional projections. We show that improved manifold topologies can facilitate building nonlinear regression models.

<sup>K. Zdybał, E. Armstrong, J. C. Sutherland, A. Parente, *Cost function for low-dimensional manifold topology assessment*, Scientific Reports 12 (2022) 14496 </sup>

<div class="row">
  <div class="column">
    <a><img src="https://github.com/kamilazdybal/kamilazdybal.github.io/raw/main/_posts/cost-function-manifold-topology-optimization.png" alt="Cost-function-seminar" style="width:150px"></a>
  </div>
  <div class="column">
    <h4><span class="fa fa-file-pdf-o"></span><a href="https://www.nature.com/articles/s41598-022-18655-1" target="_blank"> Publication</a></h4>
    <h4><span class="fa fa-video-camera"></span><a href="https://www.vki.ac.be/index.php/vki-seminars" target="_blank"> Talk</a></h4>
    <h4><span class="fa fa-github"></span><a href="https://github.com/kamilazdybal/cost-function-manifold-assessment" target="_blank"> Code</a></h4>
  </div>
</div>

<ul id="manifold-informed-state-vector"></ul>

# Manifold-informed state vector subset for reduced-order modeling

Reduced-order models (ROMs) for turbulent combustion rely on identifying a small number of parameters that can effectively describe the complexity of reacting flows. With the advent of data-driven approaches, ROMs can be trained on datasets representing the thermo-chemical state-space in simple reacting systems. For low-Mach flows, the full state vector that serves as a training dataset is typically composed of temperature and chemical composition. The dataset is projected onto a lower-dimensional basis and the evolution of the complex system is tracked on a lower-dimensional manifold. This approach allows for substantial reduction of the number of transport equations to solve in combustion simulations, but the quality of the manifold topology is a decisive aspect in successful modeling. To mitigate manifold challenges, several authors advocate reducing the state vector to only a subset of major variables when training ROMs. However, this reduction is often done *ad hoc* and without giving detailed insights into the effect of removing certain variables on the resulting low-dimensional data projection. In this work, we present a quantitative manifold-informed method for selecting the subset of state variables that minimizes unwanted behaviors in manifold topologies. While many authors in the past have focused on selecting major species, we show that a mixture of major and minor species can be beneficial to improving the quality of low-dimensional data representations. The desired effects include reducing non-uniqueness and spatial gradients in the dependent variable space. Finally, we demonstrate improvements in regressibility of manifolds built from the optimal state vector subset as opposed to the full state vector.

<sup>K. Zdybał, J. C. Sutherland, A. Parente, *Manifold-informed state vector subset for reduced-order modeling*, Proceedings of the Combustion Institute 39 (2022) 1-10</sup>

<div class="row">
  <div class="column">
    <a><img src="https://github.com/kamilazdybal/kamilazdybal.github.io/raw/main/_posts/state-vector-subset.png" alt="local-manifold-learning" style="width:150px"></a>
  </div>
  <div class="column">
    <h4><span class="fa fa-file-pdf-o"></span><a href="https://authors.elsevier.com/a/1fPcv5UKsGBnCP" target="_blank"> Publication</a></h4>
    <h4><span class="fa fa-video-camera"></span><a href="https://www.youtube.com/watch?v=MMldWMduCp0" target="_blank"> Talk</a></h4>
    <h4><span class="fa fa-github"></span><a href="https://github.com/kamilazdybal/manifold-informed-state-vector-subset" target="_blank"> Code</a></h4>
  </div>
</div>

<ul id="local-manifold-learning"></ul>

# Local manifold learning and its link to domain-based physics knowledge

In many reacting flow systems, the thermo-chemical state-space is known or assumed to evolve close to a low-dimensional manifold (LDM). Various approaches are available to obtain those manifolds and subsequently express the original high-dimensional space with fewer parameterizing variables. Principal component analysis (PCA) is one of the dimensionality reduction methods that can be used to obtain LDMs. PCA does not make prior assumptions about the parameterizing variables and retrieves them empirically from the training data. In this paper, we show that PCA applied in local clusters of data (local PCA) is capable of detecting the intrinsic parameterization of the thermo-chemical state-space. We first demonstrate that utilizing three common combustion models of varying complexity: the Burke-Schumann model, the chemical equilibrium model and the homogeneous reactor. Parameterization of these models is known *a priori* which allows for benchmarking with the local PCA approach. We further extend the application of local PCA to a more challenging case of a turbulent non-premixed *n*-heptane/air jet flame for which the parameterization is no longer obvious. Our results suggest that meaningful parameterization can be obtained also for more complex datasets. We show that local PCA finds variables that can be linked to local stoichiometry, reaction progress and soot formation processes.

<sup>K. Zdybał, G. D'Alessio, A. Attili, A. Coussement, J. C. Sutherland, A. Parente, *Local manifold learning and its link to domain-based physics knowledge* **(preprint)**, 2022 </sup>

<div class="row">
  <div class="column">
    <a><img src="https://github.com/kamilazdybal/kamilazdybal.github.io/raw/main/_posts/local-manifold-learning.png" alt="local-manifold-learning" style="width:150px"></a>
  </div>
  <div class="column">
    <h4><span class="fa fa-file-pdf-o"></span><a href="https://arxiv.org/abs/2207.00275" target="_blank"> Preprint</a></h4>
    <h4><span class="fa fa-github"></span><a href="https://github.com/kamilazdybal/local-manifold-learning" target="_blank"> Code</a></h4>
  </div>
</div>

<ul id="2022-springer"></ul>

# Reduced-order modeling of reacting flows using data-driven approaches

Stay tuned for our book chapter in collection *Lecture notes in Energy:  Machine Learning and its Application to Reacting Flows* by me and co-workers, coming soon!

<sup>K. Zdybał, M. R. Malik, A. Coussement, J. C. Sutherland, A. Parente, *Reduced-order modeling of reacting flows using data-driven approaches*, In N. Swaminathan, A. Parente, editors, *Lecture notes in Energy:  Machine Learning and its Application to Reacting Flows*, Springer, 2022</sup>

<div class="row">
  <div class="column">
    <a><img src="https://github.com/kamilazdybal/kamilazdybal.github.io/raw/main/_posts/Springer-chapter.png" alt="Springer-book-chapter" style="width:150px"></a>
  </div>
  <div class="column">
    <h4><span class="fa fa-code"></span><a href="https://nbviewer.org/github/kamilazdybal/ROM-of-reacting-flows-Springer/blob/main/PCAfold-programming-examples.ipynb" target="_blank"> Jupyter notebook</a></h4>
  </div>
</div>

<ul id="multipy"></ul>

# **multipy** - Python library for multicomponent mass transfer

Check out the beta version of our educational Python library intended to support your learning of multicomponent mass transfer! Our goal was to create a set of functions that are the essential building blocks with which you can play to get more intuition and understanding of quantities involved in multicomponent flows. With these tools you can set-up your own problems such as the Stefan tube problem or the two-bulb diffusion without a whole lot of coding. We wish you a lot of joy in studying multicomponent mass transfer!

<sup>This library is developed with the help of Professor James C. Sutherland from the University of Utah.</sup>

<div class="row">
  <div class="column">
    <a><img src="https://github.com/kamilazdybal/kamilazdybal.github.io/blob/main/_posts/multipy.png?raw=true" alt="multipy" style="width:150px"></a>
  </div>
  <div class="column">
    <h4><span class="fa fa-book"></span><a href="https://multipy-lib.readthedocs.io/" target="_blank"> Documentation</a></h4>
    <h4><span class="fa fa-code"></span><a href="https://mybinder.org/v2/gh/kamilazdybal/multipy/main?labpath=%2Fdocs%2Ftutorials" target="_blank"> Jupyter tutorials</a></h4>
    <h4><span class="fa fa-github"></span><a href="https://github.com/kamilazdybal/multipy" target="_blank"> Code</a></h4>
  </div>
</div>

<ul id="pcafold"></ul>

# **PCAfold** - Low-dimensional PCA-derived manifolds and everything in between!

Check out **PCAfold**, our Python software for generating, analyzing and improving low-dimensional manifolds.
It can be used for data clustering and sampling, dimensionality reduction, nonlinear regression and assessing the quality of low-dimensional manifolds. **PCAfold** is published in the SoftwareX journal:

<sup>K. Zdybał, E. Armstrong, A. Parente, J. C. Sutherland, *PCAfold: Python software to generate, analyze and improve PCA-derived low-dimensional manifolds*, SoftwareX 12, 2020, 100630</sup>

Reach out to the documentation for many illustrative tutorials! You can also run the tutorials as interactive Jupyter notebooks by clicking below:

<a href="https://mybinder.org/v2/git/https%3A%2F%2Fgitlab.multiscale.utah.edu%2Fcommon%2FPCAfold/master?filepath=docs%2Ftutorials%2F">
  <img src="https://mybinder.org/badge_logo.svg" alt="MyBinder Badge" style="width:150px; border:0px" height=40px/>
</a>  

<sup>This work has been produced during my PhD at Université libre de Bruxelles and my research stay at the University of Utah.</sup>

<div class="row">
  <div class="column">
    <a><img src="https://github.com/kamilazdybal/kamilazdybal.github.io/raw/main/_posts/PCAfold-logo.png" alt="PCAfold" style="width:150px"></a>
  </div>
  <div class="column">
    <h4><span class="fa fa-file-pdf-o"></span><a href="https://www.sciencedirect.com/science/article/pii/S2352711020303435" target="_blank"> Publication</a></h4>
    <h4><span class="fa fa-book"></span><a href="https://pcafold.readthedocs.io/" target="_blank"> Documentation</a></h4>
    <h4><span class="fa fa-github"></span><a href="https://gitlab.multiscale.utah.edu/common/PCAfold" target="_blank"> Code</a></h4>
  </div>
</div>

<div class="row">
  <div class="column">
    <a><img src="https://gitlab.multiscale.utah.edu/common/PCAfold/raw/master/docs/outreach/PCAfold-poster.png" alt="PCAfold" style="width:150px"></a>
  </div>
  <div class="column">
    <h4><span class="fa fa-file-pdf-o"></span><a href="https://gitlab.multiscale.utah.edu/common/PCAfold/-/raw/master/docs/outreach/PCAfold-poster.pdf" target="_blank"> Poster</a></h4>
  </div>
</div>

<ul id="tensornecessity"></ul>

# The tensor necessity - a short story about momentum transport in fluids

At first encounter, tensors can seem like strange mathematical objects. It can be challenging to grasp their meaning and their relevance might not be immediately obvious. At the same time, tensors are indispensable when studying fluid dynamics. So what's with the tensors and why do we need them?

<div class="row">
  <div class="column">
    <a><img src="https://github.com/kamilazdybal/fluid-dynamics-and-transport-phenomena/blob/master/tensor-necessity/plots/thumbnail.png?raw=true" alt="Tensor-necessity" style="width:150px"></a>
  </div>
  <div class="column">
    <h4><span class="fa fa-file-pdf-o"></span><a href="https://github.com/kamilazdybal/fluid-dynamics-and-transport-phenomena/raw/master/tensor-necessity/tensor-necessity.pdf" target="_blank"> Article</a></h4>
  </div>
</div>

<ul id="heatconduction"></ul>

# Steady-state heat conduction

A computational example of steady-state heat conduction in a lengthwise-insulated rod with internal heat production spiced up with a bit of Python!

<div class="row">
  <div class="column">
    <a><img src="https://github.com/kamilazdybal/fluid-dynamics-and-transport-phenomena/blob/master/transport-phenomena-with-Python/figures/steady-state-heat-conduction.png?raw=true" alt="Heat-transfer" style="width:150px"></a>
  </div>
  <div class="column">
    <h4><span class="fa fa-file-pdf-o"></span><a href="https://github.com/kamilazdybal/fluid-dynamics-and-transport-phenomena/raw/master/transport-phenomena-with-Python/example-heat-transfer-in-a-rod.pdf" target="_blank"> Tutorial</a></h4>
    <h4><span class="fa fa-code"></span><a href="https://mybinder.org/v2/gh/kamilazdybal/fluid-dynamics-and-transport-phenomena/master?filepath=transport-phenomena-with-Python%2Fcode%2F01-heat-conduction.ipynb" target="_blank"> Jupyter notebook</a></h4>
  </div>
</div>

<ul id="pca"></ul>

# The linear algebra of Principal Component Analysis (with Python examples)

These are notes on the linear algebra aspects of Principal Component Analysis (PCA) with a little bit more insight then you would typically get when reading about PCA from online tutorials. The notes are accompanied by several Python computational examples.

<div class="row">
  <div class="column">
    <a><img src="https://github.com/kamilazdybal/ulb-atm-phd/blob/master/PCA/plots/thumbnail.png?raw=true" alt="PCA sample" style="width:150px"></a>
  </div>
  <div class="column">
    <h4><span class="fa fa-file-pdf-o"></span><a href="https://github.com/kamilazdybal/ulb-atm-phd/raw/master/PCA/PCA.pdf" target="_blank"> Tutorial</a></h4>
    <h4><span class="fa fa-code"></span><a href="https://nbviewer.jupyter.org/github/kamilazdybal/ulb-atm-phd/blob/master/PCA/PCA-tutorial.ipynb" target="_blank"> Jupyter notebook</a></h4>
  </div>
</div>

<ul id="dmd"></ul>

# Notes on Dynamic Mode Decomposition

These are notes on Dynamic Mode Decomposition (DMD), a data-driven method for finding low-rank structures in high-dimensional data sets. These notes come mainly from two lectures by Prof. Nathan Kutz from the University of Washington but also from other sources and my own previous study of DMD.

*This is a beta version of an article. You can help me make it better by spotting errors or suggesting improvements!*

<div class="row">
  <div class="column">
    <a><img src="https://github.com/kamilazdybal/ulb-atm-phd/blob/master/DMD/DWGs/DMD-science-docs.png?raw=true" alt="DMD" style="width:150px"></a>
  </div>
  <div class="column">
    <h4><span class="fa fa-file-pdf-o"></span><a href="https://github.com/kamilazdybal/ulb-atm-phd/raw/master/DMD/DMD-theory.pdf" target="_blank"> Tutorial</a></h4>
  </div>
</div>

<ul id="objectifmorse"></ul>

# Objectif Morse - an Arduino and C++ journey through transmitting messages in Morse

Have you ever wondered what if there were two computers talking to each other using Morse code? One would send a message with light signals and the other would collect the light and understand the message? No cable connecting the computers. The information simply carried by light that travels through the air.

Well, here it is! In the Objectif Morse project you will make an interesting use of Arduino, electronic circuits and C++ while transmitting messages in Morse alphabet between computers.

<sup>This work has been produced as part of the *Arduino Study Group* meetings at the Jagiellonian University.</sup>

<div class="row">
  <div class="column">
    <a><img src="https://github.com/kamilazdybal/objectif-morse/blob/master/Documentation/cover_obj_morse.jpg?raw=true" alt="objectif_morse" style="width:150px"></a>
  </div>
  <div class="column">
    <h4><span class="fa fa-file-pdf-o"></span><a href="https://github.com/kamilazdybal/objectif-morse/raw/master/Documentation/Objectif_Morse.pdf" target="_blank"> Tutorial</a></h4>
    <h4><span class="fa fa-github"></span><a href="https://github.com/kamilazdybal/objectif-morse" target="_blank"> Code</a></h4>
  </div>
</div>

<ul id="poddmd"></ul>

# POD and DMD decomposition of numerical and experimental data

Using two data decomposition methods: Proper Orthogonal Decomposition (POD) and Dynamic Mode Decomposition (DMD), as well as concepts from linear algebra and dynamical systems within Matlab scripts, I searched for low-rank structures in the pulsating Poiseuille flow and in the velocity field of the flow behind a cylinder.

<sup>This work has been produced as part of the Short Training Programme at the von Karman Institute for Fluid Dynamics, under supervision of Professor Miguel A. Mendez.</sup>

<div class="row">
  <div class="column">
    <a><img src="https://github.com/kamilazdybal/POD-DMD-decompositions/blob/master/DWGs/GIF_2D_POD_r3.gif?raw=true" alt="POD_DMD" style="width:150px"></a>
  </div>
  <div class="column">
    <h4><span class="fa fa-file-pdf-o"></span><a href="https://github.com/kamilazdybal/POD-DMD-decompositions/raw/master/final-report/stagiaire_report_kzdybal.pdf" target="_blank"> Report</a></h4>
    <h4><span class="fa fa-github"></span><a href="https://github.com/kamilazdybal/POD-DMD-decompositions" target="_blank"> Code</a></h4>
  </div>
</div>

<ul id="associativelaw"></ul>

# Proof of the associative law for matrices

I was reviewing the amazing MIT 18.06 course on linear algebra. When the associative law appeared on the blackboard, Professor Strang said: *It’s not that easy to prove that this is correct. You have to go into the gory details of matrix multiplication, do it both ways and see that you come out the same.*

So I said: *let’s do it!*

<div class="row">
  <div class="column">
    <a><img src="https://github.com/kamilazdybal/linear-algebra/raw/master/proof-of-associative-law/proof-of-associative-law-thumbnail.png?raw=true" alt="MIT-G-Strang" style="width:150px"></a>
  </div>
  <div class="column">
    <h4><span class="fa fa-file-pdf-o"></span><a href="https://github.com/kamilazdybal/linear-algebra/raw/master/proof-of-associative-law/proof-of-associative-law.pdf" target="_blank"> Note</a></h4>
  </div>
</div>

<ul id="gpr"></ul>

# Notes on Gaussian Process Regression

Following a great [lecture](https://www.youtube.com/watch?v=UpsV1y6wMQ8) by Professor Anna Scaife I decided to reproduce her figures and write a small note on Gaussian Process Regression (GPR).

<div class="row">
  <div class="column">
    <a><img src="https://github.com/kamilazdybal/ulb-atm-phd/blob/master/GPR/DWGs/thumbnail.png?raw=true" alt="transport_phenomena" style="width:150px"></a>
  </div>
  <div class="column">
  <h4><span class="fa fa-file-pdf-o"></span><a href="https://github.com/kamilazdybal/ulb-atm-phd/raw/master/GPR/GPR.pdf" target="_blank"> Note</a></h4>
  </div>
</div>

<ul id="neutrino"></ul>

# Thermal properties of coffee containers and Newton's law of cooling

How do different coffee containers compare in keeping your coffee warm?
We perform experimental measurements using Arduino and fit the results with Newton's theoretical model for describing cooling. This article is published in **Neutrino**, a popular science magazine issued by the Physics department at the Jagiellonian University:

<sup>K. Zdybał, *Badanie własności izolacyjnych termosów. Zastosowanie prawa stygnięcia Newtona*, Neutrino, 33 (2016) 13-18</sup>

<div class="row">
  <div class="column">
    <a><img src="https://github.com/kamilazdybal/kamilazdybal.github.io/raw/main/_posts/newtons-law-of-cooling.png" alt="neutrino" style="width:150px"></a>
  </div>
  <div class="column">
  <h4><span class="fa fa-file-pdf-o"></span><a href="http://www.neutrino.if.uj.edu.pl/archiwum/2016/33" target="_blank"> Neutrino no. 33</a></h4>
  </div>
</div>

-----------------------

## Under construction

<ul id="fluidtoolbox"></ul>

# Fluid Toolbox

Fluid Toolbox is a collection of human-readable, pseudo-random study notes. It contains descriptions and explanations of various fluid mechanics concepts. It is meant to be used complimentary to the regular textbook since it may provide additional insights but it will not substitute the thoroughness of the standard course in the subject. I believe that working side by side with the course, it can become a useful toolbox of concepts that are ready-to-use and ready-to-understand.

<sup>This document is still under construction... Would you like to help in completing it?</sup>

<div class="row">
  <div class="column">
    <a><img src="https://github.com/kamilazdybal/fluid-dynamics-and-transport-phenomena/blob/master/fluid-toolbox/cover-fluid-toolbox.png?raw=true" alt="transport_phenomena" style="width:150px"></a>
  </div>
</div>

<ul id="transportphenomena"></ul>

# Computational examples in transport phenomena with Python

I collected a few interesting computational examples in transport phenomena in a form of a tutorial and created a set of Python codes to accompany a better understanding of the results.

<sup>This tutorial has been produced after taking two great courses offered by TU Delft: *The Basics of Transport Phenomena* and *Advanced Transport Phenomena*.</sup>

<sup>This document is still under construction... Would you like to help in completing it?</sup>

<div class="row">
  <div class="column">
    <a><img src="https://github.com/kamilazdybal/fluid-dynamics-and-transport-phenomena/blob/master/transport-phenomena-with-Python/figures/cover-trans-phen.jpg?raw=true" alt="transport_phenomena" style="width:150px"></a>
  </div>
</div>

# Condensed notes on combustion

These are dense notes on combustion concepts. They are a collection of knowledge that I acquired at the beginning of my PhD, being completely unfamiliar with the combustion science.
They start from the preliminary notions that are needed in understanding the combustion language. Next, they introduce the elements of thermodynamics relevant to the study of combustion, and finally present the governing differential relations for reactive flows in various systems.

<sup>This document is still under construction... Would you like to help in completing it?</sup>

<div class="row">
  <div class="column">
    <a><img src="https://github.com/kamilazdybal/kamilazdybal.github.io/raw/main/_posts/combustion.png?raw=true" alt="combustion" style="width:150px"></a>
  </div>
</div>

-----------------------

<ul id="tools"></ul>

# Tools

## [Standard Atmosphere Calculator](https://kamilazdybal.github.io/standard-atmosphere-calculator/standard-atmosphere-calculator.html)

-----------------------

# Science blog & thoughts

<ul id="blog">
  {% for post in site.posts %}
    <li>
      <a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>

<sup><a href="/kamilazdybal.github.io/#intro">Jump to the top of the page ^</a></sup>

<footer class="site-footer">

  <span class="site-footer-credits">This site uses: <a href="https://github.com/lorepirri/cayman-blog">Cayman Blog Theme</a>  by Lorenzo Pirritano (@lorepirri)  | <a href="https://github.com/lorepirri/cayman-blog/blob/master/LICENSE">Licence</a>: Creative Commons Attribution 1.0 International </span>
</footer>
