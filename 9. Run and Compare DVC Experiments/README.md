### Check experiments:
``` dvc exp show ```

### We can run the experements using command
```
dvc exp run -S n_estimators=50
dvc exp run -S n_estimators=200
dvc exp run -S n_estimators=500
```

### Apply it to the workspace:
```
dvc exp show 
dvc exp apply exp-ghijkl(experiment name)
```
