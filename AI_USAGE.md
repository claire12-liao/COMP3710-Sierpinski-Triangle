 AI Use Declaration

1. Project Overview

For this project, I used PyTorch to implement and analyse a GPU-accelerated Sierpinski Triangle.

I used ChatGPT as a learning and development assistant. It helped me understand the Part 3 requirements, compare possible fractal topics, create starting code templates and plan suitable experiments.

I completed the project step by step. I selected the Sierpinski Triangle, received approval from the teaching staff, created the public GitHub repository, configured the Google Colab GPU environment and ran every part of the notebook myself.

2. How I Used ChatGPT

Topic and Requirements

I asked ChatGPT to explain the Part 3 requirements and suggest a fractal that was valid, manageable and easy to explain during the Demo.

ChatGPT suggested the Sierpinski Triangle because it has a clear recursive structure, a known theoretical dimension and a suitable vectorised PyTorch implementation. I considered this suggestion and obtained teaching-staff approval before starting.

PyTorch Implementation

I asked ChatGPT for help creating a GPU-compatible implementation and understanding the parallel computation.

ChatGPT provided a starting code structure using PyTorch broadcasting. At each recursion level, every existing point is moved halfway towards each of the three triangle vertices. This produces three new points from every previous point and allows many coordinates to be processed together on the GPU.

I ran the code on a Tesla T4 and confirmed that CUDA was available. At recursion depth 10, the program generated 59,049 points, which matched the expected value of `3^10`.

Additional Analysis

ChatGPT suggested several experiments, including:

* Comparing different recursion depths.
* Colouring the triangle using the `x` and `y` coordinates.
* Estimating the box-counting dimension.
* Comparing CPU and GPU execution times.

I ran each experiment and checked the results before including it in the final notebook.

The estimated box-counting dimension was `1.5838`, which was close to the theoretical value of `1.5850`.

The performance experiment showed that the GPU was slower for the smallest workload because of GPU overhead. However, for recursion depth 14, the GPU achieved approximately `99.35×` speedup. This demonstrated that GPU parallelism becomes more useful as the workload increases.

GitHub and Documentation

ChatGPT suggested commit messages and helped me organise the project into separate development stages.

I created and managed the GitHub repository myself. I added the notebook, checked the changed files, corrected the duplicated `.ipynb` extension, created separate commits and pushed the completed work to the public repository.

ChatGPT did not access or operate my GitHub account.

3. My Review and Verification

I did not accept the AI-generated suggestions without checking them. I ran every code section and reviewed the outputs.

I verified:

* That PyTorch was using the Tesla T4 GPU.
* That the point count followed `3^depth`.
* That increasing the recursion depth produced the expected self-similar structure.
* That the colour plots used the same fractal coordinates.
* That the estimated dimension was close to the theoretical dimension.
* That GPU synchronisation was included in the timing experiment.
* That the project files and commit history appeared correctly on GitHub.

ChatGPT contributed to the initial code structure, explanations, comments, experiment ideas and documentation. I was responsible for selecting the topic, obtaining approval, setting up the environment, running the code, checking the results, correcting problems, managing the repository and preparing the Demo explanation.

I have reviewed this declaration and understand the code and results included in my project. The original ChatGPT conversation can be provided if required.
