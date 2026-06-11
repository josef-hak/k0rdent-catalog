# RAG and Vector Search Stack
A curated stack for building Retrieval-Augmented Generation applications. Combines full-text and vector search with document processing and a self-hosted AI chat interface for enterprise knowledge bases and semantic search systems.

The k0rdent Catalog simplifies deploying and managing production-ready platform services across multiple Kubernetes clusters. Catalog applications are packaged as service templates that can be installed once and then deployed consistently across many clusters using MultiClusterService resources.

This solution deploys a RAG-ready stack consisting of:

- Traefik – provides a standard Kubernetes ingress controller for exposing the chat UI
- OpenSearch – search and analytics engine with vector search capabilities for RAG document retrieval
- Tika – extracts text from PDFs, Office documents, and 1000+ formats for ingestion into the search index
- Open WebUI – self-hosted AI chat interface with built-in RAG support, document upload, and retrieval

Together, these components provide a production RAG pipeline:

- Users upload documents through Open WebUI, which are processed by Tika for text extraction
- OpenSearch indexes documents and provides full-text and vector similarity search
- Open WebUI retrieves relevant context from OpenSearch to augment LLM responses
- Traefik exposes the Open WebUI interface for external access

Using the k0rdent Catalog service templates, this stack can be installed once and then deployed automatically to any number of clusters.

#### Prerequisites
Deploy k0rdent {{ version }}: [QuickStart](https://docs.k0rdent.io/{{ version }}/admin/installation/install-k0rdent/){ target="_blank" }

#### Install template to k0rdent
{{ install_code  }}

#### Verify service template
{{ verify_code }}

#### Deploy stack
{{ deploy_code }}

#### Testing in child cluster
1. Access Open WebUI at the configured ingress host.

2. Upload a document (PDF, DOCX, etc.) through the Open WebUI interface to test the RAG pipeline.

3. Ask a question about the uploaded document content to verify retrieval-augmented generation is working.

4. Verify OpenSearch is running:
~~~bash
kubectl get pods -n opensearch
~~~

5. Verify Tika is running:
~~~bash
kubectl get pods -n tika
~~~
