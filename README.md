# Automatic Segmentation of Soft Tissue Sarcoma
CT-scan images of patients with soft tissue sarcoma were automatically segmented using a U-Net architecture


I followed and modified the example from the repo below to obtain reasonable results from training the model,
https://github.com/qubvel/segmentation_models/blob/master/examples/binary%20segmentation%20(camvid).ipynb

# Data
There is a total of 1246 CT-scan images comprising both trian, test, and validation data. These images are from actual patients with soft tissue sarcoma.
(a type of cancer that affects the bones and soft tissue)

The data was obainted from
https://www.kaggle.com/4quant/soft-tissue-sarcoma/

![](/assets/images/STS_003_27_.png "ct-scan")
<img src="/assets/images/tumor-overlaid-on-ct-scan.PNG" alt="image-overlaid-with-mask" width="256" height="256">

On the left you can see the CT-scan image and on the right the mask is overlaid on top of the image. Here, the mask indicates the position of the tumor.

The data was also augmented and had a number of transformations applied to it,

The following transofrmations were applied to the data,
* horizontal flip
* affine transforms
* perspective transforms
* brightness/contrast/colors manipulations
* image bluring and sharpening
* gaussian noise
* random crops

The transfomrations were implemented using the [Albumentations](https://github.com/albumentations-team/albumentations) library.

I initially was training the model without data augmentation and found that my metrics produced really bad results. 

Data augmentation helped in improving that and also aided in preventing the model from overfitting. 

# Training & Testing The Model
Make sure you have all the libraries installed, that is, 
Tensorflow, Keras, segmentation-models, cv2, albumentations, etc.

Change the file paths for x_train/val/test and y_train/val/test in `ct-scan-seg.py` with your appropriate paths,

and simply run `ct-scan-seg.py`

# Results
![](/assets/images/image-vs-predicted.PNG "results-pred")
![](/assets/images/model-iou-score.PNG "model-iou-score-vs-epoch")
![](/assets/images/model-val-loss.PNG "model-val-loss-vs-epoch")
