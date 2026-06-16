# Novus-code

Novus-code is a powerful, cloud-native Online Integrated Development Environment (IDE). It empowers developers to write code, manage files, and run a full-featured terminal directly from their browser, with isolated containerized environments managed dynamically via Kubernetes.

## 🚀 Features

- **Advanced Code Editor**: Powered by Monaco Editor (the core of VS Code) for a rich editing experience, featuring syntax highlighting, code completion, and more.
- **In-Browser Terminal**: Fully functional, interactive terminal powered by `xterm.js` that connects directly to your isolated backend container.
- **Dynamic Kubernetes Environments**: Automatically spawns isolated pods/environments for each user session using the Kubernetes API.
- **Real-Time Synchronization**: Uses WebSockets (`socket.io`) for real-time file updates, saving, and terminal interaction.
- **Cloud File Storage**: Integrates with AWS S3 for persistent cloud storage of user projects and files.
- **Modern Tech Stack**: React + Vite frontend, Express backend, PostgreSQL database with Drizzle ORM.

## 🏗 Architecture

The project is structured into three main microservices:

1. **`front-end/`**: 
   - A React-based Single Page Application (SPA) built with Vite and TailwindCSS.
   - Handles the UI, including the Monaco code editor instance, the xterm.js terminal instance, and file explorer.

2. **`code/` (Main Backend API)**:
   - An Express & Node.js backend.
   - Manages user authentication, database interactions (via PostgreSQL & Drizzle ORM), and file management (AWS S3).
   - Handles real-time WebSockets communication with the frontend for terminal streams and file changes.

3. **`k8s/` (Kubernetes Controller Service)**:
   - A dedicated Node.js service using `@kubernetes/client-node`.
   - Responsible for dynamically provisioning, managing, and proxying requests to isolated user-specific Kubernetes pods.

## 🛠 Tech Stack

- **Frontend**: React 19, Vite, TailwindCSS, Monaco Editor, xterm.js, React Router, Zod
- **Backend**: Node.js, Express, Socket.io, TypeScript
- **Database / ORM**: PostgreSQL, Drizzle ORM
- **Infrastructure / Cloud**: Kubernetes, AWS SDK (S3), Docker

## 🚦 Getting Started

### Prerequisites
- Node.js (v18+)
- PostgreSQL (running locally or remotely)
- Kubernetes Cluster (Minikube/Docker Desktop for local development)
- AWS Account S3 Credentials

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/novus547/novus-code.git
   cd novus-code
   ```

2. **Frontend Setup**
   ```bash
   cd front-end
   npm install
   npm run dev
   ```

3. **Backend API Setup**
   ```bash
   cd code
   npm install
   # Set up your .env variables (DB URL, S3, etc.)
   npm run dev
   ```

4. **Kubernetes Service Setup**
   ```bash
   cd k8s
   npm install
   # Ensure your local kubeconfig is properly configured
   npm run dev
   ```

## 📜 License

This project is licensed under the ISC License.
