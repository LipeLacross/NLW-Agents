## 🌐 [Versão em Português do README](README.md)

# NLW Agents - Rocketseat

Live Q&A platform powered by artificial intelligence, developed during Rocketseat's NLW#20 event. The project is divided into two main directories: **server** (backend) and **web** (frontend), enabling real-time question management, AI-generated answers, and live streaming integration.

## 🔨 Project Features

- 📝 Real-time question management
- 🤖 AI-generated answers (Google Gemini)
- 📡 Live streaming integration
- 🏷️ Creation and listing of themed rooms
- 🎤 Audio transcription and analysis via AI

### 📸 Project Visual Example

<div align="center"> <img src="https://github.com/user-attachments/assets/98f39725-fc46-4eed-88ef-9557d6491345" alt="Screenshot da aplicação NLW Agents" width="80%" style="margin: 16px 0; border-radius: 10px;"> </div>

## ✔️ Techniques and Technologies Used

- **Frontend**
  - React 19.1 ⚛️
  - TypeScript 5.8
  - Vite 7.0 ⚡
  - TailwindCSS 4.1 🎨
  - React Router Dom 7.6
  - TanStack React Query 5.8
  - Radix UI and Shadcn/ui
  - Lucide React (icons)

- **Backend**
  - Node.js (experimental strip types) 🟩
  - Fastify 🚀
  - TypeScript
  - PostgreSQL + pgvector 🗄️
  - Drizzle ORM
  - Zod (validation)
  - Docker 🐳
  - Biome (lint/format)
  - Google Gemini API (AI)

## 📁 Project Structure

- **LICENSE**: Project license.
- **README.md**: Main documentation (Portuguese).
- **README_EN.md**: Documentation in English.

- **server/** (Backend)
  - biome.jsonc: Lint/formatter configuration.
  - client.http: HTTP request collection for testing.
  - docker/
    - setup.sql: Script to create the vector extension in the database.
  - docker-compose.yml: Container orchestration.
  - drizzle.config.ts: Drizzle ORM configuration.
  - package.json: Backend dependencies and scripts.
  - src/
    - db/
      - connection.ts: PostgreSQL connection.
      - migrations/: Database migration scripts.
      - schema/: Table definitions (rooms, questions, audio_chunks).
      - seed.ts: Example data seeding.
    - http/: API routes and controllers.
    - server.ts: Fastify server initialization.
    - services/
      - gemini.ts: Google Gemini API integration.

- **web/** (Frontend)
  - biome.jsonc: Lint/formatter configuration.
  - components.json: Component configuration.
  - index.html: Main HTML file.
  - package.json: Frontend dependencies and scripts.
  - src/
    - app.tsx: Root component and routes.
    - components/: Reusable and UI components (including ui/ subfolder with buttons, cards, forms, etc).
    - http/: API hooks and types.
    - lib/: Utilities (e.g., dayjs, utils).
    - main.tsx: React application entry point.
    - pages/: Main app pages (create room, room, audio recording).
  - tsconfig*.json: TypeScript configuration.
  - vite.config.ts: Vite configuration.

## 🛠️ How to Run the Project

To run the project locally, follow the steps below:

1. **Make sure Node.js is installed:**
   - [Node.js](https://nodejs.org/) is required to run the project. Check if it's installed with:
     ```bash
     node -v
     ```
   - If not installed, download and install the recommended version.

2. **Clone the Repository:**
   - Copy the repository URL and run:
     ```bash
     git clone 
     ```

3. **Backend (`server/`):**
   - Enter the backend folder:
     ```bash
     cd server
     ```
   - Start the database:
     ```bash
     docker-compose up -d
     ```
   - Create the `.env` file at the project root:
     ```env
     PORT=3333
     DATABASE_URL=postgresql://docker:docker@localhost:5432/agents
     ```
   - Install dependencies:
     ```bash
     npm install
     ```
   - Run migrations:
     ```bash
     npx drizzle-kit migrate
     ```
   - (Optional) Seed the database:
     ```bash
     npm run db:seed
     ```
   - Start the server:
     - Development:
       ```bash
       npm run dev
       ```
     - Production:
       ```bash
       npm start
       ```

4. **Frontend (`web/`):**
   - Enter the frontend folder:
     ```bash
     cd web
     ```
   - Install dependencies:
     ```bash
     npm install
     ```
   - Start the development server:
     ```bash
     npm run dev
     ```
   - Access the application at: `http://localhost:5173`

> **Important:** The backend must be running at `http://localhost:3333` before starting the frontend.

## 🌐 Deploy

- **Backend:** Can be hosted on any service supporting Node.js and Docker (e.g., Heroku, Railway, Render, AWS, GCP, Azure). Just configure the environment variables and PostgreSQL database with the pgvector extension.
- **Frontend:** Can be deployed to platforms like Vercel, Netlify, or self-hosted. Make sure to configure the backend API URL according to your production environment.

Developed during Rocketseat's NLW.