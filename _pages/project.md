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

The objective of this research is to develop predictive models to classify penguin species based on their physical measurements and ecological attributes. The ability to accurately predict body weight is important for ecological monitoring and conservation projects, particularly in rapidly changing environments like the Antarctic. To achieve this, I compare the performance of different machine learning models, including Random Forest and Ridge Regression.

In addition to model development, the study employs preprocessing techniques, such as handling missing data, encoding categorical variables, and scaling numerical features, which enhance model reliability and generalizability. By interpreting the results of the predictive models, this study seeks to uncover key relationships between morphological traits and body weight, contributing to a broader understanding of penguin ecology and offering a replicable framework for similar ecological research.

---

## Data
This study uses the Palmer Station Long-Term Ecological Research (PAL-LTER) dataset, which provides morphological and ecological data for three penguin species: Adélie (Pygoscelis adeliae), Gentoo (Pygoscelis papua), and Chinstrap (Pygoscelis antarcticus). The data were collected from penguin populations on the Biscoe, Dream, and Torgersen islands in the Palmer Archipelago, Antarctica. The dataset consists of 344 observations and includes both numerical and categorical variables.

The numerical features include bill length (mm), bill depth (mm), flipper length (mm), and body mass (g), each of which are key morphological measurements for penguins. The categorical data includes species, sex, and island, along with the year of data collection. These features are important for body weight prediction and their ability to capture ecological variation among the penguins.

Some missing values are present in the dataset, particularly in the 'sex' column, requiring imputation or removal to ensure data integrity. Additionally, numerical features exhibit varying scales, requiring standardization before model training. The dataset’s size allows for efficient analysis while providing sufficient complexity to test a range of machine learning models.

The target variable for this study is the body weight of the penguin, making this a supervised classification problem. By leveraging these features, this research aims to identify key predictors of body weight and assess the effectiveness of machine learning models in accurately classifying penguin populations.

## Modelling

### Feature Engineering

O


## Results


## Discussion


## Conclusion
This study demonstrates the applicability of machine learning techniques to the prediction of body weight using the Palmer Penguins dataset. By leveraging morphological and ecological features, such as numerical data like bill length, bill depth, flipper length, body mass, and categorical data like island and sex, I developed models capable of predicting body weight for Adélie, Gentoo, and Chinstrap penguins.

The results highlight the importance of data preprocessing, including handling missing values, encoding categorical variables, and standardizing numerical features, to ensure robust model performance. The application of different techniques, namely Random Forest and Ridge Regression, captured predictive relationships within the data.

Beyond predictive accuracy, this study underscores the value of machine learning in uncovering ecological patterns and relationships that may inform biodiversity monitoring and conservation efforts. The framework established here can be adapted for similar ecological classification tasks, offering a replicable approach for future studies involving ecological datasets.

Future work could explore the integration of additional ecological or environmental variables, as well as the application of these methods to larger or more complex datasets. By advancing the use of machine learning in ecological research, such studies can contribute to a deeper understanding of species differentiation and ecological dynamics.

## References
[1] DALL-E 3

[back](./)

