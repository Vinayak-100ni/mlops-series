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


