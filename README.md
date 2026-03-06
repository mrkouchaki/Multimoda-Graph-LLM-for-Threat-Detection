# Multimoda-Graph-LLM-for-Threat-Detection
Multimoda Graph-LLM for Threat Detection
# Adaptive Cross-Attention Multimodal GraphLLM for Social Network Threat Detection

This repository implements a **Multimodal GraphLLM architecture for social network threat detection**, designed to jointly analyze **graph-structured relational data and textual user content**.

The system integrates **Graph Transformers and Language Models using an adaptive cross-attention fusion mechanism**, enabling the model to dynamically balance structural and semantic signals when detecting malicious behavior such as **bot activity on social platforms**.

This work explores **graph-text multimodal reasoning**, an emerging research direction where **Graph Neural Networks (GNNs)** and **Large Language Models (LLMs)** are combined to understand complex relational environments.

---

# Problem Motivation

Modern social networks contain **two complementary sources of information**:

### Graph structure
User relationships and interaction networks

Examples:
- follow connections
- friend networks
- posting relationships

### Textual content
User-generated text

Examples:
- tweets
- user profiles
- descriptions
- messages

Traditional approaches analyze these **modalities separately**, which leads to incomplete reasoning.

Graph-text multimodal models address this limitation by **combining relational reasoning and semantic understanding in a single architecture**.

This is particularly important for:

- bot detection
- misinformation detection
- coordinated behavior analysis
- fraud detection
- social threat monitoring

---

# Key Idea

The proposed **Multimodal GraphLLM** integrates:

| Component | Purpose |
|---|---|
| Graph Transformer | learns structural relationships between users and tweets |
| Text Transformer (BERT) | extracts semantic embeddings from textual content |
| Cross-Attention Fusion | dynamically combines graph and text representations |
| Classification Head | detects malicious or bot behavior |

Unlike static fusion methods, the model introduces an **adaptive cross-attention mechanism** that learns how much each modality should contribute to the final prediction.

This allows the model to:

- prioritize **graph structure when behavior patterns are important**
- prioritize **text semantics when linguistic signals reveal threats**

---

# Architecture Overview
The pipeline combines three main components:

1. **Graph Encoder**
   - Graph-based representation learning
   - Captures structural relationships between nodes

2. **Text Encoder**
   - Transformer-based language model
   - Processes textual node descriptions

3. **Multimodal Fusion Layer**
   - Integrates graph embeddings and text embeddings
   - Enables joint graph–text reasoning
Graph Structure ───► Graph Encoder ──┐
│
Node Text ───────► Text Encoder ─────┼──► Multimodal Fusion ─► GraphLLM
│
Graph Metadata ──────────────────────┘

```
User Graph + Tweet Network
        │
        ▼
Graph Transformer Module
(GNN + Attention)
        │
        ▼
Graph Embedding
        │

User Tweets / Descriptions
        │
        ▼
Text Transformer Module
(BERT embeddings)
        │
        ▼
Text Embedding

        ▼
Adaptive Cross-Attention Fusion
        │
        ▼
Joint Multimodal Representation
        │
        ▼
Bot Detection Classifier
```

The fusion layer performs **cross-modal attention**, where:

- text embeddings act as **queries**
- graph embeddings act as **keys and values**

allowing the model to learn **cross-modal dependencies between relational patterns and language usage**.

---

# Dataset

The system is evaluated using the **TwiBot-20 dataset**, a benchmark dataset for Twitter bot detection.

The dataset contains:

### Nodes
- user accounts
- tweets

### Edges
- follow relationships
- friend relationships
- posting interactions

### Node Features
- user descriptions
- tweet text
- metadata

Each user node is labeled as:

```
bot
human
```

---

# Graph Representation

The graph is constructed as a **heterogeneous graph** using **Deep Graph Library (DGL)**.

Node types include:

```
User nodes
Tweet nodes
```

Edge types include:

```
friend
follow
post
```

The graph transformer performs **attention-based message passing** over this heterogeneous structure.

---

# Text Representation

Text data is encoded using **BERT embeddings**.

Sources include:

- tweet text
- user profile descriptions

The BERT encoder is **frozen** during training to reduce computational cost while preserving semantic richness.

Mean pooling is applied to obtain fixed-size text embeddings.

---

# Multimodal Fusion

The fusion layer performs **adaptive cross-attention** between graph and text embeddings.

The mechanism allows the model to dynamically determine:

```
how much graph information to use
how much text information to use
```

for each sample.

This adaptive weighting improves robustness in scenarios where one modality may dominate.

---

# Key Features

• Multimodal **graph + text reasoning**  
• Adaptive **cross-attention fusion**  
• Graph Transformer for relational reasoning  
• BERT-based semantic text embeddings  
• Heterogeneous graph support  
• Scalable architecture for large social networks  

---

# Applications

The architecture can be applied to several domains beyond bot detection:

- misinformation detection
- social network security
- fraud detection
- knowledge graph reasoning
- recommendation systems
- cyber threat intelligence

---

# Research Context

This project explores concepts related to:

- Graph Neural Networks
- Graph Transformers
- Multimodal Large Language Models
- Graph-Text Interaction Models
- Social Network Threat Detection

---

# Repository Structure

```
GraphLLM/
│
├── Multimodal/
│   multimodal GraphLLM experiments
│
├── Multimodal_GraphLLM/
│   graph-text multimodal pipeline
│
├── GraphLLM-2ndType-v1-Multimodal-v4-Cleaned.ipynb
│   main implementation notebook
│
└── README.md
```

---

# Running the Notebook

Clone the repository

```
git clone https://github.com/mrkouchaki/GraphLLM.git
cd GraphLLM
```

Install dependencies

```
pip install torch transformers sentence-transformers networkx dgl
```

Run the notebook

```
jupyter notebook GraphLLM-2ndType-v1-Multimodal-v4-Cleaned.ipynb
```

---

# Author

Mohammadreza Kouchaki  
PhD Researcher — AI/ML for Communication Networks  
Mississippi State University

---

# License

Apache 2.0 License
