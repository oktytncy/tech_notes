## Data API

### What is a Data API?

A Data API (Application Programming Interface) allows two software programs to communicate with each other. An API takes requests, fetches data, or performs actions, and then returns the response back to you.

**Endpoints:** Each API has different endpoints, which are specific addresses where certain data or functions can be accessed. For example, if there's an API for a book store, there might be an endpoint like /books to get a list of books.

The Data API allows you to <a href="https://docs.datastax.com/en/astra/astra-db-vector/api-reference/dataapiclient.html" target="_blank">programmatically interact</a> with Astra DB Serverless databases, handling operations on databases, collections, and documents. It supports a client-centric approach where you begin with a DataAPIClient to execute various database operations. 

This API utilizes JSON for requests and responses and provides detailed method examples across multiple programming languages such as Python, TypeScript, and Java.

To interact with the API, you need an Astra account, a Serverless database, and an application token with administrative privileges. The API offers comprehensive documentation with examples for various operations, including database and document management, and administrative tasks.

For a detailed exploration of the Data API, you can view the <a href="https://docs.datastax.com/en/astra/astra-db-vector/api-reference/overview.html" target="_blank">official documentation</a>.

## Language Processing

Natural language processing is used when we want machines to interpret human language. The main goal is to make meaning out of text in order to perform certain tasks automatically such as spell check, translation, for social media monitoring tools, and so on.

### Key Concepts in Language Processing

1. **Sentence Segmentation:** Divides the entire paragraph into different sentences for better understanding,

2. **Word Tokenization:** Breaks the sentence into separate words or tokens. This helps understand the context of the text.

3. **Stemming:** Stemming helps in preprocessing text. The model analyzes the parts of speech to figure out what exactly the sentence is talking about. Helps to predict the parts of speech for each token. For example, intelligently, intelligence, and intelligent. These words originate from a single root word ‘intelligen’. However, in English there’s no such word as ‘intelligen’.

4. **Lemmatization:** Removes inflectional endings and returns the canonical form of a word(lemma). It is similar to stemming except that the lemma is an actual word. For example, ‘playing’ and ‘plays’ are forms of the word ‘play’. Hence, play is the lemma of these words. Unlike a stem (recall ‘intelligen’), ‘play’ is a proper word.

5. **Stop Word Analysis:** Removing common words that may not be significant for analysis, such as "and", "the", etc. So, they are filtered out so as to focus on more important words.

6. **Dependency Parsing:** Mainly used to find out how all the words in a sentence are related to each other. To find the dependency, we can build a tree and assign a single word as a parent word. 

<p align="left">
  <img src="images/1.png" alt="drawing" width="600"/>
</p>


7. **Part-of-Speech Tagging:** Tags contain verbs, adverbs, nouns, and adjectives that help indicate the meaning of words in a grammatically correct way in a sentence.

### Practical Applications

**Chatbots and Virtual Assistants:** These applications use language processing to understand user queries and provide relevant answers.

**Content Recommendations:** Language processing helps in analyzing user preferences through their interactions and providing content recommendations accordingly.

## Llama Index

<p align="left">
  <img src="images/2.png" alt="drawing" width="800"/>
</p>

LlamaIndex, formerly known as GPT Index, is an orchestration or data framework that simplifies the integration of private data with public data for building applications using Large Language Models (LLMs).

LlamaIndex provides integration of data by fetching data from multiple unique sources, and embedding that data as vectors, and storing this new vectorized data in a vector database, allowing this data to be used by applications to perform complex operations with low-latency response times, such as vector search.

LlamaIndex simplifies data ingestion by connecting existing data sources such as APIs, PDFs, SQL, NoSQL, and documents for use with LLM applications.

### Why we need LlamaIndex?

The challenge with building LLM-based applications is that they need data, typically from multiple sources and formats such as structured, semistructured, and unstructured.

That is where LlamaIndex provides the toolbox to unlock this data with data ingestion and indexing. Once ingested and indexed, retrieval augmented generation (RAG) applications can use the LlamaIndex query interface for accessing that data and powering LLMs.

### Ingestion

LlamaIndex has 100s of data loaders that provide the ability to connect custom data sources to LLMs.

A complete list of data loaders can be found on the <a href="https://llamahub.ai/" target="_blank"> Llama Hub</a>..

### Indexing and Querying

Once data is ingested, that data needs to be mathematically represented so that it can be easily queried by an LLM. With LlamaIndex, an index simply provides the ability to represent data mathematically in multiple different dimensions.

The most common approach to indexing data for machine learning and LLMs is called a vector index and once data has been indexed the mathematical representation of the data is called a vector embedding.

There are many types of indexing and embedding models. Once data is embedded, a mathematical representation of data can be used to provide semantic search, as things like text with similar meanings will have a similar mathematical representation.

For example, king and queen might be highly related if the query is royalty but not highly related if the query is gender.

LlamaIndex offers several different indexing models that are designed to provide optimizations around how you want to explore and categorize your data. 

If you know the type of operation your application needs to perform on the data, leveraging a particular index type can provide significant benefits to the application that uses the LLM and initiates the query.


| Index Type          | Structure                            | Optimal Use Cases                                                                                          | Strengths                                                              |
|---------------------|--------------------------------------|------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------|
| **List Index**      | Sequential list                      | Structured objects over time, like change logs                                                             | Optimized for querying sequential data; good for tracking changes over time |
| **Tree Index**      | Binary tree (parent and leaf nodes)  | Natural language processing, support/FAQ systems                                                           | Efficient in traversing and extracting specific segments of data      |
| **Vector Store Index** | Vector embeddings                  | Smaller datasets locally or large datasets across multiple applications; similarity searches               | Flexible use of data through vector representation; supports multiple LLMs/applications |
| **Keyword Index**   | Metadata tag mapping                 | Large volumes of tagged data like legal briefings, medical records                                          | Allows complex queries based on keywords; useful for datasets with extensive metadata |

## Langchain

<p align="left">
  <img src="images/3.png" alt="drawing" width="600"/>
</p>

LangChain is a library for building language model applications that interact with external APIs, databases, and more. 

Available in both Python and Javascript-based libraries, LangChain’s tools and APIs simplify the process of building LLM-driven applications like chatbots and virtual agents. 

LangChain’s module-based approach allows developers and data scientists to dynamically compare different prompts and even different foundation models with minimal need to rewrite code. This modular environment also allows for programs that use multiple LLMs: for example, an application that uses one LLM to interpret user queries and another LLM to author a response.

### Chains

As its name implies, chains are the core of LangChain’s workflows. They combine LLMs with other components, creating applications by executing a sequence of functions. 

The most basic chain is LLMChain. It simply calls a model and prompt template for that model. 

**For example**, imagine you saved a prompt as *ExamplePrompt* and wanted to run it against Flan-T5. You can import LLMChain from langchain.chains, then define chain_example as below;

```python
from langchain.chains import LLMChain

chain_example = LLMChain(llm = flan-t5, prompt = ExamplePrompt)
```

To run the chain for a given input, you simply call chain_example.run(“input”).

To use the output of one function as the input for the next function, you can use SimpleSequentialChain. Each function could utilize different prompts, different tools, different parameters or even different models, depending on your specific needs. 

LangChain is a framework that helps someone build an AI Application and simplify all the requirements without having to code all the little details. 

LangChain provides pre-built libraries for popular LLMs (like GPT-4 or GPT-3.5) so all a programmer has to do is provide their credentials and the prompt and wait for a response. 

## Langsmith (Monitor)

LangSmith provides tools to monitor, evaluate and debug applications, including the ability to automatically trace all model calls to spot errors and test performance under different model configurations. This visibility aims to empower more robust, cost-efficient applications.

Can be used with Python and TypeScript, For more information, please refer to the  LangSmith <a href="https://python.langchain.com/docs/langsmith/" target="_blank">documentation</a>.

### To Enable Monitoring Capabilities

```python
pip3 install -U langsmith
```

#### Create an API Key

To create an API key head to the settings <a href="https://smith.langchain.com/o/7f206571-8ff7-5ef1-ad8b-288d7de9b768/settings" target="_blank">page</a> on smith.langchain.com. Then click Create API Key.


#### Update the application

You can enable monitoring by adding the following lines to the application.

```python
os.environ['LANGCHAIN_TRACING_V2'] = 'True'
os.environ['LANGCHAIN_API_KEY'] = 'XXX'
os.environ['LANGCHAIN_ENDPOINT'] = 'https://api.smith.langchain.com'
os.environ['LANGCHAIN_PROJECT'] = 'car-models'
```

When you log in to Langsmith, you should see an output similar to the screenshot below.

<p align="left">
  <img src="images/4.png" alt="drawing" width="800"/>
</p>

In this way; you can monitor and evaluate your language model applications and  agents to help you move from prototype to production.

## LangServe (Deployment)

LangServe is a library within the LangChain framework, designed to help developers deploy LangChain applications as REST APIs using FastAPI. 

It automatically extracts and applies input and output schemas for API calls, provides detailed error messages, supports concurrent requests, and has efficient API endpoints for single and batch calls. 

The library also includes a playground page for testing and API documentation capabilities. LangServe is built on well-established Python libraries like FastAPI and Pydantic, and it offers optional tracing to LangSmith with an API key.

**Note:** FastAPI is a fast (high-performance), web framework for building APIs with Python based on standard Python type hints.

### To Create REST APIs for LangChain Applications

LangChain is a powerful framework for building applications with AI language models. It simplifies the process of interfacing with local or remote LLMs by making it easy to template prompts, configure query contexts, and chain discrete processes together to form complex pipelines.

LangServe is a LangChain project that helps you build and deliver these applications over a REST API. Under the hood, it uses FastAPI to construct routes and build web services and leverages Pydantic to handle data validation.

**Note:** Pydantic is the most widely used data validation library for Python.

1. Create a project directory that will hold the application and assets you will create.

```bash
mkdir my-langserve-app
cd my-langserve-app
```

2. Inside the created directory, create a file named .env in your text editor. Define the OPENAI_API_KEY environment variable by setting it to your OpenAI API key.

```python
# .env
OPENAI_API_KEY="<YOUR_OPENAI_API_KEY>"
```
The application will read the API key in this file to verify its requests for OpenAI services.

```python
# app/server.py
from decouple import config
from fastapi import FastAPI
from langchain_openai import ChatOpenAI
from langchain.prompts import ChatPromptTemplate
from langserve import add_routes


app = FastAPI()

model = ChatOpenAI(openai_api_key=config("OPENAI_API_KEY"))
prompt = ChatPromptTemplate.from_template("Give me a summary about {topic} in a paragraph or less.")
chain = prompt | model

add_routes(app, chain, path="/openai")

if __name__ == "__main__":
    import uvicorn

    uvicorn.run(app, host="0.0.0.0", port=8000)

```

## LangFlow


## RagStack


## NoSQLBench