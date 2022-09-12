# Rock Classification - Kaggle

The goal of this repository is to understand how to perform image classification using neural networks. I will be working with the [Rock Classification](https://www.kaggle.com/datasets/salmaneunus/rock-classification) dataset from Kaggle. The best final test accuracy is 85%.

Here is a summary of the workflow which you can find in `notebooks`.

- `01_image_cleaning.ipynb` cleans images to improve dataset quality primarily removing duplicate images.
- `02_image_augmentation.ipynb` addresses class imbalance by adding augmenting images to classes with low sample size.
- `03_image_classification.ipynb` trains and tests ResNet50 and VGG16 model, explaining how each model works.
- `uncleaned_data_image_classificaiton.ipynb` shows the first pass at image classification on an uncleaned dataset using ResNet50.

## How to run
1. Install packages from `requirements.txt`
2. Download [dataset](https://www.kaggle.com/datasets/salmaneunus/rock-classification) from Kaggle.
3. Unzip folder and nested folder
4. Remove images to clean dataset from json files in `Dataset`
5. Run `02_image_augmentation.ipynb`
6. Load the model in `03_image_classification.ipynb` (code at the bottom of the notebook).
7. Run the test code to see the results.

## So how might we improve the accuracy of the results?
- Increase the training size by adding augmented images for all classes
- Experiment with adding more layers to the model
- Add more epochs (increase training time) to find the minimum loss
- Increase the depth of the ResNet model
 
## Folder structure
```bash
rock-classification
├── img
│   ├── img.zip                                           # Original dataset from Kaggle
│   ├── output                                            # Images split into train, val and test
│   │   ├── train	                          
│   │   ├── val	            
│   │   └── test   
│   ├── Dataset                                          # Unzipped image folder, removed first hierarchy
│   │   ├── Basalt	                          
│   │   ├── Coal	            
│   │   ├── Granite	            
│   │   ├── Limestone	            
│   │   ├── Marble	            
│   │   ├── Quartzite	            
│   │   └── Sandstone
│   ├── duplicate_img_path.json                          # Relative file paths to removed duplicate images
│   └── remove_img_path.json                             # Relative file paths to manually removed images
├── notebooks
│   ├── 01_image_cleaning.ipynb             
│   ├── 02_image_augmentation.ipynb
│   ├── 03_image_classification.ipynb
│   └── uncleaned_data_image_classification.ipynb      
├── checkpoint                                          # Frozen trained model weights
│   ├── 20220909_resnet50.pth                           # Best model
│   ├── 20220910_vgg16.pth                              # Couldn't upload because it's too large
│   ├── 20220709_resnet18.pth                           # Uncleaned images, ResNet18
│   └── 20220725_resnet50_double_train.pth              # Uncleaned images, doubled training size, ResNet50
├── requirements.txt
└── plots                                               # Plots for train-val loss over time
```
