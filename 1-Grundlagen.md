# Grundlagen von Docker
Docker ist eine Plattform, die es Entwicklern ermöglicht, Anwendungen in Containern zu verpacken, zu verteilen und auszuführen. Container sind leichtgewichtige, eigenständige und ausführbare Softwarepakete, die alles enthalten, was zur Ausführung einer Anwendung erforderlich ist: Code, Laufzeit, Systemtools, Bibliotheken und Einstellungen.

## Wichtige Begriffe:

* Image: Eine schreibgeschützte Vorlage, die alle Anweisungen enthält, um einen Container zu erstellen.

* Container: Eine laufende Instanz eines Images. Container sind isoliert, aber teilen den Kernel des Host-Betriebssystems.

* Docker Hub: Ein öffentliches Repository, in dem Docker-Images gespeichert und geteilt werden können.

## Unterschied zwischen Dockerfile und docker-compose.yml

* Dockerfile: 
    * Eine Textdatei, die alle Anweisungen enthält, um ein Docker-Image zu erstellen.
    * Es enthält Befehle wie `FROM`, `RUN`, `COPY`, `CMD`, `EXPOSE`, `WORKDIR`, `ENV`, usw.
    * Wird verwendet, um ein benutzerdefiniertes Image zu erstellen.
    * Beispiel:

    ```dockerfile
    FROM alpine:3.14
    WORKDIR /app
    COPY . .
    RUN npm install
    CMD ["node", "app.js"]
    ```

* docker-compose.yml:
    * Eine YAML-Datei, die die Konfiguration für mehrere Container(Multi-Container) definiert und zu verwalten.
    * Es enthält Befehle wie `version`, `services`, `networks`, `volumes`, usw.
    * Ermöglicht das Starten mehrerer Container mit einem einzigen Befehl.
    * Beispiel:

    ```yaml
    # docker-compose.yml
version: '3'
services:
  web:
    image: my-web-app
    ports:
      - "80:80"
  db:
    image: mysql:5.7
    environment:
      MYSQL_ROOT_PASSWORD: example
        ports:
        - "3306:3306"
    ```

Ein Dockerfile beschreibt, wie ein einzelnes Docker-Image erstellt wird, während eine docker-compose.yml Datei verwendet wird, um mehrere Container zu konfigurieren und zu starten. Beide sind wichtige Bestandteile des Docker-Ökosystems und ermöglichen es Entwicklern, Anwendungen effizient zu verwalten und bereitzustellen.

## Wichtige befehle:
Hier sind einige der wichtigsten Docker-Befehle und was sie machen:

* `docker build`: Erstellt ein Docker-Image aus einem Dockerfile.
    ```docker build -t name-von-image .```

* `docker run`: Startet einen Container aus einem Image.
    ```docker run -d -p 80:80 name-von-image```

* `docker ps`: Zeigt alle laufenden Container an.
    ```docker ps``` oder ```docker ps -a```

* `docker exec`: Führt einen Befehl in einem laufenden Container aus.
    ```docker exec -it container-id bash``` oder ```docker exec -it container-id sh```

* `docker stop`: Stoppt einen laufenden Container.
    ```docker stop container-id``` oder ```docker stop $(docker ps -a -q)```

* `docker rm`: Entfernt einen oder mehrere Container.
    ```docker rm container-id``` oder ```docker rm $(docker ps -a -q)```

* `docker rmi`: Entfernt ein oder mehrere Images.
    ```docker rmi image-id``` oder ```docker rmi $(docker images -q)```

* `docker-compose up`: Startet alle Container in einem docker-compose.yml-Datei.
    ```docker-compose up -d``` oder ```docker-compose up --build```

* `docker-compose down`: Stoppt und entfernt alle Container in einem docker-compose.yml-Datei.
    ```docker-compose down``` oder ```docker-compose down -v```

Diese Befehle sind nur ein Auszug aus den vielen verfügbaren Docker-Befehlen. Sie sind jedoch einige der häufigsten und nützlichsten Befehle, die Entwickler bei der Arbeit mit Docker verwenden.

Docker Syntax hier: [Docker Syntax](./Docker-Syntax.md)