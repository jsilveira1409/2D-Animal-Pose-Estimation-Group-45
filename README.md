# CIVIL-459 OpenPifPaf SDA plugin

This repository implements the Semantic Data Augmentation (SDA) technique for Animal 2D Pose Estimation. The SDA plugin is based on the "Adversarial Semantic Data Augmentation for Human Pose Estimation" paper [1].

The SDA Plugin works by iterating over the dataset and applying cropping to different body parts using keypoint data. Each body part is masked and extracted individually, although the quality of the cropped body parts may not be perfect. Random rotation and scaling are also applied to the individual body parts. The positioning of the body parts is currently random, but in the future, Adversarial Positioning will be implemented. Adversarial Positioning aims to add leg parts next to the ground truth legs to confuse the model and improve its generalization capabilities. 

![image](https://github.com/jsilveira1409/CIVIL-459-Animal-Pose-Estimation/assets/57415447/33fc8b8b-c512-42cf-94fe-3eb4e5cf1078)

In the original paper [1], the technique was applied to a top-down single-person detection network. However, in OpenPifPaf, which is a bottom-up multi-person detection model, modifications are made to the ground truth of the samples. The keypoints of the added body parts are included in the ground truth to incorporate them into the original image.

Therefore, during the cropping phase, we extract the bodyparts and their local keypoints, which are then added to the samples and ground truth, randomly, during training.

The main goal of this approach is to enhance the model's robustness to occlusion, even when one animal occludes another. 

Bodyparts look like this:

![image](https://github.com/jsilveira1409/CIVIL-459-Animal-Pose-Estimation/assets/57415447/6b55ae36-0f0b-462b-9031-7a8a8585d67d)
![image](https://github.com/jsilveira1409/CIVIL-459-Animal-Pose-Estimation/assets/57415447/ed5ea4ae-c497-469d-ab8e-c3eaae476528)

And their Masks look like this:

![image](https://github.com/jsilveira1409/CIVIL-459-Animal-Pose-Estimation/assets/57415447/b272625f-89e5-4a4e-91c6-c6a385a8a27a)
![image](https://github.com/jsilveira1409/CIVIL-459-Animal-Pose-Estimation/assets/57415447/f2caaf40-d922-4cff-bcdb-c59908a88906)

Which then allows us to do 

## Usage/Examples

The training was conducted on [Paperspace](https://www.paperspace.com/). The Virtual Machine can be access here : 
 **[Paperspace VM](https://console.paperspace.com/jsilveira1409/notebook/rwp2eb9tnfijzsh)**

Depending on the session, OpenPifPaf and PyCocoTools need to be installed :

```bash
$ pip install openpifpaf & pip install pycocotools
```




## Authors

- [@jsilveira1409](https://github.com/jsilveira1409)

## References

[1] Yanrui Bin, Xuan Cao, Xinya Chen, Yanhao Ge, Ying Tai, Chengjie Wang, Jilin Li, Feiyue Huang, Changxin Gao, and Nong Sang. (2020). Adversarial Semantic Data Augmentation for Human Pose Estimation. arXiv preprint arXiv:2008.00697. [Link to Paper](https://arxiv.org/abs/2008.00697)



