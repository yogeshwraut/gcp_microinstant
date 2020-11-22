
sudo apt-get install git

git clone https://github.com/yogeshwraut/gcp_microinstant.git ~/gcp_microinstant

cd ~/gcp_microinstant

docker-compose pull && docker-compose up -d

#---------------------------------------------------------------------------------------------------------

if want to remove directory then

cd ~/gcp_microinstant

docker-compose stop

docker-compose down --rmi local

docker-compose rm -s -v -a -f

cd

 rm -rf ~/gcp_microinstant

#----------------------------------------------------------------------------------------------------------

 nginx:
        build: nginx
        ports:
          - "80:80"
        volumes_from:
          - application
        volumes:
          - ./logs/nginx/:/var/log/nginx

#-----------------------------------------------------------------------

web:
  image: nginx
  volumes:
   - ./templates:/etc/nginx/templates
  ports:
   - "8080:80"
  environment:
   - NGINX_HOST=foobar.com
   - NGINX_PORT=80
#-------------------------------------------------------------------------------------
    mysql:
        image: mysql:latest
        command: --default-authentication-plugin=mysql_native_password
        container_name: mysql
        restart: always
        environment:
            MYSQL_USER: wordpress
            MYSQL_PASSWORD: wordpress
            MYSQL_ROOT_PASSWORD: wordpress
            MYSQL_DATABASE: wordpress
        networks:
            - wpsite
        volumes:
            - mysql:/var/lib/mysql