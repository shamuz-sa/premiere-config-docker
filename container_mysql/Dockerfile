# Utiliser l'image MySQL officielle depuis Docker Hub
FROM mysql:latest

# Définir les variables d'environnement pour le mot de passe root MySQL
ENV MYSQL_ROOT_PASSWORD=password

# Créer un répertoire pour stocker des scripts SQL personnalisés
ENV MYSQL_INITDB_CUSTOM_SCRIPTS_DIR=/docker-entrypoint-initdb.d

# Copier les scripts SQL personnalisés dans le répertoire d'initialisation de la base de données
COPY ./ $MYSQL_INITDB_CUSTOM_SCRIPTS_DIR

