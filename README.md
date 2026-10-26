# Industrial Anomaly Detection Using Synthetic Defect Augmentation

**Course:** Applied Deep Learning 
**Assignment:** 1 — Initiate  
**Student:** Joel Alfaro Sánchez  
**Matriculation Number:** 12603029  

## 1. Project Overview

Detecting defects is an important part of quality control in industrial manufacturing. Deep learning can help automate this process, but training these models is challenging because defective products are often rare and collecting enough examples of every possible defect is difficult.

The goal of this project is to develop a model that can detect and locate defects in industrial images without needing real defective examples during training.

To achieve this, I plan to train a neural network using images of normal products and artificially generated defects. The main focus will be to investigate whether different ways of generating these artificial defects affect how well the model can detect real anomalies it has never seen before.

## 2. Project Type

**Bring Your Own Method**

I will use an existing public dataset and compare different deep learning approaches for anomaly detection.

The project will start with a simple convolutional autoencoder as a baseline. I will then implement a segmentation model trained with synthetic defects, taking inspiration from CutPaste [2] and DRAEM [3].

My proposed modification is to vary the size and blending of synthetic defects during training. I will test whether these changes improve detection and localization on real defects compared with a fixed augmentation setup, keeping the network architecture and training settings the same.

## 3. Dataset

I plan to use the [MVTec Anomaly Detection dataset (MVTec AD)](https://www.mvtec.com/research-teaching/datasets/mvtec-ad) [1].

The dataset contains 5,354 images across 15 categories of industrial objects and textures. It provides images of normal products for training, as well as normal and defective images for testing. The defective images also include masks showing where the defects are located.

To keep the project manageable, I will initially focus on two categories:

- **Bottle:** To test the model on objects with a defined shape and structure.
- **Carpet:** To test the model on repetitive textures, where defects can be harder to distinguish.

Only normal images will be used to train the models. Artificial defects will be generated from these images, while the real defective images will be reserved for evaluation.

## 4. Proposed Approach

The project will be divided into two main stages.

**Baseline model**

First, I will train a convolutional autoencoder on normal images. The model will learn to reconstruct these images, and the differences between an input image and its reconstruction will be used to identify possible defects.

This will provide a baseline for evaluating the next approach.

**Synthetic anomaly detection**

Next, I will train a small U-Net-based segmentation model using artificially generated defects and their corresponding masks.

I plan to compare two ways of generating these defects:

- **CutPaste-based augmentation:** Copying small image patches and pasting them into different locations to create irregularities.
- **Texture-based augmentation:** Introducing changes in texture or appearance within randomly shaped regions.

Both approaches will use the same network architecture so that I can compare how the generated defects influence the results.

Finally, I will evaluate the models on real defects from MVTec AD and compare their ability to detect defective images and locate the affected regions.

## 5. Work Breakdown Structure

The following table shows my estimated time for each part of the project.

| Task | Description | Estimated Time |
|---|---|---:|
| Research and planning | Read related papers and define the approach | 8 h |
| Dataset preparation | Download, explore and preprocess the images | 6 h |
| Network design and implementation | Build the autoencoder, U-Net and synthetic defect generation methods | 17 h |
| Training and fine-tuning | Train the models and adjust hyperparameters | 13 h |
| Evaluation and experimentation | Compare the approaches and analyze the results | 10 h |
| Demo application | Build a simple application to upload images and visualize detected defects | 8 h |
| Final report | Write the methodology, results and conclusions | 6 h |
| Presentation | Prepare the slides and demonstrate the project | 4 h |
| **Total** | | **72 h** |

These estimates may change depending on the training time and the results of the initial experiments.

## 6. Scientific References

**[1] Bergmann, P., Fauser, M., Sattlegger, D., & Steger, C. (2019).**  
*MVTec AD — A Comprehensive Real-World Dataset for Unsupervised Anomaly Detection.*  
IEEE/CVF Conference on Computer Vision and Pattern Recognition (CVPR).

[Read paper](https://openaccess.thecvf.com/content_CVPR_2019/html/Bergmann_MVTec_AD_--_A_Comprehensive_Real-World_Dataset_for_Unsupervised_Anomaly_CVPR_2019_paper.html)

**[2] Li, C.-L., Sohn, K., Yoon, J., & Pfister, T. (2021).**  
*CutPaste: Self-Supervised Learning for Anomaly Detection and Localization.*  
IEEE/CVF Conference on Computer Vision and Pattern Recognition (CVPR).

[Read paper](https://openaccess.thecvf.com/content/CVPR2021/html/Li_CutPaste_Self-Supervised_Learning_for_Anomaly_Detection_and_Localization_CVPR_2021_paper.html)

**[3] Zavrtanik, V., Kristan, M., & Skočaj, D. (2021).**  
*DRAEM — A Discriminatively Trained Reconstruction Embedding for Surface Anomaly Detection.*  
IEEE/CVF International Conference on Computer Vision (ICCV).

[Read paper](https://openaccess.thecvf.com/content/ICCV2021/html/Zavrtanik_DRAEM_-_A_Discriminatively_Trained_Reconstruction_Embedding_for_Surface_Anomaly_ICCV_2021_paper.html)