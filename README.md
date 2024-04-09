# Video2Chat
Video2Chat is an innovative system that analyzes cooking videos and provides users with an interactive chat interface to engage with the content. Powered by a RAG (Retrieval-Augmented Generation) based system, it offers intelligent responses to user queries based on the extracted information from the videos. 

## 1. Acquire Data
To begin, follow these steps to acquire and transcribe the necessary data:

Download Video: Utilize download_video.py to download 102 videos from YouTube.
Transcribe Video: Utilize transcribe_video.py to transcribe the videos.

## 2. Preprocess Data

Prepare the data for analysis by performing the following preprocessing steps:

Extract Cooking Steps: Utilize extract_cooking_steps_images.py to extract the cooking steps from the videos.
Extract Discussion Timestamps: Identify when the cooking steps are being discussed within the videos.
Video Processing: Utilize video_processor.py to extract images/screenshots from the YouTube videos.
All processed data is stored in the "processed_data" folder.

## 3. Build RAG
Construct the RAG using ChromaDB with OpenAI embeddings:

Implementation: The RAG implementation is stored in memory/chromadb.py.
Building the RAG: Implement the RAG construction in test.py and building_cooking_vector_db.py.
Persistent Database: The database (chroma.sqlite3) is persistently stored in memory/db/chroma.
## 4.Chat Interface 
### How to set it up 

- Install the requirements
`pip install -r requirements.txt`

- Create a .env with the following keys
`cp env_cp .env`

- Running the fastapi server 
`python app.py` 

- Returns
`.html file path`


## 5. Handles multiple recipe and combines to cook for you
The system handles multiple recipes and offers customization options:

Matching Dishes: Based on user queries, relevant dishes stored in the vectordb are retrieved.
If a match is found below the threshold of 0.15, it's considered a duplicate, and only one instance is returned.
Otherwise, dishes with matches below a threshold of 0.20 are returned.
Customization: Users can provide prompts to create custom dishes using GPT.
Image Generation: Dishes are accompanied by step-by-step image generation using Dalle-3.
HTML Rendering: Results are rendered in an HTML file for user interaction.
