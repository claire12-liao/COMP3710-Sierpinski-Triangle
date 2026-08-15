# COMP3710 Sierpinski Triangle

> A GPU-accelerated implementation and analysis of the Sierpinski Triangle using PyTorch for COMP3710 Lab 1.

[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/claire12-liao/COMP3710-Sierpinski-Triangle/blob/main/COMP3710_Sierpinski_Triangle.ipynb)

---

## Project Overview

The Sierpinski Triangle is a self-similar fractal created by repeatedly mapping points towards the three vertices of an equilateral triangle.

This project uses vectorised PyTorch operations to generate the point coordinates. When CUDA is available, the calculations are performed on the GPU.

For recursion depth `d`, the number of generated points is `3^d`. For example, depth 10 produces `3^10 = 59,049` points.

## Main Features

| Feature | Description |
|---|---|
| GPU acceleration | Uses CUDA when a compatible GPU is available |
| Vectorised generation | Uses PyTorch broadcasting to process many coordinates together |
| Depth comparison | Shows the development of the fractal at different recursion depths |
| Colour visualisation | Maps colour to horizontal and vertical coordinates |
| Dimension analysis | Estimates the box-counting dimension |
| Performance analysis | Compares CPU and GPU execution times |

## Parallel Implementation

At each recursion level, every existing point generates three new points:

`new_point = (existing_point + triangle_vertex) / 2`

PyTorch broadcasting combines the existing points with all three vertices:

| Tensor | Shape |
|---|---|
| Existing points | `[N, 1, 2]` |
| Triangle vertices | `[1, 3, 2]` |
| Broadcast result | `[N, 3, 2]` |
| Reshaped output | `[3N, 2]` |

This avoids a Python loop over individual points and allows a large number of coordinates to be processed together on the GPU.

## Results

### Box-counting Dimension

| Measurement | Result |
|---|---:|
| Estimated dimension | 1.5838 |
| Theoretical dimension | 1.5850 |
| Absolute error | 0.0012 |

The theoretical dimension is `D = log(3) / log(2)`. The small error is caused by the finite recursion depth and limited box sizes used in the numerical experiment.

### CPU and GPU Performance

The benchmark was performed on a Tesla T4 GPU using five repetitions.

| Depth | Points | CPU Time (ms) | GPU Time (ms) | Speedup |
|---:|---:|---:|---:|---:|
| 8 | 6,561 | 0.474 | 0.613 | 0.77x |
| 10 | 59,049 | 1.763 | 0.453 | 3.89x |
| 12 | 531,441 | 17.690 | 0.549 | 32.20x |
| 14 | 4,782,969 | 171.228 | 1.724 | 99.35x |

The GPU is slower for the smallest workload because of setup and synchronisation overhead. As the workload increases, GPU parallelism provides a much larger performance improvement.

## Requirements

- Python 3
- PyTorch
- NumPy
- Matplotlib
- CUDA-compatible GPU (recommended but not required)

The notebook automatically uses the CPU if CUDA is unavailable.

## How to Run

1. Click the **Open in Colab** button at the top of this page.
2. Select a GPU runtime in Google Colab.
3. Run all notebook cells from top to bottom.
4. Review the fractal images, dimension analysis and performance results.

## Repository Files

| File | Description |
|---|---|
| `COMP3710_Sierpinski_Triangle.ipynb` | Main implementation and experiments |
| `AI_USAGE.md` | Declaration of AI assistance |
| `README.md` | Project documentation |
| `LICENSE` | MIT License |
| `.gitignore` | Ignored Python files |

## AI Assistance

ChatGPT was used as a learning and development assistant. Details of its use and my verification process are recorded in [AI_USAGE.md](AI_USAGE.md).
