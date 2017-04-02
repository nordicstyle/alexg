---
title: "Have We Forgotten about Geometry in Computer Vision?"
layout: single
read_time: true
comments: true
share: true
author_profile: true
header:
  overlay_color: "#000"
  overlay_filter: "0.5"
  overlay_image: /assets/images/kings_college.jpg
excerpt: "<br><br><br>"
categories:
  - computer_vision
tags:
  - computer vision
  - deep learning
  - scene understanding
  - robotics
---

_Deep learning_ has revolutionised computer vision. 
There are not many problems today where the default solution is a deep convolutional neural network -- they tend to work fairly well out of the box!
However, deep learning models are largely big black-boxes. There are a lot of things we don't understand about them.
In this blog post I am going to argue that people often apply deep learning models naively to computer vision problems.
A lot of low hanging fruit is being claimed by researchers with the sweeping effectiveness of deep learning.

I think a really good example is with some work from the first year of my PhD. PoseNet was an algorithm I developed for learning camera pose with deep learning. 
The problem had been studied for decades in computer vision, and had some really nice surrounding theory.
However, as a naive first year graduate student, I applied a deep learning model end-to-end to the problem and obtained some nice results.
However, at the end of the post I will describe some recent follow on work which looks at this problem from a more theoretical, geometry based approach.

I think we're running out of low hanging fruit - or problems we can solve with a simple deep learning API.
I think many of the next advances in deep learning will come from insights to geometry.

## What do I mean by geometry?

Geometry involves motion, depth, shape and pose of the world around us.
It is based on continuous valued representation, rather than discrete semantic labels.

{% capture fig_img %}
![Foo]({{ "/assets/images/reconstruction_cambridge.jpg" | absolute_url }})
{% endcapture %}

<figure>
  {{ fig_img | markdownify | remove: "<p>" | remove: "</p>" }}
  <figcaption>A structure from motion reconstruction of the geometry around central Cambridge, UK - from my phone's video camera.</figcaption>
</figure>

## Aren't semantics enough?

The problem with relying just on semantics to design a representation of the world, is that semantics are defined by humans. 
It is essential for an AI system to understand semantics to form an interface with humanity. However, because semantics are defined by humans, it is also likely that these representations aren't optimal.
Learning directly from the observed geometry in the world might be more natural.

The second problem with semantics is that they are discrete qualities. An object might be classified as a 'car'.
But, really it is somewhere on a continuous and hierarchical scale, spanning multiple labels such as 'vehicle', 'car' and 'van'.
Geometry does not have this kind of ambiguity - it is formed of continuous real values.

{% capture fig_img %}
![Foo]({{ "/assets/images/segmentation.png" | absolute_url }})
{% endcapture %}

<figure>
  {{ fig_img | markdownify | remove: "<p>" | remove: "</p>" }}
  <figcaption>A machine's semantic view of the world (a.k.a. <a href='http://mi.eng.cam.ac.uk/projects/segnet/'>SegNet</a>). Each colour represents a different semantic class - such as road, pedestrian, sign, etc.</figcaption>
</figure>

## Why use geometry in deep learning

I can think of two very important areas of research which would benefit from geometry. In fact, Yann LeCun mentioned two of these areas in the top three most important problems to work on in AI.

Unsupervised learning.
When we're born - we first learn geometry largely unsupervised. Then semantics, in a weakly supervised fashion.
One of my [favourite papers](https://arxiv.org/abs/1603.04992) last year showed how to use geometry to learn depth with unsupervised training.

Memory. Memory research largely focuses on Q&A tasks. I'm excited about using Localisation and SLAM to develop deep learning memory architectures! 

## Examples in my recent research

I'd like to conclude this blog post by giving some concrete examples of how we can use geometry in deep learning from my own research.

### Learning to relocalise with PoseNet

I'm going to be presenting 

![image-center]({{ site.url }}{{ site.baseurl }}/assets/images/research/localisation.jpg){: .align-center}

### Predicting depth with stereo vision

The second example is in stereo vision -- estimating depth from binocular vision. 
I had the chance to work on this problem while spending a fantastic summer with [Skydio](https://www.skydio.com), working on the most [advanced drones in the world](https://www.technologyreview.com/s/604009/ai-powered-drone-will-follow-you-around-and-take-pictures/).

Stereo algorithms typically estimate the difference in the horizontal position of an object between a rectified pair of stereo images. 
This is known as disparity, which is inversely proportional to the scene depth at the corresponding pixel location. 
So, essentially it can be reduced to a matching problem - find the correspondences between objects in your left and right image and you can compute depth.

The top performing algorithms in stereo predominantly use deep learning, however only for creating features. The matching and regularisation steps required to produce depth estimates are largely still done by hand.

geometry + deep learning.

Here's an overview of the architecture:

![image-center]({{ site.url }}{{ site.baseurl }}/assets/images/research/deep_stereo.png){: .align-center}

Tricks were formulating it as a regression problem with a soft argmin operation over the cost volume. More details can be found in the paper [here](https://arxiv.org/pdf/1703.04309.pdf).

## Conclusions

I think the take home messages from this post are:

  * it is worth understanding classical approaches to computer vision problems (especially if you come from a machine learning or data science background)
  * learning complicated representations with deep learning is easier and more effective if the architecture can be structured to leverage the geometric properties of the problem

