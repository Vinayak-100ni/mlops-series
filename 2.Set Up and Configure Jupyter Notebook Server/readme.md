## Step 1: Activate the Virtual Environment
``` source /root/code/ml-env/bin/activate ```
Step 2: Inspect the Existing Configuration

Open the JupyterLab configuration file:

cat /root/code/jupyter_lab_config.py

Look for incorrect settings related to:

Port
IP binding
Notebook directory
Step 3: Edit the Configuration File

Open the file using nano:

nano /root/code/jupyter_lab_config.py

Ensure the following settings exist and are correct:

c.ServerApp.port = 8888
c.ServerApp.ip = '0.0.0.0'
c.ServerApp.root_dir = '/root/notebooks/'

Remove or correct any conflicting values such as:

c.ServerApp.ip = '127.0.0.1'
c.ServerApp.port = 9999
c.ServerApp.root_dir = '/some/other/path'

Save the file:

Press CTRL + O
Press Enter
Press CTRL + X
Step 4: Create the Notebook Directory

Create the required notebook root directory if it does not exist:

mkdir -p /root/notebooks/

Verify it exists:

ls -ld /root/notebooks/
Step 5: Start JupyterLab

Run JupyterLab using the corrected configuration:

jupyter lab --config=/root/code/jupyter_lab_config.py --allow-root --no-browser &
Step 6: Verify JupyterLab is Running

Check the running process:

ps -ef | grep jupyter

Check that port 8888 is listening:

ss -tulnp | grep 8888

Expected output should show:

0.0.0.0:8888
Step 7: Access the Notebook Interface

After confirming the server is running:

Click the Jupyter UI button at the top of the lab.
The notebook interface should now open successfully.
Final Expected Configuration

Your /root/code/jupyter_lab_config.py should effectively contain:

c.ServerApp.port = 8888
c.ServerApp.ip = '0.0.0.0'
c.ServerApp.root_dir = '/root/notebooks/'
