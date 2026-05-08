🚀 DevSecOps CI/CD Pipeline with Amazon EKS Deployment

End-to-End DevSecOps Automation using GitHub Actions, Docker, SonarQube, Trivy, Gitleaks, Kubernetes, and Amazon EKS.


📌 Project Overview
This project demonstrates a complete DevSecOps CI/CD Pipeline where a Java application is automatically:


Built using Maven


Scanned for vulnerabilities and secrets


Tested and validated


Analyzed using SonarQube


Containerized using Docker


Pushed to Docker Hub


Deployed to Amazon EKS


Exposed through Kubernetes Service


The pipeline is executed using a GitHub Actions Self-Hosted Runner configured on an AWS EC2 instance.

🏗️ Architecture
Developer   │   ▼GitHub Repository   │   ▼GitHub Actions CI/CD(Self-Hosted Runner on EC2)   │ ┌─┼─────────────────────┐ │ │                     │ ▼ ▼                     ▼Build  Security Scan   Testing │ ▼SonarQube Analysis │ ▼Docker Build & Push │ ▼Amazon EKS Deployment │ ▼Kubernetes Service │ ▼Application Access via Endpoint

⚙️ Tech Stack
CategoryTools UsedSource ControlGitHubCI/CDGitHub ActionsRunnerSelf-Hosted EC2 RunnerBuild ToolMavenProgramming LanguageJavaContainerizationDockerRegistryDocker HubOrchestrationKubernetesCloud PlatformAWSKubernetes PlatformAmazon EKSSecurity ToolsTrivy, GitleaksCode QualitySonarQubeInfrastructure as CodeTerraform

📂 Repository Structure
.├── .github/│   └── workflows/│       └── cicd.yml│├── kubernetes/│   ├── deployment.yml│   └── service.yml│├── Dockerfile├── pom.xml├── src/│├── terraform/│   ├── main.tf│   ├── variables.tf│   └── output.tf│└── README.md

🚀 CI/CD Pipeline Stages
The GitHub Actions workflow performs the following stages:
1. Checkout Source Code2. Setup JDK 173. Maven Compile4. Trivy File System Scan5. Gitleaks Secret Scan6. Maven Unit Testing7. Build Package8. SonarQube Analysis9. Docker Image Build10. Docker Image Push11. Deploy to Amazon EKS

🔹 Step 1: GitHub Repository Setup
Created a GitHub repository and added:


Java Maven application


GitHub Actions workflow


Kubernetes manifests


Dockerfile


Terraform configuration files



🔹 Step 2: Self-Hosted Runner Setup
Launched an AWS EC2 instance and configured it as a GitHub Actions self-hosted runner.
Installed Required Tools
sudo apt update# Install Javasudo apt install openjdk-17-jdk -y# Install Mavensudo apt install maven -y# Install Dockersudo apt install docker.io -y
Configure GitHub Runner
./config.sh --url <repo-url> --token <token>./run.sh

🔐 Security Scanning
✅ Trivy Scan
Scanned project filesystem for vulnerabilities.
trivy fs .
Detects:


Vulnerabilities


Misconfigurations


Secrets



✅ Gitleaks Scan
Scanned repository for hardcoded secrets.
gitleaks detect
Detects:


API keys


Passwords


Tokens


Sensitive credentials



🧪 Testing Stage
Executed Maven unit tests.
mvn test

📦 Build & Package
Packaged the Java application into a JAR artifact.
mvn package
Generated artifact:
target/*.jar

📊 SonarQube Analysis
Integrated SonarQube for:


Static Code Analysis


Vulnerability Detection


Code Smell Analysis


Quality Gate Validation


SonarQube Command
mvn sonar:sonar

🐳 Docker Build & Push
Build Docker Image
docker build -t username/bankapp:latest .
Push Docker Image
docker push username/bankapp:latest

☸️ Amazon EKS Setup
EKS Provisioning
Used Terraform files (main.tf, variables.tf, output.tf) to provision the EKS cluster.
Clone Terraform EKS Repository on EC2
git clone <terraform-eks-repo-url>cd terraform-eks
Terraform Commands
terraform initterraform planterraform apply

🔹 Configure Kubernetes Access
Configured kubeconfig to connect with EKS cluster.
aws eks update-kubeconfig --region ap-south-1 --name eks-cluster
Verify cluster connection:
kubectl get nodes

🚀 Kubernetes Deployment
Deploy Application
kubectl apply -f deployment.ymlkubectl apply -f service.yml

🌐 Application Exposure
Used Kubernetes Service (LoadBalancer / NodePort) to expose the application externally.
Verify Service
kubectl get svc
Access Application
http://<EXTERNAL-IP>:<PORT>
✅ Successfully accessed application login page.

📸 GitHub Actions Workflow Result
Successful Pipeline Stages


✅ compile


✅ security-check


✅ test


✅ build_project_and_sonar_scan


✅ build_docker_image_and_push


✅ deploy_to_kubernetes



🔥 Key Achievements


✅ Complete End-to-End DevSecOps Pipeline


✅ CI/CD Automation using GitHub Actions


✅ Security Integration using Trivy & Gitleaks


✅ SonarQube Quality Gate Integration


✅ Docker Containerization


✅ Kubernetes Deployment on Amazon EKS


✅ Self-Hosted Runner Implementation


✅ Infrastructure Automation using Terraform



⚠️ Challenges Faced & Solutions
IssueSolutionYAML syntax issuesFixed indentation problemsTrivy installation issuesUpdated GPG key methodapt-key deprecatedUsed keyrings approachEKS node group delaysVerified IAM roles and subnetsRunner conflictsRestarted self-hosted runnerDocker permission deniedAdded user to docker group

📈 Future Enhancements


🔹 Helm Charts


🔹 ArgoCD GitOps


🔹 Prometheus Monitoring


🔹 Grafana Dashboards


🔹 AWS ALB Ingress Controller


🔹 Slack Notifications


🔹 Blue-Green Deployment


🔹 Multi-Environment CI/CD



📚 Learning Outcomes
This project provided hands-on experience with:


DevSecOps Practices


CI/CD Automation


Kubernetes & EKS


Docker & Containerization


Security Scanning


Terraform Infrastructure as Code


GitHub Actions Workflow Automation


AWS Cloud Services



👨‍💻 Author
Ajay Goud Gunnala
Aspiring DevSecOps Engineer | AWS | Kubernetes | Terraform | Docker | GitHub Actions | CI/CD | DevSecOps Automation

⭐ Conclusion
This project demonstrates a real-world DevSecOps implementation integrating:


Continuous Integration


Security Automation


Continuous Delivery


Kubernetes Orchestration


Cloud Infrastructure Automation


using modern cloud-native tools and AWS services.

📜 License
This project is licensed under the MIT License.
