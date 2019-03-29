# # Configuration Change Management

This is to illustrate Configuration & Change Management by building an AMI image on AWS with Packer & Ansible.
This is a sequel to the previous illustration on [deploying a JS application on AWS](https://github.com/wombolo/Output-2.1-Deploy-Js-App-to-AWS).  
This illustration adds a bit of automation in order to improve productivity and speed when deploying a web app to AWS. 


### Packer
This is primarily used to create machine images which can run on any computing engine platform. Such include: AWS, Google-cloud, Vagrant. etc.
Packer is easy to use and automates the creation of any type of machine image. It embraces modern configuration management by encouraging the use a framework such as Ansible, Chef or Puppet to install and configure the software within Packer-made images.

A sample packer configuration file stored as JSON:
![](%23%20Output-2.2-Configuration-Change-Management/AFD36755-003F-41CD-951B-115DD1205AEA.png)
The configuration requires 3 main variables:
-**Variables**: This stores values which are re-usable & required by the builders section.

-**Builders**: This is an array of objects which stores the necessary details needed by the cloud platform. e.g aws, google-cloud, etc. 

-**Provisioners**: This handles the initiators of the machine image, the way software are installed and services are configures are all handles here. Examples include: Bash, ansible, etc


### Ansible
This is a software configuration management tool which allows technology teams automate tasks in order to improve productivity, reduce errors made by humans & ease of keeping records of software installed on a system.
Ansible configuration utilizes a file in the YAML `(.yml)` file format. 

A sample ansible configuration file, also called a playbook file:
![](%23%20Output-2.2-Configuration-Change-Management/E76AC839-AC9C-4026-B884-91682E32564F.png)
This playbook stores the necessary details Ansible needs to provision a system. Software can be specified to be installed, system services can be configured and run with ansible as desired. 
More information can be found in this [tutorial](https://docs.ansible.com/ansible/latest/user_guide/playbooks_intro.html#basics).



### Prerequisites
Your AWS access key and secret key will be required to build an image on AWS. Kindly follow this [Tutorial](https://aws.amazon.com/blogs/security/wheres-my-secret-access-key/) as to how to obtain yours.
Once that is done, open a terminal window and run: /`export aws_access_key=YOUR_ACCESS_KEY`/and /`export aws_secret_key=YOUR_SECRET_KEY`/

You also need to install [packer](https://www.packer.io/intro/getting-started/install.html) and [ansible](https://www.cyberciti.biz/python-tutorials/linux-tutorial-install-ansible-configuration-management-and-it-automation-tool/)) on your local machine. Follow those tutorials to get started.


### Building & Installation

* Clone this github repository: /`git clone https://github.com/wombolo/Output-2.2-Configuration-Change-Management.git`/

*  Change directory into the folder `Output-2.2-Configuration-Change-Management`

* Run the command /`packer validate packer.json`/ in the terminal with the working directory set to `Output-2.2-Configuration-Change-Management` to validate the packer config file

* Run the command /`packer build packer.json`/to build the image. If successful, the output should be similar to the below image.
![](%23%20Output-2.2-Configuration-Change-Management/FDEC0688-A6F1-4DED-B59F-7CA607CE48C0.png)


* After successfully running the command, go to your dashboard on aws, under images, check AMIs you will see the the image that was just created as shown below:
![](%23%20Output-2.2-Configuration-Change-Management/BE77CEF6-13C6-4F37-BDDF-001B1265743A.png)

* Select the image, and launch it
![](%23%20Output-2.2-Configuration-Change-Management/Screenshot%202019-03-29%20at%2012.18.17%20PM.png)

* When creating a security group, ensure you grant access to port 80.
![](%23%20Output-2.2-Configuration-Change-Management/Screenshot%202019-03-29%20at%2012.20.21%20PM.png)


* After launching the instance, visit the public IPv4 provided by the AWS Dashboard to view the application.
![](%23%20Output-2.2-Configuration-Change-Management/Screenshot%202019-03-29%20at%2012.21.52%20PM.png)


## Built With
* [Packer](https://www.packer.io/)
* [Ansible](https://www.ansible.com/)

