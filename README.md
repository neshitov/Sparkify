# Sparkify
## Project overview
The goal of this project is to build a customer churn prediciton model. We analyze user interactions with
fictious "sparkify" audio streaming service. Given a history of user actions, the model
has to predict whether is is likely that the user will downgrade from paid to the free account level.
### Dataset
We analyze a 12GB log dataset describing user interactions with the service. The data is avaliable at Udacity Amazon s3 bucket: s3n://udacity-dsnd/sparkify/sparkify_event_data.json
Every log entry includes the service page user interacted with ('next song', 'thumbs up', 'settings', etc),
user id, session id, user account level, and the timestamp.

## Model constructions
### Features design
To apply machine learning algorithms we transform log data into a feature dataset.
For every user we record the binary label indicating if the user churned and 24 numerical features: 
* the average session duration, 
* number of sessions, 
* for every page of the service 
the average time user spent on the page, 

### Prediction model
After creating a feature dataset we split the dataset in train and test parts.
We train perform feature sacaling and train logistic regression model on the training dataset.
We then use the area under ROC on the test set to evaluate the model. 
Logistic regresision model achieves 0.772 area under ROC

![alt text](https://github.com/neshitov/Sparkify/blob/master/lr_roc.png)

Then we train gradient boosted trees classifier that shows slightly better performance and achieves
0.794 area under ROC on the test set.

![alt text](https://github.com/neshitov/Sparkify/blob/master/gb_roc.png)
## Implementation details
Feature engineering and training of ML learning algorithms is performed using Apache Spark Python API.
Training is done on Amazon ElasticMapReduce cluster.
### Libraries used
* NumPy 1.15.4
* Pandas 0.23.4
* PySpark version 2.4.0
### Code
All the code is contained in the sparkify jupyter notebook
