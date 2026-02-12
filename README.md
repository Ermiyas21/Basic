# Basic

#### Download Workshop Folder from AWS Jupyter 
Jupyter cannot download folders directly. Zip the folder and download the zip. 

Step 1: **Create zip of the full workshop 
**
import shutil
shutil.make_archive(
    "amazon-bedrock-agentcore-workshop",
    "zip",
    "/home/sagemaker-user/amazon-bedrock-agentcore-workshop"
)

step 2:  **Download to your PC ** 

from IPython.display import FileLink
FileLink('amazon-bedrock-agentcore-workshop.zip')

Click the link to download the zip file to your local machine. 
 
