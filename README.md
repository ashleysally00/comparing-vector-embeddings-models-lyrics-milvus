# Comparing Vector Embeddings from Different Models Using Milvus

A project demonstrating the comparison of different language models using song lyrics and vector embeddings stored in Milvus database.

**Note: I do not really like Taylor Swift... but I do like this project, which happens to use her lyrics**🎵

## Project Overview

The project demonstrates how to compare three different multilingual models based on MiniLM from Hugging Face using Milvus as the vector database. Using song lyrics as test data, it shows how different vector embeddings can be compared and analyzed.

## What is Milvus?

Milvus is an open-source vector database built specifically for embedding vectors and similarity search. Key features include:
- Purpose-built for managing and searching vector embeddings
- Optimized for AI and machine learning applications
- Supports efficient similarity search at scale
- Provides both standalone and distributed deployment options
- Integrates well with modern AI/ML pipelines

For this project, we use Milvus to store and compare our vector embeddings because it's specifically designed for this type of vector similarity search operation.

## Models Compared

- Base multilingual paraphrase model (MiniLM)
- Version fine-tuned for intent detection
- Sprylab fine-tuned version

## Implementation Steps

1. **Setup and Installation**
   - Installed required packages: pymilvus, milvus, sentence-transformers
   - Set up Milvus server and connection

2. **Model Loading**
   - Loaded three different sentence transformer models from Hugging Face
   - All models are based on MiniLM architecture

3. **Data Preparation**
   - Used lyrics dataset from multiple songs
   - Created a dataset of 51 sentences
   - Processed lyrics into suitable format for embedding

4. **Vector Database Setup**
   - Created schema with appropriate fields
   - Set up two collections in Milvus
   - Used 384-dimensional vectors (MiniLM standard)

5. **Embedding Generation**
   - Generated embeddings for all sentences using different models
   - Stored embeddings in Milvus collections

6. **Search Implementation**
   - Implemented search functionality using L2 distance metric
   - Used inverted file index with four centroids
   - Set up comparison between different model results

## Results & Analysis

The implementation produced several interesting findings:

### Search Performance
- First search completed in 0.0034 seconds
- Second search was faster at 0.0013 seconds
- Both searches demonstrated efficient performance for vector similarity operations

### Embedding Comparison Results

For the first query (wedding scene lyrics):
```
Query: "I am not the kind of girl, who should be rudely barging in on a white veil occasion..."
1. Exact match (distance: 14.65)
2. Guard/patience lyrics (distance: 16.70)
3. Haunting lyrics (distance: 18.22)
```

For the second query (sneaking in scene):
```
Query: "I sneak in and see your friends and her snotty little family..."
1. Exact match (distance: 13.32)
2. Guard/patience lyrics (distance: 15.08)
```

### Key Findings
1. **Self-Match Accuracy**: Both models correctly identified exact matches as closest neighbors
2. **Distance Consistency**: L2 distances showed consistent patterns between queries
3. **Thematic Grouping**: The models identified thematically similar lyrics as secondary matches
4. **Search Efficiency**: The second search was notably faster, suggesting potential caching benefits

These results demonstrate the effectiveness of using Milvus for vector similarity search and validate the comparison approach between different embedding models.

## Technical Details

- Vector Dimension: 384
- Distance Metric: L2
- Index Type: IVF_FLAT
- Search Parameters: nprobe=2, limit=3
- Database: Milvus Vector Database

## Reference

Do you want to try this project jusing a different artist?
Find the blog post here: [Comparing Different Vector Embeddings](https://zilliz.com/blog/comparing-different-vector-embeddings?utm_campaign=2023-10-30_nurture_zilliz-cloud-onboarding_global&utm_medium=email&_hsenc=p2ANqtz-_eX8EXGZEqC9cKF4WKnmlKF0SmkbdkZA_z9-8L0HB3RSlcVLtFhF3YPSYlZPi4u_OwDJGmhSKMc0oONuXQbA1gpbkUXw&_hsmi=287036736&utm_source=nurture)
