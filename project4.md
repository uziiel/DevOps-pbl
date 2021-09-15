# MEAN STACK DEPLOYMENT TO UBUNTU IN AWS

MEAN Stack is a combination of following components:
MongoDB (Document database) – Stores and allows to retrieve data.
Express (Back-end application framework) – Makes requests to Database for Reads and Writes.
Angular (Front-end application framework) – Handles Client and Server Requests
Node.js (JavaScript runtime environment) – Accepts requests and displays results to end user

Step 1 - Install NodeJS
-install nodejs then mongoDB
![Screenshot 2021-09-15 at 02 07 01](https://user-images.githubusercontent.com/90186229/133353835-2a349264-88ce-4a67-ba1c-859504fcad27.png)

- Encountered this issue while trying to start the server

![Screenshot 2021-09-15 at 02 19 50](https://user-images.githubusercontent.com/90186229/133354785-a56d4cb5-a1e9-4adf-8c50-35d9344377e5.png)

- Researched this error code and it was related to the encoder and decoder - this resolved the issue adding <let { TextEncoder, TextDecoder } = require("util");> to the encoding.js file
![Screenshot 2021-09-15 at 03 07 09](https://user-images.githubusercontent.com/90186229/133358641-b87aa0f6-fb4c-4391-8ad0-472950e4e1d9.png)



![Screenshot 2021-09-15 at 03 09 39](https://user-images.githubusercontent.com/90186229/133358833-c98e9a9d-6efb-47d1-afb8-e2282b0d1204.png)

