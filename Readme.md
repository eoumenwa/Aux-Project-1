The script will read a CSV file, create each user on the server, and add the created user(s) to an existing group called developers. It will also check for the existence of the user on the system before it will attempt to create it. Each user will have a default home folder with a .ssh folder within its home folder. For each user’s SSH configuration, the script will create an authorized keys file and add a given public key to it.


### Implementation Summary


Link to git hub repository 
https://github.com/eoumenwa/firstprojectongit.git


Link to Demo 1
https://drive.google.com/file/d/14YSPcJLnhz0zPmjKqCrRFhxkjR7uerAG/view?usp=sharing

Link to Demo 2
https://drive.google.com/file/d/1uK-7CA3vb-VXGC-RrqDfvB0GTlmJBmb-/view?usp=sharing

 
Shell Scripting
In this project, we need to onboard 20 new Linux users onto a server by creating a shell script that reads a csv file that contains the first name of the users to be onboarded.
Create the project folder called Shell
mkdir Shell
Move into the Shell folder
cd Shell
Create a csv file name names.csv
touch names.csv

Open the names.csv file
vim names.csv
Insert some random names into it. (One name per line)
Create a group for the users to be onboarded using groupadd command as shown below



Script content
The script will read the CSV file, create each user on the server, and add to an existing group called developers. It will also first check for the existence of the user on the system, before it will attempt to create it. Each user will have a default home folder with a .ssh folder within its HOME folder. For each user’s SSH configuration, the script will create an authorized_keys file and add a given public key to it.



As shown above, I attempted to connect to users but was unable to do so for unknown reasons. I started to troubleshoot and research the SSH process.


Summary of challenges and errors

I did not not run ssh-keygen to generate the public and private keys. Instead I copied the public and private key from the documentation directly into the authorized key files using the script
I went ahead to manually copy both public and private keys into each user’s .ssh directory after creating the files id_rsa.pub and id_rsa.pub on some of the users
I was trying to connect to users from the root directory 

### Corrections 

I started by running ssh-keygen as shown below



listed the directory contents to confirm existence of public and private key files


Changed permissions on the public key to ‘read only’


Modifying the script to change permissions on the authorized key files created using chmod 400 and running the script to effect the change
 



Modify content of both the public and private keys using the keys provided in the documentation

Copying the public content (id_rsa.pub) to each user’s authorized_keys file already created using the following command
     cp -R "/home/ubuntu/.ssh/id_rsa.pub" "/home/$user/.ssh/authorized_keys"
    

  Connecting to users using ssh@ipaddress command

 








