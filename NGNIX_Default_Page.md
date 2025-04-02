### How to Point Configure Nginx on VPS
#
- Login SSH & Configure Nginx If not already installed or Default page not displayed:
    - Login your account via ssh credentials
    - Update or Upgrade Packages
    ```sh
      sudo apt update && sudo apt upgrade -y
    ```
    - Install Nginx
    ```sh
      sudo apt install nginx
    ```
    - After succesfully install check version
    ```sh
      nginx -v
    ```
    - Start and Enable Nginx
    ```sh
      sudo systemctl start nginx
      sudo systemctl enable nginx
    ```
    - Allow Firewall Access (If UFW is Enabled)
    ```sh
      sudo ufw status
    ```
    - Allow HTTP and HTTPS traffic:
    ```sh
      sudo ufw allow 'Nginx Full'
    ```

    - Restart Nginx Once
    ```sh
      sudo systemctl restart nginx
    ```

    - Verify Nginx Installation
    ```sh
      systemctl status nginx
    ```

    - Note: If Nginx default page is not display check path 
    ```sh
      cd /etc/nginx/sites-enabled
    ```
    - Open default.conf or default
    ```sh
      cd /etc/nginx/sites-enabled/default.conf
    ```
    - Paste it here.
    ```sh
      # Default server block for other domains or fallback
      server {
          listen 80 default_server;
          listen [::]:80 default_server;
          listen 443 default_server;
          listen [::]:443 default_server;
          ssl_reject_handshake on;
          server_name _;

          root /var/www/html;
          index index.html index.htm index.nginx-debian.html;

          location / {
              try_files $uri $uri/ =404;
          }
      }
    ``` 

- OR open your browser and go to your VPS IP address:
  ```sh
    http://your-server-ip
  ``` 
  - Desired Output is Nginx /var/www/html page display


- Note: index.html must be in /var/www/html path. 

- For More Enquiry Contact me on +91 9026628837