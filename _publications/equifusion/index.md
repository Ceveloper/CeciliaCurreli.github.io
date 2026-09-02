---
layout: publications
permalink: /publications/equifusion/
date: 2026_07_13 # determines sorting just take the date of the first publication as YYYY_MM_DD
image: /assets/teaser_animated_social.gif
# icon: /assets/favicon.ico

title: "EquiFusion: Kinematics-Agnostic Human Motion Prediction via Equivariant Latent Diffusion"
venue: ECCV 2026
authors:
  - name: ceciliacurreli
    affiliations: "1,2"
  - name: florianhofherr
    affiliations: "1,2"
  - name: dominikmuhle
    affiliations: "1,2"
  - name: abhisheksaroha
    affiliations: "1,2"
  - name: riccardomarin
    affiliations: "1,2"
  - name: danielcremers
    affiliations: "1,2"
affiliations:
  - name: tum
    length: long
  - name: mcml
    length: long


description: "EquiFusion is the first kinematics-agnostic model for Stochastic Human Motion Prediction: a permutation-equivariant latent diffusion model that reads the skeleton connectivity as input, unlocking multi-dataset training and zero-shot inference on unseen kinematics, occluded limbs, and targeted limb generation. EquiFusion achieves state-of-the-art results on standard benchmarks with 75% fewer parameters than the closest competitor."

links:
    - name: Project Page
      link: /publications/equifusion/
    - name: Paper
      link: https://arxiv.org/abs/2607.10984
      style: "bi bi-file-earmark-richtext"
    # Code button hidden until the repository is public — a dead link costs more than a missing button.
    - name: Code
      link: https://github.com/Ceveloper/EquiFusion 
    #   style: "bi bi-github"
    # - name: Video
    #   link: https://www.youtube.com/watch?v=XXXXXXXXXXX
    #   style: "bi bi-youtube"
    # - name: Poster
    #   link: /publications/equifusion/assets/eccv26_equifusion_poster.pdf
    #   style: "bi bi-file-earmark-pdf"

citation: '@inproceedings{curreli2026equifusion, title={EquiFusion: Kinematics-Agnostic Human Motion Prediction via Equivariant Latent Diffusion}, author={Cecilia Curreli and Florian Hofherr and Dominik Muhle and Abhishek Saroha and Riccardo Marin and Daniel Cremers}, booktitle={European Conference on Computer Vision}, year={2026}, organization={Springer}'
# TODO once proceedings are out switch to @InProceedings with booktitle={Proceedings of the European Conference on Computer Vision (ECCV)}

acknowledgements: 'This work was supported by the European Research Council (ERC) Advanced Grant SIMULACRON. Thanks to Maolin Gao and Felix Wimbauer for proofreading, Thomas Dagès for the detailed and constructive suggestions, Stefania Zunino and the CVG team for their unwavering support.'
---
{% include_relative content.html %}
