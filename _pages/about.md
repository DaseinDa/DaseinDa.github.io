---
layout: about
title: about
permalink: /
subtitle: Undergraduate majoring in Math and Computer Science @ Dickinson College.

profile:
  align: right
  image: prof_pic.jpg
  image_circular: false # crops the image to make it circular
  address: >
    <p>Carlisle, PA, USA</p>

news: true  # includes a list of news items
latest_posts: true  # includes a list of the newest posts
selected_papers: false # includes a list of papers marked as "selected={true}"
social: true  # includes social icons at the bottom of the page
---
## Hello!
I am a double degree student at TU Berlin(Berlin, Germany) & KTH(Stockholm, Sweden), majoring in ICT(Information and Communication Technology) & EE(Electrical Engineering). I am pursuing my master thesis internship for federated learning's hardware security enhancement at Trustworthy&Applied Cryptography, Huawei Munich Research Center.

## Currently
I am currently participating in the VIPriors ICCV 2023 Challenge with a researcher from Yonsei University. Additionally, I am working on implementing milestone papers in Computer Vision as well as recreating some basics techniques in machine learning, such as Pytorch's Autograd and Transformers.

## Recent Work/Research Experience
#### Data Analyst in the Korean Army
2021 ~ 2023

I spent the past two years working as a data analyst for the Tunnel Neutralization Team in the Republic of Korea Army Intelligence. I utilized Fast Fourier Transformation and other military AI tools to collect and process North Korean underground sound data.

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