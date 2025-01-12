# S.A.G.E: Spiritual AI-powered Gita and Enlightenment

This project, titled **S.A.G.E.** (Spiritual AI-powered Gita and Enlightenment), implements an advanced pipeline for retrieving relevant verses from the Bhagavad Gita and Patanjali Yoga Sutras (PYS) based on user queries. Leveraging state-of-the-art Information Retrieval (IR) techniques and an open-source Large Language Model (LLM) like LLaMA, the pipeline generates high-quality, contextually accurate summaries.

## Core Features

1. **Context-Aware Verse Retrieval**: Employs semantic search and ranking algorithms to identify the most contextually relevant verses.
2. **LLM-Driven Summarization**: Utilizes cutting-edge LLMs to produce concise and meaningful answers derived from retrieved verses.
3. **Robust Query Handling**: Detects and flags irrelevant or inappropriate user queries.
4. **Interoperable JSON Outputs**: Delivers structured results suitable for integration with APIs, applications, or other downstream systems.

## Architecture Overview

```
project-root/
├── data/
│   ├── Bhagwad_Gita_Verses_Concepts.csv
│   ├── Bhagwad_Gita_Verses_English.csv
│   ├── Bhagwad_Gita_Verses_English_Questions.csv
│   ├── Gita_Word_Meanings_English.csv
│   ├── Gita_Word_Meanings_Hindi.csv
│   ├── Patanjali_Yoga_Sutras_Verses_English.csv
│   ├── Patanjali_Yoga_Sutras_Verses_English_Questions.csv
├── models/
│   └── Meta-Llama-3.1-8B-Instruct-Q4_K_M.gguf
├── src/
│   ├── config.py       # Configuration management
│   ├── llm.py          # Integration with the LLM for summarization
│   ├── retriever.py    # IR logic for verse extraction and ranking
│   ├── utils.py        # Utility functions for preprocessing and postprocessing
│   ├── main.py         # Entry point for executing the pipeline
│   └── ... (supporting scripts and modules)
```

## Getting Started

### Step 1: Environment Setup

1. **Clone the repository**:
   ```bash
   git clone <repository_url>
   cd <repository_name>
   ```

2. **Install required dependencies**:
   ```bash
   pip install -r requirements.txt
   ```

3. **Download and place the model**:
   Ensure the LLaMA model file (`Meta-Llama-3.1-8B-Instruct-Q4_K_M.gguf`) is located in the `models/` directory.

### Step 2: Running the Pipeline

Execute the main script to process user queries:

```bash
python src/main.py
```

### Example Query Input

Provide a user query in JSON format, either through an API or directly via the script:

```json
{
  "query": "What guidance does the Bhagavad Gita provide about karma?"
}
```

### Example Pipeline Output

The processed output will be delivered as a JSON response:

```json
{
  "query": "What guidance does the Bhagavad Gita provide about karma?",
  "retrieved_verses": [
    {
      "verse": "Bhagavad Gita 2.47",
      "text": "You have a right to perform your prescribed duties, but you are not entitled to the fruits of your actions..."
    }
  ],
  "summary": "The Bhagavad Gita emphasizes performing duties with dedication while detaching oneself from the results."
}
```

## Technical Details

### Model Used

The pipeline leverages the **Meta-LLaMA-3.1-8B-Instruct-Q4_K_M** model, a state-of-the-art open-source Large Language Model optimized for instruction-following tasks. This model is particularly adept at generating human-like responses and summarizations while maintaining contextual integrity. By integrating this LLM, the pipeline ensures high-quality, coherent answers based on retrieved verses.

### Retrieval-Augmented Generation (RAG) Pipeline

The pipeline follows the Retrieval-Augmented Generation (RAG) architecture, which is pivotal for bridging the gap between knowledge retrieval and response generation:

1. **Retrieval Module**:
   - Extracts relevant verses using advanced semantic search and ranking algorithms.
   - Processes data from curated CSV files located in the `data/` directory.

2. **Generation Module**:
   - Constructs dynamic prompts containing retrieved verses and user queries.
   - Uses the LLaMA model to generate concise, contextually relevant answers while minimizing hallucinations.

3. **Postprocessing**:
   - Formats responses into structured JSON outputs.
   - Ensures alignment with the theological context of the verses.

### Verse Retrieval Module
- **Dataset Integration**: Processes curated datasets of verses in CSV format, located in the `data/` directory.
- **Semantic Search**: Uses cosine similarity or advanced embedding-based techniques to match queries with relevant verses.
- **Reranking**: Applies ranking heuristics to prioritize contextually significant verses.

### Summarization Engine
- **LLM Prompt Engineering**: Dynamically constructs prompts to minimize hallucinations and generate precise answers. Example prompt:

  ```
  Based on the following verses, provide an accurate and concise answer to the query:

  Verses:
  {retrieved_verses}

  Query:
  {user_query}
  ```

- **Output Optimization**: Formats the LLM's response into a coherent summary, ensuring contextual fidelity.

### Query Validation
- Detects inappropriate or irrelevant queries using a lightweight keyword matching and rule-based mechanism.

### JSON Output Specification
- Encapsulates the results into a machine-readable structure with the following schema:
  - `query`: Original user query.
  - `retrieved_verses`: List of matched verses with metadata.
  - `summary`: Generated concise response.

## Evaluation and Performance

### Metrics
1. **Retrieval Accuracy**: Precision of the retrieved verses against a set of curated queries.
2. **Summarization Quality**: Relevance and coherence of LLM-generated answers.
3. **Efficiency**: Average latency and cost per query.

### Benchmarking
- Tested with diverse user queries to ensure robustness and adaptability.
- Validated results with domain experts for theological and contextual accuracy

## Future Enhancements

1. **Multilingual Support**: Expand retrieval and summarization capabilities to include Hindi and Sanskrit verses.
2. **Fine-Tuning**: Optimize the LLM with domain-specific datasets to enhance summarization accuracy.
3. **Scalability**: Improve retrieval algorithms to handle large-scale datasets with minimal latency.
4. **Interactive UI**: Develop a web-based interface or chatbot for seamless user interaction.

## Contribution Guidelines

Contributions are highly encouraged! To contribute:

1. Fork the repository.
2. Create a feature branch.
3. Commit your changes.
4. Submit a pull request with a detailed description.

## License

This project is licensed under the MIT License. Refer to the `LICENSE` file for more information.

---

For further inquiries or support, please contact [your email/contact info].
