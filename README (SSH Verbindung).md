# SSH Konfigurieren:

### ssh install:
    sudo apt install openssh-server
    sudo systemctl status sshd


### firewall:
    which ufw/usr/sbin/ufw

    sudo ufw allow ssh
    sudo ufw allow http
    sudo ufw allow https

    sudo ufw enable
    sudo ufw status numbered


### ip addr:
    Ubuntu host	10.50.101.28
    Ubuntu server	10.50.101.62


### ssh server verbinden:
    ssh maxsimal@10.50.101.62
    exit

### neuen user anlegen server:
    sudo adduser admin
    sudo usermod -aG sudo admin
    su - admin (einlogen als admin)
    sudo chage --lastday 0 admin (eigenes Password vergeben 123)
    sudo passwd admin (passwort ändern)


### benutzer auf andres server löschen:
    sudo killall -u andre
    sudo deluser andre


### private puplic key erstellen:
    ssh-keygen
    ls -lah .ssh ( speicherort überprüfen)


### private puplic key per ssh kopieren:
    tldr ssh-copy-id
    ssh-copy-id admin@10.50.101.62
