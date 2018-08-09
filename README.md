
# Introduction
The Purpose of this Project is to perform land use classification of Sattelite Images. The dataset used for this purpose is the UC Merced dataset, which consists of 21 land use classes. There are 100 images in each of the classes. There are 100 images in each of the classes. The classes are the following -1) agricultural 2)airplane 3) baseballdiamond 4) beach 5) buildings 6) chaparral 7)denseresidential 8) forest 9)freeway 10) golfcourse 11)harbor 12) intersection 13) mediumresidential 14)mobilehomepark 15)overpass 16)parkinglot 17)river 18)runway 19)sparseresidential 20)storagetanks 21)tenniscourt.

Each image 256x256 pixels. The images were manually extracted from large images from the USGS National Map Urban Area Imagery collection for various urban areas in the US. The pixes resolution of the images is 1 foot. The UC Merced dataset falls in the category of a remote sensing dataset.

# Analysis Procedure
The following methodology will be followed in the performing the Land Use classification - 
1) The Dataset (UC merced) training dataset was studied. It was observed that the dataset consisted of 256x256 pixels. The dataset was chosen because there was no image segmentation. The images were such that each image contained only 1 land use class. 
2) For Each class, the Images were segregated as following 80 images were used for training, 10 images for validation and 10 for testing. 
3) The transfer learning technique was used for training and validation on the model. The VGG16 model, used for detecting animal images was used as the base model. The weights for the VGG16 model, trained on the imagenet dataset were loaded on the model.
4) All fully connected layers were removed from the VGG1 model and a new model- VGG16 minus the fully connected layers was created. This model was called conv_base. 
5) The input images (training and validation) were converted into arrays using the ImageDataGenerator function in Keras. The vector from this array was input into the conv_base network with frozen weights (belonging to Image net dataset). 
6) a new fully connected network was defined with a few layers. The output from the frozen conv_base network was input to this fully connected network. One of the dense layers in the network was given 256 nodes because the image consisted of 256 pixels.
