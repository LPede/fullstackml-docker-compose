# Fullstackml-docker-compose
# Introduction
Your Docker Compose sets up a development environment for machine learning (ML) and data analysis using various components. The configuration includes:

A JupyterLab service, based on the jupyter/datascience-notebook image, which provides an interactive environment for developing and running Python notebooks. You can access JupyterLab through your browser at "localhost:8888".

A MinIO service, based on the minio/minio image, which acts as a data lake and object storage. MinIO runs on ports "9000" and "9001" and can be accessed at "localhost:9000". You can manage MinIO objects through a web interface at "localhost:9001".

A MySQL database service, based on the mysql/mysql-server image, which serves as the backend for MLflow. The database runs on port "3306" and can be accessed at "localhost:3306".

An MLflow service, based on the custom "mlflow_server" image built in the "mlflow" directory of your project. MLflow is a framework for managing the lifecycle of machine learning models. The MLflow service is accessible at "localhost:5050" and uses MinIO as the S3 endpoint for artifact storage and MySQL database as the storage backend. It is configured to use the specified AWS credentials in the environment variables.

The Docker Compose configuration provides an integrated environment for developing machine learning models using JupyterLab and MLflow, with MinIO as a data lake and MySQL as the backend for data storage. You can use JupyterLab to create and share notebooks, run MLflow experiments, and store the results and associated artifacts in MinIO.

# How to run

**Clone (download) this repository**
[![Copy Code](https://img.shields.io/badge/Copy-Code-blue)](javascript:void(0))

`git clone https://github.com/LPede/fullstackml-docker-compose.git`
**cd into the fullstackml-docker-compose directory**
[![Copy Code](https://img.shields.io/badge/Copy-Code-blue)](javascript:void(0))
cd fullstackml-docker-compose

**Build and run the containers with docker-compose**
[![Copy Code](https://img.shields.io/badge/Copy-Code-blue)](javascript:void(0))
docker-compose up -d --build

**Access JupyterLab UI with [http://localhost:8888](http://localhost:8888)**

**Access MLflow UI with [http://localhost:5050](http://localhost:5050)**

**Access MinIO UI with [http://localhost:9000](http://localhost:9000)**

## Notes

- Docker Compose allows you to access environment variables from the compose file `docker-compose.yml`. All variables (usernames, passwords, db names, access keys) used in the compose file are declared in the hidden file `.env`.

- Often the TCP/5000 port used by the MLflow UI is also (ab)used by other applications. For this reason, I mapped this port to TCP/5050 on the host machine. Anyway, the port mapping can be easily changed by editing the compose file.

