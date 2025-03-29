---
#layout: single
title: "Parallelized Mandelbrot Generator using OpenMP"
date: 2025-03-29
categories: projects
excerpt: "Parallelizing the generation of the Mandelbrot set on an x86 CPU using OpenMP"
---
# Parallelized Mandelbrot Set Generator with OpenMP

<img src="/assets/images/posts/mandelbrot-generator/image.png" alt="Mandelbrot Image Black & White" width="300">
<img src="/assets/images/posts/mandelbrot-generator/image-color.png" alt="Mandelbrot Image Color" width="300">

## Introduction

A Mandelbrot set is defined as the set of all complex numbers  $\{c\}$ for which the generator function:

$f_c(z) = z^2 + c$

remains bounded (i.e., does not diverge to $\pm \infty$). We start with $z=0$ and iteratively evaluate $f_c$ as follows:

$[f_c(0), f_c(f_c(0)), f_c(f_c(f_c(0))),\dots]$

## Defining Divergence

Traditionally, divergence is defined by a threshold of the magnitude of the current element in the sequence. For example, if we choose a threshold of $f_{max} = 10$, then the sequence diverges at the $i^{th}$ iteration if $|f_c(i)| > f_{max} = 10$.

## Methods

### Approach A: Fine-Grained Parallelization

- Pixel-level parallelization, each thread evolves the Mandelbrot set for differnt starting values $c$ in the complex plane.
- Poor scaling due to critical access of shared data buffer.

### Approach B: Parallel Frame Generation for Zoom Animation

- Frame-by-frame parallelization when generating multiple frames of the Mandelbrot set at different scales to create a movie (i.e. zooming into one point of the plane).
- Each frame is assigned to a different thread for parallel processing.
- The generated frames are then compiled into a video.
- Much more efficient scaling, each thread works on independent chunck of data

## Generated Outputs

### Mandelbrot Image

<img src="/assets/images/posts/mandelbrot-generator/image-color.png" alt="Mandelbrot Image Color" width="300">

### Mandelbrot Zoom Animation

Generated animation of the Mandelbrot set zooming into specific regions:

- **Seahorse Valley** $(-0.743643887037151 + 0.131825904205330i)$: [Download Seahorse.mp4](figures/videos/seahorse-100.mp4)

    <img src="/assets/images/posts/mandelbrot-generator/seahorse-100-color.gif" alt="Seahorse Valley GIF" width="300">


- **Elephant Valley** $(0.282 + 0.5307i)$: [Download Elephant.mp4](figures/videos/elephant-100.mp4)

    <img src="/assets/images/posts/mandelbrot-generator/elephant-100-color.gif" alt="Elephant Valley GIF" width="300">

- **Feigenbaum Point** $(-1.401155 + 0i)$: [Download Feigenbaum.mp4](figures/videos/feigenbaum-100.mp4)

    <img src="/assets/images/posts/mandelbrot-generator/feigenbaum-100-color.gif" alt="Feigenbaum Point GIF" width="300">


The colormap uses the [Escape-Time Algorithm](https://en.wikipedia.org/wiki/Plotting_algorithms_for_the_Mandelbrot_set) to provide a cool visualization of the complex plane. 

## Running the Project

See my [project Github](https://github.com/RajeevBotadra/Parallel-Mandelbrot-Generator) for source code.

## Future Improvements

- Implement GPU acceleration using CUDA.
- Optimize frame generation with better load balancing.
- Enable dynamic thresholding to improve visualization quality.
- Reuse computation between frames.

