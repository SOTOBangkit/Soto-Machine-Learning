# Indonesian Food Recognition Model
This repository contains a deep learning model built using TensorFlow for the recognition of Indonesian food.

## How to Run
1. Clone this repository on your local machine or Google Colab by running the following command.
```
git clone https://github.com/Soto-Sok-Foto-Bangkit-Capstone/Soto-Machine-Learning.git
```
2. Install all the required dependencies, such as tensorflow, sklearn, pandas, seaborn, and matplotlib. By running the command:
```
pip install [the name of the package]
```
3. Open the **Transfer Learning.ipynb** and run all the cell from top to bottom sequentially. In a nutshell the process is as follows.
      - Importing the libraries (numpy, pandas, matplotlib.pyplot, tensorflow).
      - Creating file dataframe based on the dataset.
      - Splitting the data into train, validation, and test set.
      - Creating an Image generator using ImageDataGenerator using it to add variance.
      - Loading the MobileNetV2 pretrained model.
      - Adding our own new layers to MobileNetV2 layers.
      - Compiling and fitting the model.
      - Printing out the performance results of the model.
      - Saving the model to the **Model** folder as **my_model.h5**

4. After you make sure that the **my_model.h5** is already saved in the **Model** folder, run the **converter_tflite.py** script from your IDE or run the following command in the terminal that is running on the project directory. 
```
python converter_tflite.py
```
5. Your model is now saved on the **Model** folder as **model.tflite** and is now ready to be used.

<br>

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

<br>

## Model Architecture
For the main model we use transfer learning from MobileNetV2 and then added our own new layers, the input are images scale 224 x 224 x 3 (resize) and then create the model using mobilenetV2 (16 residual bottleneck layers) + 3 added new dense layers,  We then compile the model using optimizer rmsprop with learning rate = 0.0005 and the final output is the food classification (9 class in total)

![Arsitektur Model](Documentation/CNN_Model_Architecture.png) 

<br>

## Model Performance
The model achieved 89.62% accuracy on the test dataset. With details as follows.

![Test Performance](https://raw.githubusercontent.com/Soto-Sok-Foto-Bangkit-Capstone/Soto-Machine-Learning/main/Documentation/Test%20Dataset%20Performance.jpg)


![Accuracy and Loss](https://raw.githubusercontent.com/Soto-Sok-Foto-Bangkit-Capstone/Soto-Machine-Learning/main/Documentation/Loss%20and%20Accuracy.jpg)

<br>

## References
https://www.kaggle.com/datasets/faldoae/padangfood 

https://cookpad.com/id/cari/resep%20masakan%20indonesia
