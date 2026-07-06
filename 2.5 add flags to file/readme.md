## start the ml flow tracking server 
`` mlflow server --host 0.0.0.0 --port 5000 ``
## Set the tracking URI
in linux 
``` export MLFLOW_TRACKING_URI=http://localhost:5000 ```?
in cmd 
``` set MLFLOW_TRACKING_URI=http://localhost:5000 ```
## run default parameter values from your MLproject
``` mlflow run . ```
## run with custom parameters
``` mlflow run . -P n_estimators=200 -P max_depth=10 -P test_size=0.3 -P random_seed=123 ```
## Verify the run
``` http://localhost:5000 ```
