# Develop and sell a Machine Learning API - from start to end tutorial

![https://unsplash.com/photos/LJ9KY8pIH3E](https://images.unsplash.com/photo-1542393545-10f5cde2c810?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=3401&q=80)
*Photo by Daniel Korpai https://unsplash.com/photos/HyTwtsk8XqA*



# Table of Contents

- [Develop and sell a Machine Learning API - from start to end tutorial](#develop-and-sell-a-machine-learning-api---from-start-to-end-tutorial)
- [Table of Contents](#table-of-contents)
- [About this article](#about-this-article)
- [Disclaimer](#disclaimer)
- [Stack used](#stack-used)
- [1. Create project formalities](#1-create-project-formalities)
- [2. Develop a solution for a problem](#2-develop-a-solution-for-a-problem)
  - [Install packages and track jupyter files properly](#install-packages-and-track-jupyter-files-properly)
  - [Develop solution to problem](#develop-solution-to-problem)
    - [The goal](#the-goal)
    - [Download data](#download-data)
    - [Preparation](#preparation)
    - [Create classifier and predict](#create-classifier-and-predict)
  - [Build server to execute function with REST](#build-server-to-execute-function-with-rest)
    - [Serve basic frontend](#serve-basic-frontend)
    - [Load prediction](#load-prediction)
  - [BONUS: Make reproducible with Docker](#bonus-make-reproducible-with-docker)
    - [Create Dockerfile](#create-dockerfile)
- [3. Deploy to AWS](#3-deploy-to-aws)
  - [Set up zappa](#set-up-zappa)
  - [Set up AWS](#set-up-aws)
    - [AWS credentials](#aws-credentials)
      - [Set up credentials with users and roles in IAM](#set-up-credentials-with-users-and-roles-in-iam)
      - [Add credentials in your project](#add-credentials-in-your-project)
  - [AWS API Gateway](#aws-api-gateway)
- [4. Set up Rapidapi](#4-set-up-rapidapi)
  - [Create API on Rapidapi](#create-api-on-rapidapi)
  - [Test your own API](#test-your-own-api)
    - [Create private plan for testing](#create-private-plan-for-testing)
    - [Test endpoint with rapidapi](#test-endpoint-with-rapidapi)
    - [Create code to consume API](#create-code-to-consume-api)
- [End result](#end-result)
- [Inspiration](#inspiration)
- [About](#about)

# About this article

In this article I take the ideas from my previous article ["How to sell a Python API from start to end"](https://towardsdatascience.com/develop-and-sell-a-python-api-from-start-to-end-tutorial-9a038e433966) further and build a machine learning application. If the steps described here are to rough consider reading my previous article first.

There are a number of new and more complicated issues to cover in this project:
1. Machine Learning content. The application takes basic steps of building a Machine Learning model. This covers the preparation, but also the prediction.
2. In time evaluation (not in time training) of the prediction. This means that the dataset is freshly fetched and the prediction is performed on the latest data.
3. Deployment. Deploying a Machine Learning app has various challenges. In this article we met and solved the issue of outsourcing the trained model on AWS.
4. It is not only an API but also has a minor frontend.

It paints a picture for developing a Python API from start to finish and provides help in more difficult areas like the setup with AWS Lambda.

There were various difficulties, which allowed me to learn more about the deployment and building process. It is also a great way to build side projects and maybe even make some money.

As the Table of content shows, it consists of 4 major parts, namely:
1. Setting up the environment
2. Creating a problem solution with Python
3. Setting up AWS
4. Setting up Rapidapi

You will find all my code open sourced on Github:

- https://github.com/Createdd/ml_api_covid

You will find the end result here on Rapidapi:

- https://rapidapi.com/Createdd/api/covid_new_cases_prediction

If you found this article helpful let me know and/or buy the functionality on Rapidapi to show support.


# Disclaimer

I am not associated with any of the services I use in this article.

I do not consider myself an expert. If you have the feeling that I am missing important steps or neglected something, consider pointing it out in the comment section or get in touch with me. Also, always make sure to monitor your AWS costs to not pay for things you do not know about.

I am always happy for constructive input and how to improve.

There are numerous things to improve and build upon. For example the machine learning part has very low effort. The preparation was very rough and many steps are missing. From my professional work I know this. However, I cannot cover every detail in one article. Nevertheless, I am curious to hear your suggestions on improvement in the comments. :)


# Stack used

We will use

- Github (Code hosting),
- Anaconda (Dependency and environment management),
- Docker (for possible further usage in microservices)
- Jupyter Notebook (code development and documentation),
- Python (programming language),
- AWS, especiall AWS Lambda and S3(for deployment),
- Rapidapi (market to sell)

---


# 1. Create project formalities

It's always the same but necessary. I do it along with these steps:

1. Create a local folder `mkdir NAME`
2. Create a new repository on Github with `NAME`
3. Create conda environment `conda create --name NAME python=3.7`
4. Register new environment in jupyter `ipython kernel install --name NAME--user`
5. Activate conda environment `conda activate PATH_TO_ENVIRONMENT`
6. Create git repo `git init`
7. Connect to Github repo. Add Readme file, commit it and

```sh
git remote add origin URL_TO_GIT_REPO
git push -u origin master
```

# 2. Develop a solution for a problem

As we will develop a Machine Learning solution, a Jupyter Notebook will be very useful.




## Install packages and track jupyter files properly

Install jupyter notebook and jupytext:

```sh
pip install notebook jupytext
```

set a hook in  `.git/hooks/pre-commit` for tracking the notebook changes in git properly:

```sh
touch .git/hooks/pre-commit
code  .git/hooks/pre-commit
```

copy this in the file
```sh
#!/bin/sh
# For every ipynb file in the git index, add a Python representation
jupytext --from ipynb --to py:light --pre-commit
```

afterwards for making the hook executable (on mac)
```sh
chmod +x .git/hooks/pre-commit
```

## Develop solution to problem

### The goal

As currently the world is in a pandemic I thought I use one of the multiple datasets for covid-19 cases.
Given the structure of the dataset we want to predict the new cases of infections per day for a country.


```py
pip install -r requirements.txt
```

This will install all packages we need. Have a look in the `/development/predict_covid.ipynb` notebook to see what libraries are used.

Most important are the libraries
- **pandas** for transforming the dataset and
-  **sklearn** for machine learning

For the following sub headings please check out the jupyter notebook for more details:
- https://github.com/Createdd/ml_api_covid/blob/master/development/predict_covid.ipynb


### Download data

We will use the dataset from https://ourworldindata.org/coronavirus-source-data in csv format.

### Preparation

In short I did:
1. Check for missing data
2. Remove columns with more than 50% missing data
3. Remove rows with remaining missing content like continent or isocode. (Not useful for my app solution which requires a country)
4. Encode categorical data with labels
5. Fill in remaining numerical missing data with the mean of the column
6. Split into training and test set

### Create classifier and predict

1. Create a Random Forest Regressor
2. Train it on the data and evaluate
3. Perform hyperparameter tuning with RandomizedSearchCV
4. Save trained model
5. Predict the new cases by providing a country name


## Build server to execute function with REST

For the API functionality we will use a Flask server (in `app.py`)
- https://github.com/Createdd/ml_api_covid/blob/master/app.py

### Serve basic frontend

```py
@app.route('/')
def home():
    return render_template("home.html")
```

Which serves a basic html and css file.

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>Predict Covid</title>

<link type="text/css" rel="stylesheet" href="{{ url_for('static', filename='./style.css') }}">

</head>

<body>
 <div class="page">
     <form if="form" action="{{ url_for('predict')}}"method="POST">
         <input type="text" name="country" placeholder="Country" required="required" /><br>
         <h3 class='res'>{{pred}}</h3>
         <button id="button" type="submit" class="btn btn-primary btn-block btn-large">Predict</button>
        </form>
 </div>
</body>
</html>
```

### Load prediction

This is a little more complex.

Key route is this:

```py
@app.route('/predict',methods=['POST'])
def predict():
    input_val = [x for x in request.form.values()][0]
    rf = load_model(BUCKET_NAME, MODEL_FILE_NAME, MODEL_LOCAL_PATH)

    if input_val not in available_countries:
        return f'Country {input_val} is not in available list. Try one from the list! Go back in your browser', 400

    to_pred = get_prediction_params(input_val, url_to_covid)
    prediction = rf.predict(to_pred)[0]

    return render_template('home.html',pred=f'New cases will be {prediction}')
```
But before we can return the prediction result we need to get the latest data and pre-process it again.
This is done with

```py

def pre_process(df):
    cols_too_many_missing = ['new_tests',
                             'new_tests_per_thousand',
                             'total_tests_per_thousand',
                             'total_tests',
                             'tests_per_case',
                             'positive_rate',
                             'new_tests_smoothed',
                             'new_tests_smoothed_per_thousand',
                             'tests_units',
                             'handwashing_facilities']
    df = df.drop(columns=cols_too_many_missing)

    nominal = df.select_dtypes(include=['object']).copy()
    nominal_cols = nominal.columns.tolist()

    for col in nominal_cols:
        col
        if df[col].isna().sum() > 0:
            df[col].fillna('MISSING', inplace=True)
        df[col] = encoder.fit_transform(df[col])

    numerical = df.select_dtypes(include=['float64']).copy()

    for col in numerical:
        df[col].fillna((df[col].mean()), inplace=True)

    X = df.drop(columns=['new_cases'])
    y = df.new_cases

    return X, y


def get_prediction_params(input_val, url_to_covid):
    df_orig = pd.read_csv(url_to_covid)
    _ = encoder.fit_transform(df_orig['location'])
    encode_ind = (encoder.classes_).tolist().index(input_val)
    df_orig[df_orig.location == input_val]

    X, _ = pre_process(df_orig)
    to_pred = X[X.location == encode_ind].iloc[-1].values.reshape(1,-1)

    return to_pred
```

`Pre-process` again transforms the downloaded dataset for machine learning purposes, whereas `get_prediction_params` takes the input value (which is the country to be predicted) and the url to the latest dataset.

Those processes make the prediction true for the latest data, but also slows down the app.

You might wonder why we do `rf = load_model(BUCKET_NAME, MODEL_FILE_NAME, MODEL_LOCAL_PATH)`.
The reason for this is that we need to load the pre-trained model from a AWS S3 bucket to save memory when executing everything with AWS Lambda. Scroll down for more details.

But if we do not want to deploy it in the cloud we can simply do something like `joblib.load(PATH_TO_YOUR_EXPORTED_MODEL)`. In the [notebook](https://github.com/Createdd/ml_api_covid/blob/master/development/predict_covid.ipynb) we export the the model with `joblib.dump`.
More info on model exports in the [sklearn docs](https://scikit-learn.org/stable/modules/model_persistence.html)

But that is the mere functionality of the FLAK server. Providing a route for serving the html template and a route for prediction. Quite simple!

Running now

```sh
env FLASK_APP=app.py FLASK_ENV=development flask run
```

will start the server.

## BONUS: Make reproducible with Docker

Maybe you want to scale the app or allow other people to test it more easily. For this we can create a Docker container. I will not explain in detail how it works but if you are interested check one of the links in my "Inspiration" section.

Building a Docker container is not necessary for making this application work!

### Create Dockerfile

```docker
FROM python:3.7

ENV PYTHONDONTWRITEBYTECODE=1
ENV PYTHONUNBUFFERED=1

ENV FLASK_APP=app.py
ENV FLASK_ENV=development

# install system dependencies
RUN apt-get update \
    && apt-get -y install gcc make \
    && rm -rf /var/lib/apt/lists/*s

RUN python3 --version
RUN pip3 --version

RUN pip install --no-cache-dir --upgrade pip

WORKDIR /app

COPY ./requirements.txt /app/requirements.txt

RUN pip3 install --no-cache-dir -r requirements.txt

COPY . .

EXPOSE 8080

CMD ["gunicorn", "--bind", "0.0.0.0:8080", "app:app"]
```

Note: the last line is for starting the Flask server

After creating the `Dockerfile` run

```sh
docker build -t YOUR_APP_NAME .
```
and afterwards

```sh
docker run -d -p 80:8080 YOUR_APP_NAME
```

Afterwards you will see your app running on `http://localhost/`

# 3. Deploy to AWS


## Set up zappa

After we created the app locally we need to start setting up the hosting on a real server.
We will use [zappa](https://github.com/Miserlou/Zappa).

> Zappa makes it super easy to build and deploy server-less, event-driven Python applications (including, but not limited to, WSGI web apps) on AWS Lambda + API Gateway. Think of it as "serverless" web hosting for your Python apps. That means infinite scaling, zero downtime, zero maintenance - and at a fraction of the cost of your current deployments!

```sh
pip install zappa
```




As we are using a conda environment we need to specify it:
```sh
which python
```

will give you `/Users/XXX/opt/anaconda3/envs/XXXX/bin/python` (for Mac)

remove the `bin/python/` and export

```sh
export VIRTUAL_ENV=/Users/XXXX/opt/anaconda3/envs/XXXXX/
```

Now we can do

```sh
zappa init
```

to set up the config.

Just click through everything and you will have a `zappa_settings.json` like

```json
{
    "dev": {
        "app_function": "app.app",
        "aws_region": "eu-central-1",
        "profile_name": "default",
        "project_name": "pandas-transform-format",
        "runtime": "python3.7",
        "s3_bucket": "zappa-pandas-transform-format"
    }
}
```

Note that we are not yet ready to deploy. First, we need to get some AWS credentials.

## Set up AWS

### AWS credentials

First, you need te get an AWS `access key id` and `access key`

You might think it is as easy as:

To get the credentials you need to
- Go to: http://aws.amazon.com/
- Sign Up & create a new account (they'll give you the option for 1 year trial or similar)
- Go to your AWS account overview
- Account menu; sub-menu: Security Credentials

But no. There is more to permissions in AWS!


#### Set up credentials with users and roles in IAM



**My Custom policy:**



#### Add credentials in your project

Create a `.aws/credentials` folder in your root with

```sh
mkdir ~/.aws
code ~/.aws/credentials
```
and paste your credentials from AWS
```py
[dev]
aws_access_key_id = YOUR_KEY
aws_secret_access_key = YOUR_KEY
```
Same with the `config`
```sh
code ~/.aws/config
```

```py
[default]
region = YOUR_REGION (eg. eu-central-1)
```

Note that `code` is for opening a folder with vscode, my editor of choice.




Save the AWS access key id and secret access key assigned to the User you created in the file ~/.aws/credentials. Note the .aws/ directory needs to be in your home directory and the credentials file has no file extension.

Now you can do deploy your API with

```sh
zappa deploy dev
```


There shouldn't be any errors anymore. However, if there are still some, you can debug with:

```sh
zappa status
zappa tail
```

The most common errors are permission related (then check your permission policy) or about python libraries that are incompatible. Either way, zappa will provide good enough error messages for debugging.

If you update your code don't forget to update the deployment as well with

```sh
zappa update dev
```

## AWS API Gateway


# 4. Set up Rapidapi




## Create API on Rapidapi


## Test your own API

### Create private plan for testing


### Test endpoint with rapidapi



### Create code to consume API


# End result

![](../assets/pythonApi_2020-09-04-09-40-49.png)

https://rapidapi.com/Createdd/api/excel-to-other-formats



# Inspiration


---

# About

Daniel is an entrepreneur, software developer, and lawyer. He has worked at various IT companies, tax advisory, management consulting, and at the Austrian court.

His knowledge and interests currently revolve around programming machine learning applications and all its related aspects. To the core, he considers himself a problem solver of complex environments, which is reflected in his various projects.

Don't hesitate to get in touch if you have ideas, projects, or problems.

![picture of myself](https://avatars2.githubusercontent.com/u/22077628?s=460&v=4)

**Connect on:**
- [LinkedIn](https://www.linkedin.com/in/createdd)
- [Github](https://github.com/Createdd)
- [Medium](https://medium.com/@createdd)
- [Twitter](https://twitter.com/_createdd)
- [Instagram](https://www.instagram.com/create.dd/)
- [createdd.com](https://www.createdd.com/)

<!-- Written by Daniel Deutsch -->