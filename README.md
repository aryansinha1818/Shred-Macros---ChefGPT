🥗 Shred-Macros
===============

**AI-Powered Recipe & Nutrition Assistant (Dockerized Full-Stack App)**

Shred-Macros is a **production-style, Dockerized full-stack application** that demonstrates **real-world system design**, **cross-service communication**, and **LLM integration**.\
The system is built using **React, Node.js, FastAPI, LangChain, MongoDB**, and runs as **multiple isolated services using Docker Compose**.

This project focuses on **how modern applications are actually deployed**, not just built.

* * * * *

🚀 Key Capabilities
-------------------

-   **AI Recipe Generation**

    -   Veg / non-veg selection

    -   Ingredients + cooking time

    -   Context-aware follow-ups (chat memory)

-   **LLM Intelligence**

    -   Ingredient substitution handling

    -   Optional macro & micro nutrition output

    -   Structured JSON responses from AI

-   **Chat-like Experience**

    -   Conversation history preserved

    -   Incremental refinement of recipes

-   **Recipe Sharing**

    -   Persist full recipes (title, ingredients, steps, macros, image)

    -   Stored in MongoDB

* * * * *

🧠 System Architecture (Important)
----------------------------------

`Client (React)
   |
   | HTTP (REST)
   v Backend API (Node.js / Express)
   |
   | HTTP (internal service call)
   v AI Service (FastAPI + LangChain + LLM)
   |
   v MongoDB`

Each component runs as an **independent Docker container**, enabling:

-   clear service boundaries

-   scalable architecture

-   production-like deployment

* * * * *

🐳 Dockerized Services
----------------------

The entire application is orchestrated using **Docker Compose**.

### Services:

-   **frontend**

    -   React app (Vite)

    -   Exposed on `5173`

-   **backend**

    -   Node.js + Express

    -   Acts as API gateway

    -   Handles auth, recipe CRUD, DB access

    -   Exposed on `5001`

-   **ai-service**

    -   FastAPI + LangChain

    -   Handles all LLM logic

    -   Exposed on `8000`

-   **mongo**

    -   MongoDB database

    -   Internal Docker network only

-   **mongo-express** (dev only)

    -   Database UI

    -   Exposed on `8081`

* * * * *

🛠️ Tech Stack
--------------

### Frontend

-   React

-   Chat-style UI

-   Recipe form & share flow

### Backend

-   Node.js

-   Express

-   JWT authentication

-   MongoDB integration

-   Acts as **single entry point** for frontend

### AI Layer

-   Python FastAPI

-   LangChain

-   LLM-driven recipe generation

-   Conversation memory

-   Structured output enforcement

### Database

-   MongoDB

-   Local (Docker) for development

-   MongoDB Atlas for production

* * * * *

⚙️ Environment Configuration
----------------------------

### Backend (`server/.env`)

`PORT=5001
MONGO_URI=mongodb://mongo:27017/shredmacro   # Docker
JWT_SECRET=your_secret
AI_SERVICE_URL=http://ai-service:8000`

### AI Service (`ai-service/.env`)

`OPENAI_API_KEY=your_key`

* * * * *

▶️ Running the Project (Docker)
-------------------------------

### 1️⃣ Clone the repo

`git clone https://github.com/aryansinha1818/Shred-Macros.git
cd Shred-Macros`

### 2️⃣ Start all services

`docker-compose up --build`

### 3️⃣ Access the app

-   Frontend → `http://localhost:5173`

-   Backend → `http://localhost:5001`

-   AI Service → `http://localhost:8000`

-   Mongo Express → `http://localhost:8081`

* * * * *

☁️ Production Deployment
------------------------

-   **Frontend** → Vercel

-   **Backend** → Render

-   **AI Service** → Render

-   **Database** → MongoDB Atlas

Only the **connection string changes** --- code remains identical.

* * * * *

🎯 Engineering Highlights
-------------------------

-   Clean separation of concerns

-   Docker networking instead of `localhost`

-   Backend-mediated DB access (frontend never touches DB)

-   AI isolated as its own microservice

-   Production-ready architecture mindset

* * * * *

👨‍💻 Author
------------

**Aryan Sinha**\
Backend & GenAI Developer\

📧 Email: <aryan.sinha1818@gmail.com>\
🔗 LinkedIn: <https://www.linkedin.com/in/aryan-sinha-877698212/>
