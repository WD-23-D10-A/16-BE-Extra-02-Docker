# Syntax in Dockerfile und docker-compose.yml

## Dockerfile:

Ein ```Dockerfile``` enthält Anweisungen, um ein Docker-Image zu erstellen. Hier sind einige der wichtigsten Anweisungen:

* `FROM`: Definiert das Basisimage, auf dem das benutzerdefinierte Image basiert.
    ```dockerfile
    FROM alpine:3.14
    ```
* `WORKDIR`: Setzt das Arbeitsverzeichnis für alle folgenden Anweisungen im Dockerfile.
    ```dockerfile
    WORKDIR /app
    ```
* `COPY`: Kopiert Dateien vom Host in den Container.
    ```dockerfile
    COPY . .
    ```
* `RUN`: Führt Befehle im Container aus.
    ```dockerfile
    RUN npm install
    ```
* `CMD`: Definiert den Standardbefehl, der ausgeführt wird, wenn der Container gestartet wird.
    ```dockerfile
    CMD ["node", "app.js"]
    ```
* `EXPOSE`: Legt den Port fest, auf dem der Container lauscht.
    ```dockerfile
    EXPOSE 3000
    ```
* `ENV`: Setzt Umgebungsvariablen im Container.
    ```dockerfile
    ENV NODE_ENV=production
    ```
* `VOLUME`: Erstellt ein Volumen im Container.
    ```dockerfile
    VOLUME /data
    ```
* `ENTRYPOINT`: Definiert den Befehl, der ausgeführt wird, wenn der Container gestartet wird.
    ```dockerfile
    ENTRYPOINT ["node", "app.js"]
    ```

## docker-compose.yml:

Eine ```docker-compose.yml``` Datei definiert und startet Multi-Container Docker-Anwendungen. Hier sind einige der wichtigsten Anweisungen:

* `version`: Definiert die Version der docker-compose-Syntax.
    ```yaml
    version: '3'
    ```
* `services`: Definiert die Container und ihre Konfigurationen.
    ```yaml
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
    
* image: Definiert das Basisimage für den Container.
    ```yaml
    image: my-web-app
    ```

* `networks`: Definiert Netzwerke für die Containerkommunikation.
    ```yaml
    networks:
      app-network:
        driver: bridge
    ```
* `volumes`: Definiert Volumes für die Datenpersistenz.
    ```yaml
    volumes:
      data-volume:
    ```
* `depends_on`: Definiert die Reihenfolge, in der Container gestartet werden.
    ```yaml
    depends_on:
      - db
    ```
* `environment`: Setzt Umgebungsvariablen für die Container.
    ```yaml
    environment:
      NODE_ENV: production
    ```
* `restart`: Definiert das Neustartverhalten für den Container.
    ```yaml
    restart: always
    ```
* `build`: Definiert den Build-Kontext für den Container.
    ```yaml
    build: .
    ```
* `command`: Definiert den Befehl, der beim Starten des Containers ausgeführt wird.
    ```yaml
    command: npm start
    ```
* `ports`: Definiert die Ports, die für den Container freigegeben werden.
    ```yaml
    ports:
      - "3000:3000"
    ```
* `volumes`: Definiert Volumes für die Datenpersistenz.
    ```yaml
    volumes:
      - data-volume:/data
    ```
* `links`: Definiert Verknüpfungen zwischen Containern.
    ```yaml
    links:
      - db
    ```
* `expose`: Legt Ports fest, die für andere Container sichtbar sind.
    ```yaml
    expose:
      - "3000"
    ```
* `external_links`: Definiert externe Verknüpfungen zu anderen Containern.
    ```yaml
    external_links:
      - db
    ```
* `logging`: Definiert das Logging-Verhalten für den Container.
    ```yaml
    logging:
      driver: syslog
    ```

Dockerfile und docker-compose.yml sind wichtige Bestandteile des Docker-Ökosystems und ermöglichen es Entwicklern, Anwendungen effizient zu verwalten und bereitzustellen. Durch die Verwendung dieser Syntax können Entwickler Docker-Container erstellen, konfigurieren und starten, um Anwendungen in verschiedenen Umgebungen auszuführen.