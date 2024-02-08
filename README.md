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
8.Inside pm2-webui folder:<br>

  js files put in assets/js<br>
  and css in assets/css<br>
   
  in the base.html replace these 3 lines<br>
  <script src="/assets/js/jquery-3.6.0.min.js" ></script><br>
  <script src="/assets/js/tabler.min.js"></script><br>
  <link rel="stylesheet" href="/assets/css/css/tabler.min.css"><br>

  In .env<br>
  Change to HOST=0.0.0.0<br>
   
10. pm2 start a.sh or /home/nvidia/amq/bin/ionis/bin/ionis_artemis.sh --no-autorestart<br>
   pm2 save<br>
   pm2 startup<br>
   sudo env PATH=$PATH:/usr/bin /usr/local/lib/node_modules/pm2/bin/pm2 startup systemd -u nvidia --hp /home/nvidia
11. pm2 start q.sh
    pm2 save
12. pm2 start webui_start.sh
    pm2 save
13. pm2 start thermal_cam_initialization.sh -no-autorestart
    pm2 stop thermal_cam_initialization.sh
    pm2 save
14. pm2 start startup_script --restart-delay 5000 -no-autorestart
    pm2 save

15. pm2 start cli.sh
    pm2 stop cli.sh
    pm2 save
16. pm2 start i.sh
    pm2 stop i.sh
    pm2 save
 
 
