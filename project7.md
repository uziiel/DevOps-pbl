# DEVOPS TOOLING WEBSITE SOLUTION
## Step 1 - Prepare NFS Server
 - Spin up new instances on AWS service console
![Screenshot 2022-01-05 at 13 26 25](https://user-images.githubusercontent.com/90186229/148225082-76510ad1-6230-4675-aed0-de6a5d301094.png)


 - Create logical volumes to attached to the servers (ensure the volume is on the same AZ - availablity zone as the instance)
![image](https://user-images.githubusercontent.com/90186229/148226471-1b7d0a0c-47c3-4994-a12a-2fbbd4f45ca7.png)


 - ssh into your NFS instances (ssh -i "pairkey.pem" ec2-user@ec2-x.x.xxx.xx.xxx) and inspect the block (lsblk)
![Screenshot 2022-01-05 at 13 46 41](https://user-images.githubusercontent.com/90186229/148227698-83b3dbe5-1889-4c79-b5b5-f5323ca3dc30.png)


 - Create volume partition for NFS server (sudo gdisk /dev/xvdf, sudo gdisk /dev/xvdg, sudo gdisk /dev/xvdh)
![Screenshot 2022-01-05 at 14 01 22](https://user-images.githubusercontent.com/90186229/148229871-fdb73773-5b60-4ac4-a6ee-e99b51390f9f.png)

- Install LVM package (using sudo yum install lvm2. Run sudo lvmdiskscan command to check for available partitions.)
![Screenshot 2022-01-05 at 14 15 27](https://user-images.githubusercontent.com/90186229/148231959-1db3fe32-49d9-4171-a851-f4f8ae8276a2.png)


- To configure the volume partition (physical volume) run the following code:

- pvcreate - sudo pvcreate /dev/xvdf1 /dev/xvdg1 /dev/xvdh1
- sudo pvs
![Screenshot 2022-01-05 at 15 36 00](https://user-images.githubusercontent.com/90186229/148244851-e1e9391b-6dbe-46d0-9554-6e15810c6284.png)


- sudo vgcreate webdata-vg /dev/xvdh1 /dev/xvdg1 /dev/xvdf1
- sudo vgs
![Screenshot 2022-01-05 at 15 49 32](https://user-images.githubusercontent.com/90186229/148247003-8d5109c8-17d3-4648-a226-2946652c4c9d.png)


- sudo lvcreate -n lv-opt -L 14G webdata-vg used by Jenkins server
- sudo lvcreate -n lv-apps -L 14G webdata-vg
- sudo lvcreate -n lv-logs -L 14G webdata-vg
- sudo lvs
![Screenshot 2022-01-05 at 16 10 14](https://user-images.githubusercontent.com/90186229/148250182-0935a938-e75e-4488-bd93-976c63062e92.png)


- To verify the entire setup - sudo vgdisplay -v #view complete setup - VG, PV, and LV
- sudo lsblk 
- sudo mkfs -t xfs /dev/webdata-vg/lv-apps
- sudo mkfs -t xfs /dev/webdata-vg/lv-logs
- sudo mkfs -t xfs /dev/webdata-vg/lv-opt
![Screenshot 2022-01-05 at 16 30 40](https://user-images.githubusercontent.com/90186229/148253458-d1ce9756-4bde-4127-9100-2c8d17b01c88.png)


- check if /mnt exist ls 
- sudo mkdir -p /mnt/apps
- cd into /mnt to create /logs and /opt
- sudo mount /dev/webdata-vg/lv-apps /mnt/apps
- sudo mount /dev/webdata-vg/lv-opt /mnt/opt
- sudo mount /dev/webdata-vg/lv-logs /mnt/logs
![Screenshot 2022-01-05 at 16 36 03](https://user-images.githubusercontent.com/90186229/148254221-369fab1f-bcc3-4f1e-8e5f-726bc1dc7426.png)

- Time to install NFS Server
- sudo yum -y update
- sudo yum install nfs-utils -y
- sudo systemctl start nfs-server.service
- sudo systemctl enable nfs-server.service
- sudo systemctl status nfs-server.service
![Screenshot 2022-01-05 at 17 07 22](https://user-images.githubusercontent.com/90186229/148258902-30d18c5c-9a84-4d7c-b1b0-f5741adae5d2.png)

- Setup permission and restart the NFS server

- Configuring NFS server access
![Screenshot 2022-01-05 at 17 20 46](https://user-images.githubusercontent.com/90186229/148260809-7e55e266-608d-4f24-9449-91f4fd2215e8.png)


# Step 2 - Connect and setup DB server
- update and install mysql [sudo apt update; sudo apt install mysql-server]
- dive into mysql and create tooling database
![Screenshot 2022-01-05 at 17 03 13](https://user-images.githubusercontent.com/90186229/148258301-8f429eb8-e7ab-42bb-8e60-a222be87cfa6.png)

# Step 3 - Prepare the webserver
- Install NFS utility
- Mount and target NFS server's export
- Verify success mount with df -h
![Screenshot 2022-01-05 at 17 47 45](https://user-images.githubusercontent.com/90186229/148264477-c11d2e26-848c-4669-a48b-824ec828a291.png)

- Install REMI's repository, Apache and PHP
![Screenshot 2022-01-05 at 18 07 30](https://user-images.githubusercontent.com/90186229/148267010-c26bd659-2606-4fed-8fa6-c19657e71a6e.png)

- Configure all webservers, DB and NFS
![Screenshot 2022-01-05 at 20 39 30](https://user-images.githubusercontent.com/90186229/148286094-30b87f62-e0f4-4ec2-8238-bc22bd9bce9e.png)

- Fork tooling source - git clone https://github.com/darey-io/tooling.git
![Screenshot 2022-01-05 at 20 46 41](https://user-images.githubusercontent.com/90186229/148287025-f3e65261-1472-4c28-9413-0f9451c502ca.png)

- Deploy Tooling webite code
![Screenshot 2022-01-05 at 20 53 53](https://user-images.githubusercontent.com/90186229/148287941-770699f1-16ea-402d-894a-8930dee51794.png)

- Loading WEbserver Public address
![Screenshot 2022-01-05 at 21 02 15](https://user-images.githubusercontent.com/90186229/148289003-07e600ba-d1f3-4053-a795-ec23f891e7b4.png)

- Configuring DB for access
![Screenshot 2022-01-05 at 21 19 45](https://user-images.githubusercontent.com/90186229/148291026-06fb4846-7aa4-445c-9797-a07c81d439b3.png)

- Accessing DB with u/s & p/w
![Screenshot 2022-01-05 at 21 30 45](https://user-images.githubusercontent.com/90186229/148292377-2143821a-0835-46ab-9470-85cab1e363fd.png)

![Screenshot 2022-01-05 at 21 32 47](https://user-images.githubusercontent.com/90186229/148292542-fed72370-f736-43d4-9c34-6b66a5db6d70.png)
