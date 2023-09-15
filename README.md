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


## Modelling
Model 1: Basic CNN

- Architecture: This model consists of a single convolutional layer, a pooling layer, a flattening layer, a fully connected layer, and an output layer. The convolutional layer uses 32 filters of size 3x3 and ‘relu’ activation function. The output layer uses ‘sigmoid’ activation function for the binary classification.Then the model is then compiled with adam optimizer and binary-crossentropy loss function due to the binary nature of the problem.

- Perfomance: From the training results, it appears that the model is learning as the loss is decreasing over epochs. However, the validation loss seems to be fluctuating and not necessarily decreasing, which could be a sign of overfitting. The model shows a test recall of 0.8256 and F1 score of 0.7692.

Model 2: CNN with L2 Regularization

- Architecture: This model is similar to Model 1 but adds L2 regularization to the convolutional and fully connected layers. L2 regularization technique prevents overfitting by adding a penalty term to the loss function. The penalty term is proportional to the square of the magnitude of the weights, which encourages the model to have smaller weights and thus a simpler model.
- Performance: The model shows improved performance with a test recall of 0.9205 and F1 score of 0.7692. However, the validation loss still fluctuates during training, indicating potential overfitting.The test results show a recall of 0.9205 and F1 score of 0.7692, which are better than your first model. This indicates that adding L2 regularization has improved the performance of your model.

Model 3: CNN with Dropout and Additional Convolutional Layer

- Architecture: This model adds more complexity by including an additional convolutional layer and dropout layers after each pooling layer and the fully connected layer. Dropout regularization technique randomly sets a fraction of input units to 0 at each update during training time, which helps prevent overfitting.
- Performance: The model shows further improved performance with a test recall of 0.9513 and F1 score of 0.7692. 


## Modelling Results
- Model 1 (Basic CNN): Showed signs of overfitting as the validation loss increased after the second epoch. It achieved a test loss of 0.9253, recall of 0.8256, and F1 score of 0.7692.

- Model 2 (CNN with L2 Regularization): Despite adding L2 regularization, this model also showed signs of overfitting. However, it improved in terms of training loss and recall compared to Model 1. The test loss was 0.8105, with a recall of 0.9205, and an F1 score of 0.7692.

- Model 3 (CNN with L2 Regularization and Dropout): This model added dropout layers and an additional convolutional layer to learn more complex features. Despite these additions, it still showed potential overfitting. The test results showed a loss of 0.7303, recall of 0.9513, and an F1 score of 0.7692.

In all three models, the F1 score remained constant at 0.6667 across all epochs for both training and validation sets. Despite signs of overfitting in all three models, each subsequent model showed improvement in recall on the test data compared to its predecessor.


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





