# WEB SOLUTION WITH WORDPRESS

Project 6 consists of two parts:

Configure storage subsystem for Web and Database servers based on Linux OS. The focus of this part is to give you practical experience of working with disks, partitions and volumes in Linux.

Install WordPress and connect it to a remote MySQL database server. This part of the project will solidify your skills of deploying Web and DB tiers of Web solution.

## Three-tier Architecture
Generally, web, or mobile solutions are implemented based on what is called the Three-tier Architecture.

Three-tier Architecture is a client-server software architecture pattern that comprise of 3 separate layers.

- Presentation Layer (PL): This is the user interface such as the client server or browser on your laptop.
- Business Layer (BL): This is the backend program that implements business logic. Application or Webserver
- Data Access or Management Layer (DAL): This is the layer for computer data storage and data access. Database Server or File System Server such as FTP server, or NFS Server

Step 1 setup redhat ec2 instance and add volume
- While perform the partition command, I notice the partition wasn't creating 
![Screenshot 2021-09-16 at 23 24 13](https://user-images.githubusercontent.com/90186229/133693436-15f1308c-db74-4250-b39f-8e66f0b86087.png)

- Fixed: sudo gdisk /dev/xvdf > then command n > enter the partition amount > enter until prompted for another command then enter command p
![Screenshot 2021-09-16 at 23 27 04](https://user-images.githubusercontent.com/90186229/133693639-d296916f-a224-4f36-b76e-52a09c70e0ea.png)

- Output:
![Screenshot 2021-09-16 at 23 39 13](https://user-images.githubusercontent.com/90186229/133694555-c4585196-abdd-4711-a3d7-d5edfbec7872.png)

- Physical volume created in the partitioned disk 
![Screenshot 2021-09-16 at 23 43 58](https://user-images.githubusercontent.com/90186229/133694930-75e8929b-1d67-48df-bd74-78cd618530b4.png)

- Complete steps 1 & 2 - prepare webserver & database server
![Screenshot 2021-09-17 at 11 20 53](https://user-images.githubusercontent.com/90186229/133767511-9b2a4d19-9c18-47e1-8723-807ea0424085.png)

Step 3 - Instal WordPress
![Screenshot 2021-09-17 at 13 01 24](https://user-images.githubusercontent.com/90186229/133779465-311c2b71-aee0-4484-afec-0bf292d1ff30.png)

