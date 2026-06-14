# 🤖 Agente de RH com RAG e Reranking

Um assistente inteligente para consulta de políticas internas de Recursos Humanos utilizando **IA Generativa**, **RAG (Retrieval-Augmented Generation)** e **Reranking Semântico**.

O projeto permite que colaboradores façam perguntas em linguagem natural sobre documentos corporativos, como políticas de férias, home office e código de conduta, recebendo respostas contextualizadas e fundamentadas nas fontes consultadas.


## 🚀 Objetivo

Criar um agente conversacional capaz de responder dúvidas sobre políticas internas de RH utilizando documentos corporativos como base de conhecimento.

Para aumentar a precisão das respostas, o projeto implementa uma arquitetura RAG com uma etapa adicional de **reranking semântico**, garantindo que os trechos mais relevantes sejam utilizados na geração da resposta final.


## 🏗️ Arquitetura da Solução

```text
PDFs Corporativos
       │
       ▼
 Carregamento
(PyPDFLoader)
       │
       ▼
 Chunking
(RecursiveCharacterTextSplitter)
       │
       ▼
 Enriquecimento
de Metadados
       │
       ▼
 Embeddings
(OpenAI)
       │
       ▼
 Vector Store
(ChromaDB)
       │
       ▼
 Recuperação
Similarity Search
       │
       ▼
 Reranking Semântico
(GPT-4o Mini)
       │
       ▼
 Construção do Contexto
       │
       ▼
 Geração da Resposta
(GPT-4o Mini)
       │
       ▼
 Interface Streamlit
```


## ✨ Funcionalidades

### 📄 Leitura automática de documentos

O agente realiza a ingestão de múltiplos documentos PDF contendo políticas corporativas:

- Política de Férias
- Política de Home Office
- Código de Conduta


### ✂️ Chunking Inteligente

Os documentos são divididos em trechos semânticos para otimizar a recuperação de informações.

Configuração utilizada:

```python
chunk_size = 800
chunk_overlap = 150
```


### 🏷️ Enriquecimento de Metadados

Cada chunk recebe uma classificação automática baseada em seu conteúdo:

| Categoria | Critério |
|------------|------------|
| férias | Termos relacionados a férias |
| home_office | Termos relacionados a trabalho remoto |
| conduta | Termos relacionados a ética e comportamento |
| geral | Conteúdo não categorizado |


### 🧠 Busca Vetorial

Os documentos são indexados utilizando embeddings da OpenAI e armazenados em um banco vetorial Chroma.

Modelo utilizado:

```python
text-embedding-3-small
```


### 🎯 Reranking Semântico

Após a recuperação inicial dos documentos, um segundo processo de análise é executado.

O próprio LLM avalia a relevância de cada trecho para a pergunta realizada e atribui uma nota de 0 a 10.

Os documentos são então reordenados antes da geração da resposta final.

Benefícios:

- Maior precisão
- Menor ruído
- Melhor aproveitamento do contexto
- Redução de respostas incorretas


### 💬 Respostas Contextualizadas

O agente responde exclusivamente com base nos documentos corporativos fornecidos.

Além da resposta, a aplicação exibe:

- Documento de origem
- Categoria identificada
- Trechos utilizados na construção da resposta


## 🛠️ Tecnologias Utilizadas

### Backend

- Python 3.11+
- LangChain

### IA Generativa

- OpenAI GPT-4o Mini
- OpenAI Embeddings

### Banco Vetorial

- ChromaDB

### Processamento de Documentos

- PyPDFLoader

### Interface

- Streamlit


## ⚙️ Pré-requisitos

Antes de executar o projeto, certifique-se de possuir:

- Python 3.11+
- Conta OpenAI
- Chave de API válida


## 🎓 Aprendizados Demonstrados

Este projeto demonstra conhecimentos em:

- Engenharia de Prompt
- IA Generativa
- Retrieval-Augmented Generation (RAG)
- Embeddings
- Vetorização de documentos
- Busca semântica
- Reranking
- LangChain
- Streamlit
- Construção de Assistentes Corporativos


## 📄 Licença

Projeto desenvolvido para fins educacionais e de estudo em Inteligência Artificial Generativa.

## 🧑‍💻 Autor
</p>
<p align="center">
Desenvolvido com 💙 por <strong>Iridiana Campos</strong>
</p>
<p align="center">
