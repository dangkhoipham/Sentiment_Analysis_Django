# Deploy a sentiment analysis model to Heroku by Django 
## Introduction

The main purpose of this project is to build a web app for a machine learning model and deploy it into a cloud service so that we can build an API to get retrieve the predictions. The ML problem we consider in this test is the sentiment analysis for movie reviews (binary classification: positive or negative). 

## ML model and dataset

### Dataset
The dataset is movie reivews extracted from Imdb and can be found at [here](http://www.cs.cornell.edu/people/pabo/movie%2Dreview%2Ddata/). In this dataset, we have 1000 positive reviews and 1000 negative reviews

### Training model and building API

The classifier is based on Support Vector Machine and features are extracted by Tf-Idf. The modeling process can be found in the file `./modeling/ml_model.py`. The optimal classifier is saved to the binary file `model.file`.

The API is defined in the file `./modeling/views.py` and the url is defined in `./modeling/urls.py`

## Deployment

The optimal model is saved to binary file before being deployed. Firstly, we use Django to deploy it to a local machine to test the API. For example, we can call the API for a review as follows: 
1. Lauch the server on localhost
`python manage.py runserver`
2. Test the API
http://localhost:8000/model/api/predict/?review=This%is%a%great%movie. 

### Deploy to heroku
Heroku is platform that allows us to deploy our web application quickly. After creating a Heroku account and installing Heroku CLI, open terminal to set up the login credentials and create a remote.
- Create a remote for heroku git`heroku create`
- We can check the new remote by `git remote -v`
- Push the web app to Heroku service `git push heroku master`
