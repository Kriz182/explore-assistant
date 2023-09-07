# Introduction
This document provides instructions on how to install and customize the Explore Assistant demo. The demo is a web application that allows users to explore data in Looker by asking questions in natural language. To install the demo, you will need to install gcloud CLI, Vertex AI Python SDK, and Streamlit. Once the demo is installed, you can customize it by generating a summary of the model/explorer you wish to add to the Explore Assistant and using Gen AI Studio to test your changes.

Author : Anouar Hnini

------------


# Install the demo
Here are the steps on how to install Explore Assistant (on thelook/order_items explore):
- Install gcloud CLI : 
Go to the website https://cloud.google.com/sdk/docs/install
Create a folder where you will download and and save the python script.
- Install Vertex AI Python SDK: 
Go to the Vertex AI website and click on the "Get Started" button.
Follow the instructions on the website to install the Vertex AI Python SDK.
- Install Streamlit :
Go to the Streamlit website and click on the "Install" button.
Follow the instructions on the website to install the Streamlit SDK.
- Download the script:
Go to the explore-assistant.ipynb and Download the python file (or run it using Streamlit on Colab).

Save the script to the same folder where you installed streamlit and vertex AI.
Edit the following parameters : 
- Looker_base_url
- Project (your Vertex AI Project)
- Location (Location for your Vertex AI Project).

Make sure that you login to your Vertex AI

------------


# Run the app:
Before running the app, make sure that you’re logged in to the instance (Looker) and performing login using gcloud CLI (or any other preferred method to you). 

1. Open a terminal window and navigate to the directory where you saved the script.
Run the following command: (replace explore_assistant.py by the name of your script) :

```streamlit run explore_assistant.py```

2. The Explore Assistant app will open in your browser.
Note that the apps will create two logs files (all logs, and success_examples) that you could use to input into your Generative AI Studio. 


# Customize the demo
If you want to customize the demo for a specific model/explore : 
Generate a summary of the model/explore you wish to add to the Explore Assistant using this Notebook : **generate-looker-dictionnary.ipynb**

Add at least 10 or more examples.  (Examples Generation will be added soon)

1. Copy and Past the context string into the application code (View Code on the top left).
2. Configure Looker Base URL (instance.cloud.looker.com/model/explore) in the application.
Note : When creating examples, uses the Expanded URL in Looker 

It is also important to add vis_config parameter to the URL : 

```
fields=order_items.total_sale_price&f[order_items.created_date]=2 years&sorts=order_items.total_sale_price desc&vis={"type":"looker_bar"}
```

Here is the list of vis type names in Looker for the main types of visualization. If you want to add additional ones, you can review the vis parameter for the Expanded URL.

- Pie Chart : looker_pie
- Column Chart : looker_column
- Looker Single Value : single_value
- Table : looker_grid
- Bar Chart : looker_bar
- Area Chart : looker_area
- Map : looker_google_map
