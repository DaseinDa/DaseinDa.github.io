---
layout: about #使用 about.html的模板
title: about
permalink: /
subtitle: Master student at KTH EECS College

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
I am a double-degree master student at **TU Berlin(Berlin, Germany) & KTH(Stockholm, Sweden)**, majoring in  ICT (Information and Communication Technology) & EE(Electrical Engineering). I am pursuing my master thesis internship for federated learning's hardware security enhancement at Trustworthy&Applied Cryptography Huawei Munich Research Center.

## Currently
I am currently working on secure learning. I like discussing potentially feaseible methods for practical problems with nice and talented people, feel free to reach out! I am working on Intel SGX
development for a large hybrid-secure platform project concentrating on cloud secure computation.
## Recent Work/Research Experience
#### Security Research Internship, Trustworthy and applied cryptography lab
2023 June.- Dec.
I am working as a research internship student at Trustworthy and Applied Cryptography Lab, Huawei Munich Center, Germany. I deployed machine learning's TEEs(Trusted Execution Environment) low-level interfaces based on Intel SGX. My C/C++ programming skills have grown a lot, happy to get to know applied cryptography knowledge such as DP(differential Privacy), MPC(Multi-Party Computation) cryptography methods etc. With the opportunity entrying security research, I find the topic of how to prevent system from attacks and leakages very interesting, and would like to continue contributing on the secure computation work in the future.

#### Enhancing Privacy, Integrity and Security in Federated Learning: Intel SGX-based Multi-Party Computation Platform

Master thesis supervised by Prof. and Prof. 

#### Computer Vision Research
Summer 2021

I worked as a Computer Vision research assistant for [Professor John MacCormick](https://www.dickinson.edu/johnmaccormick) on the visualization techniques of Convolutional Neural Networks.

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