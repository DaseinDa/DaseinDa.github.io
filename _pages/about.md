---
layout: about #使用 about.html的模板
title: about
permalink: /
subtitle: Master student at KTH EECS College & TU Berlin Fakultät IV


profile:
  align: right
  image: prof_pic.jpg
  image_circular: false # crops the image to make it circular
  address: >
    <p>Darmstadt, Hessen, Germany</p>

news: true  # includes a list of news items
latest_posts: true  # includes a list of the newest posts
selected_papers: false # includes a list of papers marked as "selected={true}"
social: true  # includes social icons at the bottom of the page
---
## Hello!
I am a double-degree master student at **TU Berlin(Berlin, Germany) & KTH(Stockholm, Sweden)**, majoring in  ICT (Information and Communication Technology) & EE(Electrical Engineering). I am pursuing my master thesis internship for federated learning's hardware security enhancement techniques at Trustworthy & Applied Cryptography Lab.

## Currently
I am currently working on secure learning. I like discussing potentially feaseible methods for practical problems with nice and talented people, feel free to reach out! I am working on Intel SGX
development for a large hybrid-secure platform project concentrating on cloud secure computation. **I am looking for secure machine learning PhD/RA/Research Intern positions, if you are interested in working with me, feel free to reach out!**
## Recent Work/Research Experience

#### Security Research Internship, Trustworthy and applied cryptography lab
2023 June. - Dec.
I am working as a research internship student at Trustworthy and Applied Cryptography Lab, Huawei Munich Center, Germany. I deployed machine learning's TEEs(Trusted Execution Environment) low-level interfaces based on Intel SGX. My C/C++ programming skills have grown a lot, happy to get to know applied cryptography knowledge such as DP(differential Privacy), MPC(Multi-Party Computation) cryptography methods etc. With the opportunity entrying security research, **I find the topic of how to prevent system from attacks and leakages very interesting, and would like to continue contributing on the secure computation work in the future.**

#### Enhancing Privacy, Integrity and Security in Federated Learning: Intel SGX-based Multi-Party Computation Platform
2023 June. - 2024 Jan.
Abstract: With the booming development of large dataset collection and deep learning algorithm’s success into people’s life, Federated Learning(FL), which enables guests to train the desired effective model without sharing privacy with other clients, is raising more and more importance at various scenarios[1]. However, certain deep learning models, such as Generative Adversarial Networks (GANs), pose privacy risks in FL, as they can inadvertently reveal sensitive information from separate devices [2]. This poses a potential threat to users’ privacy and necessitates the development of robust privacy-preserving techniques.

Master thesis is supervised by [Dr. Tianxiang Dai](https://dblp.org/pid/188/4885.html) at lab. University supervisor: [Prof. Ming Xiao](https://www.kth.se/profile/mingx) and University examiner: [Prof. Johan Håstad](https://www.csc.kth.se/~johanh/) 

#### Research Assistant, Deep learning and Image processing
2018 -2020

I worked as a research assistant for [Prof. Shibai Yin](https://dblp.org/pid/140/0713.html) on the deep learning techniques such as transformer, combining traditional computer image theories such as atmosphere scattering model for image dehazing. The useful tools are pytorch, linux shell and git.

<a href="./assets/pdf/JinXin_Yin_publication.pdf">《Image Dehazing with Uneven Illumination Prior by Dense Residual Channel Attention Network》</a>.
#### Computational Bioinformatics Research
Spring 2021

I also worked as a computational research assistant with [Professor Michael Roberts](https://www.dickinson.edu/site/custom_scripts/dc_faculty_profile_index.php?fac=robertsm) on creating classifier models to predict EGR1 cancer relapse levels.

> Check out my [cv page](./cv) for more.

## Projects
<div class="repositories d-flex flex-wrap flex-md-row flex-column justify-content-between align-items-center">
  {% for repo in site.data.repositories.github_repos %}
    {% include repository/repo.html repository=repo %}
  {% endfor %}
</div>

> Check out my [projects page](./projects) for more.