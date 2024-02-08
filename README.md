# PM2_Installation steps: 
1. Install npm and pm2<br>
   sudo apt install npm<br>
   sudo npm install pm2 -g
2. cd ionis
3. git clone and run the commands<br>
   git clone https://github.com/suryamodulus/pm2-webui
4. npm install
5. cp env.example .env
6. npm run setup-admin-user (Required for login)<br>
   User: nvidia<br>
   password: Ionis@3fl
7. npm start
8. Inside pm2-webui folder:<br>

   
   Put js files in assets/js<br>
   and css in assets/css<br>
   
   in the views/base.html replace these 3 lines on line no: 6,7,8 <br>
   <script src="/assets/js/jquery-3.6.0.min.js" ></script><br>
   <script src="/assets/js/tabler.min.js"></script><br>
   <link rel="stylesheet" href="/assets/css/css/tabler.min.css"><br>

   
10. pm2 start a.sh<br>
   pm2 save<br>
   pm2 startup<br>
   sudo env PATH=$PATH:/usr/bin /usr/local/lib/node_modules/pm2/bin/pm2 startup systemd -u nvidia --hp /home/nvidia
11. pm2 start q.sh<br>
    pm2 save
12. pm2 start webui_start.sh<br>
    pm2 save
13. pm2 start thermal_cam_initialization.sh -no-autorestart<br>
    pm2 stop thermal_cam_initialization.sh<br>
    pm2 save
14. pm2 start startup_script --restart-delay 5000 -no-autorestart<br>
    pm2 save

15. pm2 start cli.sh<br>
    pm2 stop cli.sh<br>
    pm2 save
16. pm2 start i.sh<br>
    pm2 stop i.sh<br>
    pm2 save
 
 
