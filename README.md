# Nginx Docker Reverse Proxy Architecture

A lightweight, production-ready microservices routing setup using **Nginx** as an Edge Reverse Proxy to route traffic across isolated **Docker** backend application containers.

---

## 📐 Architecture Overview

```mermaid
graph TD
    Client[Client / Browser] -->|Port 80| Proxy[Nginx Reverse Proxy Container]
    
    subgraph Isolated Docker Network: proxy_net
        Proxy -->|/app1/| App1[App 1 Container: app1_container]
        Proxy -->|/app2/| App2[App 2 Container: app2_container]
    end
Routing Logic:
http://localhost/app1/ ──► Routes requests to app1_container

http://localhost/app2/ ──► Routes requests to app2_container

🚀 Key Features
Path-Based Routing: Seamlessly routes requests based on URL endpoints without exposing backend container ports to the host.

Isolated Networking: Containers communicate securely over a custom Docker bridge network (proxy_net).

Container Orchestration: Built and managed using Docker Compose for single-command deployment.

Lightweight Footprint: Built on nginx:alpine base images to minimize resource utilization and deployment time.

🛠️ Tech Stack
Proxy Server: Nginx

Containerization: Docker, Docker Compose

Base OS Image: Alpine Linux

Environment: Kali Linux / Any System running Docker Engine
📁 Project Structure
nginx-docker-reverse-proxy/
├── app1/
│   ├── Dockerfile
│   └── index.html
├── app2/
│   ├── Dockerfile
│   └── index.html
├── nginx/
│   └── default.conf
├── docker-compose.yml
└── README.md
⚡ Getting Started
Prerequisites
Ensure you have Docker and Docker Compose installed on your system.

Installation & Deployment
Clone the repository:

Bash
git clone [https://github.com/YOUR_USERNAME/nginx-docker-reverse-proxy.git](https://github.com/YOUR_USERNAME/nginx-docker-reverse-proxy.git)
cd nginx-docker-reverse-proxy
Build and spin up the containers:

Bash
docker compose up -d --build
Verify running containers:

Bash
docker ps
🧪 Testing the Proxy
You can test the path-based routing using curl or opening the endpoints in your browser:

Test App 1:

Bash
curl http://localhost/app1/
Output: Welcome to Application 1

Test App 2:

Bash
curl http://localhost/app2/
Output: Welcome to Application 2
