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

### Using a nginx config
to configure it with a small nginx config you will need to have full 'root' acces to the server

1. Login to the server using ssh and cd to the configuration folders

   ```cd /etc/nginx/sites-available/```
   
2. When you type `ls` you will see 2 configuration files one called Default and one called Pterodactyl.conf
we will be commiting 2 small changes to the Pterodactyl.conf. open using your favorite text editor the pterodactyl.conf

    ```nano pterodactyl.conf```


### Using nginx proxy manager



    