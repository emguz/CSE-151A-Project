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

[Milestone II](explore.ipynb)

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

5: Update your README.md to include your new work and updates you have all added. Make sure to upload all code and notebooks. Provide links in your README.md

[Milestone III](preprocess.ipynb)

6. Conclusion section: What is the conclusion of your 1st model? What can be done to possibly improve it?

In conclusion, our first model was a decent starting point but is inconsistent. Our low recall for true but not false shows the unreliability of our current model so having a more complex SVM model should be able to determine when a shot is made

## Milestone IV

1: Train your second model. Make sure you use a different model than in MS3, and you must fine-tune your model to get an accurate comparison.

2: Evaluate your model and compare training vs. test error

3: Answer the questions: Where does your model fit in the fitting graph? and What are the next models you are thinking of and why?

4: Update your README.md to include your new work and updates you have all added. Make sure to upload all code and notebooks. Provide links in your README.md

  [Milestone IV](modelling.ipynb)
  
5. Conclusion section: What is the conclusion of your 2nd model? What can be done to possibly improve it? Note: The conclusion section should be it's own independent section. i.e. Methods: will have models 1 and 2 methods, Conclusion: will have models 1 and 2 results and discussion. 

6. Provide predictions of correct and FP and FN from your test dataset.

*TODO*
- Explain that our testing and training error are similar suggesting that we are properly fitted.
- Add the fitting graph images and explain that we fitted (or slightly over/under fitted) because of how we tuned or hyperparameters
- Suggest using an Artificial Neural Network or something to leverage our many observations.

