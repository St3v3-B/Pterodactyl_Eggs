# Hastebin

## How to import the egg

If you are reading this it looks like you are looking to add this egg to your server.

1. Download any of the json files located in the folders below.
   1. It's easiest to right click the `raw` button and save as.
2. In your panel go to the `Nests` section in the admin part of the panel
3. Click the green `Import Egg` button
4. Browse to the json file you saved earlier
5. Select what nest you want to put the egg in.
   1. If you want a new nest you need to create it before importing the egg.

## You must restart your daemon after importing an egg if you are using 0.7. This is not required on 1.X.

## Instalation

Now you need to choose if you would like to use nginx proxy manager or a simple nginx config.

***Nginx config***

With the nginx config you are ready to go within 2 minutes.
But it is less practical when you have more than one or two.


***Nginx Proxy Manager***

With the Nginx Proxy Manager it gives you a nice interface for you to configure new webaplication that run trough ports other than 80/443

#### If you enounter any problems please contact me and i will help you
My Discord ```.Steve B.#0064``` Discord id: ```481830034756337676```
My discord server https://neytiri.digital/discord

### Using a nginx config
to configure it with a small nginx config you will need to have full 'root' acces to the server

1. Login to the server using ssh and cd to the configuration folders

   ```cd /etc/nginx/sites-available/```
   
2. When you type `ls` you will see 2 configuration files one called Default and one called Pterodactyl.conf
we will be commiting 2 small changes to the Pterodactyl.conf. open using your favorite text editor the pterodactyl.conf

   ```nano pterodactyl.conf```

3. When you have the pterodactyl.conf open change

	You will be needed to remove the ```default_server``` from the config
	
	```
	real_ip_header X-Forwarded-For;
	server {
		listen 80 default_server;
		server_name panel.yourhost.com;
		return 301 https://$server_name$request_uri;
	}
	server {
		listen 443 ssl http2 default_server;
		server_name panel.yourhost.com;
		root /var/www/pterodactyl/public;
	```
	When you have removed the `default_server` from the config you can save the config and we will be making a new one
	
4. You will be making the new config now open using your favorite text editor `hastebin.conf` in that config you can paste the configuration from below dont forget to change the `haste.changeyour.domain` to your domain name
   dont forget to change the `serveripandport:12345` to the server port on the pterodactyl panel then you can save the config
   
   ```
	server {
	  listen 80;
	  listen [::]:80;

	  server_name haste.changeyour.domain;

	  location / {
	    proxy_pass http://serveripandport:12345;
	   }
	}
	```
	#### With this config you will not have ssl i will be adding this later down the line.
	
	#### You can add ssl using cloudflare.

5. Now we need to enable the changes we have made and the `hastebin.conf`
to enable the `hastebin.conf` we will need to make a system link from that file

```ln /etc/nginx/sites-available/hastebin.conf /etc/nginx/sites-enabled/```

Now when you have made the system link we can restart your nginx and you are ready to use your hastebin.

```systemctl restart nginx```

### Using nginx proxy manager



    