# New-Approaches-with-PRNU-CNN-for-Image-Source-Forensics
We built a pipeline to extract the PRNU noise from the residual noise of a single image with a Resnet-based CNN architecture

Project for courses [Human robot interaction](https://sites.google.com/a/dis.uniroma1.it/human-robot-interaction/) & [Reasoning Agents](http://www.diag.uniroma1.it/patrizi/sections/teaching/reasoning-agents-21-22/index.html), DIAG, Sapienza University in Roma

![sapienza-big](https://user-images.githubusercontent.com/24941293/152373391-ac062aac-750a-45cd-bf40-9851cf2911f1.png)

Co-author:
- [PK](https://github.com/TuDou-PK)
- [SCC](https://github.com/skant626)
- [DJN](https://github.com/Ding-Jianan)

[Here is report!](https://drive.google.com/file/d/1uim4LemQ6g-ERWebdWBkJu9HuTTL09Pw/view?usp=share_link)

## HIGHLIGHTS

- Overall, we propose a pipeline for PRNU noise extraction using CNN and then classify it in this paper.
- We used the traditional wavelet method to extract the PRNU noise on the VISION dataset.
- We use the Resnet-based CNN model (modeled CSI-CNN architecture) to extract PRNU noise from Residual noise to enhance the utility of camera fingerprinting.
- Based on the PRNU noise obtained using the above Resnet-based CNN model we tried to use a DnCNN-based model as well as a Sample CNN model for classification.
- On the basis of discarding the directly obtained PRNU noise, we directly use DnCNN and a Sample CNN model to extract the high-level features of Residual noise, in other words, try to keep the complete PRNU noise structure, and then conduct classification experiments respectively.

## The Proposed Methods

![1](https://user-images.githubusercontent.com/24941293/222907513-b808b7d5-2ffe-4c71-ad68-5c9ba5fde1e3.png)

Figure 1. The pipeline we proposed for image source forensics. I is the original image from dataset, F function is denoise filter, W presents the residual noise. The final result is K classes, where K represents the number of classes.

The details of  model Resnet-based CNN for getting PRNU as follows.

![csi_pipeline](https://user-images.githubusercontent.com/24941293/222908637-b69d2024-2406-4095-bef7-de0dd3e90a60.png)

 Figure 2. The Resnet-based CNN is modeled and modified after CSI-CNN architecture, here is the modified CSI-CNN architechture of the PRNU generate model..


After get the PRNU dataset, we use the following model to classify them.

![class](https://user-images.githubusercontent.com/24941293/222908862-8818ab85-2248-47d3-8d20-69ce436216c6.png)

Figure 3. Structural details of the sample CNN classification model.


## Experiments

We use the VISION dataset for experiments. 

\begin{table*}[]
\caption{Result Comparison}
\label{tab:freq}
\begin{tabular}{cccccl}
\toprule
Model                                             & Dataset & Target & Labels & Level & Accuracy \\
\midrule
DnCNN-based model(Based on residual noise)        & VISION  & Camera & 10     & Patch & 92.83\%  \\
Our Classification Model(Based on residual noise) & VISION  & Camera & 10     & Patch & \textbf{92.41\%}  \\
Shallow CNN\cite{marra2018vulnerability}                                      & VISION  & Camera & 35     & Patch & 80.77\%  \\
DenseNet-40\cite{marra2018vulnerability}                                       & VISION  & Camera & 35     & Patch & 87.96\% \\
Roberto, C et al\cite{caldelli2018prnu}& VISION & Social Network & 3& Patch & 79.48\% \\
Roberto, C et al\cite{caldelli2018prnu}& VISION & Social Network & 3& Image & 89.83\% \\
Bondi, L et al\cite{bondi2016first} & Dresden & Camera & 18 & Patch & 72.90\% \\
\bottomrule
\end{tabular}
\end{table*}

