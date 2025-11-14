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

## Environment Variables / Configuration

### AWS Credentials
Stored securely in GitHub Secrets:
- `AWS_ACCESS_KEY_ID`: AWS access key for programmatic access.
- `AWS_SECRET_ACCESS_KEY`: AWS secret key for programmatic access.

### Flask Application Configuration
Can be set via `.env` file (for local development) or ECS task definition (for production):
- `FLASK_ENV`: Use `development` for local testing or `production` for deployed environments.
- `FLASK_APP`: Main entry point of the Flask app (e.g., `app.py`).

**Security Note:**  
Do not commit sensitive information directly to the repository. Use GitHub Secrets, AWS Secrets Manager, or environment variables for secure management.


## Setup & Usage

### 1. Clone the repository
git clone https://github.com/your-username/your-repo.git
cd your-repo

### 2. Build the Docker image locally
docker build -t final-test-api .

### 3. Run the container
docker run -p 5000:5000 final-test-api

### 4. Test locally
Open your browser and navigate to:
http://localhost:5000

### 5. Trigger the CI/CD pipeline
- Commit and push changes to the `main` branch.  
- The GitHub Actions workflow (`.github/workflows/build.yml`) will automatically:
  - Build the Docker image
  - Authenticate with AWS ECR
  - Push the image to your AWS ECR repository


## Deployment Notes

- Replace the ECR repository URI with your own, for example:
381491999801.dkr.ecr.us-east-1.amazonaws.com
- Ensure your IAM user has the correct permissions for:
- `ecr:GetAuthorizationToken`
- `ecr:BatchCheckLayerAvailability`
- `ecr:PutImage`
- `ecr:InitiateLayerUpload`

## Future Improvements
- The current workflow automates image-building and pushing to ECR.  
Future enhancements may include ECS or Kubernetes deployment steps.

- Add ECS or EKS deployment automation.  
- Integrate unit testing before image build.  
- Include monitoring and logging setup with AWS CloudWatch.

## License

This project is distributed under the MIT License. Feel free to use and modify as needed.

