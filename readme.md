# Project 2 - Deploy a High-Availability Web App using CloudFormation 

### The files included are:

* /Images : Diagram-Screenshot the result of deploy.
* /UdagramP2-V2 : Udagram App Code (Zip FIle)
* create.sh : Cloudformation create stack script. 
* update.sh : Cloudformation update stack script.
* delete.sh : Cloudformation delete stack script.
* P2_UDG_net-3.yml & P2_UDG-servers.yml  : Udagram Project's CloudFormation script.
* P2_UDG-net.json & P2_UDG-serv.json, : Udagram Project's CloudFormation script parameters.

### About:

* In this project Udagram: deployed web servers for a highly available web app using CloudFormation.
* Script that creates and deploys the infrastructure and application for an Udagram app from the ground up.
* The script begin deploying the networking components followed by servers, security roles and software.


### Instruction of Deploy , Update and delete the Project:

**To Deploy:**

* Type the following for Network and server (please create Network elements first): 

* Network:   ./create.sh udagram-Network P2_UDG_net-3.yml P2_UDG-net.json
* Servers:   ./create.sh udagram-server P2_UDG-servers.yml P2_UDG-serv.json

**To Update:**

* Type the following to update Network or server: 

* Network:   ./update.sh udagram-Network P2_UDG_net-3.yml P2_UDG-net.json
* Servers:   ./update.sh udagram-server P2_UDG-servers.yml P2_UDG-serv.json

**To delete:**
* Type the following Network or server (Please delete servers then delete Network: 
* Servers:   ./delete.sh  udagram-server
* Network:   ./delete.sh  udagram-Network 
Note: If you create a jumbox server for ssh please terminate the jumbox before deleteing the server and network

**References:**
* Udacity example templates for Network and servers
* Stack overflow looked for help on trouble shooting 504 errors and looked to see how to fix it
* https://www.youtube.com/watch?v=2ha5fpj6X1o
* https://www.youtube.com/watch?v=VNndNX-CsdI
*  https://classroom.udacity.com
* https://aws.amazon.com/cloudformation/
* https://github.com/-- reviewed multiple projects for AWS
* https://www.youtube.com/watch?v=yCl8wkdSHA8
* https://www.youtube.com/watch?v=ekfsyrFqXYI
* https://www.youtube.com/watch?v=JKbjPxIE62c
*https://www.digitalocean.com/community/tutorials/how-to-install-configure-and-use-modules-in-the-apache-web-server
* https://docs.aws.amazon.com/cli/latest/reference/elbv2/modify-load-balancer-attributes.html




## Other notes and updates




* To validate if changing the timeout value via SSH terminal fixes the 504 Gateway timeout --(yes it does)
* sudo nano /etc/apache2/apache2.conf
* cd /etc/apache2 then i VI the file to confirm changes changed default value from 5 to 75

* To work around this I created the config file and downloaded the updated file with the change and included the updated file with the change during the install process.
* Also to note I tried to change the attribute for idle timeout value but the exmaples provided by AWS did not seem to work properly :
 *Attributes:*
```
          Value": 30
          Key: idle_timeout.timeout_seconds
```          
### To SSH 
* Create Jumpbox
* Give permissions to you secure Key:
* chmod 400 UDG_P2_key.pem
* ssh to the jumpbox: 
#ssh -i UDG_P2_key.pem ubuntu@ec2-XX-XXXX-XX-XXX.us-west-2.compute.amazonaws.com
#SSH to servers in private subnets:
#ssh ec2-user@XX.XX.XX(your private subnet)


Note: Although due to my network latency this worked very slow for me so I used the Councel from the AWS web page to also connect to the servers.


