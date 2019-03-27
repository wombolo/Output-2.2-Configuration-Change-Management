# Output-2.2-Configuration-Change-Management
Output to illustrate Configuration & Change Management by building an AMI image on AWS with Packer & Ansible

### Prerequisites
Your AWS access key and secret key will be required to build an image on AWS. Kindly follow this [Tutorial](https://aws.amazon.com/blogs/security/wheres-my-secret-access-key/) as to how to obtain yours.
Once that is done, open a terminal window and run: `export aws_access_key=YOUR_ACCESS_KEY` and `export aws_secret_key=YOUR_SECRET_KEY`

You also need to install packer [here](https://www.packer.io/intro/getting-started/install.html).

### Building & Installation

* Clone this github repository: `git clone https://github.com/wombolo/Output-2.2-Configuration-Change-Management.git`

* Run the command `packer validate packer.json` to validate the packer config file
* Run the command `packer build packer.json` to build the image.
* After successfully running the command, go to your dashboard on aws, under images, check AMIs you will see the the image that was just created
* Select the image, and launch it
* When creating a security group, ensure you grant access to port 80.
* After launching the instance, visit the public IPv4 provided by the console to view the application.

## Built With

* [Packer](https://www.packer.io/)
* [Ansible](https://www.ansible.com/)
