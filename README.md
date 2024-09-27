# Activity Suggestion Chatbot

## Overview

This project is a chatbot-based application that suggests personalized activities based on the sentiment and emotion detected in user inputs. By analyzing a user's mood and preferences, the chatbot recommends activities to enhance productivity, relaxation, or mental well-being. If the user is unsatisfied with the suggested activity, the chatbot can generate a new one based on recent user inputs.

## Features
1. **Sentiment Analysis**:
    - Uses the **'distilbert-base-uncased-finetuned-sst-2-english'** model to detect the sentiment of the user input (positive or negative).
2. **Emotion Detection**:
    - Leverages the **'bhadresh-savani/distilbert-base-uncased-emotion'** model to identify the user's emotion (e.g., sadness, joy, anger) from the input.
3. **Activity Suggestion**:
    - Based on the detected sentiment and emotion, the app looks up an appropriate activity from a predefined dataset. The dataset maps different emotions and sentiments to various activities.
4. **Regenerate New Activity**:
    - If the user wants a different activity, the **'NousResearch/Llama-2-7b-chat-hf'** model generates a new activity based on recent inputs, including user feedback and the previously suggested activity.

## Models Used
- **Sentiment Model**:
    - **Name**: `distilbert-base-uncased-finetuned-sst-2-english`
    - **Purpose**: Analyzes user input to detect sentiment (positive/negative).
- **Emotion Model**:
    - **Name**: `bhadresh-savani/distilbert-base-uncased-emotion`
    - **Purpose**: Extracts the user's emotional state from the input to guide the chatbot in suggesting a relevant activity.
- **Activity Regeneration Model**:
    - **Name**: `NousResearch/Llama-2-7b-chat-hf`
    - **Purpose**: Generates a new activity suggestion if the user requests one, using previous inputs and context.

## Workflow

1. The user inputs a message describing their current mood or situation.
2. The system first applies sentiment analysis using **'distilbert-base-uncased-finetuned-sst-2-english'** to classify the sentiment.
3. Then, emotion detection is performed using **'bhadresh-savani/distilbert-base-uncased-emotion'** to identify the emotion behind the message.
4. Based on the detected sentiment and emotion, the chatbot looks up an appropriate activity suggestion from a dataset.
5. If the user requests another activity, the app will use **'NousResearch/Llama-2-7b-chat-hf'** to generate a fresh activity based on recent inputs and history.

## How to Use
1. **Input your current mood or situation**:
    - Example: "I've been feeling a bit restless and unproductive lately."
2. **Receive an activity suggestion**:
    - The chatbot will analyze the sentiment and emotion from your input and suggest an activity from the dataset.
3. **Regenerate an activity** (Optional):
    - If you're not satisfied with the suggestion, you can request a new activity, and the chatbot will generate one based on your recent inputs.

## Example Interaction
- **User**: 
```user
Today dragged on with an overwhelming sense of boredom.
```

```bash
%% Sentiment response %%
{'label': 'Negative', 'score': 0.9990234375}

%% Emotion response %%
{'label': 'Sadness', 'score': 0.90478515625} 
```
- **Chatbot**: 
```chatbot
Talk to a close friend or therapist
Please let me know if you want me to generate a new activity based on your input.
```
- **User**: 
```user
I Wanna another activity.
```
- **Chatbot**: 
```chatbot
Sure! How about we try a new activity? Let's play a game of virtual reality escape room. It's a fun and exciting way to pass the time and challenge your problem-solving skills. Would you like to give it a try?
Please let me know if you want me to generate a new activity based on your input.
```

## Installation & Requirements

1. **Install dependencies**:
    - Install the required libraries using `pip`:
        ``
    ```bash
    !pip install accelerate protobuf sentencepiece torch git+https://github.com/huggingface/transformers huggingface_hub gradio
	```
1. **Run the app**:
    - Launch the Gradio interface to start the chatbot:
    ```googlecolab
    demo.launch()
	```

## Future Improvements

- Expand the dataset to include a wider variety of activities for different emotional states.
- Enhance the context-awareness of the chatbot for better follow-up suggestions.
- Add multilingual support to reach a broader audience.
