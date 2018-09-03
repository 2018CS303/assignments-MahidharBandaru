Assignment
Blue Ocean
From the administrator account, move to Manage Jenkins -> Manage Plugins.
Install Blue Ocean (BlueOcean Aggregator) plugin from the list of Available plugins.
Install Blue Ocean along with the required dependencies.
Restart Jenkins
sudo service jenkins restart
Upon restart, enable the Blue Ocean option from the GUI.
Private repository as FreeStyle Project
Setup a new freestyle project - New Item -> Freestyle project.
Set Source Code Management to Git.
Provide the private repository link in Repository URL.
To permit Jenkins to access the Private Github repository, please update the credentials. Add -> Credentials -> Jenkins and update.
Set this as the Credentials.
Update the branch (if required) - Default : */master.
Git SCM Poll
Map the Jenkins URL to a public IP address.
Map a Public IP to your Jenkins URL using ngrok.
Download and setup ngrok from here.
Run ./ngrock http 8080 (map your Jenkins port (8080) to a public IP. The public URL http://<foo>.ngrok.io should be used as the Webhook.
Setup
Navigate Settings -> Webhooks -> Add webhook in the repository.
Update the Payload URL to the Public IP http://<foo>.ngrok.io/github-webhook/.
Set Content type as application/json.
Update Which events would you like to trigger this webhook? as per requirement.
Ensure that the Active option is selected.
Post-build Actions
Select the project and navigate Configure -> Post-build Actions
In Add post-build action choose Archive the artifacts.
Mention the files to archive ( * to archive all the files).
In the Advanced... tab, enable Archive only if build is successful and Use default excludes.
