# DataDetective
index.html
# Key Features
# What is Web Scraping

Web Scraping is an automatic way to retrieve unstructured data from a website and store them in a structured format. 

# Can you scrape from all the websites?
Scraping makes the website traffic spike and may cause the breakdown of the website server. Thus, not all websites allow people to scrape. How do you know which websites are allowed or not? You can look at the ‘robots.txt’ file of the website. You just simply put robots.txt after the URL that you want to scrape and you will see information on whether the website host allows you to scrape the website.
Example if you want to scrape amazon use " https://www.amazon.co.uk/robots.txt"

You can see that Amazon does not allow web scraping for many of its sub-websites. However, it allows certain paths like ‘ /gp/wishlist/universal’ and thus if you want to collect information on whishlist then this is a completely legal place to scrape.

# Web Scraping Youtube Steps

Generating API Key

To generate a YouTube API key for data scraping, follow these steps:

1. Go to the Google Developers Console at https://console.developers.google.com
2. Create a new project by clicking on the dropdown menu at the top of the page next to “Google Cloud Platform” and selecting “New Project.”
3. Name your project and select a billing account (if you don’t have one, you will need to create one).
4. Once your project is created, click on the “Enable APIs and Services” button.
5. Search for “YouTube Data API” and select it.
6. Click on the “Enable” button.
7. Next, you will need to create a new API key. Click on the “Create credentials” button and select “API Key.”
8. You can choose to restrict the API key to specific IP addresses, websites, or apps if desired.
9. Once you have created the API key, copy it and use it in your data scraping code to authenticate your requests to the YouTube Data API.

# Importing the libraries

import os

from googleapiclient.discovery import build
import pandas as pd
import seaborn as sns

# Scraping

We makes use of the googleapiclient module to import the build function which is used to create a client instance for interacting with Google APIs.

# Using API Key

We define an API key and a list of YouTube channel IDs. It then uses the build() function from the googleapiclient.discover module to create a connection to the YouTube Data API. The connection is authenticated using the API key, and specifies that version 3 of the API should be used. The resulting youtube object can then be used to make API calls to interact with the specified YouTube channels.

# Scraping

This code defines a function called get_channel_stats that takes two arguments, youtube and channel_ids. The youtube parameter is an instance of the googleapiclient.discovery module which is used to make requests to the YouTube API. The channel_ids parameter is a list of YouTube channel IDs for which we want to retrieve statistics.

The function makes a request to the YouTube API using the channels().list() method and passes the part parameter to specify which parts of the channel data we want to retrieve (snippet, content details, and statistics), as well as the id parameter to specify the channel IDs we want to retrieve data for. The execute() method is called on the request object to send the request and get a response.

The response contains data for all the channels specified in the channel_ids list. The function loops over each channel in the response and extracts relevant data such as the channel name, subscriber count, total views, and total videos. It then stores this data in a dictionary object and appends it to the all_data list.

Finally, the function returns the all_data list containing statistics for all the channels specified in the channel_ids list. This function is useful for retrieving statistics for multiple YouTube channels at once and can be used for data analysis or visualization.

# Processing the response
Convert the json data recieved to the dataframe using pandas

# Visualize 
We can draw graph using seaborn for comparison. Here I have used barchart

# Insert into firestore
Once we recieved the data either can expost to csv or can store the data to database. Here I have used firestore.

# Connecting to Firestore
Import the required libraries and connect to the firestore

# Steps
# 1. Generating Service Account Key

To use the SDK we’ll need to have a Service Account Key. You can generate this by using Firebase Console > Project Settings:
Then selecting Service accounts and clicking Generate new private key
This will produce a .json file with the credentials needed to access the Firebase project.

# 2. install: firebase-admin google-cloud-firestore
pip install firebase-admin google-cloud-firestore
This provides firebase-admin package to allow the connections as well as the google-cloud-firestore package.
Move your copy of the Service Account Key to the working folder, and for ease I renamed mine to google_service_account.json

# Connecting to Firestore
You can now connect to the Firestore for your project, I’ll just demonstrate how to do this and get some data then go on to adding data imported from a csv file.


# Pre-requestes
# 1. Python and pip installed on local machine

