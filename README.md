# AI-chatbot
This is a production-grade, AI-powered chatbot built usingFastAPI for the backend, and ChromaDB for memory management. It is containerized with Docker for easy deployment.

## Project Structure

```
.
├── app/
│   ├── api.py           # FastAPI routes
│   ├── chatbot.py       # Chat logic using GPT-4o
│   ├── config.py        # API key loading and validation
│   ├── memory_store.py  # ChromaDB-based memory handler
│   ├── models.py        # Pydantic models
│   └── utils.py         # Utility functions
├── main.py              # Application entry point
├── requirements.txt     # Python dependencies
├── Dockerfile           # Docker setup
├── .env                 # Environment variables (excluded in .gitignore)
└── .gitignore           # Ignore sensitive and compiled files
```

## Setup Instructions

### 1. Clone the Repository

```bash
git clone https://github.com/your-username/ai-chatbot.git
cd ai-chatbot
```

### 2. Create and Configure Environment

Create a `.env` file in the project root:

```bash
OPENAI_API_KEY=your_openai_key_here
```

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

### 4. Run the Application

```bash
python main.py
```

Visit `http://localhost:8000/chat`

### 5. Test the Chat Endpoint

```bash
curl -X POST http://localhost:8000/chat \
     -H "Content-Type: application/json" \
     -d '{"message": "Hello, chatbot!"}'
```

## Run with Docker

```bash
docker build -t ai-chatbot .
docker run -d -p 8000:8000 --env-file .env ai-chatbot
```

## API Endpoint

**POST** `/chat`

Request Body:
```json
{
  "message": "Hello!"
}
```

Response:
```json
{
  "response": "Hello! How can I help you today?"
}
```
