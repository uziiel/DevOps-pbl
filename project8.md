# Project 8 - Load Balancer Solution With Apache
- Configure Apache
- Spin an Ubuntu instance 
![Screenshot 2022-01-05 at 22 50 32](https://user-images.githubusercontent.com/90186229/148300892-d89c1548-00b6-4fe1-a4f8-91fc51319263.png)

- Install Apache LB
![Screenshot 2022-01-05 at 22 53 50](https://user-images.githubusercontent.com/90186229/148301244-e0f1566a-ff74-49ca-a468-87a75886c3f7.png)

- Ensure Apache is running
![Screenshot 2022-01-05 at 22 55 11](https://user-images.githubusercontent.com/90186229/148301390-b9ac37bb-d3af-4777-bc2f-407759b63077.png)

- Configure Load Balancer
![Screenshot 2022-01-05 at 23 11 23](https://user-images.githubusercontent.com/90186229/148302862-8d17f49a-1dee-4535-b729-3c2c4379c5b9.png)


![Screenshot 2022-01-14 at 19 15 04](https://user-images.githubusercontent.com/90186229/149572255-9b68c288-d689-48ca-989a-784fe17587a3.png)


Initially, I was prompted with a login screen
![Screenshot 2022-01-14 at 19 18 19](https://user-images.githubusercontent.com/90186229/149572597-86f54e4c-5c62-4e52-9abf-6b0692880c91.png)

Provided login detail to access the page - LB working
![Screenshot 2022-01-14 at 19 16 31](https://user-images.githubusercontent.com/90186229/149572362-9118a97b-f304-4698-a139-128ec92b49aa.png)

Side Self Study
sudo vi /etc/hosts then enter your webserver ip address
![Screenshot 2022-01-14 at 19 59 58](https://user-images.githubusercontent.com/90186229/149577477-425f937c-340e-43a5-a8d3-005d9af6d646.png)

Update LB config
![Screenshot 2022-01-14 at 20 03 26](https://user-images.githubusercontent.com/90186229/149577874-b118ace0-8f25-4722-8d51-a673945cd551.png)

Call client URL using curl http://Web1 - the following is displayed (html code in the ternminal which is same what user can see on the URL)
![Screenshot 2022-01-14 at 20 05 24](https://user-images.githubusercontent.com/90186229/149578138-5325eb67-51e6-4a98-a1d8-ddeec1821136.png)
