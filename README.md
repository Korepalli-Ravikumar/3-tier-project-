
1.Create rds database into private subnets
2.Create two private  servers in private subnets one is for frontend and another one is for backend
3.Create two TG and loadbalncers one is for frontend another one is for backend 
4.Create both loadblancers in public subnets only and loadbalancer type s internet facing only becuser internal loadbalncer not working for our project 

->>connect to backend server------------------

5. git clone https://github.com/CloudTechDevOps/2nd10WeeksofCloudOps-main.git
   cd backend 
6. edit the .env file in bellow path if u dont have any .env file just create in below path

7. 2nd10WeeksofCloudOps-main.git/backend/.env

### add this mater
DB_HOST=book.rds.com	#change rds endpoint
DB_USERNAME=admin	#cahnge to nyour rds user name 
DB_PASSWORD="veera"   # change to your rds password
PORT=3306
##############################
sudo yum install mariadb105-server

8.SSH into backend server and then run test.sql script from backend to create tables and records 

mysql -h book.rds.com -u admin -p<password> < test.sql


### Backend deploy process ###

sudo dnf install -y nodejs

cd backend

npm install

npm install -g pm2

pm2 start index.js --name node-app

9. #### after that create backend tg and loadbalncer and check your loadbalncer is giving hello response or not 


---------------------------------- FrontEnd---------------------------------------

-------Step-1-------install dependencies ------

sudo yum install httpd -y 
sudo systemctl start httpd -y
sudo systemctl enable httpd -y
sudo dnf install -y nodejs

 ### Frontend deploy process ###
git clone https://github.com/CloudTechDevOps/2nd10WeeksofCloudOps-main.git
   
10. checkout client cd client 

11. edit the config.js

vi client/src/pages/config.js
  
const API_BASE_URL = "http://api.narni.co.in";
 
12. in above line change to your backend loadbalncer url
const API_BASE_URL = "http://backend-loadbalancer-url";


13. then go to client directory 
14.run below commands

****(Use npm run build:
When preparing the app for deployment (e.g., to a server or hosting service like AWS, Netlify, or Vercel).
Use npm start:
During development or to start the app in production (for backend apps).)*****

npm install 
npm run build
sudo cp -r build/* /var/www/html

your frontend part is completed 

15. ### #### after that create frontend tg and loadbalncer and check your loadbalncer is giving project output along with books 
16. add the books 
