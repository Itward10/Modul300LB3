# Modul 300 LB3
Weiterbildung Modul 300 LB3

## Dokumentation

Zuerst installierten wir eine Virtuelle Ubuntu Maschine auf unser Notebook und Muriel Rüegg entschied sich sogar ein Duallbootsystem zu benutzen. 
Da es eine neue Maschine war Installieren wir die update und upgrades:
```
apt-get update
apt-get upgrade 
```
Nachdem versuchten wir uns ein überblick zu machen über alle Docker Bespiele

Wir installierten zum Start das DOCKER.io
```
sudo apt-get install -y docker.io 
``` 
Wir fingen zuerst mit einem ganz einfachen Beispiel

Wir erstellen ein File namens Dockerfile, in diesem gaben wir den folgenden script an:

```
From Ubuntu       #hohlt sich das Packet Ubuntu

MAINTAINER Sarah Schmid

RUN apt-get update

CMD ["echo", "Hello World...! from my first docker image"]
``` 
From Ubuntu hohlt sich das packet von: <https://hub.docker.com/_/ubuntu> 

Danach bauten wir den Docker:
``` 
sudo docker build -t myimage .
``` 
Um danach das Dockerfile laufen zu lassen:
```
sudo docker run myimage
```
### Projekt umsetztung:

Zuerst planten wir unser Porjekt. Wir erstellten im Visio ein Netwerkplan in dem wir unsere Ideen visualisierten. 
Die meisten konzepten waren sehr gross gedacht.

![image](https://user-images.githubusercontent.com/89509863/135975697-5852ef07-3f06-4044-9cf7-6fa410b55bd6.png)

Danach erstellten wir mit den zwei Vorlagen, zwei Container:
```
Modul 300 Lb3


#SQL Server
FROM Ubuntu

Maintainer Sarah Schmid und Muriel Ruegg <schmidsarah21@gmail.com>

RUN apt-get update

#root Passwort setzen
RUN echo 'mysql-server mysql-server/root_password password Start123$' | debconf>
RUN echo 'mysql-server mysql-server/root_password_again password Start123$' | d>

#Installation
apt-get install -y mysql-server

# mysql config - oeffnung von jedem Port
RUN sed -i -e"s/^bind-address\s*127.0.0.1/bind-address = 0.0.0.0/" /etc/mysql/m>

Expose 3306

Volume /var/lib/mysql

CMD ["mysqld"]

#Apache Server
FROM Ubuntu
Maintainer Sarah Schmid und Muriel Ruegg <schmidsarah21@gmail.com>

RUN apt-get update
RUN apt-get -q -y install apache2 

# Konfiguration Apache
ENV APACHE_RUN_USER www-data
ENV APACHE_RUN_GROUP www-data
ENV APACHE_LOG_DIR /var/log/apache2

RUN mkdir -p /var/lock/apache2 /var/run/apache2

EXPOSE 80

VOLUME /var/www/html

CMD /bin/bash -c "source /etc/apache2/envvars && exec /usr/sbin/apache2 -DFOREGROUND"
``` 
Auf einmal merkten wir das wir keine Docker berechtigt wurden. 
```
sudo usermod -a -G docker $USER
```
Wir versuchten viele Sachen aus. Es war ein Kampf und danach versuchten wir eine Anleitung, aber wir bekamen die ganze Zeit eine Fehlermeldung:
```
ERROR: Couldn't connect to Docker daemon at http+docker://localhost - is it running?

If it's at a non-standard location, specify the URL with the DOCKER_HOST environment variable.
``` 

Danach versuchte ich diese Anleitung: <https://techoverflow.net/2019/03/16/how-to-fix-error-couldnt-connect-to-docker-daemon-at-httpdocker-localhost-is-it-running/>

Nachdem ich alle Schritte genau befolgt habe, bekam ich die genau gleiche Fehlermeldung. Dies machte uns stutzig und suchten nach der Fehlermeldung.
Es kam den Lösungsvorschlag mit der Berechtigung und neustarten des Docker Dienst.

Als es nach grossen hin und her. Auf einmal versuchten wir es mit dem command

``` sudo docker-compose up -d ``` 

Dazu erstellten wir auch den neuen Plan

![image](https://user-images.githubusercontent.com/89509863/136079390-b3ff5032-a34e-4c7d-8d49-1ac52835f0d0.png)

