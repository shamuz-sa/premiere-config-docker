# Utilisation de l'image MySQL officielle
FROM mysql

# Définition du mot de passe root pour MySQL
ENV MYSQL_ROOT_PASSWORD mon_mot_de_passe

# Utilisation de l'image phpMyAdmin officielle
FROM phpmyadmin/phpmyadmin

# Configuration de phpMyAdmin pour se connecter à la base de données MySQL
ENV PMA_HOST db
ENV PMA_USER root
ENV PMA_PASSWORD mon_mot_de_passe

# Exposition du port 8080 pour phpMyAdmin
EXPOSE 8080
