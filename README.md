
# 🚀 DevOps CI/CD Project: Dockerized Flask App with Jenkins
---
## 🛠️ Tools & Technologies Used

- **Linux (RHEL)**
- **Flask (Python Framework)**
- **Docker & DockerHub**
- **Git & GitHub**
- **Jenkins (CI/CD Tool)**
---

## 📁 Project Structure
```
devops_project/
├── app.py            # Flask App
├── test_app.py       # Basic test case
├── Dockerfile        # For containerizing app
```
---
## 📌 Project Goals

- Containerize a basic Flask application using Docker.
- Push image to DockerHub.
- Set up CI/CD pipeline with Jenkins.
- Run Jenkins build on GitHub push.

---

## ✅ Step-by-Step Setup

### 1. Create Files (Windows CMD)
```bash
mkdir devops_project
cd devops_project
ni app.py
ni test_app.py
ni Dockerfile
```

### 2. Add Code to Files

#### app.py
```python
from flask import Flask
app = Flask(__name__)

@app.route('/')
def home():
    return "Hello from Dockerized Flask App!"

if __name__ == "__main__":
    app.run(host='0.0.0.0', port=5000)
```

#### test_app.py
```python
def test_home():
    assert True
```

#### Dockerfile
```Dockerfile
FROM python:3.9-slim
WORKDIR /app
COPY . .
RUN pip install flask
CMD ["python", "app.py"]
```

### 3. GitHub Setup
- Create a new repo named `devops_project`.
- Push code:

```bash
git init
git add .
git commit -m "Initial CI/CD project"
git branch -M main
git remote add origin https://github.com/<your-username>/devops_project.git
git push -u origin main
```

### 4. Clone in RHEL
```bash
cd ~
git clone https://github.com/<your-username>/devops_project.git
cd devops_project
```

### 5. Build Docker Image
```bash
docker build -t <dockerhub-username>/devopsapp:v1 .
```

### 6. Docker Login (RHEL)
```bash
docker login
```
> It will prompt for OTP and DockerHub verification.

### 7. Push Docker Image
```bash
docker push <dockerhub-username>/devopsapp:v1
```

### 8. Access Jenkins on RHEL
```bash
ip a
# or
ifconfig
```
- Go to browser → `http://<your-ip>:8080`

### 9. Create Jenkins Job
- Click **New Item → Freestyle Project**
- Source Code Management → Git → Add your repo link
- Branch: `*/main`
- Save and **Build Now**

> Check console output for build success ✅


