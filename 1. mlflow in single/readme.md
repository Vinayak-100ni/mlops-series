1. Install uv if not already installed
```
curl -LsSf https://astral.sh/uv/install.sh | sh
```
reload shell
```
source ~/.local/bin/env 
```

Create the environment:
```
uv venv mlflow-env --python 3.12
source mlflow-env/bin/activate
```
Install MLflow
```
uv pip install mlflow
```
Start MLflow
```
mlflow server \
  --host 0.0.0.0 \
  --port 5000 \
  --backend-store-uri sqlite:////home/ubuntu/mlflow-backend/mlflow.db \
  --artifacts-destination /home/ubuntu/mlflow-artifacts \
  --cors-allowed-origins '*' \
  --allowed-hosts '*'
```
load metrics and params
```
import mlflow

mlflow.set_tracking_uri("http://204.236.221.134:5000")
mlflow.set_experiment("vinayak")

with mlflow.start_run(run_name="logging"):
    mlflow.log_param("learning_rate", 0.03)

    parameters = {
     "learning" : 0.04,
     "epoch1" : 200
    }
    mlflow.log_params(parameters)

    # metrics

    metrics = {
       "accuracy" : 0.99,
       "accuracy1" : 0.88
    }
    mlflow.log_metrics(metrics)

    artifact_path = "/home/ubuntu/lossgraph.webp"
    mlflow.log_artifact(artifact_path)
```


