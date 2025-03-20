# Installing Jenkins in Linux and creating a freestyle Nginx project


## Installing JDK 17
```bash
sudo apt install -y openjdk-17-jdk
sudo update-alternatives --config java
```

![1](https://github.com/user-attachments/assets/75ed3b14-c3ee-41e1-b83f-681c6bafd641)

 - After this you'll be prompted to select a java version select the index with java-17

![1](https://github.com/user-attachments/assets/5ca00311-ea4c-44eb-b27c-a4e793ac5752)

## Installing Jenkins
```bash
sudo wget -O /usr/share/keyrings/jenkins-keyring.asc \
  https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key
echo "deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc]" \
  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt-get update
sudo apt-get install jenkins
```

![1](https://github.com/user-attachments/assets/467fc754-01ee-490e-a71e-e14b916494de)

## Starting Jenkins
```bash
sudo systemctl status jenkins
sudo systemctl enable jenkins
sudo systemctl start jenkins
sudo systemctl status jenkins
```
 - Copy the password provided in this step

![1](https://github.com/user-attachments/assets/8f7d48c8-66ac-4d48-b0ef-e420dcbc3b13)

## Jenkins Initial Setup
 - Open a browser and go to `localhost:8080` and paste in the password

![1](https://github.com/user-attachments/assets/23cefbc4-25ca-4ddc-a59c-3c958275764c)

 - Click on `continue`

![1](https://github.com/user-attachments/assets/ea2b865f-689d-4d00-801c-8e4847a20adb)

 - Click on `Install Suggested Plugins`

![1](https://github.com/user-attachments/assets/4fe685f6-5245-4075-ad4c-a87e981c25ca)

 - The plugins will eb installed one by one and you'll be redirected to the next page click `Start Jenkins`

![Screenshot from 2025-03-18 10-54-45](https://github.com/user-attachments/assets/75d87cd5-1bb9-49bd-b60e-fdffda5a0b91)
)

 - Fill in your details and create user id and password then click `save and continue`
> [!NOTE]  
> Remember this user id and password. This will overwrite the `Initial Password` generated, and will be required to login everytime you restart Jenkins.

![image](https://github.com/user-attachments/assets/0146a230-0951-4671-b88c-6ded7564a01f)


 - Leave the default Jenkins URL then click `Save and Finish`

![1](https://github.com/user-attachments/assets/7dc3ae3c-85f4-4820-80a4-9b455affc3ae)


## Setting up a Nginx freestyle project in Jenkins
 - In Jenkins home page click on `create a job`

![Screenshot from 2025-03-18 10-55-16](https://github.com/user-attachments/assets/7c0a4675-c73d-4f23-b632-cfbdd94c85f1)
)

 - Enter a project name
 - Select `Freestyle Project`
 - Click `Ok`

![Screenshot from 2025-03-18 10-58-37](https://github.com/user-attachments/assets/f525680d-95d2-4de1-bbd4-d330445b854a)
)

 - In the next page scroll down to `Build Steps`
 - Click `Add Build Step`
 - Select `Execute Shell`

![1](https://github.com/user-attachments/assets/60f7d6b0-85e9-44eb-a78b-9a94e8d46a94)

 - Paste in the below code
```bash
#!/bin/bash
# Update package lists
sudo apt update -y

# Install Nginx
sudo apt install -y nginx

# Start and enable Nginx
sudo systemctl enable nginx.service
sudo systemctl start nginx

# Verify Nginx is running
systemctl status nginx
```

![1](https://github.com/user-attachments/assets/27fd056c-ea7e-4069-9f23-fd7887260f96)

 - Click `Build Now` in the left side panel
   
![Screenshot from 2025-03-18 11-02-04](https://github.com/user-attachments/assets/2c74e8e9-338b-4c20-81e4-9f91adb35421)
)

 - Your first Nginx project using Jenkins is successfully deployed!
 - Click on the Build in `Builds` and click on the `Console Output` to view the logs
![Screenshot from 2025-03-20 09-40-51](https://github.com/user-attachments/assets/988974ed-1096-41f2-8049-d272d9885878)
)
