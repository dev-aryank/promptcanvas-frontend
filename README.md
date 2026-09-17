# PromptCanvas Frontend

Frontend client for [PromptCanvas](https://github.com/dev-aryank/promptcanvas), an AI-powered application builder.

**Main backend repository:**  
https://github.com/dev-aryank/promptcanvas

This repository contains the user-facing interface for PromptCanvas, including authentication, project management, AI chat, generated file exploration, and live application previews.

The initial frontend implementation was generated with the help of an LLM and is being adapted and integrated with the PromptCanvas backend.

---

## What is PromptCanvas?

PromptCanvas is an AI-powered application builder where users can describe an application in natural language and continue modifying it through conversation.

The basic idea is:

```text
Describe an application
        ↓
AI generates the code
        ↓
Application runs
        ↓
Live preview is shown
        ↓
Ask for changes through chat
        ↓
AI modifies the existing project
        ↓
Preview updates
```

The main engineering focus of the project is the Spring Boot backend, which handles AI generation, project context, tool calling, file storage, chat history, authentication, billing, and the execution layer.

This repository provides the frontend needed to interact with that system.

---

## Tech Stack

- React
- TypeScript
- Vite
- Tailwind CSS
- React Router
- TanStack Query
- React Hook Form
- Zod
- Lucide React

Additional libraries may be added as the frontend evolves.

---

## Project Structure

A simplified version of the project structure looks like this:

```text
promptcanvas-frontend/
│
├── public/
│
├── src/
│   ├── components/
│   ├── pages/
│   ├── hooks/
│   ├── services/
│   ├── lib/
│   ├── App.tsx
│   └── main.tsx
│
├── .gitignore
├── package.json
├── package-lock.json
├── tsconfig.json
├── vite.config.ts
└── README.md
```

---

## Running the Frontend Locally

### Prerequisites

Before starting, make sure you have the following installed:

- [Node.js](https://nodejs.org/)
- npm
- Git

You can verify your installations using:

```bash
node --version
npm --version
git --version
```

---

### Step 1 — Clone the Repository

Open a terminal and clone the frontend repository:

```bash
git clone https://github.com/dev-aryank/promptcanvas-frontend.git
```

---

### Step 2 — Move Into the Project Folder

```bash
cd promptcanvas-frontend
```

---

### Step 3 — Install Dependencies

Run:

```bash
npm install
```

or:

```bash
npm i
```

This installs all dependencies listed in `package.json`.

A local `node_modules` directory will be created automatically.

---

### Step 4 — Configure Environment Variables

Create a `.env` file in the root of the project.

Example:

```env
VITE_API_BASE_URL=http://localhost:8080
```

This tells the frontend where the PromptCanvas backend is running.

Do not commit the `.env` file to GitHub.

You can use a `.env.example` file to document the required environment variables:

```env
VITE_API_BASE_URL=http://localhost:8080
```

---

### Step 5 — Start the PromptCanvas Backend

The frontend depends on the PromptCanvas Spring Boot backend for authentication, projects, AI generation, project files, billing, and other functionality.

Clone the backend repository separately:

```bash
git clone https://github.com/dev-aryank/promptcanvas.git
```

Then follow the setup instructions available in the backend repository.

By default, the backend should be available at:

```text
http://localhost:8080
```

---

### Step 6 — Start the Frontend

From inside the `promptcanvas-frontend` folder, run:

```bash
npm run dev
```

Vite should start the development server.

You should see output similar to:

```text
VITE ready

Local: http://localhost:5173/
```

Open:

```text
http://localhost:5173
```

in your browser.

The PromptCanvas frontend should now be running locally.

---

## Quick Start

If you already have Node.js installed and the PromptCanvas backend is running, the setup is simply:

```bash
git clone https://github.com/dev-aryank/promptcanvas-frontend.git

cd promptcanvas-frontend

npm install

npm run dev
```

Then open:

```text
http://localhost:5173
```

---

## Environment Variables

Example `.env` file:

```env
VITE_API_BASE_URL=http://localhost:8080
```

The required environment variables may change as more services are integrated.

Do not commit secrets or private configuration values.

---

## Backend Requirement

This frontend is designed to work with the main PromptCanvas backend.

Backend repository:

https://github.com/dev-aryank/promptcanvas

The backend handles the core platform functionality, including:

- JWT authentication
- Project management
- Project permissions
- Stripe subscriptions
- Project file storage using MinIO
- AI generation using Spring AI
- OpenRouter + GPT-5.3 Codex
- Tool calling
- Project-aware context
- Server-Sent Events
- Chat history
- Generated file persistence
- Kubernetes-based execution and live preview infrastructure

---

## Development Flow

The intended application flow is:

```text
Frontend
   ↓
User sends prompt
   ↓
Spring Boot backend
   ↓
AI understands the current project
   ↓
AI reads required files
   ↓
AI generates updated files
   ↓
Response is streamed through SSE
   ↓
Frontend displays progress
   ↓
Generated files are updated
   ↓
Application reruns
   ↓
Live preview updates
```