# 🎬 Catálogo de Filmes

Mini-plataforma de catálogo de filmes feita com **API em Python (FastAPI)**, **PostgreSQL**, **Frontend em Nginx** e **observabilidade com Grafana + Prometheus**.  
Tudo rodando com **Docker Compose** e CI/CD no **GitHub Actions**.

---

## 🚀 Funcionalidades

- **API (FastAPI)**  
  - Rota `/health` para verificação de status (retorna 200).  
  - CRUD completo de filmes: criar, listar, editar e excluir.  
  - Rota `/metrics` para integração com Prometheus.  

- **Banco de Dados (Postgres)**  
  - Volume persistente, dados não se perdem após `docker compose down/up`.  

- **Frontend (Nginx)**  
  - Interface simples servida em `http://localhost:8080`.  

- **Observabilidade**  
  - Prometheus coleta métricas da API.  
  - Grafana mostra dashboard com CPU, memória e requisições em tempo real.  

---

## 📂 Estrutura do Projeto

.
├── .env.example
├── .github/workflows/ci.yml
├── api/
│ ├── Dockerfile
│ ├── .dockerignore
│ ├── main.py
│ └── requirements.txt
├── docker-compose.yml
├── frontend/
│ ├── index.html
│ ├── script.js
│ ├── style.css
│ └── nginx/
│ ├── Dockerfile
│ └── nginx.conf
├── grafana/
│ ├── provisioning/
│ │ ├── dashboards.yml
│ │ └── dashboards/
│ │ └── api-dashboard.json
├── prometheus.yml
└── README.md


---

## 🛠 Como Rodar o Projeto

### 1. Pré-requisitos
- Docker  
- Docker Compose  

### 2. Clonar o repositório
```bash
git clone https://github.com/seu-usuario/catalogo-filmes.git
cd catalogo-filmes

3. Configurar variáveis de ambiente
cp .env.example .env

4. Subir os containers
docker compose up -d --build

🔎 Acessos

API → http://localhost:8000

Documentação Swagger → http://localhost:8000/docs

Frontend → http://localhost:8080

Prometheus → http://localhost:9090

Grafana → http://localhost:3000

usuário: admin

senha: admin

⚙️ CI/CD

O repositório tem pipeline no GitHub Actions (.github/workflows/ci.yml) que:

Builda a imagem da API

Faz push da imagem para o container registry (Docker Hub ou GitHub Packages)

Roda automaticamente quando há push na branch main