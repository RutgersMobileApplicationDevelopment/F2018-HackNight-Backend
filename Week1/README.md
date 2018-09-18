# Hack Night 1: Intro To Flask

Welcome to RUMAD Hack Nights! Tonight we are going to build a simple web backend API giving a quick introduction to flask.

## What is Flask?
Flask Is a simple but powerful web microframework for **python**. Flask is easy to install so we can get our web api up and running in minutes. 

## Setting Up Flask

 - ## Mac
	 1. Install pip package manager so we can install the flask packages in your terminal run: ``` sudo easy_install pip ``` 
	 2. Install Flask using pip run:  ``` pip install Flask ```
	 3. You're all done Proceed to the "Hello Flask" section
- ## Debian Linux Distros
	1. Run in your terminal ``` sudo apt-get install python-pip ```
	2. Do steps 2 & 3 in the Mac section 
- ## Windows
	1. Install python 
	2. Do each step in the mac section from command prompt

## "Hello Flask"
Now that we have flask installed it is time to start making something awesome
If you have not already download the week 1 folder.

- To make sure your Flask install is working properly in your command line navigate inside the week1 folder and run the command: ``` FLASK_APP=HelloWorld.py flask run```
- Navigate to the given URL (http://127.0.0.1:5000/) in your browser, If you see Hello Flask you installed everything correctly
- If it does not work ask and someone will be able to help you
- In the next section we will take a deep dive into HelloWorld.py to help you understand how it works.

## Understanding HelloWorld.py
We will go line by line to give a general understanding of our hello flask application.

```python
from flask import Flask
app = Flask(__name__)
```

```python
@app.route("/")
```

```python
def hello():
	return "Hello Flask"
```
