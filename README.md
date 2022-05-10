# AWS Development in VS Code
This skeleton project will get you set up with all the necessary tools and VS Code integrations to develop and deploy applications in AWS.

**Prerequisites:**

Docker
VS Code

**What's Included**

* Development container based on Ubuntu 22.04
* Automatic installation of VS Code extensions to integrate with AWS (AWS Toolbox and more)
* Pyenv and Pipenv with Python 3.9.12 as default
* NodeJS 16
* AWS CLI
* AWS SAM
* AWS Amplify
* AWS CDK
* AWS credentials and settings automatically mounted in to container if already locally configured

## Installing Docker
**macOS and Windows**

Install Docker Desktop from https://www.docker.com/products/docker-desktop/ and follow the instructions given.  For Windows users, using WSL2 is recommended, but shouldn't be necessary.

**Ubuntu (and derivatives)**

Docker is provided in the official Ubuntu repositories.  To install, run the following commands:
```
# Install Docker
sudo apt install docker.io

# Enable the Docker service and start it immediately
sudo systemctl enable docker --now

# Add your user to the docker group
sudo usermod -aG docker $(whoami)
```
After running the above commands, logout and back in or completely reboot so that the docker group membership takes effect.

## Install VS Code
Download VS Code for all platforms at https://code.visualstudio.com/download.  VS Code is also included in the Ubuntu software repository as a Snap package and may work.

## Start Coding
After cloning this repository*, open it in VS Code.  Agree to any prompts to open in a workspace and install recommended plugins.  After the recommended plugins are installed, agree to the prompt to reopen in a container.  VS Code will then start a container and build the development environment.  This will take around 5 minutes, but only needs to happen once.  The integrated terminal in VS Code will open a shell in the development container where all development tools and AWS tools are available.  If you need to rebuild the container, press Ctrl(Cmd)-Shift-P to open the command palette (also available in the menu at View -> Command Palette) and search for "Remote-Containers: Rebuild and Reopen in Container" (Instead of typing the full name, you can just type "rebuild" as a shortcut and select the correct command)

The AWS Toolbox extension for VS Code will automatically be installed and provides integration with AWS resources. Learn more about AWS Toolbox here - https://aws.amazon.com/visualstudiocode/

*\* Note:  Make sure to clone this repository to a local filesystem and not something like OneDrive or Dropbox otherwise Docker will be unable to mount the project inside the container and the build of the development container will fail.* 

