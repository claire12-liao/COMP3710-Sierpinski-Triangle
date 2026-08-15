# AI Use Declaration

## Project Overview

For this project, I used PyTorch to implement and analyse a GPU-accelerated Sierpinski Triangle.

I used ChatGPT as a learning and development assistant. It helped me understand the Part 3 requirements, compare possible fractal topics, develop the initial PyTorch structure, plan experiments and improve the project documentation.

I completed the project step by step. I selected the topic, obtained approval from the teaching staff, created the public GitHub repository, configured Google Colab, ran every notebook section and checked the results myself.

## Project-Related AI Interactions

### 1. Understanding the Requirements and Selecting a Fractal

**My prompt/request:**

“Explain the Part 3 requirements carefully and suggest a fractal that is simpler to implement and explain during the Demo.”

**AI output and reasoning:**

ChatGPT explained that the project required a new GitHub repository, a substantially different fractal, meaningful use of PyTorch, reasonable parallelism and additional analysis when AI was used.

It compared several possible fractals and recommended the Sierpinski Triangle because it has a clear recursive structure, a known theoretical dimension and a suitable vectorised implementation.

**My contribution:**

I considered the suggestion, selected the Sierpinski Triangle and obtained approval from the teaching staff before starting.

### 2. PyTorch and GPU Implementation

**My prompt/request:**

“Guide me step by step to implement the approved Sierpinski Triangle using PyTorch and the GPU.”

**AI output and reasoning:**

ChatGPT suggested representing the triangle vertices and generated points as PyTorch tensors. At each recursion level, every existing point is moved halfway towards each of the three vertices.

PyTorch broadcasting was used to combine tensors with shapes `[N, 1, 2]` and `[1, 3, 2]`. This produces three new points from every existing point and allows many coordinates to be processed together on the GPU.

The recursion levels remain sequential because each level depends on the points produced by the previous level.

**My contribution and verification:**

I ran the implementation on a Tesla T4 GPU and confirmed that CUDA was available. At recursion depth 10, the program generated 59,049 points, matching the expected value of `3^10`.

### 3. Code Comments and Explanation

**My prompt/request:**

“Add some Chinese and English comments to the code so that I can understand and explain it during the Demo.”

**AI output and reasoning:**

ChatGPT suggested bilingual comments and docstrings explaining the tensor shapes, broadcasting, midpoint calculation and device selection.

**My contribution:**

I added the comments to the notebook, ran the code again and confirmed that the comments did not change the program’s behaviour.

### 4. Visualisation Experiments

**My prompt/request:**

“Help me compare different recursion depths and create simple colour visualisations.”

**AI output and reasoning:**

ChatGPT suggested comparing several recursion depths to demonstrate the development of the fractal. It also suggested mapping colour to the horizontal and vertical coordinates.

**My contribution and verification:**

I generated and checked the depth comparison plots. I also produced two colour visualisations: one based on the x-coordinate and another based on the y-coordinate.

### 5. Fractal Dimension Analysis

**My prompt/request:**

“Help me add a substantial analysis of the Sierpinski Triangle using the box-counting dimension.”

**AI output and reasoning:**

ChatGPT explained the box-counting method and suggested counting occupied boxes at different box sizes. A linear fit of `log(number of occupied boxes)` against `log(1 / box size)` was used to estimate the dimension.

The theoretical dimension is:

`log(3) / log(2) ≈ 1.5850`

**My contribution and verification:**

I ran the analysis and obtained an estimated dimension of 1.5838. The absolute error from the theoretical value was approximately 0.0012, so the result was consistent with the expected dimension.

### 6. CPU and GPU Performance Analysis

**My prompt/request:**

“Help me compare the CPU and GPU execution times fairly.”

**AI output and reasoning:**

ChatGPT suggested using repeated measurements, a GPU warm-up and CUDA synchronisation around the timed GPU operations. It also recommended timing the tensor-generation calculation separately from plotting and transferring results to the CPU.

**My contribution and verification:**

I ran the benchmark five times for each recursion depth. At depth 8, the GPU was slightly slower because the workload was too small to overcome GPU launch overhead. As the workload increased, the GPU became much faster.

At depth 14, the program generated 4,782,969 points and achieved an observed speedup of approximately 99.35 times on the Tesla T4.

### 7. GitHub and Documentation

**My prompt/request:**

“Help me organise the README and AI usage declaration so that the project is clear and easy to review.”

**AI output and reasoning:**

ChatGPT suggested a README structure containing the project overview, implementation method, results, requirements and instructions for running the notebook.

**My contribution:**

I created and managed the GitHub repository myself. I downloaded the notebook from Colab, added it to the repository, reviewed the documentation and created separate commits for the implementation, visualisations, dimension analysis, performance benchmark, AI declaration and README improvements.

## Evaluation of the AI Output

I did not accept the AI suggestions without checking them. I ran every section of the notebook and verified:

* CUDA was available and the tensor calculations used the Tesla T4 GPU.
* The number of points matched `3^depth`.
* The generated plots showed the expected Sierpinski Triangle structure.
* The coordinate-based colour plots behaved as expected.
* The estimated box-counting dimension was close to the theoretical value.
* CUDA synchronisation was included in the GPU benchmark.
* GPU acceleration became more effective as the workload increased.
* The GitHub repository contained the correct notebook, documentation and commit history.

The AI occasionally gave suggestions that required clarification or adjustment. I tested the results, checked tensor shapes and timing behaviour, and only kept code and explanations that I could understand and verify.

## Ownership Statement

ChatGPT contributed explanations, initial code structures, comments, experiment ideas and documentation suggestions.

I selected the project topic, obtained teaching-staff approval, configured the environment, ran and checked all experiments, reviewed the results, managed the GitHub repository and prepared the final project.

I understand how the Sierpinski Triangle is generated, why the recursion levels are sequential, how PyTorch broadcasting provides parallel computation, how the box-counting dimension is estimated and why the GPU is more effective for larger workloads.

The relevant ChatGPT conversation history remains available and can be shown to the demonstrator if additional evidence is requested.
