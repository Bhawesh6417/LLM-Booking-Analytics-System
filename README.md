# Hotel Booking Analytics & RAG-based Q&A System

## Overview
This project is a Hotel Booking Analytics & RAG (Retrieval-Augmented Generation) system. It provides insights into hotel booking trends and allows users to ask questions about the dataset using a retrieval-based approach integrated with an LLM.

## Features
- **Booking Analytics**: Generates revenue trends and cancellation rates from the dataset.
- **Retrieval-Augmented Generation (RAG)**: Uses FAISS for efficient document retrieval.
- **FastAPI Interface**: Exposes APIs for analytics and query-based responses.
- **Sentence Embeddings**: Uses `sentence-transformers` to store and retrieve relevant data.
- **Google Gemini API**: Enhances responses with an LLM-powered text generation model.

## Requirements
- Python 3.10 or lower (TensorFlow is not yet supported on Python 3.12)
- Install dependencies using:

```sh
pip install pandas faiss-cpu fastapi uvicorn google-generativeai sentence-transformers matplotlib seaborn
```

## Setup
1. Clone the repository:
   ```sh
   git clone https://github.com/your-username/hotel-booking-rag.git
   cd hotel-booking-rag
   ```

2. Install dependencies:
   ```sh
   pip install -r requirements.txt
   ```

3. Run the FastAPI server:
   ```sh
   uvicorn main:app --reload
   ```

## API Endpoints

### 1. Get Analytics
**Endpoint:** `POST /analytics`

**Description:** Returns booking analytics including revenue trends and cancellation rates.

**Example Request:**
```sh
curl -X 'POST' 'http://127.0.0.1:8000/analytics' -H 'accept: application/json'
```

**Example Response:**
```json
{
  "revenue_trend": {"2024-01": 5000, "2024-02": 4500},
  "cancellation_rate": 15.3
}
```

### 2. Ask a Question
**Endpoint:** `POST /ask`

**Description:** Retrieves relevant booking information and generates a response using the LLM.

**Example Request:**
```sh
curl -X 'POST' 'http://127.0.0.1:8000/ask' -H 'accept: application/json' -H 'Content-Type: application/json' -d '{"question": "What was the ADR for City Hotel?"}'
```

**Example Response:**
```json
{
  "answer": "The ADR for City Hotel in the retrieved records is $120."
}
```

## Implementation Details
- **Dataset:** The dataset is preprocessed, and relevant features like `reservation_status_date`, `lead_time`, and `adr` are used for analytics.
- **FAISS Indexing:** Stores sentence embeddings of booking descriptions to efficiently retrieve relevant information.
- **Google Gemini API:** Enhances responses by providing context-aware generated text.
- **FastAPI:** Provides an interactive API for querying analytics and retrieving responses.

## Known Issues
- The project **does not support Python 3.12** due to TensorFlow limitations. Please use Python 3.10 or lower.
- Ensure that `hotel_bookings.csv` is available in the project directory before running the script.

## Future Enhancements
- Deploying the model as a cloud-based API using AWS Lambda or GCP Functions.
- Enhancing document retrieval with hybrid search (BM25 + FAISS).
- Expanding analytics with more detailed insights on seasonal trends.

## Author
Your Name - [GitHub Profile](https://github.com/your-username)

## License
This project is licensed under the MIT License.

