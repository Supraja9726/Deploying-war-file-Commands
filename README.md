# Deploying-war-file-Commands in Linux-based-System

##Installing Docker:::

___1. Install the necessary packages required for docker. Execute the below command:___

    $ sudo apt-get install apt-transport-https ca-certificates curl gnupg-agent software-properties-common

___2. Add the docker gpg key with the below command:___

    $ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

___3. Execute the below command to add the docker repository in your system:___
    
    $ sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"

___4. Install docker with the below commands:___
    
    $ sudo apt update -y
    $ sudo apt install docker-ce -y

___5. Docker is installed successfully. Execute the below command to verify the installation and check the docker version:___
    
    $ docker version

___6. Execute the below command to check if docker is running or not:___
   
    $ sudo systemctl status docker

___7. Check if docker is running or not:___
    
    $ sudo systemctl status docker

___8. If it is running, status as ‘active’ will be displayed. Press ‘q’ to exit the status screen. If docker is not running, execute the below command to start it:___
    
    $ sudo systemctl start docker

___9. Create a symlink for docker service with the below command so that the docker service starts as soon as you start your machine:___
    
    $ sudo systemclt enable docker
    
##Deploying War file on Tomcat Docker Container:::

___1. Create a war file of the project___

___2. Create a directory and copy the war file in it:___
   
    $ cd
    $ mkdir docker_deploy
    $ cp /path_to_war/Test.war docker_deploy

___3. Create a dockerfile as below in the directory where you have the war file (docker_deploy):___
  
    $ cd docker_deploy
    $ nano dockerfile

___4. Add the below lines in the file:___
   
    FROM tomcat                  //Determines the image we want to use. The image is fetched from the
    COPY Test.war /usr/local/tomcat/webapps
    CMD ["catalina.sh", "run"]

___5. Save and Exit.___

___6. Build a docker image and run it as a container___
  
       $ docker build -t test .      //Execute the dockerfile to create an image out of it;name the image test.
       $ docker run -itd -p 8085:8080 test     //docker run command is used to run a docker image as a container.
       $ docker ps      //displays the information about the currently running containers.
   
___7. The war file has been deployed. Now we can access our application with the URL: http://public_ip:8085/Test/___

___8. To stop a docker running:____
  
    $ sudo docker stop [CONTAINERID]
   
   
   
   
