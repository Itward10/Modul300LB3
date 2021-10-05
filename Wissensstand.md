# Persönlicher Wissenstand

## Linux

Wir konnten die Basic Befehle wiederhohlen:

Command | Bedeutung 
------- | ----------
cd      | Inhaltsverzeichnis wechseln
dir/ls  | Anzeigen was im Verzeichnis ist
sudo    | Als administrator ausführen
usermod -a -G docker $USER | User zur Sicherheits Gruppe docker hinzufügen
apt-get update/ apt-get upgrade | updated die Programme auf den aktuellsten Stand
touch | File erstellen

## Docker

Docker ist eine Freie Software, dies Bedeutet, dass jeder es gratis benutzen und bearbeiten kann. Bei diesem kann man Containervirtualisierung zu Isolierung von Anwendungen kreiren.

### Docker Befehle

Command | Bedeutung
-------| -----------
apt-get install -y docker.io | Installiert das docker.io
docker build -t "name" . | Den Container aufbauen, die Datei nehmen in dem Verzeichnis
docker run myimage | Den Container starten
docker kill "name" | stopt den Container prozess
docker stats | Zeigt die CPU Leistung an
docker system prune | löscht alle Container
docker container ls -a | Listet alle Container auf

### Wie ertellt man ein Dockerfile

Zuerst erstellt man file namens Dockerfile ohne Endung.
``` From Ubuntu ```
Man sucht sich das Image aus vom Docker Hub

![image](https://user-images.githubusercontent.com/89509863/136073807-1c5d0b6c-8e4d-4796-940c-7b3363121811.png)

Man könnte auch im Terminal ein Docker erstellen mit dem Befehl ``` docker pull ubuntu ```

Danach gibt man den "Maintainer" an ``` Maintainer Sarah Schmid und Muriel Ruegg <beispiel@mail.ch> ```

```RUN``` kann man Befehle ausführen wie beispielweise: ``` RUN apt-get update ``` 

``` CMD ["echo", "Hello World...! from my first docker image"] ``` Im Terminal eine Eingabe machen

``` sudo docker build -t myimage .``` stellt den Docker her mit dem Namen "myimage" und danach kann man den Pfad eingeben, aber wenn man schon richtigen Pfad ist, kann man einfach einen Punkt setzen.


