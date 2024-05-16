

# Dockerfile pour un serveur web Apache avec un mini-projet web

Ce Dockerfile vous permet de créer une image Docker contenant un serveur web Apache avec un mini-projet web préconfiguré. Il utilise l'image de base Apache HTTP Server (httpd) et installe Git pour récupérer le mini-projet depuis un dépôt GitHub.

## Utilisation

1. Assurez-vous d'avoir Docker installé sur votre machine.

2. Créez un nouveau répertoire et placez le Dockerfile à l'intérieur.

3. Construisez l'image Docker en exécutant la commande suivante dans le répertoire où se trouve le Dockerfile :

```bash
docker build -t nom_image:tag .
```

Remplacez "nom_image" par le nom que vous souhaitez donner à votre image et "tag" par une étiquette de version.

4. Une fois la construction terminée, vous pouvez exécuter un conteneur à partir de l'image créée en utilisant la commande suivante :

```bash
docker run -p port_hôte:port_conteneur nom_image:tag
```

Remplacez "port_hôte" par le numéro de port de votre machine hôte que vous souhaitez mapper au port du conteneur Apache (généralement 80). Remplacez également "nom_image" et "tag" par le nom et l'étiquette de version que vous avez utilisés lors de la construction de l'image.

## Contenu du Dockerfile

- **FROM httpd**: Utilise l'image de base Apache HTTP Server (httpd).
- **RUN apt update && apt upgrade -y**: Met à jour les référentiels de paquets du système d'exploitation de l'image Docker et installe les mises à jour disponibles.
- **RUN DEBIAN_FRONTEND="noninteractive" apt-get -y install tzdata**: Installe le paquet tzdata pour gérer le fuseau horaire, en évitant toute interaction utilisateur pendant l'installation.
- **RUN apt-get install -y -q git apache2**: Installe Git et Apache HTTP Server dans l'image Docker.
- **ENTRYPOINT /usr/sbin/apache2ctl -D FOREGROUND**: Définit la commande qui sera exécutée lorsque le conteneur sera démarré, démarrant Apache en mode "foreground".
- **RUN mv /var/www/html/index.html /var/www/html/index.html.old**: Renomme le fichier index.html par défaut d'Apache en index.html.old.
- **RUN git clone https://github.com/archidote/get-ready-simple-countdown-html-css-js**: Clone le repository Git "get-ready-simple-countdown-html-css-js" depuis GitHub.
- **RUN cd get-ready-simple-countdown-html-css-js && cp * /var/www/html/**: Copie tous les fichiers du mini-projet web vers le répertoire de base d'Apache où les fichiers web sont servis.

---

Vous pouvez personnaliser ce README en fonction de vos besoins et des détails spécifiques de votre projet.