# Cardiovascular Disease Prediction

A project that makes a data analysis and creates a model for classification of cardiovascular disease.

## Dataset Information

<p align="center">
  <img src="https://github.com/LuisNagano/cardiovascular_disease_prediction/blob/main/coracao-de-atleta-868.jpg" width="50%" alt="Cardiovascular System" />
</p>

This dataset was published on the Kaggle competition platform. For more information it can be seen accessing [this link](url-para-o-dataset-no-kaggle-aqui). However the context was created by author of the site [Be a Data Scientist](url-para-be-a-data-scientist-aqui).

### Attributes

1. Age | Objective Feature | age | int (days)
2. Height | Objective Feature | height | int (cm) |
3. Weight | Objective Feature | weight | float (kg) |
4. Gender | Objective Feature | gender | categorical code |
5. Systolic blood pressure | Examination Feature | ap_hi | int |
6. Diastolic blood pressure | Examination Feature | ap_lo | int |
7. Cholesterol | Examination Feature | cholesterol | 1: normal, 2: above normal, 3: well above normal |
8. Glucose | Examination Feature | gluc | 1: normal, 2: above normal, 3: well above normal |
9. Smoking | Subjective Feature | smoke | binary |
10. Alcohol intake | Subjective Feature | alco | binary |
11. Physical activity | Subjective Feature | active | binary |
12. Presence or absence of cardiovascular disease | Target Variable | cardio | binary |

## Context
> This context was created by Meigarom from [Be a Data Scientist](https://beadatascientist.com). So this is a totally fictional context.

Cardio Catch Diseases is a company that specializes in detecting heart disease in the early stages. Its business model is service type, that is, the company offers an early diagnosis of cardiovascular disease for a certain price.

Currently, the diagnosis of cardiovascular disease is made manually by a team of specialists. The current accuracy of the diagnosis varies between 55% and 65%, due to the complexity of the diagnosis and also the fatigue of the team who take turns to minimize the risks. O custo de cada diagnóstico, incluindo os aparelhos e a folha de pagamento dos analistas, gira em torno de $ 1,000.00.

The price of the diagnosis, paid by the client, varies according to the precision achieved by the team of specialists, the client pays R$ 500.00 for every 5% accuracy above 50%. For example, for an accuracy of 55%, the diagnosis costs R$ 500.00 for the client, for an accuracy of 60%, the value is R$ 1000.00 and so on. If the diagnostic accuracy is 50%, the customer does not pay for it.

## Objective

Your objective as the Data Scientist hired by Cardio Catch Diseases is to create a tool that increases the accuracy of the diagnosis and that this accuracy is stable for all diagnoses.

## Methodology

This project will be based on Cross-industry standard process for data mining (CRISP-DM). A standard idea about data science project may be linear: data preparation, modeling, evaluation and deployment. However, when we use CRISP-DM methodology a data science project become circle-like form. Even when it ends in Deployment, the project can restart again by Business Understanding. How might it help?

<p align="center">
  <img src="https://github.com/LuisNagano/cardiovascular_disease_prediction/blob/main/1024px-CRISP-DM_Process_Diagram.png" width="50%" alt="CRISP-DM Process" />
</p>

It may help to avoid the data scientist to stop in one specific step and waste time on it. When all the project is completed the data scientist can return to initial step and do every step again. Therefore, the main goal it is to follow circles as it needs.

## Pipeline

- Opening
- Data Descriptions
- Feature Engineering
- Data Exploration
- Filtering Variables
- Exploratory Data Analysis
- Data Preparation
- Feature Selection
- Machine Learning Modeling
- Hyperparameter Fine Tuning
- Traduction and Error's Interpretation
- Deploy

## References

- [Be a Data Scientist](#)
- [Cardiovascular Disease Dataset](#)
- [Image Reference](#)
- [CRISP-DM Image](#)
