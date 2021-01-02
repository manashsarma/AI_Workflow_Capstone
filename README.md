# AI Enterprise Workflow Capstone Project

# Project folder structure

This project uses time series to forecast revenue prediction for the next 30 days.
Files and folders are kept in this hiearchy:

Dockerfile*
Notebook_Case_Study_part1_ingest_visuallization.ipynb*
Notebook_Model_Performance.ipynb*
Notebook_Monitoring.ipynb*
Notebook_UnitTest.ipynb*
README.md*
UnitTest_Model.py*
UnitTest_allTestCases.py*
UnitTests_API.py*
UnitTests_logger.py*
__pycache__/
app.py*
cslib.py*
data/
logger.py*
logs/
model.py*
models/
requirements.txt*
static/
templates/  

# Install any needed packages specified in requirements.txt
pip install --no-cache-dir -r requirements.txt

# Data ingestion

The python script 'cslib.py' supports  methods by which it extracts data from 
json source files, process them and transport to proper dataframe for further. 
The JSON files may not contain uniformly named features. So data ingestion
methods takes care of this including extracting time series information :

1. fetch_data(data_dir)
2. convert_to_ts(df_orig, country=None)
3. fetch_ts(data_dir, clean=False)

# Unit testing

For simplicity, all unit test case scripts are kept in the main folder itself. The
unit test cases file name start with prefix 'UnitTests_'. They can be executed by with the
command in the same directory / folder :

$python UnitTests_logger.py


The file 'UnitTest_allTestCases.py' is the single script to execute all the test cases.  

However, to execute the API test cases in the file UnitTests_API.py, it is required to
start the flask app in normal or debug mode:

$ python app.py

or

$ python app.py -d

You can go to http://0.0.0.0:8080/ and to see a basic website that can be customtized.

## To test the model directly and train the model

see the code at the bottom of `model.py`

$ python model.py

## prodution models and logs

Production models are separately kept in models folder and logs are lept in logs folder

## Notebook for verification of different results

Notebooks files are prefixed with 'Notebook_' and are used for verifying:

- API and test cases work as expected work as expected in 'Notebook_UnitTest.ipynb'
- Data ingestion in Notebook_Case_Study_part1_ingest_visuallization.ipynb
- EDA investigation in Notebook_Case_Study_part1_ingest_visuallization.ipynb
- performance monitoring in Notebook_Monitoring.ipynb
- models comparison for performance in Notebook_Model_Performance_comparison.ipynb

# To build the docker container

```bash
~$ docker build -t iris-ml .
```

Check that the image is there.

```bash
~$ docker image ls

