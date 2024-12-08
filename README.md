# CSE-151A-Project


## Milestone II

1. Create a GitHub ID

2. Create a GitHub Repository (Public or Private it is up to you. In the end it will have to be Public) and add your group members as collaborators

Linked here: https://github.com/emguz/CSE-151A-Project

3. Perform the data exploration step (i.e. evaluate your data, # of observations, details about your data distributions, scales, missing data, column descriptions) Note: For image data you can still describe your data by the number of classes, # of images, plot example classes of the image, size of images, are sizes uniform? Do they need to be cropped? normalized? etc.

**Data Overview** 

- Observations: 4,231,262
- Features: 26
- Feature Breakdown: Identifiers (e.g. TEAM_ID, PLAYER_ID, GAME_ID), categorical date (e.g. POSITION_GROUP, ACTION_TYPE, SHOT_TYPE) numerical data (coordinates - LOC_X & LOC-Y, SHOT_DISTANCE, QUARTER, MINS_LEFT, SECS_LEFT)

**Preprocessing**

- Our data is mostly complete, with some data to do with location missing. Any shots with missing data were dropped.
- Our inital data helped us look at how the data was distributted so we could get a sense of what type of models we could try out.
- We dropped any columns that were highly correlated. To do this we looked at the heatmap.

![heatmap](images/heatmap.png)

4. Plot your data. For tabular data, you will need to run scatters, for image data, you will need to plot your example classes.

![pairplot](images/pairplot.png)

6. How will you preprocess your data? You should only explain (do not perform pre-processing as that is in MS3) this in your README.md file and link your Jupyter notebook to it. All code and  Jupyter notebooks have be uploaded to your repo.

We plan to encode some ordinal values for streamlined analysis in future milestones: this includes encoding attributes such as event type, shot type, zone, etc. that can be used to anticipate our final predictor variable (shot success). Most of our data from Kaggle is already cleaned, no empty values excluding a few 'nan' for player positions when shots are made, which is expected.

6. You must also include in your Jupyter Notebook, a link for data download and environment setup requirements:

Data can be downloaded via Kaggle, here: https://www.kaggle.com/datasets/mexwell/nba-shots
Environment should be set up via Anaconda, with installed glob (installation code included in 'combine_data_csv'), and other standard libraries such as numpy, seaborn, sklearn, and pandas. 

[Milestone II Notebook](explore.ipynb)

## Milestone III

1: Finish Major Preprocessing

Finish major preprocessing, this includes scaling and/or transforming your data, imputing your data, encoding your data, feature expansion, Feature expansion (example is taking features and generating new features by transforming via polynomial, log multiplication of features).

2: Train your first model

3: Evaluate your model and compare training vs. test error

*Training report*

| Class     | Precision | Recall | F1-Score | Support  |
|-----------|-----------|--------|----------|----------|
| False     | 0.62      | 0.85   | 0.71     | 1835231  |
| True      | 0.67      | 0.38   | 0.48     | 1549778  |
| **Accuracy** |         |        | 0.63     | 3385009  |
| **Macro Avg** | 0.64   | 0.61   | 0.60     | 3385009  |
| **Weighted Avg** | 0.64   | 0.63   | 0.61     | 3385009  |

*Testing report*

| Class     | Precision | Recall | F1-Score | Support  |
|-----------|-----------|--------|----------|----------|
| False     | 0.62      | 0.84   | 0.71     | 459481   |
| True      | 0.67      | 0.38   | 0.48     | 386772   |
| **Accuracy** |         |        | 0.63     | 846253   |
| **Macro Avg** | 0.64   | 0.61   | 0.60     | 846253   |
| **Weighted Avg** | 0.64   | 0.63   | 0.61     | 846253   |


4: Answer the questions: Where does your model fit in the fitting graph? and What are the next models you are thinking of and why?

Our model is doing an okay job but is underfitting the graph because our recall is low and our accuracy isn't great. This means we need to add more complexity to our model which is why we were thinking about using SVM models because it can handle higher complexity and can handle non-linear data better.

![logfitting](images/logfitting.png)

5: Update your README.md to include your new work and updates you have all added. Make sure to upload all code and notebooks. Provide links in your README.md

[Milestone III Notebook](preprocess.ipynb)

6. Conclusion section: What is the conclusion of your 1st model? What can be done to possibly improve it?

In conclusion, our first model was a decent starting point but is inconsistent. Our low recall for true but not false shows the unreliability of our current model so having a more complex SVM model should be able to determine when a shot is made

## Milestone IV

1: Train your second model. Make sure you use a different model than in MS3, and you must fine-tune your model to get an accurate comparison.

For our second model, we employed a Decision Tree using Gini Impurity. To fine tune, we trained our model on various levels of complexity to find the optimal fit.

2: Evaluate your model and compare training vs. test error

**Training Performance**

| Class       | Precision | Recall | F1-Score | Support  |
|-------------|-----------|--------|----------|----------|
| **False**   | 0.62      | 0.85   | 0.72     | 1,831,715 |
| **True**    | 0.69      | 0.39   | 0.50     | 1,546,950 |
| **Accuracy**|           |        | 0.64     | 3,378,665 |
| **Macro Avg** | 0.65    | 0.62   | 0.61     | 3,378,665 |
| **Weighted Avg** | 0.65 | 0.64   | 0.62     | 3,378,665 |

---

**Test Performance**

| Class       | Precision | Recall | F1-Score | Support |
|-------------|-----------|--------|----------|---------|
| **False**   | 0.62      | 0.85   | 0.72     | 458,689 |
| **True**    | 0.68      | 0.39   | 0.50     | 385,978 |
| **Accuracy**|           |        | 0.64     | 844,667 |
| **Macro Avg** | 0.65    | 0.62   | 0.61     | 844,667 |
| **Weighted Avg** | 0.65 | 0.64   | 0.62     | 844,667 |

The model is mediocre, performing only slightly better than a naive classifier with an accuracy of .64. Similar to our first model, this models struggles with recalling True values.

3: Answer the questions: Where does your model fit in the fitting graph? and What are the next models you are thinking of and why?

![fittinggraph](images/fittinggraph.png)

Our model is fitted well in the fitting graph. It strikes the balance between underfitting and overfitting, lying at the local minima of the test log-loss curve. Some optimization could be made to improve perfomance for **True**, such as adjusting the class weight for **True**, and employing a Decision Tree with modified thresholds for certain decision nodes. Given that we have a lot of observations to work with, using an Artificial Neural Network may allow us to finely tune our decision thresholds for **True**. 

4: Update your README.md to include your new work and updates you have all added. Make sure to upload all code and notebooks. Provide links in your README.md

[Milestone IV Notebook](modelling.ipynb)

For our second model, we used a Decision Tree.
Utilizing the train/test splits from the previous model, we fit the Decision Tree on a variety of complexities. After computing the predictions and the Log Loss for each train/test run, we plotted each model on a train/test error vs complexity graph to determine the optimal complexity, which was 10. 
We calculated metrics using the optimal model, creating a confusion matrix, a classification report for train and test performance, Log Loss, and other statistics.  
  
5. Conclusion section: What is the conclusion of your 2nd model? What can be done to possibly improve it? Note: The conclusion section should be it's own independent section. i.e. Methods: will have models 1 and 2 methods, Conclusion: will have models 1 and 2 results and discussion. 

Model 2 Conclusion

The second model performs similarly, if not slightly better, to our first model. Like the first model, the second model also struggles with misclassifying shot successes as **False**, with a recall for **True** of .39. **True** precision and recall, **False** recall, and accuracy have marginally improved by about 1 percent from the first model. Other metrics have not shifted. Although the model is well-fitted, it performs only marginally better than our Logistic Regression model, which is inadequate. Some optimization could be made to improve perfomance for **True**, such as adjusting the class weight for **True**, or adjusting the feature importance scores for features that impact **True** recall significantly. 
 
6. Provide predictions of correct and FP and FN from your test dataset.

Correct: TP + TN = 386,637 + 146,726 = 533,363

FP: 72,052

FN: 239,252

We also have a table with the predictions classified as correct, FP or FN in the notebook. Here is the head.

**Classified predictions of Test Dataset:**

We provided this in the notebook, but here is a sample.


|          | Actual  | Predicted | Type    |
|----------|---------|-----------|---------|
| 1118264  | False   | False     | Correct |
| 3970316  | True    | True      | Correct |
| 1457364  | False   | False     | Correct |
| 1849149  | False   | True      | FN      |
| 2776147  | False   | False     | Correct |



## Milestone 5

### INTRODUCTION

Our project aimed to develop a model to predict whether or not an NBA field goal will be made, given game and shot details. Our dataset was acquired from Kaggle, and contained NBA in-season and post-season shots taken from 2003-2024. It includes features such as cartesian coordinates of shot, player position, time left in quarter, and more. The model is trained to predict what factors lead to shot success, which would be incredibly useful to players to visualize and measure the contributing features to making points. With a reliable predictive model, we can reveal what controllable features are most valuable in ensuring that a shot is made, ultimately leading to NBA team and player success.

We developed two models, a Logistic Regression and Decision Tree predictor model, and evaluated each using performance metrics such as precision, recall, and accuracy. Ultimately, both models performed alright, but not incredibly strong.

### METHODS

#### Data Exploration
During the data exploration phase, a few basic visualizations were constructed to better understand the working data. Taking snapshots of data, features were separated into categories: identifiers (TEAM_ID, PLAYER_ID, etc), categorical data (ACTION_TYPE, SHOT_TYPE, etc), and numerical data (LOC_X, LOC_Y, SECS_LEFT, etc). The first heatmap and pairplots gave a general overview of correlation, where feature distribution and some expected correlations were noted. Next steps included a plan to encode features for streamlined analysis, as well as excluding Nan and null values.

#### Preprocessing
There was minimal work to be done for data preprocessing, as the files obtained from Kaggle were mostly cleaned, already. During the exploration phase, there were minimal irregularities and outliers. Our preprocessing consisted of encoding categorical data, dropping missing values (few out of 4.2mil total observations), excluding any unrelated/duplicate features. 

#### Model 1
The first constructed model was a Logistic Regression model. Our data was split 80:20 for training and testing, with scaling of numerical data post-split. We ran classification reports on both train and test data (actual vs predicted) to evaluate performance. 

#### Model 2
The second model constructed was a Decision Tree Classifier using Gini Impurity, in order to capture greater complexity. We tested various hyperparameters to find an optimal fit, while still maintaining generalizability and preventing any model overfitting. In a fitting graph to measure error and complexity, the Decision Tree model was fitted well, lying between under and overfitting. Similar to the Logistic Regression model, training and testing performance was observed in classification reports.


### RESULTS

#### Data Exploration
Generating heatmaps and pairplots of the data, there were a few expected trends—for example, higher correlation between shot distance vs y-coordinate, shot distance vs shot type; dense limited ranges of values for locational values (limited to court size). Otherwise, there were limited linear correlations.

<img src="./images/heatmap.png" alt="heatmap" width="800">
<img src="./images/pairplot.png" alt="pairplot" width="800">

#### Preprocessing
After preprocessing, the final dataset contained 15 features with 4,223,332 observations. Missing values were dropped, reducing around 0.002% of total observations of the raw Kaggle data. Categorical variables were encoded and highly correlated features dropped (shot type vs distance, etc), reducing 4 out of the starting 19 attributes. After splitting the data into training and testing sets and scaling the numerical measures, the data is prepared for analysis.

```
xTrain shape: (3378665, 15)
yTrain shape: (3378665,)
xTest shape: (844667, 15)
yTest shape: (844667,)
```

#### Model 1
The Logistic Regression model performed relatively mediocre, with an accuracy of 0.63 on predicting both train and test data. There is average precision and low recall for True values. When plotting error against regularization strength (graph below), we can observe that increasing regularization strength does not significantly decrease model error. This suggests that the model may be underfitting the data. 

*Training report*

| Class     | Precision | Recall | F1-Score | Support  |
|-----------|-----------|--------|----------|----------|
| False     | 0.62      | 0.85   | 0.71     | 1835231  |
| True      | 0.67      | 0.38   | 0.48     | 1549778  |
| **Accuracy** |         |        | 0.63     | 3385009  |
| **Macro Avg** | 0.64   | 0.61   | 0.60     | 3385009  |
| **Weighted Avg** | 0.64   | 0.63   | 0.61     | 3385009  |

*Testing report*

| Class     | Precision | Recall | F1-Score | Support  |
|-----------|-----------|--------|----------|----------|
| False     | 0.62      | 0.84   | 0.71     | 459481   |
| True      | 0.67      | 0.38   | 0.48     | 386772   |
| **Accuracy** |         |        | 0.63     | 846253   |
| **Macro Avg** | 0.64   | 0.61   | 0.60     | 846253   |
| **Weighted Avg** | 0.64   | 0.63   | 0.61     | 846253   |

<img src="./images/logfitting.png" alt="logfitting" width="800">


### Model 2
The Decision Tree model performed minimally better than the previous Logistic Regression model, with a slightly greater accuracy (0.64 compared to 0.63) and minimally improved precision and recall for each outcome. Like the last model, recall for True values is weak. Observing the graph of error vs model complexity, the model finds the optimal depth for minimizing error (at a maximum depth of 10).

**Training Performance**

| Class       | Precision | Recall | F1-Score | Support  |
|-------------|-----------|--------|----------|----------|
| **False**   | 0.62      | 0.85   | 0.72     | 1,831,715 |
| **True**    | 0.69      | 0.39   | 0.50     | 1,546,950 |
| **Accuracy**|           |        | 0.64     | 3,378,665 |
| **Macro Avg** | 0.65    | 0.62   | 0.61     | 3,378,665 |
| **Weighted Avg** | 0.65 | 0.64   | 0.62     | 3,378,665 |

---

**Test Performance**

| Class       | Precision | Recall | F1-Score | Support |
|-------------|-----------|--------|----------|---------|
| **False**   | 0.62      | 0.85   | 0.72     | 458,689 |
| **True**    | 0.68      | 0.39   | 0.50     | 385,978 |
| **Accuracy**|           |        | 0.64     | 844,667 |
| **Macro Avg** | 0.65    | 0.62   | 0.61     | 844,667 |
| **Weighted Avg** | 0.65 | 0.64   | 0.62     | 844,667 |

<img src="./images/fittinggraph.png" alt="logfitting" width="800">
![fittinggraph](images/fittinggraph.png)


### DISCUSSION

Our team's plan, as a generalization, was to start simple and tune as we made new observations through each step and additional model. Through our data exploration, we were looking for any clear, significant relationships between features that could give us insight into what may be the most important in shot success. However, there was nothing that particularly jumped out, indicating early on that our data was more complex than direct paired relationships. Next, with our logistic regression model, we could see how well a simple machine learning model performs to predict our data of interest. It didn't perform amazingly well, but also was not completely hopeless. Results were not unexpected—performance across measures of precision, recall, and accuracy were mediocre, with the model especially struggling with recall. Because there were not significant correlations in our exploratory graphs, there wasn't an expectation of great predictability.

With our final Decision Tree Classifier, we hoped to study our data with a model more capable of handling complex data. We also tuned various hyperparameters to find an optimal fit, which did improve performance, but minimally so. The results for this final model are still a bit lacking, indicating that perhaps our data is too complex, or that there is no significant relationship between our measured attributes and our target variable.


### CONCLUSION

For potential next steps, different types of models could be created that may have a better performance than those that we tried. SVMs or neural network models may do better at handling complex data. Any patterns that exist between different attributes seem subtle, and might only be picked up with models that structure or analyze data through a more complex front. To achieve greater performance through our models, it would have been more efficient to start with such models from the beginning, after our team noticed that there were no clear correlations in exploration.

However, another likely possibility is that there simply are no good measurable factors within our dataset that can accurately predict shot success in the NBA. More than likely, there are non-physical factors that contribute (player health, energy, stress level, etc) that simply aren't practical to measure or are unable to be manipulated. 


### STATEMENT OF COLLABORATION

Emil Guzman (Project Manager): Project planning + ideation, data processing
Nicholas Jobe (Coding): Model creation + training, data visualization
Kekoa Picket (Coding): Model creation + training, data visualization
Ethan Han (Analysis): Data exploration, model evaluation + visualization
Stephanie Li (Writing): Data exploration, data preprocessing, milestone writing

