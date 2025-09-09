# Virtualization_and-_Containerization_Assignment_1

 
**Course:** Cloud Computing for Data Analysis 
**Student:** V Sai Tarun (ID: 801421332)  

---

## 📌 Project Overview  
This project demonstrates how to set up and run a **multi-container application** using Docker and Docker Compose.  

- **Service 1 (PostgreSQL):** Initializes a `trips` table with seed data (`city`, `minutes`, `fare`).  
- **Service 2 (Python app):** Connects to the database, queries records, computes simple statistics, and outputs results.  

The Python app produces a **JSON summary** of:  
- Total number of trips  
- Average fare per city  
- Top N longest trips by duration  

Results are written to `out/summary.json` and also printed to the console.  

---

## ⚙️ Prerequisites  
- [Docker Desktop](https://www.docker.com/products/docker-desktop/)  
- Docker Compose (comes with Docker Desktop)  
- Git & GitHub Desktop (to clone and manage repo)  
- An IDE (VS Code, PyCharm, or similar)  

---

## 🛠️ How to Run  

### 1. Build and start the stack
```bash
docker compose up --build
```
<img width="940" height="753" alt="image" src="https://github.com/user-attachments/assets/438ae9ea-9cf6-4571-b38e-1ac575def3bc" />


### 2. Alternative: One-command run with Makefile
```bash
make all
```

### 3. Stop and remove containers + volumes

```bash
docker compose down -v
```

## 📂 Project Structure
<code>.
├── app/
│ ├── Dockerfile
│ └── main.py
├── db/
│ ├── Dockerfile
│ └── init.sql
├── out/
│ └── summary.json
├── compose.yml
├── Makefile
└── README.md</code>


---

## 🖥️ Example Output  

### Stdout (printed in terminal)
```json
{
  "total_trips": 6,
  "avg_fare_by_city": [
    {"city": "Charlotte", "avg_fare": 16.25},
    {"city": "New York", "avg_fare": 19.0},
    {"city": "San Francisco", "avg_fare": 20.25}
  ],
  "top_by_minutes": [
    {"city": "San Francisco", "minutes": 28, "fare": 29.3},
    {"city": "New York", "minutes": 26, "fare": 27.1},
    {"city": "Charlotte", "minutes": 21, "fare": 20.0},
    {"city": "San Francisco", "minutes": 11, "fare": 11.2},
    {"city": "Charlotte", "minutes": 12, "fare": 12.5}
  ]
}
```

<img width="1279" height="766" alt="image" src="https://github.com/user-attachments/assets/7edd7769-fee0-4478-9016-34998f057d9a" />


### Reflection
This assignment taught me how to:
Run a PostgreSQL service in a container with seeded data.
Use Docker Compose to orchestrate multiple containers.
Connect a Python app to a database using environment variables.
Automate workflows with a Makefile for reproducibility.
In the future, I would improve the project by adding larger datasets and extending the app to compute additional statistics.


