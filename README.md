# Modul 300 LB3
Weiterbildung Modul 300 LB3

##Dokumentation

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
