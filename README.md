# Hierarchical HAR-PBD architecture
[![GitHub stars](https://img.shields.io/github/stars/Mvrjustid/IMWUT-Hierarchical-HAR-PBD)](https://github.com/Mvrjustid/IMWUT-Hierarchical-HAR-PBD)
[![GitHub folks](https://img.shields.io/github/forks/Mvrjustid/IMWUT-Hierarchical-HAR-PBD)](https://github.com/Mvrjustid/IMWUT-Hierarchical-HAR-PBD)
[![GitHub](https://img.shields.io/github/license/Mvrjustid/IMWUT-Hierarchical-HAR-PBD)](https://github.com/Mvrjustid/IMWUT-Hierarchical-HAR-PBD)
[![GitHub issues](https://img.shields.io/github/issues/Mvrjustid/IMWUT-Hierarchical-HAR-PBD)](https://github.com/Mvrjustid/IMWUT-Hierarchical-HAR-PBD/issues)
[![My achievement](https://img.shields.io/badge/Milestone-1st%20IMWUT-orange?style=flat-square&logo=Google-Keep)](https://github.com/Mvrjustid/IMWUT-Hierarchical-HAR-PBD)

<p align=center>
   <img src=/assets/avatars_2.png width="650x"/>
</p>

This is for our paper,
[Leveraging Activity Recognition to Enable Protective Behavior Detection in Continuous Data](https://wangchongyang.ai/assets/pdf/Leveraging_Activity_Recognition_to_Enable_Protective_Behavior_Detection_in_Continuous_Data_IMWUT.pdf),\
accepted in Proceedings of the ACM on Interactive, Mobile, Wearable and Ubiquitous Technologies (IMWUT), Feb round, 2021.

***

### General
From this repository, you will find all the necessary components that you may feel interesting and helpful for your own research in our paper.\
However, codes provided here are not directly executable, e.g., you would not be able to download and run simply with a python command on your machine. You will be able to copy the useful segments, paste and modify into your own script.\
This is mainly because, the [EmoPain](https://ieeexplore.ieee.org/abstract/document/7173007/) data is not publicly available, but downloadable upon application.
In the end, the testing data is held by the EmoPain developer.

***

### Intro
In this paper, our aim was to establish accurate **protective behavior detection (PBD)** along a continuous movement data sequence of a participant with chronic pain (CP). A figure illustrating such data sequence is given below.

<p align=center>
   <img src=/assets/sequence.png width="650x"/>
</p>

Along the data sequence, the participant performed five activities-of-interest (AoIs), between which he/she was allowed to take some rest and move freely, referred to as transition activities.

The proposed solution is to leverage the **human activity recognition (HAR)** to contextualize the PBD using a hierarchical architecture, which is, by default, a two stage process during training and an end-to-end process during inference or testing. This architecture comprising two modules (HAR and PBD) could be trained together, and the code is available.

**Tips**

Check if i) joint training of the two modules fits your own problem better; ii) using one-hot encoding for the HAR output during contextualization is doable for your experiment, otherwise you may just pass a number (n) representing the predicted class of activity or using extra embedding layers to help pass the information.

<p align=center>
   <img src=/assets/HAR-PBD.png width="650x"/>
</p>

***

### Code
**Prerequisites**

The code has been tested on a machine with RTX 3080 (: D) and R9 3900X, with
- tensorflow (tf-nightly-gpu==2.6.0) (dev20210409)
- keras (keras-nightly==2.6.0) (dev2021040900, installed automatically with tf-nightly-gpu)
- cuda (11.2)
- cudnn (8.1.0)
- python (>=3.8.0)

You may not need to use such an up-to-date environment, depending on the GPU version you have.
For 20s or 10s GPU, older versions of these packages are 100% doable. BUT, be careful to change some codes thereon, given the update of tensorflow always come with different properties. You can leave an issue if this troubles you too much.

**Description**

- utils.py: useful plug-and-play functions, e.g. the Class-balanced Focal Categorical Cross-entropy (CFCC) loss and a function to build callbacks. The callbacks are used by me to automatically save the best results during training and Skip the current training if acc reaches 100%. 
- gc-LSTM.py: a basic GC-LSTM implementation, which could be adapted to be the PBD/HAR GC-LSTM.
- HierarchicalHAR-PBD.py: the hierarchical HAR-PBD architecture in its joint-training variant, see Section 5.3 of the paper.

With the above codes, you are ready to implement the methods proposed in our paper, while also develop yours.

***

### Reference
Feel benefited?
Please consider citing

Chongyang Wang, Yuan Gao, Akhil Mathur, Amanda C. De C. Williams, Nicholas D. Lane, and Nadia Bianchi-Berthouze.
2021. Leveraging Activity Recognition to Enable Protective Behavior Detection in Continuous Data. Proc. ACM Interact. Mob.
Wearable Ubiquitous Technol (IMWUT). 5, 2. https://doi.org/10.1145/3463508
```
@article{wang2021leveraging,
     title={Leveraging Activity Recognition to Enable Protective Behavior Detection in Continuous Data},
     author={Wang, Chongyang and Gao, Yuan and Mathur, Akhil and Williams, Amanda C. DE C. and Lane, Nicholas D and Bianchi-Berthouze, Nadia},
     journal={Proceedings of the ACM on Interactive, Mobile, Wearable and Ubiquitous Technologies (IMWUT)},
     volume={5},
     number={2},
     DOI={10.1145/3463508},
     publisher={ACM},
     year={2021}}
```
