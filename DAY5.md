# Task 5

## Install Maven
```bash
sudo apt install maven
```
![1](https://github.com/user-attachments/assets/a8bf051b-d601-4da7-a507-7e3f43874c90)
)

## Fork the repo on github

![2](https://github.com/user-attachments/assets/a1180456-ec45-4df8-a618-bd4733218957)
)

## Configure Jenkins
 - In Jenkins go to `configure jenkins` > `tools`
 - Locate JDK section
 - Uncheck `Install Automatically`
 - Name `Java 17`
 - Go to terminal and enter the command and get the java 17 path:

```bash
update-java-alternatives --list 
```

 - paste the java path in `JAVA_HOME`

![3](https://github.com/user-attachments/assets/3ee9cd2f-8921-4ad4-ba43-71795c19170c)
)

## Fork The Repo and build the pipeline
![4](https://github.com/user-attachments/assets/15e1554d-9665-4103-98ba-d221a682780b)
)
