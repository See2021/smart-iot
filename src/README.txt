#################### Run compose.yaml ##############################

                    docker compose up -d

####################################################################

At the initial the mqtt broker are allow anonymous, to
make broker credetial "2 things" to setup 

################### first: make credential file ####################

docker exec -it mosquitto /bin/sh
/ # mosquitto_passwd -c /mosquitto/config/credentials <username>
password: 
comfirm password:
/ # cd mosquitto/config/     

################### Rewrite mosquitto.conf #########################

persistence true
persistence_location /mosquitto/data/
user mosquitto
listener 1883
allow_anonymous false
log_dest file /mosquitto/log/mosquitto.log
log_dest stdout
password_file /mosquitto/config/credentials

################### Restart mosquitto container ####################

docker container restart mosquitto

####################################################################

################### second: modify telegraf.conf ###################

by uncomment
# username = "mqtt"
# password = "mn403193"

this username and password should be the same with credential setup

####################################################################

################### Restart telegraf container #####################

docker container restart telegraf

####################################################################