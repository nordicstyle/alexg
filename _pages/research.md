---
layout: single
read_time: false
comments: false
share: false
title: Research Highlights
permalink: /research/
header:
  overlay_color: "#000"
  overlay_filter: "0.5"
  overlay_image: /assets/images/trinity.jpg
  caption: "Photo: [Olly McMillan](https://www.youtube.com/watch?v=kQkZeXHfgwA&t=1s)"
excerpt: "Geometry and Uncertainty in Deep Learning for Computer Vision<br><br><br>"
gallery_uncertainty:
  - image_path: /assets/images/research/input.png
    alt: "Black and grays with a hint of green"
  - image_path: /assets/images/research/segmentation.png
    alt: "Made for open text placement"
  - image_path: /assets/images/research/uncertainty.jpg
    alt: "Fog in the trees"
---

# Bayesian Deep Learning

Deep learning is great for achieving state-of-the-art results - however these models can't understand what they don't know.
Bayesian deep learning is a very exciting framework for understanding the model uncertainty.
[This paper](https://arxiv.org/pdf/1703.04977.pdf) is an introduction to Bayesian deep learning for computer vision. 
I've also found it useful for [localisation](http://arxiv.org/abs/1509.05909) and [scene understanding](http://arxiv.org/abs/1511.02680).

{% include gallery id="gallery_uncertainty" caption="Bayesian deep learning for semantic segmentation. From left to right: input image, semantic segmentaion and model uncertainty." %}

---

# Scene Understanding

Scene understanding is a critical task in computer vision which requires understanding geometry and semantics. 
Initially, I worked on a semantic segmentation algorithm called [SegNet](http://mi.eng.cam.ac.uk/projects/segnet/). 
More recently, I've been interested in learning depth, instance and semantic segmentation from a unified architecture.

![image-center]({{ site.url }}{{ site.baseurl }}/assets/images/research/multitask.jpg){: .align-center}

---

# Localisation

PoseNet is an algorithm for relocalisation - estimating the position and orientation of the camera from an image within a previously explored area. 
It works over large outdoor urban environments or inside buildings. 
It takes only 5ms to do this from a single colour image, [here is a demo](http://mi.eng.cam.ac.uk/projects/relocalisation/).

![image-center]({{ site.url }}{{ site.baseurl }}/assets/images/research/localisation.jpg){: .align-center}

---

# Other Projects

Some more details of other projects, including an autonomous drone and augmented reality, [can be found here](/other_projects/).
