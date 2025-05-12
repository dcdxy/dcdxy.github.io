---
layout: page
title: "peaKO"
description: Finding transcription factor binding motifs using knockout controls
img: assets/img/project_images/peako_fig1.jpeg
importance: 1
category: work
related_publications: peaKO
---

<b>PeaKO is a computational tool to identify motifs relevant to ChIP-seq experiments by combining two differential analysis approaches.</b> It often improves elucidation of the target motif over other methods and highlights the benefits of knockout controls. <a href="https://hoffmanlab.org/proj/peako/">Click here for a detailed description page.</a>

    ---
    Denisko D, Viner C, Hoffman MM. 
    Motif elucidation in ChIP-seq datasets with a knockout control. 
    Bioinformatics Advances, 2023. 
    Available from: https://doi.org/10.1093/bioadv/vbad031.
    ---

I developed peaKO during my MSc at the University of Toronto. I used `Snakemake` to write the main workflow that ties together a series of `Python` scripts. It works with `Slurm` scheduling or just locally. The name "peaKO" (pee-koh) comes from "peak" and "KO" (knockout), but it's also a reference to the name my grandma would have chosen for a hedgehog, as in "orange pekoe" :)

[//]: # "style='height: 400px; object-fit: cover;'"

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.html path="assets/img/project_images/peako_fig1.jpeg" title="peaKO Figure 1" class="img-fluid rounded z-depth-1" style="height: 400px; object-fit: cover;" %}
    </div>
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.html path="assets/img/project_images/peako_fig3.jpeg" title="peaKO Figure 3" class="img-fluid rounded z-depth-1" style="height: 400px; object-fit: cover;" %}
    </div>
</div>
<div class="caption">
    Overview of peaKO (left) and the similarity of <i>de novo</i> motifs to canonical known motifs (right).
</div>

<b>Longer description:</b> PeaKO is a computational method for identifying transcription factor binding motifs from wild-type/knockout paired ChIP-seq datasets. PeaKO optimizes motif analyses by implementing a dual-pipeline approach. The first pipeline incorporates differential motif analysis, while the second incorporates differential peak calling. We combined these pipelines to select for motifs that both have consistent matches within peaks and fall within regions of significant read pileup. PeaKO computes a new metric based on the proportion of overlapping peaks between both pipelines, with overlaps interpreted as genuine binding events. PeaKO uses this metric to rank a collection of known or <i>de novo</i> motifs, where top-ranked motifs are thought to be relevant to the ChIP-seq experiment.

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.html 
            path="assets/img/project_images/peako_fig1.jpeg" 
            title="peaKO Figure 1" 
            class="custom-fixed-image img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.html 
            path="assets/img/project_images/peako_fig3.jpeg" 
            title="peaKO Figure 3" 
            class="custom-fixed-image img-fluid rounded z-depth-1" %}
    </div>
</div>

<style>
.custom-fixed-image {
    height: 300px;
    width: 100%;
    object-fit: cover;
    object-position: center;
}
</style>


<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/project_images/peako_fig2.jpeg" title="peaKO Figure 2" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/project_images/peako_fig4.jpeg" title="peaKO Figure 4" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/project_images/peako_fig6.jpeg" title="peaKO Figure 6" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

The code is simple.
Just wrap your images with `<div class="col-sm">` and place them inside `<div class="row">` (read more about the <a href="https://getbootstrap.com/docs/4.4/layout/grid/">Bootstrap Grid</a> system).
To make images responsive, add `img-fluid` class to each; for rounded corners and shadows use `rounded` and `z-depth-1` classes.
Here's the code for the last row of images above:

{% raw %}
```html
<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.html path="assets/img/6.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.html path="assets/img/11.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
```
{% endraw %}
