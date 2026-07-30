### install venv first:
For Ubuntu/Debian:
```
sudo apt update
sudo apt install python3-venv -y
```
### Create the virtual environment
```
python3 -m venv ml-env
```
### To activate the virtual environment:
```
source /root/code/ml-env/bin/activate
```
```
mlflow server \
  --host 0.0.0.0 \
  --port 5000 \
  --backend-store-uri sqlite:////root/code/mlflow-backend/mlflow.db \
  --artifacts-destination /root/code/mlflow-artifacts \
  --cors-allowed-origins '*' \
  --allowed-hosts '*'
```
