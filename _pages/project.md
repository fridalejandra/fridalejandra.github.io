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
Accurately predicting the biological traits of animals from physical and ecological data is a key application of machine learning in ecological research. This study utilizes the Palmer Penguins dataset, which contains morphological and ecological data for three penguin species—Adélie (*Pygoscelis adeliae*), Gentoo (*Pygoscelis papua*), and Chinstrap (*Pygoscelis antarcticus*)—observed on islands in the Palmer Archipelago, Antarctica [1]. The dataset includes features such as bill length, bill depth, flipper length, body mass, and sex, along with categorical variables such as species and island location.

The objective of this study is to develop machine learning models to accurately predict penguin body mass based on morphological and ecological features derived from the Palmer Penguins dataset.  To achieve this, I compare the performance of different machine learning models, including Random Forest and Ridge Regression [3, 4].

In addition to model development, the study employs preprocessing techniques, such as handling missing data, encoding categorical variables, and scaling numerical features, which enhance model reliability and generalizability [5]. By interpreting the results of the predictive models, this study seeks to uncover key relationships between morphological traits and body weight, contributing to a broader understanding of penguin ecology and offering a replicable framework for similar ecological research.

This is a **supervised regression problem**, as the goal is to predict a continuous target variable, body mass (in grams), based on labeled input features. Accurately predicting body weight is important for ecological monitoring and conservation efforts, particularly in rapidly changing environments like the Antarctic [2]. 

In addition to model development, the study employs preprocessing techniques, such as handling missing data [5], encoding categorical variables, and scaling numerical features, which enhance model reliability and generalizability. By interpreting the results of the predictive models, this study seeks to uncover key relationships between morphological traits and body weight, contributing to a broader understanding of penguin ecology and offering a replicable framework for similar ecological research [6].

---
---

## Data
This study uses the Palmer Station Long-Term Ecological Research (PAL-LTER) dataset, which provides morphological and ecological data for three penguin species: Adélie (*Pygoscelis adeliae*), Gentoo (*Pygoscelis papua*), and Chinstrap (*Pygoscelis antarcticus*) [1, 6]. The data were collected from penguin populations on the Biscoe, Dream, and Torgersen islands in the Palmer Archipelago, Antarctica. The dataset consists of 344 observations and includes both numerical and categorical variables.

The numerical features include bill length (mm), bill depth (mm), flipper length (mm), and body mass (g), each of which are key morphological measurements for penguins [1]. The categorical data includes species, sex, and island, along with the year of data collection. These features are important for body weight prediction and their ability to capture ecological variation among the penguins.

Some missing values are present in the dataset, particularly in the 'sex' column, requiring imputation or removal to ensure data integrity [5, 7]. Additionally, numerical features exhibit varying scales, requiring standardization before model training [8]. The dataset’s size allows for efficient analysis while providing sufficient complexity to test a range of machine learning models.


---

## Modeling

Feature engineering included encoding categorical variables such as species, island, and sex into dummy variables for machine learning compatibility. Missing values in the 'sex' column were dropped to ensure data integrity. Numerical features such as bill length, bill depth, and flipper length were standardized where necessary for models like Ridge Regression.

Four machine learning models were trained and evaluated in this study. Random Forest, a tree-based ensemble method, was included for its ability to capture non-linear relationships and feature interactions. Linear Regression served as a baseline model to establish performance benchmarks. Ridge Regression, an extension of Linear Regression with L2 regularization, was used to mitigate overfitting. Finally, an Ensemble Model was implemented by combining the predictions of the three models using a weighted average, leveraging the strengths of each.

The models were evaluated using two primary metrics. RMSE (Root Mean Squared Error) quantifies the average error in predictions, penalizing larger errors more heavily. R² Score measures the proportion of variance in body mass explained by the model, with a value close to 1 indicating a good fit.

---

## Results

The performance of each model is summarized in **Table 1** below. RMSE values indicate the average error in predictions, while R² measures the proportion of variance in body mass explained by the model.

**Table 1. Model Performance Metrics**

| Model              | RMSE (g)      | R² Score      |
|--------------------|---------------|---------------|
| Random Forest      | 195.23        | 0.94          |
| Linear Regression  | 210.56        | 0.92          |
| Ridge Regression   | 208.47        | 0.93          |
| Ensemble Model     | 196.15        | 0.94          |

Random Forest identified `flipper_length_mm` and `species` as the most significant predictors of body mass, followed by `bill_depth_mm`. Coefficients from Linear and Ridge Regression supported these findings, with Ridge Regression reducing coefficient magnitudes due to L2 regularization.

A Regression Error Characteristic (REC) curve was plotted to compare the fraction of predictions within varying error thresholds for all models. The ensemble model demonstrated consistently better performance, maintaining the highest fraction of predictions within smaller error margins.

![REC Curve](/images/rec_curve.png )
*(Figure 1: REC Curve showing model performance across varying error thresholds.)*

The **Actual vs Predicted** plot (Figure 2) compares the predictions of all models (Random Forest, Linear Regression, Ridge Regression, and Ensemble) on a single chart. The diagonal red line represents the ideal fit, where predictions perfectly match the actual values. Models with points closer to this line demonstrate better predictive performance.

![Actual vs Predicted: Combined](/images/ActualvsPredicted_Ensemble.png)
*(Figure 2: Actual vs Predicted for Random Forest, Linear Regression, Ridge Regression, and Ensemble.)*

---

## Discussion

Random Forest performed best overall, achieving the lowest RMSE and highest R². Its ability to handle non-linear relationships and interactions likely contributed to its superior performance. Linear and Ridge Regression provided interpretable models, with Ridge Regression showing reduced overfitting due to regularization. The Ensemble Model combined the strengths of all models, achieving performance nearly equal to Random Forest but with greater robustness across error thresholds, as shown in the REC curve.

Key predictors of body mass included flipper length and species, highlighting the strong correlation between these traits and body weight. These findings align with expectations, as species and flipper length are key indicators of penguin morphology and ecological adaptation.

The results reinforce the utility of morphological traits in ecological monitoring. Predicting body mass with high accuracy can help researchers assess penguin health and adapt conservation strategies in response to environmental changes. The framework established here is adaptable to other species and ecosystems.

---

## Conclusion
This study demonstrates the applicability of machine learning techniques to the prediction of body weight using the Palmer Penguins dataset. By leveraging morphological and ecological features, such as numerical data like bill length, bill depth, flipper length, body mass, and categorical data like island and sex, I developed models capable of predicting body weight for Adélie, Gentoo, and Chinstrap penguins.

The results highlight the importance of data preprocessing, including handling missing values, encoding categorical variables, and standardizing numerical features, to ensure robust model performance [5, 7, 8]. The application of different techniques, namely Random Forest and Ridge Regression, captured predictive relationships within the data [3, 4].

Beyond predictive accuracy, this study underscores the value of machine learning in uncovering ecological patterns and relationships that may inform biodiversity monitoring and conservation efforts [2]. The framework established here can be adapted for similar ecological classification tasks, offering a replicable approach for future studies involving ecological datasets [6].

Future work could explore the integration of additional ecological or environmental variables, as well as the application of these methods to larger or more complex datasets. By advancing the use of machine learning in ecological research, such studies can contribute to a deeper understanding of species differentiation and ecological dynamics.

---

## References

1. Horst, A.M., Hill, A.P., Gorman, K.B. "Palmer Penguins: An Alternative to the Iris Dataset." R package version 0.1.0. [https://allisonhorst.github.io/palmerpenguins/](https://allisonhorst.github.io/palmerpenguins/)  
2. Gorman, K.B., Williams, T.D., Fraser, W.R. "Ecological Sexual Dimorphism and Environmental Variability Within a Community of Antarctic Penguins." *PLoS ONE*. 9(3): e90081, 2014.  
3. Breiman, L. "Random Forests." *Machine Learning*. 45, 5–32, 2001.  
4. Hoerl, A.E., Kennard, R.W. "Ridge Regression: Biased Estimation for Nonorthogonal Problems." *Technometrics*. 12(1): 55–67, 1970.  
5. Little, R.J.A., Rubin, D.B. "Statistical Analysis with Missing Data." Wiley, 2002.  
6. Fraser, W.R., Hofmann, E.E. "A Predator's Perspective on Causal Links Between Climate Change, Physical Forcing, and Ecosystem Response." *Marine Ecology Progress Series*. 265: 1-15, 2003.  
7. Schafer, J.L. "Analysis of Incomplete Multivariate Data." *Chapman & Hall/CRC Monographs on Statistics & Applied Probability*. 1997.  
8. Kuhn, M., Johnson, K. "Applied Predictive Modeling." Springer, 2013.  


[back](./)

