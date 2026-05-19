# Python Dependency Lockfile Setup Using uv

The xFusionCorp Industries ML team uses `uv` and lockfiles to keep Python dependencies reproducible across machines.

This guide explains how to correct the existing `requirements.in` file and generate a pinned `requirements.txt` lockfile.

---

# Step 1: Navigate to the Project Directory

```bash
cd /root/code/fraud-detection
```

---

# Step 2: Review Existing requirements.in

Check the current contents:

```bash
cat requirements.in
```

---

# Step 3: Replace requirements.in with Correct Dependencies

The specification must contain exactly these four top-level packages:

- scikit-learn
- mlflow
- pandas
- numpy

Each package must include a valid version constraint.

Replace the file contents using:

```bash
cat > requirements.in <<EOF
scikit-learn>=1.4.0
mlflow>=2.12.0
pandas>=2.2.0
numpy>=1.26.0
EOF
```

---

# Step 4: Compile the Lockfile Using uv

Generate the fully pinned lockfile:

```bash
uv pip compile requirements.in -o requirements.txt
```

This command will:

- Resolve compatible versions from PyPI
- Pin exact versions using `==`
- Include all transitive dependencies

---

# Step 5: Verify Generated requirements.txt

Check the generated file:

```bash
cat requirements.txt
```

Expected output format:

```text
mlflow==2.x.x
numpy==1.x.x
pandas==2.x.x
scikit-learn==1.x.x
...
```

The file will also include additional transitive dependencies resolved by `uv`.

---

# Final Result

You will now have:

- Corrected `requirements.in`
- Fully pinned `requirements.txt`
- Reproducible Python dependency environment
