# Installation Instructions

Following information will help you in setting up a nodejs application running on a Docker container.
These instructions were tested on ubuntu 14.04.1 LTS operating system with nodejs 0.12.4 and Docker version 1.2.0.

### Pre-Requisites:
1. Linux OS. (Vencore used Ubuntu 14.04.1 LTS with nodejs version 0.12.4)
2. Docker client 1.2.0 is installed
3. Docker daemon 1.2.0 is installed
4. Execute the following command to make sure docker client and daemon is running               
               ```sudo docker version```
5. Docker server should have internet access to be able to download Docker image from Docker Hub.
6. Port 80 should be available on server where the docker container is being created.
7. Linux user account being used to executing these scripts should have sudo privileges to execute any command or use root user account.

### Docker Container creation and application install process:
1. Connect to the Docker Machine and create a folder. eg: "/vencore/docker"

2. Change to the folder created in step 1 and clone vencore git repository. 

```sudo git clone https://github.com/vencoreinc/18FAGILEPROTOTYPE/vfdademo.git```

3. change to folder "18FAGILEPROTOTYPE/dist" and make sure you have the following files.
                
                Dockerfile
                archive.tar
                vencoreDemoApp.sh
             
4. Execute the following command to make the file executable

                sudo chmod +x vencoreDemoApp.sh

5. Execute the following command to build the docker container and launch application on port 80. If you need to change the application folder or application port, update the script file (vencoreDemoApp.sh) before executing the script file. Update "AppDir" variable to change application folder eg: AppDir="/vencore/docker/vfdademo-master". Update "PMap" variable to change application port eg: PMap="80".

                sudo ./vencoreDemoApp.sh > "VencoreDemoAppInstall-$(date +"%Y-%m-%d:%T").log"

6. Check if application started properly by using application url ```http://<DockerHostIP or DNS>:<application port> ```  eg: http://192.162.1.1:80

### Install application on another server (non-docker):
1. Make sure you have nodejs, npm, pm2, grunt-cli and git installed.
2. Clone vencore git repository to local folder.

	```sudo git clone https://github.com/vencoreinc/18FAGILEPROTOTYPE/vfdademo.git```

3. Change to folder "18FAGILEPROTOTYPE/vfdademo" and execute the following command to start the application on port 80. If port 80 is not available update 80 to available port in the following command before executing it.

	   sudo PORT="80" pm2 start app.js

4. test the application using url ```http://<Host IP or DNS>:<application port> ```  eg: http://192.162.1.1:80