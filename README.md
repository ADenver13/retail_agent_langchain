# Retail Agent Chatbot

This chatbot helps users identify items from images, check stock availability, and recommend similar items if the desired item is out of stock. It uses a pre-trained MobileNetV2 model for image classification and Langchain with OpenAI's API for recommendations.

## Table of Contents

- [Features](#features)
- [Langchain](#langchain)
- [Setup](#setup)
- [Usage](#usage)

## Features

- **Image Classification**: Users can upload an image, and the bot will identify the item using a MobileNetV2 model.
- **Stock Checking**: The bot checks if a specified item is in stock and returns its price.
- **Recommendations**: If an item is out of stock, the bot recommends similar items that are available.

## Langchain

  Langchain is a framework for integrating multiple LLMs into applications in an easy to understand way. In this case, we create an agent by providing the agent tools and using OpenAI's API to decide which tool to use based on user
  input and tool descriptions provided. More information can be found [here](https://python.langchain.com/v0.1/docs/modules/agents/).

## Setup

1. **Clone the repository**:
   ```bash
   git clone https://github.com/yourusername/stock-checker-chatbot.git
   cd stock-checker-chatbot
   ```
2. **Install Requirements**:
   ```bash
   pip install -r requirements.txt
   ```
3. **.env**
  In order to use the OPENAI API and Langchain, API keys are required. These will have to be set in a .env file in the format below:
  ```bash
  LANGCHAIN_API_KEY = 'KEY_HERE'
  OPENAI_API_KEY = 'KEY_HERE'
  ```
After this, you can run all code inside the Jupyter Notebook.

## Usage
  The chatbot can be run just like any other Jupyter Notebook.

## Tips
  - The bot does have a tendency to hallucinate, as do all LLMs. This likelihood of hallucinating could be reduced with more careful prompts or by adjusting the temperature.
  - Whenever you run the bot, it will first ask you about a laptop. This is because of the demo cell designed to produce a bar chart to demo the image classification. You can remove that by removing this cell:
   ```python
  #Example to show how image classification is working
  match_image_to_description('C:\\Users\\histo\\retail_agent_demo\\71EVBJVMSoL.jpg', debug=True)
   ```
  - Currently, the bot wil tell you what it's thinking and try to rationalize decisions to you. This can be removed by setting verbose=False in the following code:
   ```python
   agent_executor = initialize_agent(
    tools=tools,
    llm=OpenAI(temperature=0.4), #Could use some adjusting
    agent_type=AgentType.ZERO_SHOT_REACT_DESCRIPTION,
    verbose=True
   )
   ```


   
