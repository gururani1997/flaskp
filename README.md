# FlaskP – Full‑Stack Web Application

A full-stack web application featuring:

- **Frontend**: Built with **Node.js** and **Express.js**  
- **Backend**: Built with **Python** and **Flask**  
- **Infrastructure**: Both services are containerized using **Docker** and orchestrated with **Docker Compose**

---

##  Architecture Overview

[ Client Browser ]
↓
[ Express (Node.js) – Frontend ]
↕ HTTP (e.g., REST calls)
[ Flask (Python) – Backend ]

yaml
Copy
Edit

The frontend serves user interfaces and communicates with the Flask backend via API calls to fetch or process data.

---

##  Getting Started

### Prerequisites

- Docker  
- Docker Compose  
- (Optional) Git  

### Run the Application

1. Clone the repository:
    ```bash
    git clone https://github.com/gururani1997/flaskp.git
    cd flaskp
    ```

2. Start both services using Docker Compose:
    ```bash
    docker-compose up --build
    ```

3. Open your browser and navigate to the frontend (e.g. `http://localhost:3000`), which will communicate with the Flask backend seamlessly.

---

##  Project Structure (Suggested)

flaskp/
├── frontend/ # Express (Node.js) frontend
│ ├── Dockerfile
│ ├── package.json
│ └── ...
├── backend/ # Flask (Python) backend
│ ├── Dockerfile
│ ├── requirements.txt
│ └── ...
├── docker-compose.yaml
└── README.md

yaml
Copy
Edit

---

##  Docker & `docker-compose.yml`

`docker-compose.yaml` binds both services in a single network (`app-network`) and handles port mappings:

```yaml
services:
  frontend:
    build: ./frontend
    ports:
      - "3000:3000"
    networks:
      - app-network

  backend:
    build: ./backend
    ports:
      - "5000:5000"
    networks:
      - app-network

networks:
  app-network:
    driver: bridge
This way, Express can communicate with Flask using http://backend:5000.

Development Workflow
Modify frontend code → rebuild container → frontend updates reflect immediately

Modify backend code → rebuild backend container → frontend gets updated responses accordingly

Additional Enhancements
Add a .env file to manage configuration (e.g. ports, API endpoints, secrets)

Set up hot-reload tools like nodemon for Express or flask --reload for Python

Include CI/CD pipelines for automated testing and deployment

Enhance with authentication, database integration, or UI frameworks

Contributing
Feel free to submit PRs, file issues, or suggest improvements!
Make sure to:

Fork the repo

Create a feature branch

Open a pull request once your changes are ready

License
Include your preferred license here (e.g., MIT, Apache 2.0, GPL).

Contact
Created by Pankaj Gururani – welcome to connect, suggest, or collaborate!