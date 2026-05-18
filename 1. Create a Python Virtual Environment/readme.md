### install venv first:

For Ubuntu/Debian:
```
sudo apt update
sudo apt install python3-venv -y
```
### Go to the target directory
```
cd /root/code/
```
## Create the virtual environment
```
python3 -m venv ml-env
```
### To activate the virtual environment:
```
source /root/code/ml-env/bin/activate
```
### Install the required packages:
```
pip install numpy pandas scikit-learn matplotlib
```
### Generate the requirements.txt file:
```
pip freeze > /root/code/requirements.txt
```
### Verify the file:
```
cat /root/code/requirements.txt
```
