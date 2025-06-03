---
layout: publications
permalink: /publications/skeletondiffusion/
# external_link:  https://ceveloper.github.io/CeciliaCurreli.github.io//publications/skeletondiffusion/
date: 2024_08_27 # determines sorting just take the date of the first publication as YYYY_MM_DD
image: /assets/teaser.gif
# image_mouseover: /assets/header_vid.mp4
# icon: /assets/favicon.ico

title: "Nonisotropic Gaussian Diffusion for Realistic 3D Human Motion Prediction"
venue: CVPR 2025
authors:
  - name: ceciliacurreli
    affiliations: "1,2"
  - name: dominikmuhle
    affiliations: "1,2"
  - name: abhisheksaroha
    affiliations: "1,2"
  - name: zhenzhangye
    affiliations: "1"
  - name: riccardomarin
    affiliations: "1,2"
  - name: danielcremers
    affiliations: "1,2"
affiliations:
  - name: tum
    length: long
  - name: mcml
    length: long


description: "SkeletonDiffusion is a novel nonisotropic diffusion approach for 3D Human Motion Prediction, and the first computer vision method to show that nonisotropic diffusion leads to unequivocally better performance without computational drawbacks for a structured task. We generate diverse and realistic motions achieving state-of-the-art performance on the Human3.6M and AMASS datasets."

links:
    - name: Project Page
      link: /publications/skeletondiffusion/
    - name: Paper
      link: https://arxiv.org/abs/2501.06035 
      style: "bi bi-file-earmark-richtext"
    - name: Code
      link: https://github.com/Ceveloper/SkeletonDiffusion/tree/main
      style: "bi bi-github"
    - name: Video
      link: https://www.youtube.com/watch?v=W9GzdDXN41M
      style: "bi bi-youtube"
    - name: Poster
      link: https://cvpr.thecvf.com/virtual/2025/poster/33243
    # - name: Video
    #   link: # after video was created
    #   style: "bi bi-youtube"

citation: '@inproceedings{curreli2025nonisotropic,
  title={Nonisotropic Gaussian Diffusion for Realistic 3D Human Motion Prediction},
  author={Cecilia Curreli and Dominik Muhle and Abhishek Saroha and Zhenzhang Ye and Riccardo Marin and Daniel Cremers},
  booktitle = {Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition},
  year={2025}
}'
# author       = {Baez, John C. and Lauda, Aaron D.},
# date         = {2004-10-27},
# version      = 3,
# langid       = {english},
# langidopts   = {variant=american},
# eprinttype   = {arxiv},
# eprint       = {math/0307200v3},

acknowledgements: 'This work was supported by the ERC Advanced Grant SIMULACRON. Thanks to Dr. Almut Sophia Koepke, Yuesong Shen and Shenhan Qian for the proofreading and feedback, Lu Sang for the discussion, Stefania Zunino and the whole CVG team for the support.'
---
{% include_relative content.html %}