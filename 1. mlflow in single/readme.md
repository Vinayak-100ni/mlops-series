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
log table 
```
import kagglehub
import mlflow
import pandas as pd

    demo_df = pd.DataFrame({"name" : ["Dan","sam"]})
    mlflow.log_table(demo_df, "file_name.json")


    # Download latest version
    path = kagglehub.dataset_download("yasserh/titanic-dataset")

    print("Path to dataset files:", path)


    read_table = pd.read_csv("/root/.cache/kagglehub/datasets/yasserh/titanic-dataset/versions/1/Titanic-Dataset.csv")
    mlflow.log_table( read_table, "test.json")
```

### Log and register the model 
```
import mlflow
import pandas as pd
from sklearn import datasets
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LogisticRegression
from sklearn.metrics import accuracy_score, precision_score, recall_score, f1_score

# Load the Iris dataset
X, y = datasets.load_iris(return_X_y=True)

# Split the data into training and test sets
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Define the model hyperparameters
params = {
    "solver": "lbfgs",
    "max_iter": 1000,
    "random_state": 8888,
}


mlflow.set_tracking_uri("http://54.227.39.114:5000")
mlflow.set_experiment("sk_learn")

with mlflow.start_run(run_name="model"):  # Start an MLflow run
    lr = LogisticRegression(**params)     # Create model with hyperparameters
    lr.fit(X_train, y_train)              # Train the model


    mlflow.sklearn.log_model(             # Save trained model to MLflow
        sk_model=lr,                         # The trained sklearn model
        name="fraud_detection_model",       # Model artifact name
        input_example=X_train[:5],          # Example input
        registered_model_name="FraudModel"  # Register in Model Registry
    )
    mlflow.log_params(params)             # Log hyperparameters to MLflow<F2>
```
## use the registered model using 
```
export MLFLOW_TRACKING_URI=http://100.26.43.38:5000 
mlflow models serve   -m "models:/FraudModel/1"   -p 4560   --host 0.0.0.0   --no-conda

```
