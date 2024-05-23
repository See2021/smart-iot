# Use the official eclipse-mosquitto image as a base
FROM eclipse-mosquitto

# RUN echo "persistence true" > /mosquitto/config/mosquitto.conf && \
#     echo "persistence_location /mosquitto/data/" >> /mosquitto/config/mosquitto.conf && \
#     echo "user mosquitto" >> /mosquitto/config/mosquitto.conf && \
#     echo "listener 1883" >> /mosquitto/config/mosquitto.conf && \
#     echo "allow_anonymous true" >> /mosquitto/config/mosquitto.conf && \
#     echo "log_dest file /mosquitto/log/mosquitto.log" >> /mosquitto/config/mosquitto.conf && \
#     echo "log_dest stdout" >> /mosquitto/config/mosquitto.conf

RUN touch /mosquitto/config/credentials && \
    chmod 0700 /mosquitto/config/credentials && \
    mosquitto_passwd -b /mosquitto/config/credentials mqtt 123456 > /mosquitto/config/credentials && \
    echo "persistence true" > /mosquitto/config/mosquitto.conf && \
    echo "persistence_location /mosquitto/data/" >> /mosquitto/config/mosquitto.conf && \
    echo "user mosquitto" >> /mosquitto/config/mosquitto.conf && \
    echo "listener 1883" >> /mosquitto/config/mosquitto.conf && \
    echo "allow_anonymous false" >> /mosquitto/config/mosquitto.conf && \
    echo "log_dest file /mosquitto/log/mosquitto.log" >> /mosquitto/config/mosquitto.conf && \
    echo "log_dest stdout" >> /mosquitto/config/mosquitto.conf && \
    echo "password_file /mosquitto/config/credentials" >> /mosquitto/config/mosquitto.conf



