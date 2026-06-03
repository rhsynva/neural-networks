# neural-networks
Project Overview

In this notebook, I have implemented a seamless pipeline for training a machine learning model and deploying it as a RESTful web service. Instead of treating model development and deployment as isolated steps, I constructed a unified workflow that transitions from data fitting directly to an active API endpoint within the same environment. Here is a breakdown of the workflow:
Data Preparation: I instantiated a foundational dataset mapping property areas in square meters to their corresponding market prices in AZN.
Base Model Training: I selected a simple yet robust Linear Regression algorithm to establish the underlying relationship between square footage and cost. I trained this model directly on the raw data arrays to capture the linear trend.
API Construction (The Core Deployment Logic): Instead of exporting the model for external hosting, I manually implemented a Flask web server directly within the notebook. I defined a prediction route designed to accept HTTP POST requests, parse incoming JSON payloads for the specific area feature, and execute the model's prediction method dynamically.
Threaded Server Execution: To avoid blocking the notebook's execution kernel, I deployed the Flask application on a parallel background thread. This architectural choice allowed the server to run continuously while enabling subsequent cells to interact with it.
Endpoint Evaluation: I programmatically verified the deployment by constructing a client-side request using the internal networking library. I dispatched a test payload representing a 75-square-meter property to the local endpoint and successfully parsed the JSON response to validate the predicted price.
Architecture and Methodology

This repository contains my implementation of an end-to-end Machine Learning API built and tested entirely within a Jupyter environment. Rather than relying on external deployment platforms immediately, I manually programmed the server routing and asynchronous threading mechanics to deeply understand the architecture behind serving predictive models.
Integrating a Flask application within a data science notebook presents a unique challenge in process management; if the server blocks the main thread, the environment becomes unresponsive. My code demonstrates how to properly circumvent this using a threaded execution strategy, culminating in a functional, queryable REST API built purely with standard Python networking and web frameworks.
Technologies Used

Python 3
NumPy for numerical data structuring
Scikit-learn for the regression algorithm
Flask for backend API development and routing
Threading for asynchronous server management
Requests for client-side API testing
