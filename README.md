# Flask CI/CD Pipeline with Docker and AWS ECR

This repository contains a Flask application integrated with a CI/CD pipeline using GitHub Actions. The pipeline builds a Docker image, pushes it to a private AWS ECR (Elastic Container Registry), and can be extended for deployment.

---

## Features

- **Flask Application**: Simple Python web application using Flask.
- **Dockerized**: Application runs inside a Docker container.
- **CI/CD Pipeline**: Fully automated using GitHub Actions (`build.yml`).
- **AWS ECR Integration**: Docker images are pushed to a private Amazon ECR repository.
- **GitHub Actions**:
  - Checks out code.
  - Configures AWS credentials.
  - Builds Docker image.
  - Tags and pushes image to AWS ECR.

---

## Project Structure

├── app.py # Flask application entry point
├── requirements.txt # Python dependencies
├── Dockerfile # Docker image build instructions
├── .github/
│ └── workflows/
│ └── build.yml # CI/CD pipeline for GitHub Actions
└── README.md




