
# Docker und Docker Compose in Ubuntu


##  Quellen:

https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-20-04-de
	
---

### Docker auf Ubuntu installieren

	sudo apt update
	
	sudo apt install apt-transport-https ca-certificates curl software-properties-common
	
	curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
	
	sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable"
	
	sudo apt update
	
	apt-cache policy docker-ce
	
	sudo apt install docker-ce
	
	sudo systemctl status docker
	
---
		
### Docker auf ArchLinux installieren
	
	sudo pacman -Syyu docker
	
---
	
### Docker starten	
	
	docker --version

	sudo systemctl start docker

	sudo systemctl enable docker

	sudo systemctl status docker
	
---	
	
### Docker-Compose installieren

	wget https://github.com/docker/compose/releases/latest/download/docker-compose-$(uname -s)-$(uname -m)
	
	sudo mv docker-compose-$(uname -s)-$(uname -m) /usr/local/bin/docker-compose

	sudo chmod -v +x /usr/local/bin/docker-compose
	
	docker-compose version
	
	sudo docker info
	
---	
	
### Image Busybox installieren

	sudo docker pull busybox
	
	sudo docker images
	
	sudo docker run busybox "Hallo Welt"
	
	sudo docker ps -a #(zeigt alle Container)
	
	sudo docker rm + ContainerID #(löscht)
	
---	
	
### Befehle im Container ausführen

	sudo docker run -it busybox sh #(in busybox daten bearbeiten)
	
	exit
	
---
	
### Webapp mit Nginx

	sudo docker pull nginx
	
	sudo docker run nginx
	
	sudo docker run -p 5000:80 nginx
	
	Webbrowser: http://localhost:5000/
	
----	

### Container starten stoppen bearbeiten und mit der Shell an anderen Sachen rumfrickeln

	Detached Mode 	
	
		sudo docker run -p 5000:80 nginx #(Detached Mode)
	
		sudo docker exec -ti #(Container Nummer) bash (Zugriff für Veränderungen)
		
		exit
	
	Atached Mode (logs)

		sudo docker run -p 5000:80 -d -ti nginx

		sudo docker attach #(Container Nummer)
		
		strg p strg p #(exit mode)
	
---	
	
### Nginx Daten übergeben (Ordner mit Index.html erstellen und in den Terminal ziehen. Ordner verknüpfen)

	sudo docker run -p 5000:80 -d -v '/home/schoeppach/NGINX':/usr/share/nginx/html nginx
	
	http://localhost:5000/ #(Test der Website)
	
---
	
### Container stoppen loeschen von Images und Containern

	Container
	
		sudo docker ps #(Uebersicht)
	
		sudo docker stop "Container ID"
	
		sudo docker rm "Container ID"
		
	Images
	
		sudo docker image ls
		
		sudo docker container prune #(loescht alle inaktiven Container)
		
		sudo docker image rm "Container ID" #(oder Name)
		
		sudo docker image prune #(alle inaktiven loeschen)
	
		sudo docker image rm "Image ID" #(oder Name)
		
---
		
### Container automaisch starten (always, on-failure, no, unless-stopped

	sudo systemctl stop docker #(erstmal stoppen)
	
	sudo docker run -p 5000:80 -dit --restart unless-stopped -v '/home/schoeppach/NGINX':/usr/share/nginx/html nginx
  
  
  
