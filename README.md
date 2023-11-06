### Cell_Instance_Segmentation

## 1 Introduction

Neurological disorders, including Alzheimer’s and brain tumors, are a major global cause of death and disability. This report outlines efforts to address the challenge of accurately segmenting neuronal cells in images, with the goal of advancing neurobiology research.

## 2 Dataset

### 2.1 Description

- All images are of size 704*520 and in grayscale.
- 606 images with a total of 73586 annotations for 3 classes (cort, astro, shsy5y).
- 5837 images from the "LIVE CELL" dataset with annotations for cell segmentation for 8 classes.

### 2.2 Preprocessing

- 606 images divided into 578 train, 22 validation, and 6 test images.
- Annotations converted to COCO format, segmentation masks can be in RLE or polygon.

## 3 Model

# MMDetection-YOLACT

You Only Look At CoefficienTs (YOLACT) is proposed, which is a simple, fullyconvolutional
model for real-time instance segmentation, which is trained using one GPU
only.It has two parallel subtasks: (1) generating a set of prototype masks and (2) predicting
per-instance mask coefficients. Then, instance masks are produced by linearly combining
the prototypes with the mask coefficients.To ensure the suitability of the model for our
specific task, we initiated the process by overfitting it to a limited dataset comprising only
12 images. This intensive overfitting phase involved training the model for an extensive
400 epochs. This approach allowed us to closely scrutinise the model’s performance on
our targeted task and assess its adaptability to our data.Then we trained the model on the
full dataset for 45 epochs and the results per class are in the Table 3, loss graph in figure 9,
mAP graph in figure 10 and samples in figures 11 and 12.
![image](https://github.com/Ahmedzayan1/Cell_Instance_Segmentation/assets/87100830/d6848533-3b81-4523-ad42-663f4f83ffea)
 -mAP graph
![image](https://github.com/Ahmedzayan1/Cell_Instance_Segmentation/assets/87100830/191df42d-ea79-4e07-8cb8-22e09a720c63)
-loss graph

#### Results
Class mAP mAP 50 mAP 75 mAPs mAPm
shsy5y 0.088 0.262 0.025 0.088 0.0
astro 0.075 0.261 0.013 0.061 0.181
cort 0.403 0.755 0.415 0.403 nan
![image](https://github.com/Ahmedzayan1/Cell_Instance_Segmentation/assets/87100830/fe942e68-8c39-4cde-b317-396a185b8cfd) -good prediction

![image](https://github.com/Ahmedzayan1/Cell_Instance_Segmentation/assets/87100830/5a9d8111-37ae-408a-a2a1-fcfbb99c0cbf) -bad prediction

