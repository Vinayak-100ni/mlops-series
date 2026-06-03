` cd /root/code/fraud-detection `

### Stop Git from tracking the dataset but keep the file on disk
` git rm --cached data/raw/transactions.csv `

###  Track the dataset with DVC
` dvc add data/raw/transactions.csv `

###  Stage the DVC pointer file and generated .gitignore
` git add data/raw/transactions.csv.dvc   `

` git add data/raw/.gitignore `

###  Record the change in Git
` git commit -m "Track transactions dataset with DVC" `
