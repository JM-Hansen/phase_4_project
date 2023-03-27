## phase_4_project

### Pneumonia Identification - A Convolutional Neural Network Model

### Pneumonia infection

Pneumonia is a common acute respiratory infectiom that affects the alveoli and distal airways. It is associated with high morbidity and is a major health problem with both short term and long term affects. Pneumonia is also widespread occuring in all parts of the globe across all age groups. It is more common in the very young (< 5 years of age) and older adults, particularly amonsgt those who suffer from other health conditions. Nearly one million children per year lose their lives to pneumonia and related causes. The causes of pneumonia have multiple vectors - viral, bacterial, and fungal. Individuals with pneumonia face both respiratory and systemic symptoms. Accurate diagnosis of the infection requires both clinical and radiological (x-ray) methods. Rapid and accurate diagnosis is also crucial to successful treatment, often with a range of antimicrobial therapies. Rapid imaging assessment is a matter of life and death.

### Business Case - Intermountain Health Care

Intermountain Health Care (IHC) is a not-for-profit healthcare system based in Utah. Over the past several years they have been working to extend their reach to rural areas. IHC now operates nine hospitals and 23 rural community medical clinics. Despite their reach they face a shortage of medical specialists, particularly radiologists. According to the Association of American Medical Colleges there is a growing shortage of trained medical specialist, especially in radiology, psychiatry, and pathology. On average, the number of medical imaging studies increases by a rate of up to five percent per year, but the number of radiology residency positions only increases by two percent. Decreased numbers of radiologists increases the time to make an accurate diagnosis. IHC cannot meet the demand for trained radiologists across their hospital system. The turnaround time for accurate imaging diagnosis is increasing which impacts patient care and outcomes. IHC is looking for a data science imaging solution.

### Dataset Description

The dataset was collated from past patients at the Guangzhou Women and Children’s Medical Center in Guangzhou, China. The data contains a total of 5,856 x-ray images (anterior - posterior) of pediatric patients under the age of 5 years old. The dataset is divided into three folders made up of jpegs: training, validation, and test folders. Each folder contains two classes: Normal and Pneumonia. The images were previously labeled and validated by two expert physicians. To further reduce error a third expert validated their work. The data is available from Kaggle at https://www.kaggle.com/datasets/paultimothymooney/chest-xray-pneumonia

### Modeling Goals

The data science goal is to build a neural network model that accurately identifies an x-ray image as 'normal' or 'pneumonia'. The modeling process starts with a baseline model that then progresses to a more finely tuned model more appropritate for image analysis - a convolutional neural network model. The goal is to increase the number of true positive identifications while minimizing the number of false negatives.  

### Modeling process and notebook flow 

The data was loaded and processed. It was divided into three datasets: a training dataset to generate the model, a validation dataset to understand how the model is performing (whether it is too sensitive to noise or not sensitive enough), and a test dataset. The test dataset is held out to test the trained model on images it has not seen. Here is the process in more detail:

Load Data -->   Process Data for Modeling -->    Baseline Model -->    CNN Model 1 -->   

Model 2 with Data Augmentation to address class imbalance -->    Model 3 with added layering and padding for greater complexity-->                                    

Model 4 with regularization to prevent overtraining the model -->    Model 5 with more fine tuning  --> Model Evaluation  --> 

Recommendations

### Visuals

Class counts in training dataset for Pneumonia and Normal 

![class_imbalance_train-Copy1](https://user-images.githubusercontent.com/104652254/227075870-6a430426-5e11-48f8-90e0-ceaf8343e0e0.png)

Normal Lung Image - Pediatric

![IM-0001-0001 copy](https://user-images.githubusercontent.com/104652254/227076755-aa2d4748-dea9-4515-8c55-bc15156d6dce.jpeg)

Viral Origin Pneumonia Image - Pediatric

![person3_virus_15 copy](https://user-images.githubusercontent.com/104652254/227077723-b0c96b7a-9f15-4589-81d5-ce7417e9c379.jpg)

Bacterial Origin Pneumonia Image - Pediatric

![person78_bacteria_380 copy](https://user-images.githubusercontent.com/104652254/227077729-f61dd398-0ace-4a22-b91a-0135fbe02440.jpg)


### Results

The final model generated an overall accuracy score of 88%, but it is important to examine the recall scores closely. Recall is the measure of the model correctly identifying true positives. The higher the recall score the more we are able to reduce the number of false negatives. Meaning, we want to avoid telling someone they don't have pneumonia when they actually do, we would miss a chance to give potentially life-saving care to that individual patient. Recall scores for correctly identifying pneumonia is 94%, a good score but with some false negatives still being generated. 

                             precision    recall  f1-score   support

          Normal (Class 0)       0.89      0.78      0.83       234
       Pneumonia (Class 1)       0.88      0.94      0.91       390

                  accuracy                           0.88       624
                  

### Recommendations 

### 1. 
The final model can be prototyped in the clinic for pediatric patients with a 91% pneumonia f-1 accuracy rate. Wait times for radiology results are often the cause of delay in diagnosis times. Use of the model can reduce diagnosis turnaround times to reduce costs and improve patient outcomes. 

### 2. 
Neural network models are often useful for other problems. This model can be trained on images for other groups of patients, particularly the elderly who suffer poorer outcomes from pneumonia. Gathering quality controlled images of lungs of elderly patients to train a new model for deployment would be beneficial for rapid assessment and diagnosis, improved patient outcomes and reduced costs. 

#### Model Limitations
There are two important things to note about the model. The first is that the model identifies whether a patient has pneumonia or not with a higher rate of false positives compared to false negatives, a better outcome for patients with pneumonia at the cost of some false positives. The second is that the model does not discriminate among viral, bacterial, or fungal origins. It also does not identify whether pneumonia is community or hospital acquired. Clinicians and radiologists will still need to be involved in key stages after diagnosis of pneumonia.

