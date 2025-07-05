# Assessment Checker

An intelligent programming exam evaluation system that uses Azure OpenAI (Grok-3) to automatically assess student answers against ideal solutions. The system provides objective scoring based on logical correctness rather than language or presentation style.

## Features

- **Multi-language Support**: Evaluates answers in English, Malayalam, or mixed languages
- **Objective Scoring**: Focuses on logic and content correctness, not grammar or presentation
- **Azure OpenAI Integration**: Uses Grok-3 model for intelligent evaluation
- **Structured Output**: Returns JSON-formatted results with scores and evaluations
- **Batch Processing**: Can evaluate multiple questions simultaneously

## Prerequisites

- Python 3.8 or higher
- Azure OpenAI API access with Grok-3 deployment
- Azure API key

## Installation

1. **Clone the repository**
   ```bash
   git clone <your-repository-url>
   cd assessment-checker
   ```

2. **Create a virtual environment**
   ```bash
   python -m venv venv
   ```

3. **Activate the virtual environment**
   ```bash
   # Windows
   venv\Scripts\activate
   
   # macOS/Linux
   source venv/bin/activate
   ```

4. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

5. **Set up environment variables**
   Create a `.env` file in the project root:
   ```env
   AZURE_API_KEY=your_azure_api_key_here
   ```

## Configuration

The system is configured to use Azure OpenAI with the following settings:

- **Endpoint**: `https://deyoze-tech-resource.services.ai.azure.com/`
- **Deployment**: `grok-3`
- **API Version**: `2024-05-01-preview`
- **Temperature**: `0` (for consistent results)

## Usage

### Basic Usage

Run the main script to evaluate sample questions:

```bash
python main.py
```

### Programmatic Usage

```python
from main import process_assessment, check_answer_langchain

# Evaluate a single answer
result = check_answer_langchain(
    question="What is an IP address?",
    student_answer="IP address is a unique identifier for devices on network",
    ideal_answer="An IP address is a numerical label assigned to each device connected to a computer network"
)

# Process multiple assessments
results = process_assessment()
```

## Scoring System

The evaluation system uses a **0-2 point scale**:

- **0 points**: Incorrect or completely wrong answer
- **1 point**: Partially correct with some understanding
- **2 points**: Correct answer with clear understanding

### Evaluation Criteria

The system evaluates based on:
- ✅ **Logic and reasoning**
- ✅ **Content accuracy**
- ✅ **Conceptual understanding**
- ❌ **Language/grammar** (ignored)
- ❌ **Spelling mistakes** (ignored)
- ❌ **Presentation style** (ignored)
- ❌ **Capitalization** (ignored)

## Sample Questions

The system includes sample questions covering:

1. **IP Addresses** - Types and definitions
2. **Web Servers** - Definition and examples
3. **Internet** - Global network concepts
4. **DNS** - Domain Name System
5. **Programming Methods** - find() method explanation

## Output Format

The system returns structured JSON responses:

```json
{
  "id": 1236,
  "question": "What is an IP address?",
  "ideal_answer": "An IP address is a numerical label...",
  "student_answer": "IP address is a unique identifier...",
  "evaluation": {
    "ideal_answer": "An IP address is a numerical label assigned to each device...",
    "score": 2
  }
}
```

## Project Structure

```
assessment-checker/
├── main.py              # Main application logic
├── requirements.txt     # Python dependencies
├── README.md           # This file
├── .env                # Environment variables (create this)
└── venv/               # Virtual environment
```

## Dependencies

- **python-dotenv**: Environment variable management
- **langchain**: Prompt templates and output parsing
- **langchain-openai**: Azure OpenAI integration

## API Requirements

- Azure OpenAI API access
- Grok-3 deployment configured
- Valid API key with appropriate permissions


