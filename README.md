# PM2_Installation steps: 
1. Install npm and pm2  
sudo apt install npm
   sudo npm install pm2 -g
2. cd ionis
3. git clone and run the commands
   git clone https://github.com/suryamodulus/pm2-webui
4. npm install
5. cp env.example .env
6. npm run setup-admin-user (Required for login)
   User: nvidia
   password: Ionis@3fl
7. npm start
8.Inside pm2-webui folder:

  js files put in assets/js
  and css in assets/css
   
  in the base.html replace these 3 lines
  <script src="/assets/js/jquery-3.6.0.min.js" ></script>
  <script src="/assets/js/tabler.min.js"></script>
  <link rel="stylesheet" href="/assets/css/css/tabler.min.css">

  In .env
  Change to HOST=0.0.0.0
   
10. pm2 start a.sh or /home/nvidia/amq/bin/ionis/bin/ionis_artemis.sh --no-autorestart
   pm2 save
   pm2 startup
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
 
 
