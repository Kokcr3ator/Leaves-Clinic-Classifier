# Project Name

## Overview

This project is the first challenge of the course "Artificial Neural Networks and Deep Learning" at Politecnico di Milano for the academic year 2023-2024. The objective is to classify images of leaves as healthy or unhealthy using a deep learning approach. The model achieved outstanding results, demonstrating an accuracy of 94.00% and 92.70% on the preliminary and final test sets, respectively. This performance underscores the strong robustness and efficiency of our augmentation strategies, showcasing the model's excellent generalization capabilities. Notably, our team secured the first position among more than 150 teams, surpassing others by a significant margin of 2%.

## Dataset

The dataset used for this project can be found [here](https://drive.google.com/file/d/1llWCmIbaW-uHvZcD-soT8DJQJYmm8zAA/view?usp=drive_link). Please make sure to download and reference it appropriately.

## Table of Contents

1. [Data Preprocessing](#data-preprocessing)
2. [Training](#training)
   - [Transfer Learning](#transfer-learning)
   - [Fine-Tuning](#fine-tuning)
3. [Learning Rate Scheduler and Optimizer](#learning-rate-scheduler-and-optimizer)
4. [Augmentation](#augmentation)
   - [RandAugment](#randaugment)
   - [Test Time Augmentation](#test-time-augmentation)
5. [Performance Assessment and Further Optimization](#performance-assessment-and-further-optimization)

## Data Preprocessing

The dataset initially consisted of 5200 96x96 RGB images, categorized into healthy and unhealthy leaves. Outliers were identified and removed using the t-SNE algorithm, resulting in a refined dataset of 4850 images. To tackle class imbalance, over-sampling was applied, and a 90-degree rotation was used on randomly selected unhealthy samples.

## Training

### Transfer Learning

Various ImageNet pre-trained architectures were evaluated, with the ConvNeXt family (specifically ConvNeXtLarge and ConvNeXtXLarge) proving optimal for the classification task. The classifier's architecture included a Softmax activation function, Swish activation in hidden layers, Global Average Pooling (GAP), batch normalization, and an AdamW optimizer.

### Fine-Tuning

The pre-trained model was fine-tuned by unfreezing the first half of the convolutional network, progressively unfreezing more layers. This process significantly improved accuracy on the validation set.

## Learning Rate Scheduler and Optimizer

An in-depth analysis of optimizers (Adam, AdamW, Experimental SGD, Lion) and a dynamic learning rate scheduler was conducted. The chosen configuration involved AdamW with specific hyperparameters, resulting in improved model performance.

## Augmentation

To enhance generalization, RandAugment, a preprocessing layer, was applied. Test Time Augmentation (TTA) with 11 geometric transformations was employed during model evaluation.

## Performance Assessment and Further Optimization

The ROC curve analysis led to the identification of an optimal threshold, enhancing the model's ability to distinguish between healthy and unhealthy leaves.

## References

## References

1. Ding H. et al. KA-Ensemble: towards imbalanced image classification ensembling under-sampling and oversampling. 2020. DOI: [10.1007/s11042-019-07856-y](https://doi.org/10.1007/s11042-019-07856-y).
2. Andrew G. Howard et al. MobileNets: Efficient Convolutional Neural Networks for Mobile Vision Applications. 2017. arXiv: [1704.04861 [cs.CV]](https://arxiv.org/abs/1704.04861).
3. Mingxing Tan and Quoc V. Le. EfficientNet: Rethinking Model Scaling for Convolutional Neural Networks. 2020. arXiv: [1905.11946 [cs.LG]](https://arxiv.org/abs/1905.11946).
4. Zhuang Liu et al. A ConvNet for the 2020s. 2022. arXiv: [2201.03545 [cs.CV]](https://arxiv.org/abs/2201.03545).
5. Prajit Ramachandran, Barret Zoph, and Quoc V. Le. Searching for Activation Functions. 2017. arXiv: [1710.05941 [cs.NE]](https://arxiv.org/abs/1710.05941).
6. Min Lin, Qiang Chen, and Shuicheng Yan. Network In Network. 2014. arXiv: [1312.4400 [cs.NE]](https://arxiv.org/abs/1312.4400).
7. Sergey Ioffe and Christian Szegedy. Batch Normalization: Accelerating Deep Network Training by Reducing Internal Covariate Shift. 2015. arXiv: [1502.03167 [cs.LG]](https://arxiv.org/abs/1502.03167).
8. Ilya Loshchilov and Frank Hutter. Decoupled Weight Decay Regularization. 2019. arXiv: [1711.05101 [cs.LG]](https://arxiv.org/abs/1711.05101).
9. Sanjeev Arora Zhiyuan Li. An Exponential Learning Rate Schedule for Deep Learning. [Link](https://doi.org/10.48550/arXiv.1910.07454).
10. Frank Hutter Ilya Loshchilov. Decoupled Weight Decay Regularization. 2019. [Link](https://openreview.net/forum?id=Bkg6RiCqY7).
11. Xiangning Chen et al. Symbolic Discovery of Optimization Algorithms. 2023. arXiv: [2302.06675 [cs.LG]](https://arxiv.org/abs/2302.06675).
12. Mingle Xu et al. “A Comprehensive Survey of Image Augmentation Techniques for Deep Learning”. In: Pattern Recognition, Volume 137 (2023).
13. Sebastien C. Wong et al. “Understanding Data Augmentation for Classification: When to Warp?” In: (2016), pp. 1–6. DOI: [10.1109/DICTA.2016.7797091](https://doi.org/10.1109/DICTA.2016.7797091).
14. Luke Taylor and Geoff Nitschke. “Improving Deep Learning with Generic Data Augmentation”. In: (2018), pp. 1542–1547. DOI: [10.1109/SSCI.2018.8628742](https://doi.org/10.1109/SSCI.2018.8628742).
15. Rajneesh Tiwari, Aritra Sen, and Arindam Banerjee. “Generalization through augmentation in deep neural networks for handwritten character recognition”. In: International Journal of Scientific & Engineering Research 11.9 (2020).
16. Lewy D. and Ma´ndziuk J. “An overview of mixing augmentation methods and augmentation strategies.” In: Artif Intell Rev, 56 (2023). DOI: [10.1007/s10462-022-10227-z](https://doi.org/10.1007/s10462-022-10227-z).
17. Ekin D. Cubuk et al. RandAugment: Practical automated data augmentation with a reduced search space. 2019. arXiv: [1909.13719 [cs.CV]](https://arxiv.org/abs/1909.13719).
18. Masanari Kimura. “Understanding Test-Time Augmentation”. In: Neural Information Processing. Ed. by Teddy Mantoro et al. Cham: Springer International Publishing, 2021, pp. 558–569. ISBN: 978-3-030-92185-9.
19. Jayawant N. Mandrekar. “Receiver Operating Characteristic Curve in Diagnostic Test Assessment”. In: Journal of Thoracic Oncology 5.9 (2010), pp. 1315–1316. ISSN: 1556-0864. DOI: [10.1097/JTO.0b013e3181ec173d](https://doi.org/10.1097/JTO.0b013e3181ec173d). URL: [https://www.sciencedirect.com/science/article/pii/S1556086415306043](https://www.sciencedirect.com/science/article/pii/S1556086415306043).




