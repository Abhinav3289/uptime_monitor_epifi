

# AI Collaboration Log

## 1. AI Tech Stack

The following AI tools were used during development:

- ChatGPT (OpenAI GPT-5.5) – Architecture planning, backend development, frontend guidance, debugging, Docker configuration, and documentation.
- GitHub Copilot – Code completion for repetitive React and Express boilerplate.

---

## 2. The Prompts that Shipped It

### Backend

> Build a production-ready Express.js backend in TypeScript for an uptime monitoring application. Create REST APIs to add, update, delete, and list monitors. Use MongoDB with Mongoose, Axios for health checks, and Node-Cron to poll websites every 30 seconds. Organize the project using controllers, routes, services, and models.

### Frontend

> Build a responsive React + TypeScript + Vite dashboard using Tailwind CSS. Create pages to add, edit, delete, and view monitors. Display uptime status, response time, last checked timestamp, and recent health history. Use Axios for API communication and React Router for navigation.

### Docker

> Generate Dockerfiles for the frontend and backend along with a docker-compose.yml that starts the complete application with MongoDB using a single `docker compose up` command.

---

## 3. Course Corrections

One issue encountered was that the AI initially suggested storing the monitoring loop inside individual API requests, which would have started duplicate polling jobs for every request. This architecture would not scale and could lead to multiple health checks running for the same monitor.

The solution was to refactor the design by implementing a single centralized Node-Cron scheduler that periodically retrieves all monitors from the database and performs health checks independently of incoming API requests.

Another issue occurred while configuring Docker networking, where the AI initially used `localhost` for the MongoDB connection. This prevented communication between containers. The configuration was corrected by using the Docker Compose service name (`mongodb`) as the database host.

---

## 4. Verification

All AI-generated code was reviewed, modified where necessary, tested locally, and integrated manually. AI was used as a development assistant, while all implementation decisions and final validation were performed by the project author.