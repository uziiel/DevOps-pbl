# WEB STACK IMPLEMENTATION (LAMP STACK) IN AWS

A technology stack is a set of frameworks and tools used to develop a software product. This set of frameworks and tools are very specifically chosen to work together in creating a well-functioning software. They are acronymns for individual technologies used together for a specific technology product. some examples are…

LAMP (Linux, Apache, MySQL, PHP or Python, or Perl)
LEMP (Linux, Nginx, MySQL, PHP or Python, or Perl)
MERN (MongoDB, ExpressJS, ReactJS, NodeJS)
MEAN (MongoDB, ExpressJS, AngularJS, NodeJS

Step 1 - Install apache and updating the firewall on my EC2 ubuntu instance
- set up and connect to AWS E2C instance via bash terminal
![Screenshot 2021-09-14 at 19 20 31](https://user-images.githubusercontent.com/90186229/133312579-ff7a62ea-6c8c-4812-9aba-5f269911c0cc.png)

- Update, install apache2 after which confirm installation
![Screenshot 2021-09-14 at 19 31 05](https://user-images.githubusercontent.com/90186229/133313848-3d946c26-2906-4629-a6b6-72341f73e386.png)

- retrieve public DNS using to access the web server
![Screenshot 2021-09-14 at 19 48 01](https://user-images.githubusercontent.com/90186229/133316339-2f4c6e1e-c3b5-466d-9fed-a63657849604.png)

Step 2 - Installing mysql
- install and confirm mysql
![Screenshot 2021-09-14 at 19 54 36](https://user-images.githubusercontent.com/90186229/133317235-517b7d4b-ae72-471d-9a4b-edd832801078.png)

Step 3 - Installing PHP
- install and confirm php installation
![Screenshot 2021-09-14 at 19 59 58](https://user-images.githubusercontent.com/90186229/133317929-dba2968f-a082-4a2d-a3ff-a4b8619d7f1c.png)

Step 4 - Creating a virtual host
- configure virtual host and ensure the new website is active
![Screenshot 2021-09-14 at 20 10 54](https://user-images.githubusercontent.com/90186229/133319356-c772ed70-99db-44cd-9466-d07003ec096f.png)

Step 5 - enable php on website
- create directory on appache and update with php script
![Screenshot 2021-09-14 at 20 16 40](https://user-images.githubusercontent.com/90186229/133320118-d6e4b906-4408-4253-82b9-13e3cacbdc99.png)

