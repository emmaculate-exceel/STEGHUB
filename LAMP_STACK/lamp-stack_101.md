# Setting up my lamp stack for the aws ec2 instance
## Screen shot as an indication as a proof of work.
### Setting up my workspace for assignments and tutorials

1. installing the the linux terminal
![installations of he windows terminal](https://github.com/user-attachments/assets/445fce40-42d7-4ea8-aee5-735cd6f0f318)

* i installed the linux terminal from the windows store very quick and user friendly


2. installing vscode and some vscode extensions
![installation of visual studio code](https://github.com/user-attachments/assets/711fb891-b55d-4a90-a0fd-cdcc0dc2b17c)

* installed Microsoft visual studio code on my system from the microsoft store 

![installation vscode extensions](https://github.com/user-attachments/assets/eafb3f2a-fe4f-4839-a26a-2aa81976136c)

* downloaded some neccesary extensions

3. creating and initialzing a workspace folder
![Creating and initilazing of my cloud/devops workspace](https://github.com/user-attachments/assets/15944492-02bc-4f11-8c92-0161bcdf7d1c)

* created my workspace for easy of access 
* using the command mkdir <name of directory>
* created a README.md using the touch <name of file>

4. Installing git and using git command lines
![installation of git command lines into the terminal](https://github.com/user-attachments/assets/6896e96d-721c-41c1-917c-21247b24aae6)


* installed the git command lines into the terminal for easy access
* sudo apt install net-tools
* git init

5. installing ssh and openssh
![installation of ssh and openss into the terminal](https://github.com/user-attachments/assets/e276fda6-5a6a-41fa-b303-e5b65bdddc9e)

* installed ssh and openssh for connecting to my ec2 instance from my local computer.
* sudo apt install openssh-server

6. Creating an instance in aws (aws and git)
![registration of my aws free tier account](https://github.com/user-attachments/assets/a10985ed-86a1-4f54-9823-299268d2a96e)

* created an account
* created an ec2 instance of the server

7. ssh instance in image
![sshing into my ec2 instance](https://github.com/user-attachments/assets/6d8d99ec-50f3-4d56-ac28-7cd81b1eaa2e)

* connecting to my instance from my local computer
* sudo chmod 0400 <private_key>.pem
* ssh -i <private_key>.pem ubuntu@serveripaddress
