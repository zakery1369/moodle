# Moodle

![Moodle Docker](https://miro.medium.com/max/700/1*OGJsQYR5fFb6Tw0k-N7MVw.png)

- ## How to use this image:

1. Download the image from dockerhub
```
docker pull zakery1369/moodle:[tag]
```
2. Clone or download all files from  [GitHub Page](https://github.com/zakery1369/moodle/)
3. Download moodle.tar.gz from [Moodle Downloads](https://download.moodle.org/)
4. Extract moodle-xx.tar.gz to the following directory:
```
/var/www/html/moodle
```
5. Run the command below :
```
docker-compose up -d
```
6. Open up your web browser, and proceed to the following address to start the installation ( Remember that my configuration will start the server at port 80, in case you want to change the hostname/port, proceed to the next section to customize this image )

```
127.0.0.1
```
7. In the Database settings, adjust the following :
```
Database host = sql
Database name = moodle
Database user = moodle
Database password = 147258369
Tables prefix = mdl_
Database port = 3306
Unix socket = it's blank
```


# Customize this image

- ## Use domain with SSL and change Nginx configurations
in the files downloaded from this [GitHub Page](https://github.com/zakery1369/moodle/)
1. In this directory, uncomment the lines in the ``moodle.conf`` and replace your domain with **example.com**
```
/nginx/conf.d/moodle.conf
```
2. Following the guides from [Letsencrypt](https://letsencrypt.org/getting-started/) (certbot), copy the privkey.pem and fullchain.pem to the following directory. (Remember that from the previous step, the cert files names should correspond with these config file) :
```
/nginx/conf.d/certs
```
3. In case you want to configure your Nginx, you can find the config file in the following directory :
```
/nginx/nginx.conf
```

- ## Change mysql configurations
1. Customize your configs in the following file :
```
/mysql/my.cnf
```
2. Change the mysql environment variables in the docker-compose.yml file :
```
environment:
        MYSQL_ROOT_PASSWORD: 147258369
        MYSQL_DATABASE: moodle
        MYSQL_USER: moodle
        MYSQL_PASSWORD: 147258369
```
- ## Change php-fpm configurations
Add your customized configurations in these files :
```
/php-fpm/php.ini-development
/php-fpm/php.ini-production
/php-fpm/www.conf
/php-fpm/php.ini
```

- ## Exposing external port
Edit docker-compose.yml to change the exposed ports :
``` 
ports:
     - 80:80
     - 443:443
```
