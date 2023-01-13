# Nginx or Apache2 Installieren:

### Pakete Update Nginx Installation:

    sudo apt update
    
    sudo apt install nginx
    
    sudo apt install apache2


### Firewall anpassen: 

    sudo ufw app list
    
    sudo ufw allow 'Nginx HTTP'
    
    sudo ufw allow 'Apache'
    
    sudo ufw status

### Webserver testen:
    sudo systemctl status nginx
    sudo systemctl status apache2

    ip a (ip herausfinden)
    hostname -I
    ip im Browser eingeben

### Index HTML anpassen:
    /var/www als root öffen Index bearbeiten

### Apache verwalten:
    sudo systemctl stop apache2
    sudo systemctl start apache2

    sudo systemctl restart apache2
    sudo systemctl reload apache2

    sudo systemctl disable apache2
    sudo systemctl enable apache2

### deinstallieren:
    Nginx
    sudo apt purge nginx nginx-common nginx-core
    
    Apache2
    sudo apt-get autoremove apache2
