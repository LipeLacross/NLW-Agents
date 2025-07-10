## 🌐 [English Version of README](README_EN.md)

# NLW Agents - Rocketseat

Plataforma de perguntas e respostas ao vivo com inteligência artificial, desenvolvida durante o NLW#20 da Rocketseat. O projeto é dividido em dois diretórios principais: **server** (backend) e **web** (frontend), permitindo o gerenciamento em tempo real de perguntas, respostas automáticas por IA e integração com streaming ao vivo.

## 🔨 Funcionalidades do Projeto

- 📝 Gerenciamento de perguntas em tempo real
- 🤖 Respostas automáticas geradas por IA (Google Gemini)
- 📡 Integração com streaming ao vivo
- 🏷️ Criação e listagem de salas temáticas
- 🎤 Transcrição e análise de áudio via IA

### 📸 Exemplo Visual do Projeto

<div align="center"> <img src="https://github.com/user-attachments/assets/98f39725-fc46-4eed-88ef-9557d6491345" alt="Screenshot da aplicação NLW Agents" width="80%" style="margin: 16px 0; border-radius: 10px;"> </div>

## ✔️ Técnicas e Tecnologias Utilizadas

- **Frontend**
  - React 19.1 ⚛️
  - TypeScript 5.8
  - Vite 7.0 ⚡
  - TailwindCSS 4.1 🎨
  - React Router Dom 7.6
  - TanStack React Query 5.8
  - Radix UI e Shadcn/ui
  - Lucide React (ícones)

- **Backend**
  - Node.js (experimental strip types) 🟩
  - Fastify 🚀
  - TypeScript
  - PostgreSQL + pgvector 🗄️
  - Drizzle ORM
  - Zod (validação)
  - Docker 🐳
  - Biome (lint/format)
  - Google Gemini API (IA)

## 📁 Estrutura do Projeto

- **LICENSE**: Licença do projeto.
- **README.md**: Documentação principal.
- **README_EN.md**: Documentação em inglês.

- **server/** (Backend)
  - biome.jsonc: Configuração do lint/formatador.
  - client.http: Coleção de requisições HTTP para testes.
  - docker/
    - setup.sql: Script para criação da extensão vector no banco.
  - docker-compose.yml: Orquestração dos containers.
  - drizzle.config.ts: Configuração do ORM Drizzle.
  - package.json: Dependências e scripts do backend.
  - src/
    - db/
      - connection.ts: Conexão com o banco PostgreSQL.
      - migrations/: Scripts de migração.
      - schema/: Definição das tabelas (rooms, questions, audio_chunks).
      - seed.ts: População do banco com dados de exemplo.
    - http/: Rotas e controladores da API.
    - server.ts: Inicialização do servidor Fastify.
    - services/
      - gemini.ts: Integração com a API Google Gemini.

- **web/** (Frontend)
  - biome.jsonc: Configuração do lint/formatador.
  - components.json: Configuração de componentes.
  - index.html: HTML principal da aplicação.
  - package.json: Dependências e scripts do frontend.
  - src/
    - app.tsx: Componente raiz e rotas.
    - components/: Componentes reutilizáveis e UI (inclui subpasta ui/ com botões, cards, forms, etc).
    - http/: Hooks para consumo da API e tipos.
    - lib/: Utilitários (ex: dayjs, utils).
    - main.tsx: Ponto de entrada da aplicação React.
    - pages/: Páginas principais do app (criar sala, sala, gravação de áudio).
  - tsconfig*.json: Configuração do TypeScript.
  - vite.config.ts: Configuração do Vite.

## 🛠️ Abrir e rodar o projeto

Para iniciar o projeto localmente, siga os passos abaixo:

1. **Certifique-se de que o Node.js está instalado**:
   - O [Node.js](https://nodejs.org/) é necessário para rodar o projeto. Você pode verificar se já o tem instalado com:
     ```bash
     node -v
     ```
   - Se não estiver instalado, baixe e instale a versão recomendada.

2. **Clone o Repositório**:
   - Copie a URL do repositório e execute o comando abaixo no terminal:
     ```bash
     git clone 
     ```

3. **Backend (`server/`)**:
   - Acesse a pasta do backend:
     ```bash
     cd server
     ```
   - Suba o banco de dados:
     ```bash
     docker-compose up -d
     ```
   - Crie o arquivo `.env` na raiz do projeto:
     ```env
     PORT=3333
     DATABASE_URL=postgresql://docker:docker@localhost:5432/agents
     ```
   - Instale as dependências:
     ```bash
     npm install
     ```
   - Execute as migrações:
     ```bash
     npx drizzle-kit migrate
     ```
   - (Opcional) Popule o banco:
     ```bash
     npm run db:seed
     ```
   - Inicie o servidor:
     - Desenvolvimento:
       ```bash
       npm run dev
       ```
     - Produção:
       ```bash
       npm start
       ```

4. **Frontend (`web/`)**:
   - Acesse a pasta do frontend:
     ```bash
     cd web
     ```
   - Instale as dependências:
     ```bash
     npm install
     ```
   - Inicie o servidor de desenvolvimento:
     ```bash
     npm run dev
     ```
   - Acesse a aplicação em: `http://localhost:5173`

> **Importante:** O backend deve estar rodando em `http://localhost:3333` antes de iniciar o frontend.

## 🌐 Deploy

- **Backend:** Pode ser hospedado em qualquer serviço que suporte Node.js e Docker (ex: Heroku, Railway, Render, AWS, GCP, Azure). Basta configurar as variáveis de ambiente e o banco PostgreSQL com extensão pgvector.
- **Frontend:** Pode ser publicado em plataformas como Vercel, Netlify ou hospedado em um servidor próprio. Certifique-se de configurar a URL da API do backend conforme o ambiente de produção.

Desenvolvido durante o NLW da Rocketseat.
