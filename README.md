# CSE-151A-Project

![Open In Colab] 

1. Create a GitHub ID

2. Create a GitHub Repository (Public or Private it is up to you. In the end it will have to be Public) and add your group members as collaborators

Linked here: https://github.com/emguz/CSE-151A-Project

3. Perform the data exploration step (i.e. evaluate your data, # of observations, details about your data distributions, scales, missing data, column descriptions) Note: For image data you can still describe your data by the number of classes, # of images, plot example classes of the image, size of images, are sizes uniform? Do they need to be cropped? normalized? etc.

Done in 'combine_data_csv' and 'explore,' where the former combines our raw data files into one csv for analysis, and the latter evaluates data attributes, observations, and visualizations. 

4. Plot your data. For tabular data, you will need to run scatters, for image data, you will need to plot your example classes.

Done in 'explore,' with a heatmap of numerical attributes and a pairplot of a small random sample of data pieces (full dataset too large to run atm).

5. How will you preprocess your data? You should only explain (do not perform pre-processing as that is in MS3) this in your README.md file and link your Jupyter notebook to it. All code and  Jupyter notebooks have be uploaded to your repo.

We plan to encode some ordinal values for streamlined analysis in future milestones: this includes encoding attributes such as event type, shot type, zone, etc. that can be used to anticipate our final predictor variable (shot success). Most of our data from Kaggle is already cleaned, no empty values excluding a few 'nan' for player positions when shots are made, which is expected.

6. You must also include in your Jupyter Notebook, a link for data download and environment setup requirements:

Data can be downloaded via Kaggle, here: https://www.kaggle.com/datasets/mexwell/nba-shots
Environment should be set up via Anaconda, with installed glob (installation code included in 'combine_data_csv'), and other standard libraries such as numpy, seaborn, sklearn, and pandas. 

[Link to primary notebook file](explore.ipynb)
