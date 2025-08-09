# Projeto CRUD - FastAPI + Streamlit

Este projeto é um sistema CRUD (Create, Read, Update, Delete) completo para gerenciamento de produtos, com backend em FastAPI e frontend em Streamlit. O objetivo é demonstrar a integração entre uma API moderna e uma interface web simples e funcional.

## Estrutura do Projeto

```
projeto_crud/
├── backend/           # API FastAPI (Python)
│   ├── main.py        # Inicialização da aplicação FastAPI
│   ├── crud.py        # Funções CRUD (criar, ler, atualizar, deletar)
│   ├── models.py      # Modelos ORM (SQLAlchemy)
│   ├── schemas.py     # Schemas Pydantic (validação)
│   ├── database.py    # Configuração do banco de dados SQLite
│   ├── router.py      # Rotas da API
│   ├── requirements.txt
│   └── ...
├── frontend/          # Interface Streamlit (Python)
│   ├── app.py         # Interface web para interação CRUD
│   ├── logo.png       # Logo exibida na interface
│   ├── requirements.txt
│   └── .streamlit/    # Configuração do Streamlit
├── docker-compose.yml # Orquestração dos containers
├── pyproject.toml / poetry.lock
└── README.md
```

## Backend (FastAPI)

O backend é responsável por expor uma API REST para manipulação dos produtos. Principais arquivos:

- **main.py**: Inicializa a aplicação FastAPI e inclui as rotas.
- **models.py**: Define o modelo do produto (campos: id, name, description, price, categoria, email_fornecedor, created_at).
- **schemas.py**: Define os schemas de entrada e saída, com validação de campos e categorias.
- **crud.py**: Funções para criar, buscar, atualizar e deletar produtos no banco de dados.
- **router.py**: Define as rotas da API para cada operação CRUD.
- **database.py**: Configura o banco SQLite e a sessão do SQLAlchemy.

### Principais Endpoints
- `POST /products/` - Cria um novo produto
- `GET /products/` - Lista todos os produtos
- `GET /products/{id}` - Busca um produto pelo ID
- `PUT /products/{id}` - Atualiza um produto
- `DELETE /products/{id}` - Remove um produto

## Frontend (Streamlit)

O frontend permite ao usuário interagir com a API de forma visual e intuitiva:

- Adicionar produto: formulário para inserir nome, descrição, preço, categoria e email do fornecedor.
- Visualizar produtos: exibe todos os produtos em tabela.
- Buscar produto: busca por ID e exibe detalhes.
- Atualizar produto: formulário para atualizar qualquer campo de um produto existente.
- Deletar produto: remove produto pelo ID.

Imagem do frontend: 
![alt text](image-2.png)

## Como Executar o Projeto

### Usando Docker Compose (Recomendado)
1. Certifique-se de ter Docker e Docker Compose instalados.
2. Na raiz do projeto, execute:
   ```bash
   docker-compose up --build
   ```
3. O backend estará disponível em `http://localhost:8000` (Swagger em `/docs`).
4. O frontend estará disponível em `http://localhost:8501`.

### Manualmente (sem Docker)
1. Crie e ative um ambiente virtual Python.
2. Instale as dependências do backend e frontend (requirements.txt ou poetry).
3. Inicie o backend:
   ```bash
   cd backend
   uvicorn main:app --reload --host 0.0.0.0 --port 8000
   ```
4. Em outro terminal, inicie o frontend:
   ```bash
   cd frontend
   streamlit run app.py
   ```

## Observações
- O banco de dados utilizado é SQLite, criado automaticamente na primeira execução.
- O projeto já está pronto para deploy em containers Docker.
- O frontend se comunica com o backend via HTTP.

---

