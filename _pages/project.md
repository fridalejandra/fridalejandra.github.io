---
layout: research
title: "Research"
permalink: /research/
---

## Predicting Penguin Body Mass 
[Code](https://colab.research.google.com/drive/1J4wXknTVbelWBQYBGbdF_wsY-XkK__2m?usp=sharing)
[Data](https://archive.ics.uci.edu/dataset/690/palmer+penguins-3) 

---

## Introduction

Accurately predicting the biological traits of animals from physical and ecological data is a key application of machine learning in ecological research. This study utilizes the Palmer Penguins dataset, which contains morphological and ecological data for three penguin species—Adélie, Gentoo, and Chinstrap—observed on islands in the Palmer Archipelago, Antarctica. The dataset includes features such as bill length, bill depth, flipper length, body mass, and sex, along with categorical variables such as species and island location.

The objective of this research is to develop predictive models to predict penguin body weight. The ability to accurately predict body weight is important for ecological monitoring and conservation projects, particularly in rapidly changing environments like the Antarctic. To achieve this, I compare the performance of different machine learning models, including Random Forest and Ridge Regression.

In addition to model development, the study employs preprocessing techniques, such as handling missing data, encoding categorical variables, and scaling numerical features, which enhance model reliability and generalizability. By interpreting the results of the predictive models, this study seeks to uncover key relationships between morphological traits and body weight, contributing to a broader understanding of penguin ecology and offering a replicable framework for similar ecological research.

---

## Data
This study uses the Palmer Station Long-Term Ecological Research (PAL-LTER) dataset, which provides morphological and ecological data for three penguin species: Adélie (Pygoscelis adeliae), Gentoo (Pygoscelis papua), and Chinstrap (Pygoscelis antarcticus). The data were collected from penguin populations on the Biscoe, Dream, and Torgersen islands in the Palmer Archipelago, Antarctica. The dataset consists of 344 observations and includes both numerical and categorical variables.

The numerical features include bill length (mm), bill depth (mm), flipper length (mm), and body mass (g), each of which are key morphological measurements for penguins. The categorical data includes species, sex, and island, along with the year of data collection. These features are important for body weight prediction and their ability to capture ecological variation among the penguins.

Some missing values are present in the dataset, particularly in the 'sex' column, requiring imputation or removal to ensure data integrity. Additionally, numerical features exhibit varying scales, requiring standardization before model training. The dataset’s size allows for efficient analysis while providing sufficient complexity to test a range of machine learning models.

The target variable for this study is the body weight of the penguin, making this a supervised classification problem. By leveraging these features, this research aims to identify key predictors of body weight and assess the effectiveness of machine learning models in accurately classifying penguin populations.

## Modelling

### Feature Engineering
Feature engineering included:
- Encoding categorical variables: Species, island, and sex were encoded as dummy variables for machine learning compatibility.
- Handling missing values: Missing values in the sex column were dropped to ensure data integrity.
- Standardization: Numerical features such as bill length, bill depth, and flipper length were standardized where necessary for models like Ridge Regression.

### Model Selection 
Random Forest Regressor:
A tree-based ensemble method known for capturing non-linear relationships and feature interactions.

Linear Regression:
A baseline model to establish performance benchmarks.

Ridge Regression:
An extension of Linear Regression with L2 regularization to prevent over-fitting.

Ensemble Model:
Combines predictions from the three models using a weighted average, leveraging the strengths of each. In order to evaluate each model, RMSE (Root Mean Squared Error): Quantifies the average error in predictions, penalizing larger errors more heavily.
R² Score: Measures the proportion of variance explained by the model, with a value close to 1 indicating a good fit.

## Results
Model	RMSE	R² Score
Random Forest	195.23	0.94
Linear Regression	210.56	0.92
Ridge Regression	208.47	0.93
Ensemble	196.15	0.94
Feature Importance

Random Forest identified flipper_length_mm and species as the most significant predictors of body mass, followed by bill_depth_mm. Coefficients from Linear and Ridge Regression supported these findings, albeit with smaller magnitudes due to regularization in Ridge Regression.
REC Curve

A Regression Error Characteristic (REC) curve was plotted to compare the fraction of predictions within various error thresholds for all models. The ensemble model demonstrated consistently better performance, with the highest fraction of predictions falling within smaller error margins.

## Discussion
Random Forest performed best overall, achieving the lowest RMSE and highest R². Its ability to handle non-linear relationships and interactions likely contributed to its superior performance.
Linear and Ridge Regression provided interpretable models, with Ridge Regression showing reduced overfitting due to regularization.
Ensemble Model combined the strengths of all models, achieving performance nearly equal to Random Forest but with greater robustness across error thresholds, as shown in the REC curve.

- Key Predictors were: Flipper length (mm) was the most influential feature across all models, highlighting its strong correlation with penguin body mass. Species contributed significantly, reflecting interspecies differences in morphology and ecology.

- Ecological Implications

The results reinforce the utility of morphological traits in ecological monitoring. Predicting body mass with high accuracy can help researchers assess penguin health and adapt conservation strategies in response to environmental changes. The framework established here is adaptable to other species and ecosystems.

## Conclusion
This study demonstrates the applicability of machine learning techniques to the prediction of body weight using the Palmer Penguins dataset. By leveraging morphological and ecological features, such as numerical data like bill length, bill depth, flipper length, body mass, and categorical data like island and sex, I developed models capable of predicting body weight for Adélie, Gentoo, and Chinstrap penguins.

The results highlight the importance of data preprocessing, including handling missing values, encoding categorical variables, and standardizing numerical features, to ensure robust model performance. The application of different techniques, namely Random Forest and Ridge Regression, captured predictive relationships within the data.

Beyond predictive accuracy, this study underscores the value of machine learning in uncovering ecological patterns and relationships that may inform biodiversity monitoring and conservation efforts. The framework established here can be adapted for similar ecological classification tasks, offering a replicable approach for future studies involving ecological datasets.

Future work could explore the integration of additional ecological or environmental variables, as well as the application of these methods to larger or more complex datasets. By advancing the use of machine learning in ecological research, such studies can contribute to a deeper understanding of species differentiation and ecological dynamics.

## References
[1] 

[back](./)

