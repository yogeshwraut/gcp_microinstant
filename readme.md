
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

