# Indonesian Food Recognition Model
This repository contains a deep learning model built using TensorFlow for the recognition of Indonesian food.

## How to Run
1. Import libraries (numpy, pandas, matplotlib.pyplot, tensorflow).

2. We need creating file dataframe from the dataset.

3. Split the data into train and test set.

4. Creating Image generator using ImageDataGenerator to add variance.

5. Using MobileNetV2 as pretrained model.

6. Add pretrained model as input in new layer for modelling.

7. Compile and fit the model.

8. Tune hyperparameter until get the best result.

9. Make sure that the .h5 model is already saved in the “Model” folder. 

10. Run the converter_tflite.py script from your IDE or run the following command in the terminal that is running on the project directory. 
```
python converter_tflite.py
```
11. Your .tflite model is now saved on the “Model” folder. 

## Dataset
![Dataset_SS](Documentation/Dataset.jpg)

Our dataset consists of 1920 total images divided into 9 classes, with details as follows.

| Class | Amount | 
| --- | --- |
| Ayam Goreng | 211 |
| Ayam Pop | 208 |
| Gulai Ikan | 211 |
| Gulai Tambusu | 203 |
| Gulai Tunjang | 222 |
| Rendang | 214 |
| Dendeng | 242 |
| Telur Balado | 206 |
| Telur Dadar | 203 |

But in our training process, we limit each class to only use 203 images. The dataset itself is sourced from various sites, mainly from Kaggle, with addition from Cookpad, Twitter, Instagram, etc.

## Model Architecture
For the main model we use transfer learning from MobileNetV2 and then added our own new layers, the input are images scale 224 x 224 x 3 (resize) and then create the model using mobilenetV2 (16 residual bottleneck layers) + 3 added new dense layers,  We then compile the model using optimizer rmsprop with learning rate = 0.0005 and the final output is the food classification (9 class in total)

![Arsitektur Model](Documentation/CNN_Model_Architecture.png) 

## Model Performance
The model achieved 89.62% accuracy on the test dataset. With details as follows.

![Test Performance](https://raw.githubusercontent.com/Soto-Sok-Foto-Bangkit-Capstone/Soto-Machine-Learning/main/Documentation/Test%20Dataset%20Performance.jpg)


![Accuracy and Loss](https://raw.githubusercontent.com/Soto-Sok-Foto-Bangkit-Capstone/Soto-Machine-Learning/main/Documentation/Loss%20and%20Accuracy.jpg)

## References
https://www.kaggle.com/datasets/faldoae/padangfood 

https://cookpad.com/id/cari/resep%20masakan%20indonesia
