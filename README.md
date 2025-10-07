# 🧠 Estudo de RAG com Agente ReAct, LangGraph e Groq

![Python](https://img.shields.io/badge/Python-3.11-blue?style=for-the-badge&logo=python)
![LangChain](https://img.shields.io/badge/LangChain-Framework-green?style=for-the-badge)
![Groq](https://img.shields.io/badge/Groq-LPU%20Inference-orange?style=for-the-badge)

## 🎯 Sobre o Projeto

Este repositório contém um estudo prático sobre a implementação de um sistema de **RAG (Retrieval-Augmented Generation)** utilizando um agente autônomo (padrão ReAct). O objetivo é demonstrar como construir um assistente de IA capaz de consultar diferentes bases de conhecimento para responder perguntas de forma contextual e precisa.

O projeto utiliza a velocidade da LPU da **Groq** para inferências com o modelo Llama 3 e o poder da biblioteca **LangChain** (e **LangGraph**) para orquestrar o fluxo de dados e a lógica do agente.

A demonstração é feita em um Jupyter Notebook (`RAG_Study.ipynb`) onde o agente aprende a escolher a fonte de dados correta (entre PDFs sobre a NASA, Dengue e Agricultura) para responder às perguntas do usuário.

## ✨ Funcionalidades Principais

- **Múltiplas Fontes de Conhecimento**: Carregamento e vetorização de múltiplos documentos PDF a partir de URLs.
- **Agente Inteligente (ReAct)**: Um agente que raciocina e escolhe a melhor "ferramenta" (base de dados) para cada pergunta.
- **Orquestração com LangGraph**: Um grafo de estados gerencia o ciclo de vida do agente e sua memória de conversação.
- **Embeddings de Alta Performance**: Uso do modelo `mxbai-embed-large-v1` da HuggingFace para criar embeddings de qualidade.
- **Inferência Ultra-Rápida**: Respostas geradas em tempo real graças à API da Groq.

## 🛠️ Tecnologias Utilizadas

* **Linguagem**: Python 3.11+
* **Orquestração de IA**: LangChain, LangGraph
* **Modelo de Linguagem (LLM)**: Llama 3 (via API Groq)
* **Vetorização (Embeddings)**: LangChain HuggingFace (`mxbai-embed-large-v1`)
* **Bibliotecas de Apoio**: PyPDF, python-dotenv, ipywidgets
* **Ambiente**: Gerenciado com `uv`

## 🚀 Como Executar o Projeto

Siga os passos abaixo para configurar e executar o projeto em seu ambiente local.

**1. Clone o Repositório**
```bash
# Lembre-se de substituir pela URL do seu repositório!
git clone [https://github.com/SEU-USUARIO/SEU-REPOSITORIO.git](https://github.com/SEU-USUARIO/SEU-REPOSITORIO.git)
cd SEU-REPOSITORIO
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
   - Inicie o Jupyter Lab:
     ```bash
     jupyter lab
     ```
   - Abra o arquivo `RAG_Study.ipynb` e execute as células em ordem.

## 📖 Estrutura do Notebook

O notebook `RAG_Study (1).ipynb` foi refatorado e agora segue uma estrutura limpa e organizada:

1.  **Setup e Configurações Iniciais**:
    * Carregamento seguro da chave de API do arquivo `.env`.
    * Centralização de todas as importações de bibliotecas.
    * Inicialização dos modelos globais (LLM da Groq e modelo de Embeddings da Hugging Face).

2.  **Funções de Apoio e Criação das Bases de Conhecimento**:
    * Definição de uma função auxiliar (`carrega_pdf`) para baixar e vetorizar documentos de forma reutilizável.
    * Criação das três bases de conhecimento (`vector_store_nasa`, `vector_store_agriculture`, `vector_store_dengue`) usando a função auxiliar.

3.  **Definição das Ferramentas do Agente**:
    * Cada base de conhecimento é encapsulada em uma função e marcada com o decorador `@tool`. Isso as expõe como "ferramentas" que o agente pode escolher usar.

4.  **Construção do Agente com LangGraph**:
    * Definição do `system_prompt` que instrui o agente sobre seu comportamento e sobre como usar as ferramentas.
    * Criação do agente ReAct e compilação do grafo que gerencia a lógica de execução e a memória.

5.  **Interagindo com o Agente**:
    * Definição de uma função de chat (`chat_com_agente`) para facilitar a comunicação com o agente, gerenciando o histórico da conversa.
    * Células de exemplo que testam a capacidade do agente de escolher a ferramenta correta e manter o contexto em uma conversa.

## Agradecimentos

Este projeto foi desenvolvido como parte dos estudos realizados no curso de RAG da **Alura**.

---