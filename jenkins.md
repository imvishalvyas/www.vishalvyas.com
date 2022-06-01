Jenkins is an open-source automation server.  It allows you to automate the parts of software development related to building, testing and deploying, facilitating continuous integration and continuous delivery. It's a java-based open-source server that runs on any server.

In this article, We will install Jenkins on Ubuntu 20.04.

Prerequisites
- I recommend starting with at least 1 GB of RAM for testing purposes and using 4GB+ RAM in the production environment.
- Oracle JDK 11 installed.

Installing Jenkins
You can install Jenkins from the default repository but sometimes that version is often behind the latest version.

1. Update the below command to install Jenkins.
```
wget -q -O - https://pkg.jenkins.io/debian-stable/jenkins.io.key | sudo apt-key add -
sudo sh -c 'echo deb http://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'
sudo apt-get update
sudo apt-get install jenkins
```

2. Starting Jenkins service.
- Start service.
```
sudo systemctl start jenkins
```
- Start jenkins on boot.
```
sudo systemctl enable jenkins
```
- Check status of the service.
```
$ sudo systemctl status jenkins
```

3. Allowing Firewall.
By default, Jenkins runs on port `8080`, So We need to allow port `8080` from the firewall using `ufw`.
```
sudo ufw allow 8080
```
```
sudo ufw status
```

4. Setup Jenkins
Open the Jenkins from the browser using `http://serverIP:8080`
You should see the Unlock Jenkins screen. Which shows the location of the initial password.
-----IMAGE--------


- Go to the command line and view the password using `cat` command.
```
cat /var/lib/jenkins/secrets/initialAdminPassword
```
-----IMAGE--------

Copy the above password and enter it in the Jenkins in the browser.
-----IMAGE--------


Next, You will get the screen for installing plugins, You can select whatever you want. I am going with `Install suggested plugins`.
-----IMAGE--------


You can see that started installing plugins immediately.
-----IMAGE--------


Now, It will ask to create a new administrator user OR you can skip this step to continue with the default `admin` user and use the password we used above. 
I will create a user with admin rights.

----Image-------


You will get an `Instance Configuration` page that will ask you to confirm the preferred URL, You can confirm either the localhost or your domain name or IP address there.
------IMAGE----

Click on `Save and Finish` to complete the setup of Jenkins installation. Now you will get the page `Jenkins is Ready!`
----- IMAGE------


Click on the `Start Using Jenkins` to access the main Jenkins Dashboard.
------IMAGE ------
