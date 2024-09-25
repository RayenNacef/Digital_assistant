# Innovative LLM based Digital Assistant for Enhanced User Interaction in Automotive Field
## Done by Rayen Naced and Amine Meddeb
## Description of the project
This project focuses on creating an advanced digital assistant to improve user engagement with our tool. The digital assistant will be equipped to perform several key functions, including:

- **Search:** Allowing users to swiftly and effectively locate information within the tool.
- **Wireshark Analysis:** Enabling users to read and analyze data captured from Wireshark.
#  Project Setup
To set up the virtual environement of the project:
- Create a virtual environement with python using for ubuntu users:
```bash
python -m venv myenv
source myenv/bin/activate 
```
- run the **envir.txt** file inside the virtual environement  
```bash
pip install -r envir.txt 
``` 

To run this notebook, ensure that you have the following dependencies installed:

1. **mxbai-embed-large** model for embedding
2. **llama3.1:8b-instruct-q5_0** LLM model
3. **ollama**
4. **Docker**

**To set up Milvus**
NB: We used Docker Compose:
- Install Milvus standalone with docker compose : intall the YAML file to run milvus and make sure the YAML file is in the same folder of your code.
- Run this command in the terminal:
```bash
wget https://github.com/milvus-io/milvus/releases/download/v2.3.21/milvus-standalone-docker-compose.yml -O docker-compose.yml

```

- Make sure to run this command before running the kernel ( they use the same port ).

```bash
sudo docker compose up -d 
```
- Verify that the 3 containers run 'etcd' ,'standalone' and 'minio'. 
```bash
sudo docker ps  
```
### Installation

You can install these models using the following links:
[Install Docker](https://docs.docker.com/desktop/install/ubuntu/)

[Install Ollama](https://ollama.com/download)
To pull ollama model
```bash
ollama pull llama3.1:8b-instruct-q5_0
```
To run ollama
```bash
ollama run llama3.1:8b-instruct-q5_0
```
[Install Milvus Version:**2.3**](https://milvus.io/docs/v2.3.x/install_standalone-docker-compose.md)
## Running Inference in the Notebook
**If you need to add data to the model, then you need to run all the Notebook.**
To add data, you need to make modification to insert your data to the following cells:
- "Load your txt document" (If your data is in file.text)
- "Extract informations from sites that are stored in a csv file" (If you want to add url links to the file.csv)


**If you need to do an inference to have a conversation with the Chatbot then  you only need to run the following cells:**


**NB:** Note: The notebook is well-documented, with each cell clearly defined. Follow the names provided for each cell to perform the inference.
- "import librairies"
- "Connnect to Milvus"
- "import json"
- "count json files"
- "create a list"
- "Define a Milvus collection "
- "Create a Milvus collection "
- "Create index and load collection"
- "Insert data into Milvus collection"
- "Create an index on the "embedding" field"
- "Load collection"
- "Define search params"
- "Search function"
- "ADD MEMORY" 
- "Initialize memory"
- "Genrate response"
- "Cerate interface by tkinter"
# Technologies Used
In this section, we will describe the technologies we used to develop the project
## RAG (Retrieval Augmented Generation) 
### What is RAG?
 RAG is a technique that combines information retrieval with text generation. It first retrieves relevant information from a large database or external source, then uses that information to generate more accurate and contextually relevant responses or content.

 ![RAG_Technique](https://community.intel.com/t5/image/serverpage/image-id/51771i70A3502B3A2876AE/image-size/large?v=v2&px=999&whitelist-exif-data=Orientation%2CResolution%2COriginalDefaultFinalSize%2CCopyright)

### Why RAG?
- **Enhanced Accuracy:** Combines retrieval of relevant information with text generation to improve response accuracy.
- **Up-to-Date Information:** Accesses real-time or specialized knowledge, ensuring responses are current and relevant.
- **Contextual Relevance:** Uses retrieved data to generate content that is better aligned with the specific query or context.
- **Scalable Knowledge:** Leverages large external databases, allowing the model to handle a broader range of topics without needing exhaustive training.
## LLM : 'llama3.1:8b-instruct-q5_0'
 llama3.1:8b-instruct-q5_0 is chosen for its balance of performance and efficiency. With 8 billion parameters. The choice of the model was made after comparison with other LLMs of similar size. Size is a critical factor due to our hardware limitations, and this model offers an optimal balance between performance and resource efficiency, making it the best fit for our requirements. 
## Embedding model : "mxbai-embed-large"
The "mxbai-embed-large" embedding model was selected for its ability to generate high-quality, dense vector representations of text.
Vector Data Base : Milvus ( it is a DB that can support a lot of documents and minimise the time in retrieving)

It needs Docker to be run.
## Ollama
Ollama is a platform that simplifies working with large language models (LLMs). It provides an interface to interact with, manage, and deploy LLMs
## Milvus
Milvus is a high-performance, open-source vector database designed for efficient similarity search and handling large-scale, high-dimensional data. 
## Tkinter
Tkinter is a popular choice for building graphical user interfaces in Python due to its inclusion in the standard library, ease of use, and cross-platform capabilities.


# Workflow

- Data Collection: (data was in form of pdf and urls from the internet)
- Data Cleaning
- Chuncking
- Embedding the chuncks
- Storing the embeddings in Milvus
- Searching for the k relevant chuncks
- Passing the original prompt and the k relevant chuncks to the LLM
- Adding memory to chatbots to get a whole conversation with it
- Develop a tkinter interface to interact with the user

<p align="center">
  <img src="https://www.mlexpert.io/_next/image?url=%2F_next%2Fstatic%2Fmedia%2Fadvanced-rag-architecture.3de2fee5.png&w=3840&q=75" alt="AWorkflow Diagram" />
</p>

### Demo of the conversation with the model
Open /Demo/answers of our model folder
### Benchmarking our model to the basic ollama model and with ChatGPT-4o mini
Open Demo folder
