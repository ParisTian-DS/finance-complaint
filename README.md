# Finance-Complaint 

### Problem Statement
Complaints can give us insights into problems people are experiencing in the marketplace and help us to undestand the reason and do necessary modification in exisiting financial product if required.

### Solution Proposed
By understanding existing complaints registered against financial products we can create an ML model that can help us to identify newly registered complaints whether they are problematic or not and accordingly company can take quick action to resolve the issue, and satisfy the customer's need.

The problem is to identify registered complaint will be disputed by customer or not.

### Tech Stack Used
Python
PySpark
PySpark ML
Airflow as Scheduler
MongoDB

### Infrastructure Required
GCP Compute Engine
S3 Bucket
Artifact Registry

### Dashboarding
Grafana
Prometheus
Node Exporter
Promtail
Loki

### How to run?
#### WorkFLow setup

Create .env file
```
AWS_ACCESS_KEY_ID=
AWS_SECRET_ACCESS_KEY=
MONGO_DB_URL=
TRAINING=1
PREDICTION=1
```
1- Trigger 0- Bypass

#### Build docker image
```
docker build -t tc:lts .
Lauch docker image
```
```
docker run -it -v $(pwd)/finance_artifact:/app/finance_artifact  --env-file=$(pwd)/.env fc:lts
```

### Steps to run project in local system

#### Build docker image
```
docker build -t fc:lts .
```

#### Set envment variable
```
export AWS_ACCESS_KEY_ID=
export AWS_SECRET_ACCESS_KEY=
export MONGO_DB_URL=
export AWS_DEFAULT_REGION="ap-south-1"
export IMAGE_NAME=fc:lts
```

#### To start your application
```
docker-compose up
```

#### To stop your application
```
docker-compose down
```

### In your local system to setup airflow

#### AIRFLOW SETUP

How to setup airflow
Set airflow directory
```
export AIRFLOW_HOME="~/airflow"
```

To install airflow
```
pip install apache-airflow
```

To configure databse
```
airflow db init
```

To create login user for airflow
```
airflow users create  -e paristian.pro@gmail.com -f Paris -l Tian -p admin -r Admin  -u admin
```

To start scheduler
```
airflow scheduler
```

To launch airflow server
```
airflow webserver -p <port_number>
```

Update in airflow.cfg

enable_xcom_pickling = True