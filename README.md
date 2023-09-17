# Phase-4-Project
## Introduction
Pneumonia is an infection that causes inflammation in one or both of the lungs and may be caused by a virus,bacteria,fungi or other germs.When pneumonia is suspected, a chest X_ray is often recommended as part of the diagnostic process.
A chest X-ray helps the doctor diagnose pneumonia and determine the exact location of the infection.X-ray images helps to confirms the presence of pneumonia by showing areas of opacity in the lungs,which are indicative of inflammation.
In the X-ray image, pneumonia is often seen as a white or gray patch(or patches),which represents the area of the lung affected by pneumonia. The rest of the lung appears darker on the X-ray image.The contrast allows the doctor to identify areas of pneumonia.However, while X-rays are a valuable tool in diagnosing pneumonia,they do have limitations.For instance, it's often difficult to diagnose pneumoia in people with pre-existing lung diseases since their lungs may already show abnormalities on the X-ray.Due to some of this limitations in diagnosing the presence of pnemonia, the Radiology department in conjuction with the Health Information Department(HIM) department from Kenyatta National Hospital have seen the need to employ deep learning to help them build a neural network that may help in the diagnosis of pneumonia.

Kenyatta National Hospital, located in Nairobi,Kenya is the largest public tertiary,referral hospital in the country.It holds about 1800 beds in the public wing and 209 beds in the private wing.The Radiology team in Kenyatta National Hospital(KNH) is equipped with state-of-the-art equipment.The department offers various specialized services to both adults and children,which include CT Scans,MRI(with sedation and anaesthesia), Ultrasound and Interventional Radiology.They carry out both non-vascular and vascular procedures such as image guided biopsies of the lungs among others.
On the other hand, the Health Information Management(HIM)department is responsible for collection, analysis and the protection of digital and traditional medical information vital to providing quality patient care.They ensure that data is properly stored, cleaned and made available for use.They also play a cricial role in ensuring that all data management practices comply with the various legal and ethical standards which includes things like patients privacy laws and regulation related to the storage of medical data.
The collaboration of this two departments is crucial in the effective running of KNH since the Radiology department generates vast amounts of data from various imaging procedures. This data needs to be properly managed to ensure it can be easily accessed and used by healthcare providers and this where the HIM Department comes in.

This project aims to develop a neural network model for the detection of pneumonia from chest X-rays images inorder to help the radiologist and other healthcare providers in Kenyatta National Hospital to make more accurate diagnoses by identifying patterns in X-ray images that may be difficult for humans to detect.By providing preliminary diagnosis,the model can save radiologists time,allowing them to focus on more complex cases, faster and more accurate diagnosis means that patients can receive treatment sooner,potentially leading to better outcomes.


## The Problem Statement
Pneumonia is a common lung infection caused by bacteria, a virus or fungi.It is a major cause of death among all age groups resulting in 2.56 million deaths worldwide in 2017. The diagnosis of pneumonia involves a physical exam followed by a chest X-ray. However, the interpretation of chest X-rays requires expert knowledge and can be time consuming.Morever, the accuracy of diagnosis can vary based on the experience and expertise of the radiologist.Since false diagnosis of pneumonia can lead to escalated medical conditions,increased risk of infection and incorect treatment,this has possed a problem to the KNH radiology team therefore, a need for an automated, reliable and efficient method to interpret chest X-rays and diagnose pneumonia.
This project aims to develop a neural network model that can accurately detect pneumonia from chest X-rays images,thereby assisting radiologists in Kenyatta National Hospital in diagnosis,reducing the time taken for diagnosis and ultimately leading to timely treatment and improved patient outcomes.


## The Main Objective
To develop a neural network that can accurately and effectively detect pneumonia from the chest X-rays images, thereby assisting radiologists in diagnosis,reducing false diagnosis and time taken for diagnosis and ultimately leading to timely treatment and improved patient outcomes.


## Specific Objectives
(i) Analyze the characteristics of chest X-ray images of pneumonia cases and compare them to those without.

(ii) Identify potential correlations or patterns in chest X-ray images that might be indicative of pneumonia.

(iii) Evaluate the quality and usability of the data for model training

(iv) Build a neural network for pneumonia diagnosis and tune the model for the best results

 
 ## Data Understanding
 The data is from Chest X-ray images (anterior-posterior)  selected from retrospective cohorts of pediatric patients of one to five years old from Guangzhou Women and Children’s Medical Center.The data has 3 sets. The training set , the validation set and the test set. The train set contains 5216 images,1341 X_rays of normal cases and 3875 of pneumonia cases.The validation set contains 16 images with equal number of images of both the normal cases and the pneumonia cases.The test dataset contains 624 images,with 234 images of normal cases and 390 images of pneumonia cases.Each of these images vary in size, brightness and contrast.Both the test and the training datasets have class imbalance.Images of pneumonia cases show a distict feature of a patchy and consolidated area in the lungs which might help the CNN model distinguish between the two cases.


## Modelling
Model 1: Basic CNN

- Architecture: The model is a simple Convolutional Neural Network (CNN) with one convolutional layer, one max pooling layer, a flatten layer, and two dense layers. The final layer uses a sigmoid activation function for binary classification.
- Performance: The model achieved an accuracy of approximately 43% on the test data, and a recall of approximately 56% for identifying ‘Pneumonia’ cases.

Model 2: CNN with an additional convolutional layer and class weights

- Architecture: The model is a Convolutional Neural Network (CNN) with two convolutional layers, each followed by a max pooling layer, a flatten layer, and two dense layers.
- Performance: The model achieved an accuracy of approximately 49% on the test data, and a recall of approximately 72% for identifying ‘Pneumonia’ cases


Model 3: CNN with L2 regularization

 - Architecture: The model is a Convolutional Neural Network (CNN) with two convolutional layers, each followed by a max pooling layer, a flatten layer, and two dense layers. It also includes L2 regularization in the convolutional layers to prevent overfitting.
- Performance: The model achieved an accuracy of approximately 54% on the test data, and a recall of approximately 80% for identifying ‘Pneumonia’ cases. This suggests that the model correctly identified whether pneumonia was present in about 54% of the test images, and it correctly identified 80% of all actual ‘Pneumonia’ cases in the test data.

## Modelling results
Model 1 (Simple CNN):

Accuracy: 43%
Recall (Pneumonia): 56%
This model had a relatively high number of false positives and false negatives, suggesting it often incorrectly classified instances.
Model 2 (CNN with additional convolutional layer and class weights):

Accuracy: 49%
Recall (Pneumonia): 72%
This model showed some improvements in terms of accuracy and recall compared to Model 1. However, the precision for the ‘No Pneumonia’ class was quite low, suggesting that the model might be over-predicting the ‘Pneumonia’ class due to the use of class weights.
Model 3 (CNN with L2 Regularization and class weights):

Accuracy: 53%
Recall (Pneumonia): 80%
This model showed further improvements in terms of accuracy and recall compared to the previous models. However, similar to Model 2, the precision for the ‘No Pneumonia’ class was quite low.


## Conclusions
- The group of pneumonia cases has pixel values closer to 1 which might be due to the patchy consolidated area that indicates pneumonia in X-rays. 
- The chest X-rays of pneumonia cases appear to have distinct features compared to those of non-pneumonia cases . This indicates that the model can potentially learn these patterns to distinguish between pneumonia and non-pneumonia cases.
- All three models learned from the training data, as indicated by decreasing loss over epochs. However, they also showed signs of overfitting as indicated by increasing validation loss after the second epoch. Despite this, each subsequent model showed improvement in recall on the test data compared to its predecessor. This means each model was able to correctly identify more positive cases.
- The third model, which incorporated L2 regularization and dropout layers, achieved the highest recall on the test data (0.9513), indicating it was most successful at correctly identifying positive cases. This could potentially be a valuable tool for KNH Radiology and HIM departments in assisting with pneumonia diagnosis.


## Recommendations
- The CNN models developed can assist in identifying pneumonia cases from chest X-rays, thus aiding in faster and potentially more accurate diagnosis.
- To further improve model performance and generalizability, consider exploring other techniques to mitigate overfitting such as early stopping.
- Regular updates and retraining of the model with new data can help in maintaining its performance over time.
- It’s important to note that while the model can aid in diagnosis, it should not replace professional medical advice and should be used as a supplementary tool.


## Next Steps
- Model Integration: Beginning the process of integrating the model with existing hospital information systems.
- Performance Monitoring System: Set up a system for continuously monitoring the model’s performance in a real-world setting. 
- Staff Training: Planning and executing a training program for relevant staff members. This should cover how to use the model, interpret its results, and understand its limitations.





