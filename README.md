# 👨‍🔬🧑‍🔬👩‍🔬 Scientific Website Template

Welcome to the repository of my website. The idea is to provide a quick and easy to use solution that requires little html or css skills by providing a usefull template that only needs to be filled with content. It follows the style currently popular for project pages in computer vision. It is based on the [minimal mistakes](https://github.com/mmistakes/minimal-mistakes) theme for [jeykll](https://jekyllrb.com) and extends it to a template for scientific project pages and an overview of publications.

## 📇 Using the template

If you want to use and modify the template, you are more than welcome to do so. The following tries to guide you through the process of setting up your own webpage with this template using `github.io`. This process is far from perfect and reflects my very limited understanding of this process. I am happy for any suggestions for improvement. It also acts as an overview of the different parts of this repository.

### 💾 Copying the repository

You can either clone or fork this repository from the github webpage. The repository should already include all the content and style files you need or install them if necessary.

### 🏃‍♂️ Running it locally

As this template uses [jeykll](https://jekyllrb.com) it is easy to deploy locally and test the website, before pushing any changes. To setup jekyll locally, follow the [instructions](https://jekyllrb.com/docs/installation/) for your operating system. If you have setup **ruby** and **jekyll**, you can navigate to this directory and run `jekyll serve`. You can work on this repository in the meantime. Refreshing the website will update the content.

### 📡 On github

If you have cloned the repository instead of forking it, you need to change the location to the remote repository on your github profile. After setting up the remote repository, you have to create a workflow to deploy the website. You can either create a manual workflow (which didn't work for me), or use the **pages** option under **settings**.

## 🔍 Understanding the template

### 👀 Overview

The template is currently divided into

- a front page: where you can introduce yourself and share any exiting news that you have
- the meta data: stores all the information about the authors and affiliations
- a publication overview: a listing of all the exiting projects you took part in
- the individual project pages: provide more details about your projects on these pages

Of course it is possible to add more pages such as a CV. For this, you must get familiar with jekyll itself. But it is not too difficult.

### 🧑 The front page

The landing page of your website. Share any information you want to share, give a short introduction and present any exiting news. You should also replace the image in `assets/images/profile-photo.jpg` with a picture of you. The information presented on the page is found in `_config.yaml`, `_layouts/welcome.hmtl`, and `_data/news.yml`.

`_config.yaml` includes the information presented on the left side of the front page. This includes your

- name
- file name for your photo
- short bio
- links to social media containing a `label`, `icon`, and `url`

Apart from that `_config.yaml` includes informations about the theme used. ❗ Only touch this if you know what you are doing.

`_layouts/welcome.hmtl` fills the right column with content and imports the news from `_data/news.yml`. It is a *jekyll* so, either change it carefully or familirize yourself with the *jekyll* proceedure.

`_data/news.yml` contains the news entries you want to share ordered by date. It is a simple `.yml` file with a list. Each list entry contains

- date
- description

So nothing fancy.

### Ⓜ️ The meta data

Are you tired of always searching for peoples website or the names of affiliations. Is if **TU Munich**, **Technical University Munich**, or **Technical University of Munich**? In the files `_data/affiliations.yaml`, `_data/authors_external.yaml`, and `_data/authors_internal.yaml` you store the information about you and your co-authors and their affiliations so you avoid mistakes in the future.

For authors, the scheme is

```yaml
{shortname}:
  first_name: ...
  last_name: ...
  website: (optional)
  is_me: true # to mark yourself
```

For affiliations it is:

```yaml
{shortname}:
  long: ...
  short: ...
```

### 🖼️ The publication overview

This collects all your publications to a central place. It lists all the publications from the newest to the oldest. The layout is defined in `_pages/publication_overview.html`. However, the idea is, that you do not need to add anything manually. The layout automatically gets all the relevant information from the individual publications in `_publications/*` and formats them automatically with title, authors, venue. It even allows for a thumbnail with mouseover that even supports video sequences.

### 📖 The individual publications

This is where you should spend most of your time. Every publication is a subdirectory of `_publications` containing at least an `index.md` file. However, if you want to also have a proper publication page, you should also add a `content.hmtl` file and an assets folder. The layout of the header for the publications is defined in `_layouts/publications.html`.

`index.md` contains all the meta information about publications that is used in `_layouts/publications.html` to generate the project page. `_layouts/publications.html` itself uses smaller snippets from `_include` to generate a header, citation, and acknowledgements. We show an example file to introduce the different options

```yaml
layout: publications # defines the layout used for this publication. Leave it as publications or create your own layout under _layouts
permalink: /publications/pnec/ # defines the link used to publish the website
date: 2022_05_26 # determines sorting just take the date of the first publication as YYYY_MM_DD
image: assets/teaser.pdf # defines the asset used in the thumbnail for the publication overview. Doesn't have to be a local file, can also use a file from another repository, e.g. if the actual project page is somewhere external
image_mouseover: assets/trajectory_8.pdf # defines the mouseover asset. Also supports .mp4 otherwise same as above

title: "Probabilistic Normal Epipolar Constraint for Frame-To-Frame Rotation Optimization under Uncertain Feature Positions" # Should be self-explanatory
venue: CVPR, 2022 # Should be self-explanatory
authors: # A list of authors with their affiliations (based on the affiliations list at the bottom). As affiliations are not constant, this is one of the easiest solutions. Add equal_contribution to denote equal contribution
  - name: dominikmuhle
    affiliations: "1"
    equal_contribution: True
  - name: lukaskoestler
    affiliations: "1"
    equal_contribution: True
  - name: nikodemmel
    affiliations: "1"
  - name: florianbernard
    affiliations: "1,2"
  - name: danielcremers
    affiliations: "1"
  
affiliations: # The list of the affiliations based on the numbers above. Also denote whether you want the short or long version.
  - name: tum
    length: short
  - name: bonn
    length: short
  
description: "We propose a probabilistic extension to the normal epipolar constraint (NEC) which we call the PNEC. It allows to account for keypoint position uncertainty in images to produce more accurate frame to frame pose estimates." # A short description for the project overview

links: # A list of links you want add to your publication e.g. paper, code, video, poster, etc. The project page is mandatory and can either be a local link or an external link. This is used only on the overview page. You can add symbols to your links with the style attribute. However, I have no idea where to look this up.
  - name: Project Page
    link: /publications/pnec/
  - name: Paper
    link: https://arxiv.org/abs/2204.02256
    style: "bi bi-file-earmark-richtext"
  - name: Code
    link: https://github.com/tum-vision/pnec
    style: "bi bi-github"
  - name: Video
    link: https://youtu.be/YraCHnR5dmg
    style: "bi bi-youtube"
citation: '@inproceedings{muhle2022pnec, 
  author = {D Muhle and L Koestler and N Demmel and F Bernard and D Cremers},
  title = {The Probabilistic Normal Epipolar Constraint for Frame-To-Frame Rotation Optimization under Uncertain Feature Positions}, 
  booktitle = {IEEE Conference on Computer Vision and Pattern Recognition (CVPR)},
  year = {2022},
}' # (Optional) A citation, that is automatically formatted with linebreaks and tabs. That took me a very long time. If provided, it will create a citation section a handy citation buttion that will copy this to the clipboard on the project page and the overview. 
acknowledgements: 'We thank our colleagues, especially Florian Hofherr, for proofreading and helpful discussions. This work was supported by the ERC Advanced Grant SIMULACRON and by the Munich Center for Machine Learning.' # (Optional) Will add a acknowledgements section on the project page. 
```

The rest of the project page you have to define in the `content.html` file, where the template cannot help you anymore execpt to provide you with examples. More, maybe later.

### Includes

Includes are supposed to provide reusable templates to make content sections more consistent and easy to use. One example would be `comparison-slider.html`. This allows you to overlay two images with a slider reactive to the mouse. In can be used in the `content.html` file with

```html
<...>
  {% include comparison_slider.html 
    first_img="{path to first image}" 
    second_img="{path to second image}" 
    (optional first_caption="{caption text}")
    (optional second_caption="{caption text}")
    (optional caption="{caption text}")
  %}
</...>

<script defer src="/js/slider-component.js"></script>
```

Jekyll allows to pass arguments to the includes that can be used in the `hmtl` code as you can see in the example. In this case, since a `.js` script is needed for this component, we have to add the script at the end of our `content.html` as well. Also be mindful, that the `slider-component.css` file is alread included in the `publications.html` file. (There should probably be a cleaner solution for this.)

If you want to add your own reusable components you can just add them to the `includes` directory. (Cleaning up would be important at some point.)
