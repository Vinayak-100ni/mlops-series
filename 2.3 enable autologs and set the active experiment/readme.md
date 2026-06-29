### enable autologging for the sklearn flavour so that the subsequent model.fit(...) call records parameters, metrics, and
### the trained model on the active experiment automatically.
```
mlflow.sklearn.autolog()    
```
###  set the active experiment to "autolog-demo" so the autologged run lands in that experiment rather than the Default one.
```
mlflow.set_experiment("autolog-demo")
```
