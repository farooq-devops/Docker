# Dockerized 3-Tier Application Architecture

This repository demonstrates a **production-style Dockerized 3-tier application architecture** consisting of a frontend service, backend API, and MySQL database.  
The goal of this project is to showcase **containerization, service isolation, and inter-service communication** using Docker, following real-world DevOps practices.

---

## Architecture

The application is deployed on a single Docker host and follows a **classic 3-tier design pattern**:

- **Frontend (fe-app)**  
  Handles incoming client requests and forwards them to the backend service.

- **Backend (be-app / datastore:v1)**  
  Implements application logic and exposes APIs consumed by the frontend.  
  Communicates with the database over an internal Docker network.

- **Database (mydb)**  
  MySQL database responsible for persistent data storage, accessible only to the backend service on port `3306`.

All components run as **independent containers** and communicate over a **Docker bridge network**, ensuring isolation and controlled connectivity.

---

## Request Flow

1. Client traffic is received by the frontend container.
2. The frontend forwards requests to the backend service.
3. The backend processes the request and connects to the MySQL database on port `3306`.
4. The response flows back from the database → backend → frontend → client.

---

## Technology Stack

- Docker
- Docker Networking
- Linux
- MySQL

---

## Container Overview

| Component | Container Name | Responsibility |
|---------|---------------|----------------|
| Frontend | `fe-app` | Client-facing service |
| Backend | `be-app` (`datastore:v1`) | Business logic & API layer |
| Database | `mydb` | Persistent data storage |

---

## Key Design Considerations

- Clear separation of concerns using a 3-tier architecture
- Service-to-service communication via Docker networking
- Database access restricted to backend service only
- Versioned backend image (`datastore:v1`)
- Stateless application containers with externalized data storage

---

## Deployment Overview

The application is deployed using standard Docker commands:

1. A dedicated Docker network is created for service communication.
2. The database container is started first.
3. The backend container is deployed and connected to the database.
4. The frontend container is exposed to accept client traffic.

This approach reflects how containerized applications are commonly deployed in real-world environments before moving to orchestration platforms.

---

## Learning Outcomes

- Designing and running multi-container applications with Docker
- Implementing a clean 3-tier architecture using containers
- Managing inter-container communication and isolation
- Applying container best practices used in DevOps workflows
- Understanding how Docker-based setups translate to Kubernetes deployments

---

## Future Enhancements

- Introduce Docker Compose for declarative multi-container orchestration
- Add persistent storage using Docker volumes
- Implement container health checks
- Integrate CI/CD pipeline for automated image builds
- Migrate the architecture to Kubernetes (EKS)

---

## Reference

This project is documented and explained in detail in my LinkedIn post:  
https://www.linkedin.com/posts/farooqmohammed9_docker-aws-devops-activity-7408458913819365376-mHIh
