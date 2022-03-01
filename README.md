# Deploying-war-file-Commands in Linux-based-System

Installing Docker:::
1. Install the necessary packages required for docker. Execute the below command:
    $ sudo apt-get install apt-transport-https ca-certificates curl gnupg-agent software-properties-common
2. Add the docker gpg key with the below command:
    $ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
3. Execute the below command to add the docker repository in your system:
    $ sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
4. Install docker with the below commands:
    $ sudo apt update -y
    $ sudo apt install docker-ce -y
5. Docker is installed successfully. Execute the below command to verify the installation and check the docker version:
    $ docker version
6. Execute the below command to check if docker is running or not:
    $ sudo systemctl status docker
7. Check if docker is running or not:
    $ sudo systemctl status docker
8. If it is running, status as ‘active’ will be displayed. Press ‘q’ to exit the status screen. If docker is not running, execute the below command to start it:
    $ sudo systemctl start docker
9. Create a symlink for docker service with the below command so that the docker service starts as soon as you start your machine:
    $ sudo systemclt enable docker
    
Deploying War file on Tomcat Docker Container:::
1. Create a war file of the project
2. Create a directory and copy the war file in it:
   $ cd
   $ mkdir docker_deploy
   $ cp /path_to_war/Test.war docker_deploy
3. Create a dockerfile as below in the directory where you have the war file (docker_deploy):
   $ cd docker_deploy
   $ nano dockerfile
4. Add the below lines in the file:
   FROM tomcat                                        //FROM command determines the image we want to use. The image is fetched from the
   COPY Test.war /usr/local/tomcat/webapps
   CMD ["catalina.sh", "run"]
5. Save and Exit.
6. Build a docker image and run it as a container
   $ docker build -t test .          //The docker build command will execute the dockerfile to create an image out of it, and name the image hello.
   $ docker run -itd -p 8085:8080 test        //docker run command is used to run a docker image as a container.
   $ docker ps      //displays the information about the currently running containers.
   
7. The war file has been deployed. Now we can access our application with the URL: http://public_ip:8085/Test/
   
   
   
   
   
