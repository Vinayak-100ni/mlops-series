# MLflow Model Registry Lab Guide

## Objective

Register two existing MLflow runs as versions of a new registered model
and assign aliases.

## Steps

### 1. Open the MLflow UI

Open:

`http://<server-ip>:5000`

(or `http://localhost:5000` if running locally)

### 2. Open the Experiment

-   Go to **Experiments**.
-   Open **fraud-detection**.
-   Verify the two runs:
    -   **Baseline**
        -   `n_estimators=100`
        -   `max_depth=5`
        -   `f1_score=0.80`
    -   **Improved**
        -   `n_estimators=200`
        -   `max_depth=10`
        -   `f1_score=0.89`

### 3. Register the Baseline Run (Version 1)

1.  Open the baseline run.
2.  Open the **model** artifact.
3.  Click **Register Model**.
4.  Select **Create New Model**.
5.  Enter the model name:

```{=html}
<!-- -->
```
    fraud-detector

6.  Click **Register**.

This creates **Version 1**.

### 4. Register the Improved Run (Version 2)

1.  Open the improved run.
2.  Open the **model** artifact.
3.  Click **Register Model**.
4.  Select **Existing Registered Model**.
5.  Choose:

```{=html}
<!-- -->
```
    fraud-detector

6.  Click **Register**.

This creates **Version 2**.

### 5. Add a Model Description

Open **Model Registry → fraud-detector**.

Add a description containing the word **fraud**, for example:

> Fraud detection model for xFusionCorp transactions.

Save the description.

### 6. Assign Aliases

**Version 1**

Add the alias:

    challenger

**Version 2**

Add the alias:

    champion

## Final Verification

Open **Model Registry → fraud-detector** and verify:

  Version   Run                          Alias
  --------- ---------------------------- ------------
  1         Baseline (`f1_score=0.80`)   challenger
  2         Improved (`f1_score=0.89`)   champion

Also verify that: - The registered model is named **fraud-detector**. -
The model description contains the word **fraud**. - Both versions are
visible in the registry.
