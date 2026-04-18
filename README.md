\# Jenkins CI/CD Pipeline Demo



\## Tools Used

\- Jenkins

\- Docker

\- Node.js

\- GitHub



\## Pipeline Stages

1\. Checkout - Get code from GitHub

2\. Install Dependencies - npm install

3\. Test - Run tests

4\. Build Docker Image - Build app image

5\. Deploy - Run the container



\## How to Run

docker run -d -p 8080:8080 jenkins/jenkins:lt

