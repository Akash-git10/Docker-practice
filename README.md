# Docker-practice
1️⃣ Five DevOps Concepts
1. Continuous Integration (CI)

Developers push code frequently to a shared repository. Automated builds and tests run on every change to detect issues early.

2. Continuous Deployment (CD)

Code changes that pass testing are automatically deployed to production without manual steps.

3. Infrastructure as Code (IaC)

Managing infrastructure (servers, networks, containers) using code. Tools include Terraform, Ansible, Docker, Kubernetes.

4. Version Control (Git)

Tracking changes in code, enabling rollback, branching, merging, and collaboration.

5. Containerization (Docker)

Packaging applications and dependencies into isolated environments so they run the same everywhere.

2️⃣ How I Completed This Assignment (Step-by-Step Explanation with Commands)

Below are the exact steps and terminal commands used to complete the assignment.

🔹 Step 1 — Create Dockerfile

I created a Dockerfile that installs basic tools like curl, git, vim, tree, and prints Linux command outputs.

FROM ubuntu:latest

RUN apt-get update -y && apt-get install -y \
    curl \
    vim \
    git \
    tree \
    procps \
    && apt-get clean

WORKDIR /app

RUN echo "echo '--- Basic Linux Commands ---'" > run.sh && \
    echo "echo 'Current Directory:' && pwd" >> run.sh && \
    echo "echo 'List Files:' && ls -la" >> run.sh && \
    echo "echo 'System Date:' && date" >> run.sh && \
    echo "echo 'Disk Usage:' && df -h" >> run.sh && \
    echo "echo 'Memory Usage:' && free -m" >> run.sh && \
    chmod +x run.sh

CMD ["bash", "run.sh"]

🔹 Step 2 — Build Docker Image
docker build -t linux-commands-demo:local .

🔹 Step 3 — Run Docker Container
docker run --rm linux-commands-demo:local

🔹 Step 4 — Login to DockerHub
docker login

🔹 Step 5 — Tag Image for DockerHub
docker tag linux-commands-demo:local sakshi210502/linux-commands-demo:latest

🔹 Step 6 — Push Image to DockerHub
docker push sakshi210502/linux-commands-demo:latest

🔹 Step 7 — Initialize Git Repository
git init
git add .
git commit -m "Added Dockerfile and README"

🔹 Step 8 — Connect GitHub Repository
git remote add origin https://github.com/sakshimangulkar/Docker_practice.git
git branch -M main

🔹 Step 9 — Fix Merge Issue and Push
git pull origin main --allow-unrelated-histories
git push -u origin main

3️⃣ How This Project Helps Me Learn DevOps, Linux, Git, and Docker
✔ Linux

I practiced commands like ls, df, free, pwd, and learned how to automate them in shell scripts.

✔ Git

I learned how to initialize repos, commit files, fix push errors, merge changes, and connect to GitHub.

✔ Docker

I learned:

how to write Dockerfiles

how to build images

how to run containers

how to push images to DockerHub

how to tag Docker images

✔ DevOps

This assignment teaches the core DevOps pipeline:
Code → Build → Run → Push → Deploy

It shows how automation and containerization make the process more efficient.
