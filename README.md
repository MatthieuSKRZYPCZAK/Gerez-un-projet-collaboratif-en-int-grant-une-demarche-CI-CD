![BobApp](readme-assets/bobapp.png)

# 📘 BobApp

Bienvenue / Welcome! 👋

Veuillez choisir votre langue / Please choose your language:

🇫🇷 [Lire en français](#bobapp---automatisation-cicd)  
🇬🇧 [Read in English](#bobapp---cicd-automation)

## Rapports de Qualité (SonarCloud)

### Back

[![Quality Gate Status](https://sonarcloud.io/api/project_badges/measure?project=matthieuskrzypczak_bobapp-back&metric=alert_status)](https://sonarcloud.io/summary/new_code?id=matthieuskrzypczak_bobapp-back)
[![Coverage](https://sonarcloud.io/api/project_badges/measure?project=matthieuskrzypczak_bobapp-back&metric=coverage)](https://sonarcloud.io/summary/new_code?id=matthieuskrzypczak_bobapp-back)

### Front

[![Quality Gate Status](https://sonarcloud.io/api/project_badges/measure?project=matthieuskrzypczak_bobapp-front&metric=alert_status)](https://sonarcloud.io/summary/new_code?id=matthieuskrzypczak_bobapp-front)
[![Coverage](https://sonarcloud.io/api/project_badges/measure?project=matthieuskrzypczak_bobapp-front&metric=coverage)](https://sonarcloud.io/summary/new_code?id=matthieuskrzypczak_bobapp-front)

Vous pouvez consulter le rapport détaillé de la qualité de code sur [SonarCloud](https://sonarcloud.io/organizations/matthieuskrzypczak/projects).

---

# BobApp - Automatisation CI/CD

Bienvenue sur **BobApp**, une application full-stack dévelopéée avec Spring Boot (Java) pour le back-end et Angular pour le front-end. L'objectif du projet est double, faire rire les utilisateurs avec une blague du jour et surtout professionnaliser le cycle de développement avec une **démarche CI/CD**.

## Stack Technique
- **Back** : Java 11, Spring Boot, Maven
- **Front** : Angular, Node.js
- **CI/CD** : GitHub Actions, SonarCloud, Docker Hub

## 🚀 Mise en route

### Cloner le projet

```bash
      git clone https://github.com/MatthieuSKRZYPCZAK/Gerez-un-projet-collaboratif-en-int-grant-une-demarche-CI-CD.git
```

### Back-end

```bash
    cd back
    mvn clean install
    mvn spring-boot:run
```

### Front-end

```bash
    cd front
    npm install
    npm run start
```

## 🐳 Docker

### Option 1 : Lancer manuellement

Pour permettre la communication entre le front et le back, les deux conteneurs doivent se trouver sur un **réseau Docker commun**. 

#### Créer un réseau Docker

```bash
    docker network create bobapp-net 
```

#### Back-end

1. Construire l'image
```bash
    docker build -t bobapp-back .
```

2. Lancer le back
```bash
    docker run --network bobapp-net --name back -d bobapp-back
```

#### Front-end

1. Construire l'image
```bash
    docker build -t bobapp-front .
```
2. Lancer le front sur le même réseau

```bash
    docker run --network bobapp-net -p 4200:80 --name bobapp-front -d bobapp-front
```

### Option 2 : Utiliser Docker compose (recommandé)

Assurez-vous d'être à la **racine du projet**, là où se trouve le fichier `docker-compose.yml`. 

Lancer les conteneurs avec :

```bash
    docker-compose up -d
```

Pour arrêter :
```bash
    docker-compose down
```

## 🔄 Pipeline CI/CD

Un workflow GitHub Actions est une série d'étapes automatisées visant à fiabiliser les livraisons de code. Dans ce projet, plusieurs workflows collaborent pour garantir une chaîne complète d'intégration et de déploiement :

- **CI (Intégration Continue)** : à chaque push ou pull request, les tests sont lancés automatiquement et la qualité du code est analysée.
- **CD (Déploiement Continu)** : si la CI est validée, les images Docker sont générées et déployées sur Docker Hub.

Voici les rôles des workflows utilisés :
- **`main.yml`** : point d'entrée principal qui orchestre le déclenchement des autres workflows
- **`back-tests.yml`** : lance les tests sur le backend
- **`front-tests.yml`** : lance les tests sur le frontend
- **`back-sonarqube.yml`** : analyse la qualité du code backend
- **`front-sonarqube.yml`** : analyse la qualité du code frontend
- **`docker.yml`** : construit et pousse les images Docker (back et front) sur Docker Hub

Le projet s'appuie sur ces workflows pour garantir que seul un code validé, testé et analysé peut être déployé.

> Chaque étape est conditionnelle : sans test OK, pas de build. Sans build, pas de déploiement.


---

## Quality Reports (SonarCloud)

### Back

[![Quality Gate Status](https://sonarcloud.io/api/project_badges/measure?project=matthieuskrzypczak_bobapp-back&metric=alert_status)](https://sonarcloud.io/summary/new_code?id=matthieuskrzypczak_bobapp-back)
[![Coverage](https://sonarcloud.io/api/project_badges/measure?project=matthieuskrzypczak_bobapp-back&metric=coverage)](https://sonarcloud.io/summary/new_code?id=matthieuskrzypczak_bobapp-back)

### Front

[![Quality Gate Status](https://sonarcloud.io/api/project_badges/measure?project=matthieuskrzypczak_bobapp-front&metric=alert_status)](https://sonarcloud.io/summary/new_code?id=matthieuskrzypczak_bobapp-front)
[![Coverage](https://sonarcloud.io/api/project_badges/measure?project=matthieuskrzypczak_bobapp-front&metric=coverage)](https://sonarcloud.io/summary/new_code?id=matthieuskrzypczak_bobapp-front)

You can access detailed code quality reports on [SonarCloud](https://sonarcloud.io/organizations/matthieuskrzypczak/projects).

---

# BobApp - CI/CD Automation

Welcome to **BobApp**, a full-stack application built with Spring Boot (Java) for the backend and Angular for the frontend. The project has two main goals: to make users laugh with a joke of the day, and to professionalize the development cycle through a **CI/CD approach**.

## Stack Technique
- **Back** : Java 11, Spring Boot, Maven
- **Front** : Angular, Node.js
- **CI/CD** : GitHub Actions, SonarCloud, Docker Hub

## 🚀 Getting Started

### Clone the repository

```bash
      git clone https://github.com/MatthieuSKRZYPCZAK/Gerez-un-projet-collaboratif-en-int-grant-une-demarche-CI-CD.git
```

### Back-end

```bash
    cd back
    mvn clean install
    mvn spring-boot:run
```

### Front-end

```bash
    cd front
    npm install
    npm run start
```

## 🐳 Docker

### Option 1 : Manual Launch

To allow communication between the frontend and backend, both containers must be on a **shared Docker network**.

#### Create a Docker network

```bash
    docker network create bobapp-net 
```

#### Back-end

1. Build the image
```bash
    docker build -t bobapp-back .
```

2. Run the backend container
```bash
    docker run --network bobapp-net --name back -d bobapp-back
```

#### Front-end

1. Build the image
```bash
    docker build -t bobapp-front .
```
2. Run the frontend container on the same network

```bash
    docker run --network bobapp-net -p 4200:80 --name bobapp-front -d bobapp-front
```

### Option 2 : Use Docker Compose (recommended)

Make sure you're at the **root of the project**, where the `docker-compose.yml` file is located.

Launch the containers with :

```bash
    docker-compose up -d
```

To stop them :
```bash
    docker-compose down
```

## 🔄 CI/CD Pipeline

A GitHub Actions workflow is a series of automated steps designed to ensure reliable code delivery. In this project, several workflows work together to provide a complete integration and deployment chain :

- **CI (Continuous Integration)** : on every push or pull request, tests are run and code quality is analyzed.
- **CD (Continuous Deployment)** : if CI passes, Docker images are built and pushed to Docker Hub.

Workflows used in this project :
- **`main.yml`** : main entry point, orchestrates other workflows
- **`back-tests.yml`** : runs backend tests
- **`front-tests.yml`** : runs frontend tests
- **`back-sonarqube.yml`** : analyzes backend code quality
- **`front-sonarqube.yml`** : analyzes frontend code quality
- **`docker.yml`** : builds and pushes Docker images (backend and frontend) to Docker Hub

This project relies on these workflows to ensure that only validated, tested, and reviewed code gets deployed.

> Each step is conditional: no successful tests = no build. No build = no deployment.
