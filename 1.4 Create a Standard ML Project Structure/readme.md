cd /root/code

# Create project if missing
mkdir -p fraud-detection

cd fraud-detection

# Create required directory structure
mkdir -p data/raw
mkdir -p data/processed
mkdir -p models
mkdir -p notebooks
mkdir -p src/data
mkdir -p src/features
mkdir -p src/models
mkdir -p src/utils
mkdir -p tests
mkdir -p configs

# Create __init__.py files
touch src/data/__init__.py
touch src/features/__init__.py
touch src/models/__init__.py
touch src/utils/__init__.py

# Create requirements.txt
cat > requirements.txt <<EOF
scikit-learn
pandas
numpy
mlflow
EOF

# Create README.md
cat > README.md <<EOF
# fraud-detection
EOF
