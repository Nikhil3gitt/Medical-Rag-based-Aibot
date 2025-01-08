[Watch the demo on YouTube](https://www.youtube.com/watch?v=3up95NvxLog)

This project leverages Azure Form Recognizer, MongoDB, and multiple LLM providers groq to create an AI-powered medical assistant. The app enables document analysis of PDF files and generates medical interpretations and health insights using an LLM. 

### Installation

1. **Clone the repository**:
   ```bash
   git clone https://github.com/Abhisheknakka/rag-medical-bot.git
   cd rag-medical-bot


## Running the application
streamlit run main_app.py

Also install required libraries from requirement.txt

```
pip install -r requirements.txt
```

replace your .env file with you creds

```
AZURE_FORM_RECOGNIZER_ENDPOINT="https://trenthackdocuments.cognitiveservices.azure.com/"
AZURE_FORM_RECOGNIZER_KEY="6GApC"
# MONGO DB
API_HOST=groq

MONGODB_USER=
MONGODB_PASSWORD=
MONGODB_URI = ""

GROQ_MODEL= llama3-8b-8192
GROQ_API_KEY='gsk_'

```
## Project Structure

```
├── main_app.py                  # Main application script for Streamlit interface
├── document_analysis.py         # document analysis
├── text_generation.py           # Text generation and response handling functions
├── requirements.txt             # Python dependencies
├── .env                         # Environment variables (not included in repo)
└── README.md                    # Project documentation
```

## Dataset for llm integration
We fetched  directly  from hugging face


## Features

- **Document Analysis**: Upload PDF documents for content extraction and analysis using Azure Form Recognizer.
- **LLM-Generated Prescription Summaries**: Generate accurate, helpful responses related to medical content, enhanced with a human touch for clarity and guidance.
- **Criticality Analysis**: Assess the urgency of symptoms based on keywords and provide step-by-step guidelines for emergencies.
## Medical Analysis Components

The project includes predefined constants to enhance emergency response and symptom categorization for improved health guidance:

### Emergency Keywords and Criticality Scoring

To assess the urgency of medical conditions, a list of `EMERGENCY_KEYWORDS` is used to score symptom severity based on keywords commonly associated with emergencies. Each keyword is assigned a score from 0.7 to 1.0, representing its criticality, where higher scores signify more severe conditions.

```python
EMERGENCY_KEYWORDS = {
    'severe': 0.8,  
    'emergency': 1.0,
    'critical': 0.9,
    'urgent': 0.8,
    'immediate': 0.7,
    'life-threatening': 1.0,
    'unconscious': 1.0,
    'bleeding heavily': 0.9,
    'heart attack': 1.0,
    'stroke': 1.0,
    'difficulty breathing': 0.9,
    'seizure': 0.9,
    'overdose': 1.0,
    'suicide': 1.0,
    'trauma': 0.8,
    'chest pain': 0.9
}
```
- **Symptom Categorization**: Identify relevant health categories based on the query, such as respiratory, cardiac, neurological, etc.
```python
SYMPTOM_CATEGORIES = {
    'respiratory': ['breathing', 'cough', 'wheeze', 'chest congestion'],
    'cardiac': ['chest pain', 'heart', 'palpitations', 'shortness of breath'],
    'neurological': ['headache', 'dizziness', 'numbness', 'seizure'],
    'gastrointestinal': ['nausea', 'vomiting', 'diarrhea', 'abdominal pain'],
    'musculoskeletal': ['joint pain', 'muscle pain', 'back pain', 'injury'],
    'psychological': ['anxiety', 'depression', 'stress', 'panic'],
}

```

- **Feedback Storage**: Collect and store user feedback in MongoDB for improving future interactions.
- **Additional Resources & Tips**: Access reputable health resources and general tips on healthy living.

## Getting Started

### Prerequisites

- Python 3.8+
- Azure Form Recognizer API Key and Endpoint
- MongoDB URI
- API keys for the supported LLM providers (e.g., Groq, OpenAI)

insert images

![Screenshot 2024-11-10 123045](https://github.com/user-attachments/assets/daa03fbd-c1ed-49e1-8d87-b7c5cfa44651)

![Screenshot 2024-11-10 093154](https://github.com/user-attachments/assets/24514bcd-5800-4ebc-9e6c-587f9fca41b7)

![Screenshot 2024-11-10 093233](https://github.com/user-attachments/assets/bcc66b11-b8fa-459b-8f37-b1e3d3739463)


### Acknowledgment

Azure AI and Form Recognizer team
OpenAI, Groq, and NVIDIA for LLM models
Streamlit for the interactive web interface
