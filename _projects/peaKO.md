---
layout: page
title: peaKO
description: Finding transcription factor binding motifs using knockout controls
img: assets/img/project_images/peako_fig1.jpeg
importance: 1
category: work
related_publications: peaKO
---

<style>
.custom-fixed-image {
    height: 300px;
    width: 100%;
    object-fit: contain;
    object-position: center;
    background-color: white;
}
</style>

<style>
.custom-fixed-short-image {
    height: 150px;
    width: 100%;
    object-fit: contain;
    object-position: center;
    background-color: white;
}
</style>

<b>PeaKO is a computational tool to identify motifs relevant to ChIP-seq experiments by combining two differential analysis approaches.</b> It often improves elucidation of the target motif over other methods and highlights the benefits of knockout controls. <a href="https://hoffmanlab.org/proj/peako/">Click here for a detailed description page.</a>

    ---
    Denisko D, Viner C, Hoffman MM. 
    Motif elucidation in ChIP-seq datasets with a knockout control. 
    Bioinformatics Advances, 2023. 
    Available from: https://doi.org/10.1093/bioadv/vbad031.
    ---

Quick links: 
<a href="https://github.com/hoffmangroup/peako" target="_blank">
  <i class="fab fa-github fa-lg"></i>
</a>
<a href="https://hoffmanlab.org/proj/peako/" target="_blank">
  <i class="fas fa-globe fa-lg"></i>
</a>
<a href="https://pypi.org/project/peako/" target="_blank">
  <i class="fab fa-python fa-lg"></i>
</a>

I developed peaKO during my MSc at the University of Toronto. I used `Snakemake` to write the main workflow that ties together a series of `Python` scripts. It works with `Slurm` scheduling or just locally. The name "peaKO" (pee-koh) comes from "peak" and "KO" (knockout), but it's also a reference to the name my grandma would have chosen for a hedgehog, as in "orange pekoe" :)

[//]: # "style='height: 400px; object-fit: cover;'"

[//]: # "To generate padded images: convert peako_fig1.jpeg -bordercolor white -border 50x50 peako_fig1_border.jpeg"

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        <a href="/assets/img/project_images/peako_fig1_border.jpeg" target="_blank">
            {% include figure.html 
                path="assets/img/project_images/peako_fig1.jpeg" 
                title="peaKO Figure 1" 
                class="custom-fixed-image img-fluid rounded z-depth-1" %}
        </a>
    </div>
    <div class="col-sm-4 mt-3 mt-md-0">
        <a href="/assets/img/project_images/peako_fig3_border.jpeg" target="_blank">
            {% include figure.html 
                path="assets/img/project_images/peako_fig3.jpeg" 
                title="peaKO Figure 3" 
                class="custom-fixed-image img-fluid rounded z-depth-1" %}
        </a>
    </div>
</div>
<div class="caption">
    Overview of peaKO (left) and the similarity of <i>de novo</i> motifs to canonical known motifs (right).
</div>

<b>Longer description:</b> PeaKO is a computational method for identifying transcription factor binding motifs from wild-type/knockout paired ChIP-seq datasets. PeaKO optimizes motif analyses by implementing a dual-pipeline approach. The first pipeline incorporates differential motif analysis, while the second incorporates differential peak calling. I combined these pipelines to select for motifs that both have consistent matches within peaks and fall within regions of significant read pileup. PeaKO computes a new metric based on the proportion of overlapping peaks between both pipelines, with overlaps interpreted as genuine binding events. PeaKO uses this metric to rank a collection of known or <i>de novo</i> motifs, where top-ranked motifs are thought to be relevant to the ChIP-seq experiment.

<div class="row justify-content-sm-center">
    <div class="col-sm mt-3 mt-md-0">
        <a href="/assets/img/project_images/peako_fig2_border.jpeg" target="_blank">
            {% include figure.html 
                path="assets/img/project_images/peako_fig2.jpeg" 
                title="peaKO Figure 2" 
                class="custom-fixed-short-image img-fluid rounded z-depth-1" %}
        </a>
    </div>
    <div class="col-sm mt-3 mt-md-0">
        <a href="/assets/img/project_images/peako_fig4_border.jpeg" target="_blank">
            {% include figure.html 
                path="assets/img/project_images/peako_fig4.jpeg" 
                title="peaKO Figure 4" 
                class="custom-fixed-short-image img-fluid rounded z-depth-1" %}
        </a>
    </div>
    <div class="col-sm mt-3 mt-md-0">
        <a href="/assets/img/project_images/peako_fig6_border.jpeg" target="_blank">
            {% include figure.html 
                path="assets/img/project_images/peako_fig6.jpeg" 
                title="peaKO Figure 6" 
                class="custom-fixed-short-image img-fluid rounded z-depth-1" %}
        </a>
    </div>
</div>
<div class="caption">
    Comparing motif rankings across methods (left), highlighting an example (GATA3 transcription factor) in which peaKO outperforms other methods (centre), using input controls instead of knockout controls, which give rise to worse rankings (right).
</div>

To install peaKO, follow the <a href="https://github.com/hoffmangroup/peako">steps on GitHub</a>:

{% raw %}
```bash
conda create --name peako
conda activate peako # or source activate peako
conda install python=3.7
conda install -c anaconda beautifulsoup4=4.7 pandas
conda install -c bioconda -c conda-forge -c anaconda snakemake-minimal flake8 pathlib2 ipython twine
conda install -c bioconda pybedtools

python3 -m pip install peako

peako --help

# Usage: peako <outdir> <wt-bam> <ko-bam> <organism> <chr-sizes> <trf-masked-genome> <motif-database> [options]
```
{% endraw %}
