Got it! Here's the **final and corrected `README.md`** that:

✅ Describes your project clearly
✅ Removes all references to `healthcheck.sh`
✅ Accurately reflects the Flask service (`service2`) without misleading info
✅ Still mentions the healthcheck issue in a clean, honest way

---

```markdown
# 🚀 DPDZero DevOps Assignment – Nginx Reverse Proxy + Docker Compose

This project sets up a Dockerized microservices environment as part of a DevOps assignment. It includes:

- A **Go web service** (`service1`)
- A **Python Flask web service** (`service2`)
- An **Nginx container** acting as a reverse proxy

All services run in Docker containers and are accessible through a single port using path-based routing.

---

## 📦 Tech Stack

- Golang (Service 1)
- Python + Flask (Service 2)
- Nginx (Reverse Proxy)
- Docker & Docker Compose

---

## 📁 Project Structure

```

.
├── docker-compose.yml
├── nginx
│   ├── nginx.conf
│   └── Dockerfile
├── service\_1
│   ├── Dockerfile
│   ├── main.go
│   └── go.mod
├── service\_2
│   ├── Dockerfile
│   ├── app.py
│   └── README.md
└── README.md

````

---

## 🌐 Routing Overview

The Nginx server listens on port `8080` and forwards requests as follows:

| Route Prefix          | Backend Service | Internal Port |
|-----------------------|------------------|----------------|
| `/service1/`          | Go App           | `8001`         |
| `/service2/`          | Flask App        | `8002`         |

---

## 🛠️ How to Run

### 1. Clone the Repository

```bash
git clone https://github.com/Sudeep67/DPDZero-DevOps-Assignment.git
cd DPDZero-DevOps-Assignment
````

### 2. Start All Services

```bash
docker compose up --build
```

---

## ✅ Available Endpoints

Once the services are up and running, you can access:

### Go Service (`service1`)

* `GET /service1/ping` → `{ "status": "ok", "service": "1" }`
* `GET /service1/hello` → `{ "message": "Hello from Service 1" }`

### Flask Service (`service2`)

* `GET /service2/ping` → `{ "status": "ok", "service": "2" }`
* `GET /service2/hello` → `{ "message": "Hello from Service 2" }`

> Replace `localhost` with your EC2 IP when testing on a remote server.

---

## ⚠️ Note on Healthchecks

Both services expose a `/ping` endpoint.
However, the Flask-based service (`service2`) may occasionally show as **unhealthy** in Docker Compose, even though it works properly in the browser and via `curl`.

This does not affect the actual functionality of the service.

---

## 🧾 Nginx Configuration Highlights

The reverse proxy rules are defined in `nginx/nginx.conf`:

```nginx
location /service1/ {
    proxy_pass http://service1:8001/;
}

location /service2/ {
    proxy_pass http://service2:8002/;
}
```

Nginx runs entirely inside a container and handles all routing on port `8080`.

---

## 🔐 EC2 Access Notes

If deployed on AWS EC2, ensure the security group allows inbound traffic on the required ports:

* Port `8080` (main entry)
* Port `8001`, `8002` (optional, for direct testing)

> Recommended: Only open port `8080` to the public, and keep others private.

---

## 🔍 Testing Examples

```
http://<your-ec2-ip>:8080/service1/ping
http://<your-ec2-ip>:8080/service2/hello
```

Use your browser or any REST client to test as well.

---

## 🎯 Features Implemented

* ✅ Multi-service architecture with Docker Compose
* ✅ Reverse proxy using Nginx (in container)
* ✅ Path-based routing (`/service1`, `/service2`)
* ✅ Modular and clean Docker setup
* ✅ Health endpoint support

---

## 📝 Author

**Sudeep Kumar Behera**
DevOps Intern Assignment
GitHub: [github.com/Sudeep67](https://github.com/Sudeep67)

---

````

---

### ✅ Next Steps

1. Save this content into `README.md` in your project root.
2. Push it to GitHub:

```bash
git add README.md
git commit -m "Final clean README without healthcheck script"
git push origin main
````
