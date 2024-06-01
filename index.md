---
title: Science Doc(k)s
layout: default
---
<head>
<meta name="google-site-verification" content="pPaEg0Fsm_rm7Cdrm7nUz6Qb_mBsRWhOyPflWYtzYmo" />
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.min.css">
</head>

<script type="text/javascript" async="" src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.4/MathJax.js?config=TeX-MML-AM_CHTML">
</script>

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
  <a href="https://github.com/kamilazdybal/kamilazdybal.github.io/raw/main/CV-kamila-zdybal.pdf">
    <img src="https://img.shields.io/badge/download_my_CV-gainsboro?style=for-the-badge&logo=latex&logoColor=black" alt="CV" style="width:180px; border:0px" height=40/>
  </a>
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
  <a href="https://www.youtube.com/channel/UCv_HIIdhPlJKdew31vXgt4g">
    <img src="https://img.shields.io/badge/youtube-firebrick?style=for-the-badge&logo=youtube&logoColor=white" alt="YouTube Badge" style="width:125px; border:0px" height=40/>
  </a>
  <a href="https://kamilazdybal.academia.edu/">
    <img src="https://img.shields.io/badge/academia.edu-darkgrey?style=for-the-badge&logo=academia&logoColor=black" alt="Academia.edu Badge" style="width:165px; border:0px" height=40/>
  </a>
  <a href="https://www.buymeacoffee.com/kamilazdybal">
    <img src="https://img.shields.io/badge/buy_me_a_coffee-yellow?style=for-the-badge&logo=buymeacoffee&logoColor=white" alt="buymeacoffee Badge" style="width:175px; border:0px" height=40/>
  </a>
</div>

You can contact me at: **`kamilazdybal at gmail dot com`**

<ul id="intro"></ul>

### **Hi, I'm Kamila, welcome to my personal website!**

I'm a postdoctoral researcher in the [Computational Engineering Lab](https://www.empa.ch/web/s305) at Empa, a Swiss federal laboratory,
where I combine reinforcement learning and data-driven modeling with experimental fluid dynamics.
Previously, I was a Ph.D. student at Université Libre de Bruxelles in the group of Prof. [Alessandro Parente](https://brite-research.be/), 
working on reduced-order modeling of reacting flows.

My research interests revolve around using **representation learning** to **understand high-dimensional datasets** and 
**model high-dimensional systems** with computational efficiency. I'm passionate about science outreach, academic writing, 
creating open-source educational content, and developing open-source scientific software.

**Would you like to support my efforts in creating open-source science and education?** 
You can now make a small donation on [buymeacoffee.com/kamilazdybal](https://buymeacoffee.com/kamilazdybal) or become a member for €3/month.
As a supporter, you gain access to extra materials on being a researcher, making effective graphics, academic writing, life-long learning, and the like!
Many thanks for your support! 🚀

<img src="https://github.com/kamilazdybal/kamilazdybal.github.io/blob/main/_posts/kamila.jpg?raw=true" alt="about-me" style="width:300px">

<sup>That's me at the Capilano suspension bridge<br>
in Vancouver, Canada, 2022.</sup>

-----------------------

# Science blog & thoughts

<ul id="blog">
  {% for post in site.posts %}
    <li>
      <a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>
-----------------------

This website is a collection of tutorials, articles, coding projects, and study notes that are the product 
of most of my passions that I have for life, the universe, and everything else. 
Many of the materials gathered here are related to my research work, and I have hopes that by sharing them, 
you might find pursuing science fascinating! When it comes to learning, 
I believe in the quote of Einstein: *You do not really understand something unless you can explain it to your grandmother*. 
My aim is to implement that level of understanding into the documents 
I write (although many times I will assume certain prerequisites that your grandmother should have!). 
Of course, if you wish to profit from the materials presented here, you will need to incorporate them into your journey. 
I have hopes that you will find doing science fascinating, rewarding, and inspiring!

<ul id="Python-for-ac"></ul>

# Python for academics 🐍 → 🎓

I've launched a series of YouTube tutorials called "*Python for academics*" where I teach you how to automate the everyday academic life with Python! The first 20 videos are here!

My goal is to provide you with extra tools and ideas that you haven't thought about using or implementing before. The best use of these tutorials, as I see it, is that you take those tools and ideas and start building your own Python toolbox that can help you in your everyday academic life. My hope is that you'll find pieces of useful advice that can help you automate your work, your own way! The audience I think will benefit a lot from these tutorials are Ph.D. students, especially at the beginning of their Ph.D. I believe that the earlier you learn how to automate dull tasks the better! My motivation is to teach you things that I wish I had learned early in my Ph.D. But, of course, academics at all stages of their careers are welcome to join along!

<div class="row">
  <div class="column">
    <a><img src="https://github.com/kamilazdybal/kamilazdybal.github.io/raw/main/_posts/python-for-academics.png" alt="PyforAc" style="width:150px"></a>
  </div>
  <div class="column">
    <h4><span class="fa fa-video-camera"></span><a href="https://www.youtube.com/playlist?list=PL7gWbAt3_3KEuRQfwFeI_RH3EZr87nslf" target="_blank"> Tutorials</a></h4>
    <h4><span class="fa fa-github"></span><a href="https://github.com/kamilazdybal/python-for-academics" target="_blank"> Code</a></h4>
  </div>
</div>

<ul id="t-SNE"></ul>

# The beauty and pitfalls of t-SNE

Check out my recent lecture on t-SNE, a manifold learning method used for data visualization!
Part 1 introduces t-SNE and shows applications to biomedical data. Part 2 connects with my research on manifold quality.
I talk about the strengths of t-SNE and about the things to watch out for when creating t-SNE embeddings.

<div class="row">
  <div class="column">
    <a><img src="https://github.com/kamilazdybal/kamilazdybal.github.io/raw/main/_posts/t-SNE-talk.png" alt="t-SNE-talk" style="width:150px"></a>
  </div>
  <div class="column">
    <h4><span class="fa fa-video-camera"></span><a href="https://youtu.be/tfk6Jo0pUQ8" target="_blank"> Part 1</a></h4>
<h4><span class="fa fa-video-camera"></span><a href="https://youtu.be/8fqk-3Z7J4Y" target="_blank"> Part 2</a></h4>
  </div>
</div>

<ul id="literature-talk"></ul>

# Grad school advice: Finding, reading & using literature as a Ph.D. student

How much effort should you dedicate to finding, reading, and using scientific literature throughout your Ph.D.?
Check out my talk on staying on top of literature as a Ph.D. student! 
My goal was to share with you the tips that worked for me in my Ph.D. journey.

<div class="row">
  <div class="column">
    <a><img src="https://github.com/kamilazdybal/kamilazdybal.github.io/raw/main/_posts/literature-talk.png" alt="literature-talk" style="width:150px"></a>
  </div>
  <div class="column">
    <h4><span class="fa fa-video-camera"></span><a href="https://youtu.be/qum8UQoP2kI" target="_blank"> Talk</a></h4>
  </div>
</div>

<ul id="ML-lecture"></ul>

# Introduction to machine learning and artificial neural networks

Check out my invited lecture on machine learning and artificial neural networks at the University of Utah. Thanks to Professor Tony Saad for inviting me!

<div class="row">
  <div class="column">
    <a><img src="https://github.com/kamilazdybal/kamilazdybal.github.io/raw/main/_posts/ML-lecture.png" alt="ML-lecture" style="width:150px"></a>
  </div>
  <div class="column">
    <h4><span class="fa fa-video-camera"></span><a href="https://www.youtube.com/watch?v=IGEWE81FWMA" target="_blank"> 2024 Lecture</a></h4>
    <h4><span class="fa fa-video-camera"></span><a href="https://www.youtube.com/watch?v=wPL2l1K6KPM" target="_blank"> 2023 Lecture</a></h4>
  </div>
</div>

<ul id="nonlinear-decoding"></ul>

# Improving reduced-order models through nonlinear decoding of projection-dependent outputs

Large datasets are abundant in various scientific and engineering disciplines. Multiple physical variables are frequently gathered into one dataset, leading to high data dimensionality. Visualizing and modeling multivariate datasets can be achieved through dimensionality reduction. However, in many reduction techniques to date, there is no guarantee that the reduced data representation will possess certain desired topological qualities. We show that the quality of reduced data representations can be significantly improved by informing data projections by target quantities of interest (QoIs), some of which are functions of the projection itself. The target QoIs can include closure terms required in modeling, important physical variables, or class labels in the case of categorical data. This work can have particular relevance in data visualization and efficient modeling of dynamical systems with many degrees of freedom, as well as in fundamental research of representation learning.

<sup>K. Zdybał, A. Parente, J. C. Sutherland. *Improving reduced-order models through nonlinear decoding of projection-dependent outputs*, Patterns 4 (2023)</sup>

<div class="row">
  <div class="column">
    <a><img src="https://github.com/kamilazdybal/kamilazdybal.github.io/raw/main/_posts/nonlinear-decoding.png" alt="nonlinear-decoding" style="width:150px"></a>
  </div>
  <div class="column">
    <h4><span class="fa fa-file-pdf-o"></span><a href="https://doi.org/10.1016/j.patter.2023.100859" target="_blank"> Article</a></h4>
    <h4><span class="fa fa-github"></span><a href="https://github.com/kamilazdybal/nonlinear-decoding" target="_blank"> Code</a></h4>
    <h4><span class="fa fa-video-camera"></span><a href="" target="_blank"> Video</a></h4>
  </div>
</div>

<ul id="how-to-phd"></ul>

# How to complete a Ph.D.

Doing a Ph.D. has been an immensely rewarding journey for me. It has been really difficult at times, and I mean sobbing-at-my-desk difficult. And at other times, I felt like conquering the top of the world! I’m grateful for every experience from my Ph.D. Those experiences taught me so much, made me more resilient and more confident. This note is a collection of items that helped me complete my Ph.D. and thrive in a Ph.D. program. I’m sharing those with you in hopes that they will help you complete your own journey! You can absolutely end your Ph.D. with a smile on your face and a great sense of accomplishment!

<div class="row">
  <div class="column">
    <a><img src="https://github.com/kamilazdybal/kamilazdybal.github.io/raw/main/_posts/how-to-phd.png" alt="how-to-phd" style="width:150px"></a>
  </div>
  <div class="column">
    <h4><span class="fa fa-file-pdf-o"></span><a href="https://github.com/kamilazdybal/ulb-atm-phd/raw/master/how-to-complete-a-phd/how-to-complete-a-PhD.pdf" target="_blank"> Article</a></h4>
  </div>
</div>

<ul id="PCAfold-2.0"></ul>

# Introducing **PCAfold 2.0**! Novel tools and algorithms for low-dimensional manifold assessment and optimization

We describe an update to our open-source Python package, **PCAfold**, designed to help researchers generate, analyze and improve low-dimensional data manifolds. In the current version, **PCAfold 2.0**, we introduce novel tools and algorithms for assessing and optimizing low-dimensional manifolds. This includes a method that generates a “map” of local feature sizes that can help pinpoint researchers to problematic regions on a manifold. We introduce a novel cost function that characterizes the quality of a manifold topology with a single number. We develop two algorithms for feature selection based on principal component analysis (PCA) that use the cost function as an objective function to minimize. We introduce a quantity of interest (QoI)-aware dimensionality reduction strategy where data projections are computed using an artificial neural network and are directly optimized towards representing various projection-independent and projection-dependent QoIs. We also introduce an implementation of partition of unity networks (POUnets) for efficient reconstruction of QoIs from low-dimensional manifolds based on combining neural network classification with localized polynomial regression. Our software can be broadly applicable in all domains of science and engineering that aim to reduce data dimensionality, as well as in the fundamental research on representation learning.

<div class="row">
  <div class="column">
    <a><img src="https://github.com/kamilazdybal/kamilazdybal.github.io/raw/main/_posts/PCAfold-2.0.png" alt="PCAfold" style="width:150px"></a>
  </div>
  <div class="column">
    <h4><span class="fa fa-file-pdf-o"></span><a href="https://www.sciencedirect.com/science/article/pii/S2352711023001437" target="_blank"> Publication</a></h4>
    <h4><span class="fa fa-book"></span><a href="https://pcafold.readthedocs.io/" target="_blank"> Documentation</a></h4>
    <h4><span class="fa fa-github"></span><a href="https://gitlab.multiscale.utah.edu/common/PCAfold" target="_blank"> Code</a></h4>
  </div>
</div>

<ul id="PCAfold-tutorials"></ul>

## Check out **PCAfold** video tutorials!

PCAfold is our open-source Python library for handling high-dimensional datasets and modeling high-dimensional systems with computational efficiency. In this new series of videos, I provide an overview of possible functionalities in generating, analyzing, and improving low-dimensional data projections, as well as building efficient regression models based on those projections. Stay tuned for more!

<div class="row">
  <div class="column">
    <a><img src="https://github.com/kamilazdybal/kamilazdybal.github.io/raw/main/_posts/PCAfold-tutorials.png" alt="PCAfold" style="width:150px"></a>
  </div>
  <div class="column">
    <h4><span class="fa fa-video-camera"></span><a href="https://www.youtube.com/playlist?list=PL7gWbAt3_3KFYchpPZKv2xJHD8q1Wjr-i" target="_blank"> Tutorials</a></h4>
  </div>
</div>

<ul id="2023-phd-dissertation"></ul>

# My Ph.D. dissertation

On 17 April, 2023, I defended my Ph.D. thesis titled "*Reduced-order modeling of turbulent reacting flows using data-driven approaches*"!
My Ph.D. work has recently been awarded the [**18th ERCOFTAC da Vinci prize**](https://www.ercoftac.org/about/ercoftac-da-vinci-competition/18th-da-vinci-2023/). Check out the recent [interview with me](https://www.ercoftac.org/about/ercoftac-da-vinci-competition/18th-da-vinci-2023/kamila-zdybal/)!

<img src="https://github.com/kamilazdybal/kamilazdybal.github.io/blob/main/_posts/defense-presentation.jpg?raw=true" alt="about-me" style="width:900px">

My dissertation is freely available for download below:

<div class="row">
  <div class="column">
    <a><img src="https://github.com/kamilazdybal/kamilazdybal.github.io/raw/main/_posts/phd-dissertation.png" alt="PhD-dissertation" style="width:150px"></a>
  </div>
  <div class="column">
    <h4><span class="fa fa-file-pdf-o"></span><a href="https://www.researchgate.net/publication/370097058_Reduced-order_modeling_of_turbulent_reacting_flows_using_data-driven_approaches" target="_blank"> Dissertation</a></h4>
  </div>
</div>

<ul id="2023-springer"></ul>

# Reduced-order modeling of reacting flows using data-driven approaches

Data-driven modeling of complex dynamical systems is becoming increasingly popular across various domains of science and engineering. This is thanks to advances in numerical computing, which provides high fidelity data, and to algorithm development in data science and machine learning. Simulations of multicomponent reacting flows can particularly profit from data-based reduced-order modeling (ROM). The original system of coupled partial differential equations that describes a reacting flow is often large due to high number of chemical species involved. While the datasets from reacting flow simulation have high state-space dimensionality, they also exhibit attracting low-dimensional manifolds (LDMs). Data-driven approaches can be used to obtain and parameterize these LDMs. Evolving the reacting system using a smaller number of parameters can yield substantial model reduction and savings in computational cost. In this chapter, we review recent advances in ROM of turbulent reacting flows. We demonstrate the entire ROM workflow with a particular focus on obtaining the training datasets and data science and machine learning techniques such as dimensionality reduction and nonlinear regression. We present recent results from ROM-based simulations of experimentally measured Sandia flames D and F. We also delineate a few remaining challenges and possible future directions to address them. This chapter is accompanied by illustrative examples using the recently developed Python software, PCAfold. The software can be used to obtain, analyze and improve low-dimensional data representations. The examples provided herein can be helpful to students and researchers learning to apply dimensionality reduction, manifold approaches and nonlinear regression to their problems.

<sup>K. Zdybał, M. R. Malik, A. Coussement, J. C. Sutherland, A. Parente, *Reduced-order modeling of reacting flows using data-driven approaches*, In N. Swaminathan, A. Parente, editors, *Lecture notes in Energy:  Machine Learning and its Application to Reacting Flows*, Springer, 2023</sup>

<div class="row">
  <div class="column">
    <a><img src="https://github.com/kamilazdybal/kamilazdybal.github.io/raw/main/_posts/Springer-chapter.png" alt="Springer-book-chapter" style="width:150px"></a>
  </div>
  <div class="column">
    <h4><span class="fa fa-file-pdf-o"></span><a href="https://link.springer.com/content/pdf/10.1007/978-3-031-16248-0_9.pdf?pdf=inline%20link" target="_blank"> Book chapter</a></h4>
    <h4><span class="fa fa-file-pdf-o"></span><a href="https://link.springer.com/book/9783031162473" target="_blank"> Entire book</a></h4>
    <h4><span class="fa fa-code"></span><a href="https://nbviewer.org/github/kamilazdybal/ROM-of-reacting-flows-Springer/blob/main/PCAfold-programming-examples.ipynb" target="_blank"> Jupyter notebook</a></h4>
  </div>
</div>

<ul id="2022-vki-ulb-cup"></ul>

# Advancing reacting flow simulations with data-driven models

The use of machine learning algorithms to predict behaviors of complex systems is booming. However, the key to an effective use of machine learning tools in multi-physics problems, including combustion, is to couple them to physical and computer models. The performance of these tools is enhanced if all the prior knowledge and the physical constraints are embodied. In other words, the scientific method must be adapted to bring machine learning into the picture, and make the best use of the massive amount of data we have produced, thanks to the advances in numerical computing. The present chapter reviews some of the open opportunities for the application of data-driven reduced-order modeling of combustion systems. We provide examples of feature extraction in turbulent combustion data, empirical low-dimensional manifold (ELDM) identification, classification, regression, and reduced-order modeling.

<sup>K. Zdybał, G. D'Alessio, G. Aversano, M. R. Malik, A. Coussement, J. C. Sutherland, A. Parente, *Advancing reacting flow simulations with data-driven models*, In M. A. Mendez, A. Ianiro, B. R. Noack,  S. L. Brunton, editors, *Data-Driven Fluid Dynamics: Combining First Principles and Machine Learning*, Cambridge University Press, 2023</sup>

<div class="row">
  <div class="column">
    <a><img src="https://github.com/kamilazdybal/kamilazdybal.github.io/raw/main/_posts/flame.png" alt="CUP-book-chapter" style="width:150px"></a>
  </div>
  <div class="column">
    <h4><span class="fa fa-file-pdf-o"></span><a href="https://arxiv.org/abs/2209.02051" target="_blank"> Book chapter</a></h4>
    <h4><span class="fa fa-file-pdf-o"></span><a href="https://www.cambridge.org/core/books/datadriven-fluid-mechanics/0327A1A43F7C67EE88BB13743FD9DC8D" target="_blank"> Entire book</a></h4>
    <h4><span class="fa fa-video-camera"></span><a href="https://www.datadrivenfluidmechanics.com/" target="_blank"> VKI Lecture Series</a></h4>
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

<sup>**This publication has received the Distinguished Paper Award for Numerical Combustion from The Combustion Institute.**</sup>

<div class="row">
  <div class="column">
    <a><img src="https://github.com/kamilazdybal/kamilazdybal.github.io/raw/main/_posts/state-vector-subset.png" alt="local-manifold-learning" style="width:150px"></a>
  </div>
  <div class="column">
    <h4><span class="fa fa-file-pdf-o"></span><a href="https://www.researchgate.net/publication/361985981_Manifold-informed_state_vector_subset_for_reduced-order_modeling" target="_blank"> Publication</a></h4>
    <h4><span class="fa fa-video-camera"></span><a href="https://www.youtube.com/watch?v=MMldWMduCp0" target="_blank"> Talk</a></h4>
    <h4><span class="fa fa-github"></span><a href="https://github.com/kamilazdybal/manifold-informed-state-vector-subset" target="_blank"> Code</a></h4>
  </div>
</div>

<ul id="local-manifold-learning"></ul>

# Local manifold learning and its link to domain-based physics knowledge

In many reacting flow systems, the thermo-chemical state-space is known or assumed to evolve close to a low-dimensional manifold (LDM). Various approaches are available to obtain those manifolds and subsequently express the original high-dimensional space with fewer parameterizing variables. Principal component analysis (PCA) is one of the dimensionality reduction methods that can be used to obtain LDMs. PCA does not make prior assumptions about the parameterizing variables and retrieves them empirically from the training data. In this paper, we show that PCA applied in local clusters of data (local PCA) is capable of detecting the intrinsic parameterization of the thermo-chemical state-space. We first demonstrate that utilizing three common combustion models of varying complexity: the Burke-Schumann model, the chemical equilibrium model and the homogeneous reactor. Parameterization of these models is known *a priori* which allows for benchmarking with the local PCA approach. We further extend the application of local PCA to a more challenging case of a turbulent non-premixed *n*-heptane/air jet flame for which the parameterization is no longer obvious. Our results suggest that meaningful parameterization can be obtained also for more complex datasets. We show that local PCA finds variables that can be linked to local stoichiometry, reaction progress and soot formation processes.

<sup>K. Zdybał, G. D'Alessio, A. Attili, A. Coussement, J. C. Sutherland, A. Parente, *Local manifold learning and its link to domain-based physics knowledge*, Applications in Energy and Combustion Science, Special issue: Machine learning methods for reactive flows (2023) </sup>

<div class="row">
  <div class="column">
    <a><img src="https://github.com/kamilazdybal/kamilazdybal.github.io/raw/main/_posts/local-manifold-learning.png" alt="local-manifold-learning" style="width:150px"></a>
  </div>
  <div class="column">
    <h4><span class="fa fa-file-pdf-o"></span><a href="https://doi.org/10.1016/j.jaecs.2023.100131" target="_blank"> Publication</a></h4>
    <h4><span class="fa fa-file-pdf-o"></span><a href="https://arxiv.org/abs/2207.00275" target="_blank"> Preprint</a></h4>
    <h4><span class="fa fa-github"></span><a href="https://github.com/kamilazdybal/local-manifold-learning" target="_blank"> Code</a></h4>
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

Keep calm and

<span class="math display">$$\frac{\partial \rho Y_i}{\partial t} = -
\nabla \cdot (\rho Y_i \mathbf{v}) - \nabla \cdot \mathbf{j}_i +
\omega_i$$</span>

<sup><a href="/kamilazdybal.github.io/#intro">Jump to the top of the page ^</a></sup>

<footer class="site-footer">

  <span class="site-footer-credits">This site uses: <a href="https://github.com/lorepirri/cayman-blog">Cayman Blog Theme</a>  by Lorenzo Pirritano (@lorepirri)  | <a href="https://github.com/lorepirri/cayman-blog/blob/master/LICENSE">Licence</a>: Creative Commons Attribution 1.0 International </span>
</footer>
