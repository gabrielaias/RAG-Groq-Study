# 🧠 Estudo de RAG com Agente ReAct, LangGraph e Groq

![Python](https://img.shields.io/badge/Python-3.10%2B-blue?style=for-the-badge&logo=python)
![LangChain](https://img.shields.io/badge/LangChain-Framework-green?style=for-the-badge)
![Groq](https://img.shields.io/badge/Groq-LPU%20Inference-orange?style=for-the-badge)

## 🎯 Sobre o Projeto

Este repositório contém um estudo prático sobre a implementação de um sistema de **RAG (Retrieval-Augmented Generation)** utilizando um agente autônomo (padrão ReAct). O objetivo é demonstrar como construir um assistente de IA capaz de consultar diferentes bases de conhecimento para responder perguntas de forma contextual e precisa.

O projeto utiliza a velocidade da LPU da **Groq** para inferências com o modelo Llama 3 e o poder da biblioteca **LangChain** (e **LangGraph**) para orquestrar o fluxo de dados e a lógica do agente.

A demonstração é feita em um Jupyter Notebook (`RAG_Study.ipynb`) onde o agente aprende a escolher a fonte de dados correta (entre PDFs sobre a NASA, Dengue e Agricultura) para responder às perguntas do usuário.

## ✨ Funcionalidades Principais

- **Múltiplas Fontes de Conhecimento**: Carregamento e vetorização de múltiplos documentos PDF.
- **Agente Inteligente (ReAct)**: Um agente que raciocina e escolhe a melhor "ferramenta" (base de dados) para cada pergunta.
- **Orquestração com LangGraph**: Um grafo de estados gerencia o ciclo de vida do agente: pergunta -> pensamento -> ferramenta -> resposta.
- **Embeddings de Alta Performance**: Uso do modelo `mxbai-embed-large-v1` da HuggingFace para criar embeddings de qualidade.
- **Inferência Ultra-Rápida**: Respostas geradas em tempo real graças à API da Groq.

## 🛠️ Tecnologias Utilizadas

* **Linguagem**: Python 3.10+
* **Orquestração de IA**: LangChain, LangGraph
* **Modelo de Linguagem (LLM)**: Llama 3 (via API Groq)
* **Vetorização (Embeddings)**: LangChain HuggingFace (`mxbai-embed-large-v1`)
* **Manipulação de Dados**: PyPDF
* **Ambiente**: Gerenciado com `uv`

## 🚀 Como Executar o Projeto

Siga os passos abaixo para configurar e executar o projeto em seu ambiente local.

**1. Clone o Repositório**
```bash
git clone [https://github.com/](https://github.com/)[SEU-USUARIO]/[NOME-DO-REPOSITORIO].git
cd [NOME-DO-REPOSITORIO]
```

**2. Crie e Ative o Ambiente Virtual com `uv`**
```bash
# Criar o ambiente virtual na pasta .venv
uv venv

# Ativar o ambiente (Windows - PowerShell)
.venv\Scripts\Activate.ps1

# Ativar o ambiente (Linux/macOS)
source .venv/bin/activate
```

**3. Instale as Dependências**
```bash
uv pip install -r requirements.txt
```

**4. Configure sua Chave de API**
   - Crie um arquivo chamado `.env` na raiz do projeto.
   - Adicione sua chave da API da Groq dentro dele:
     ```
     GROQ_API_KEY="sua_chave_api_aqui"
     ```

**5. Execute o Jupyter Notebook**
   - Inicie o Jupyter Lab ou Notebook:
     ```bash
     jupyter lab
     ```
   - Abra o arquivo `RAG_Study.ipynb` e execute as células.

## 📖 Estrutura do Notebook

O notebook `RAG_Study.ipynb` está dividido nas seguintes seções:

1.  **Instalação de Dependências**: Comandos `pip` para instalar as bibliotecas.
2.  **Configuração da API**: Carregamento da chave da Groq a partir do arquivo `.env`.
3.  **Construção da Base de Conhecimento (RAG)**:
    - Carregamento de um PDF de exemplo (da NASA).
    - Criação de um `retriever` para buscar informações no documento.
    - Teste da cadeia RAG simples.
4.  **Criação de Ferramentas (Tools)**:
    - Generalização do processo para carregar múltiplos PDFs (Dengue, Agricultura).
    - Definição de `tools`, onde cada uma é um `retriever` para uma base de conhecimento específica.
5.  **Criação do Agente com LangGraph**:
    - Definição do `system_prompt` que instrui o agente a como escolher as ferramentas.
    - Construção do grafo que define a lógica de execução (agente -> ferramenta -> agente).
6.  **Execução e Testes**:
    - Demonstração do uso do agente com perguntas sobre diferentes tópicos.
    - Inclusão de memória para que o agente se lembre do histórico da conversa.

## Agradecimentos

Este projeto foi desenvolvido como parte dos estudos realizados no curso de RAG da **Alura**.

---