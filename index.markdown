---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

# layout: home
layout: page
---
# Who am I
I'm a PhD student of UCLA in biomedical physics supervised by Dr [Ke Sheng]. I'll move with our group to UC Berkeley/UCSF. My research interest lies in the application of optimization, high-performance computing, machine learning, and Monte Carlo methods in biomedical research and beyond. I obtained my B.S. in applied physics in University and Science and Technology of China in 2020. I was a visiting student in UCLA at my current lab though CSST program. Prior to starting my PhD, I was a visiting student of [HPC-AI Lab] at NUS in collaboration with Dr Yang You, during which we conducted research in the application of distributed matrix-matrix multiplication algorithms to the parallelization of large language models.

I shamelessly declare I have a strong background in mathematics, physics, and programming. I'm an active and fast learner. I'm interested in a lot of topics, and know a little about everyting. I find my recent interest in economics and history out of the eager to find out how the world evolves and how humans act. We are living in a fast-changing world. My beliefs and understandings have been reformed again and again since I went to university. But some of the beliefs have not changed and seem to apply to the current world.

I'm open to topics about HPC and scientific computing, and eager for a chance to make a real impact or find real-world applications. I want to have industry experience before my graduation to enrich my mindset. 

# Skills
* General: Linux, Windows, git, ssh
* Programming: C++ (CMake, CUDA), Python (PyTorch), MATLAB, Bash
* Documentation: Word, LaTeX, markdown

# Projects
* **Direct beam angle optimization with simulated annealing based on GPU dose calculation** (on going) [[github](https://github.com/xuqifan897/EndtoEnd)]
  
  <details>
  <summary><span style="color:blue">background</span></summary>
  External beam radiation therapy planning aims to maximize the dose to tumor while sparing normal tissues. Each radiation beam can be characterized by its beam angles and fluence map. While fluence map can be optimized using standard convex optimization methods when beam angles are fixed, it's nontrivial to select the optimal beam angles. In previous works, dose matrix for a set of around 1000 candidate beams is pre-calculated and stored, which is a sparse matrix reflecting the linear relationship between the dose and fluence map, and a subset of around 20 beams is selected. The number of candidate beams is restricted by the memory, and the optimization space is limited. In this work, we
  </details>

  * Utilize the massive parallelism of GPU to achieve on-the-fly dose calculation
  * Apply simulated annealing to optimize the beam angles, while updating the fluence map using gradient descent
  * Achieved lower loss compared with previous methods, which potentially leads to better treatment quality.

* **Low-dose CT reconstruction integrating deep learning and model-bsed optimization** [[paper](https://ieeexplore.ieee.org/document/9761612)]

  <details>
  <summary><span style="color:blue">background</span></summary>
  Low-dose CT can lower the radiation exposure to patients, with the expense of higher image noise. Previous methods address this problem primarily in the image domain, as post-processing methods. However, the sinogram domain (the directly measured projection data) is of higher dimension, which could be more informative than the reconstructed image domain. Moreover, previous benchmarking metrics are usually conventional ones like MSE, PSNR, or more recent metrics like SSIM, which may not directly reflect clinical relevance. Besides, deep learning based image denoising methods results in either over-smoothness (supervised learning), or unrealistic features (GAN). On the other hand, model-based methods, which usually formulate the denoising methods as an optimization problem, involve a set of parameters, which depend heavily on emperical manual tuning. So in this work, we integrate neaural networks into optimization, specifically:
  </details>

    * Propose to use loop-independed neural network denoisers as plugins to address the domain mismatch issue in different optimization loops
    * Evaluate the resulting images with clinical relevant metrics, including noise power spectrum and segmentation accuracy, both of which demonstrate the advantage of our method in both statistical properties and fidelity.

* **Distributed deep learning systems development** [[paper1](https://arxiv.org/abs/2104.05343)][[paper2](https://arxiv.org/abs/2105.14500)][[paper3](https://arxiv.org/abs/2105.14450)][[github](https://github.com/xuqifan897/Optimus)] [[Colossal-AI]]

  <details>
  <summary><span style="color:blue">background</span></summary>
  Huge neural networks have shown unprecedented performance in real-world applications. However, training these neural networks has imposed challenges on both hardware and software. Distributed algorithms have been utilized to alleviate the memory burden and make full use of the computation resources on each computation node. The most widely used paradigms are data parallelism and model parallelism. The former duplicates the model parameters on different processors, each processing distinct data; the latter partitions the model parameters to different processors, on which are data processed collectively. Usually, data parallelism has higher efficiency, and model parallelism is used only when the memory of a processor cannot accommodate the whole model. Existing model parallelism methods, such as Mesh-Tensorflow and Megatron-LM, though provide elegant model distribution and computation parallelization, are based on one-dimensional matrix partition, which is sub-optimal for both memory performance and communication efficiency. However, existing distributed matrix-matrix multiplication algorithms are proven to provide higher performance. Based on this insight, we:
  </details>

    * Integrate [2D](https://netlib.org/lapack/lawnspdf/lawn96.pdf), [2.5D](https://netlib.org/lapack/lawnspdf/lawn248.pdf), and [3D](https://ieeexplore.ieee.org/document/5389455) Methods into Transformer-style neural-networks, enabling both model parallelism and data parallelism.
    * Achieve both higher memory performance and communication efficiency.
    * Open-source [Colossal-AI], a framework providing supports to large-scale neural network model training.
  

[Ke Sheng]: https://shenglab.dgsom.ucla.edu/pages/
[HPC-AI Lab]: https://ai.comp.nus.edu.sg/
[Mesh-Tensorflow]: https://arxiv.org/abs/1811.02084
[Megatron-LM]: https://arxiv.org/abs/1909.08053
[Colossal-AI]: https://github.com/hpcaitech/ColossalAI