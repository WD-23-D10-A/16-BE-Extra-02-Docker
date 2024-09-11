# 16-BE-Extra-02-Docker

-   Docs: `docs`-Branch [hier.](https://github.com/WD-23-D10-A/16-BE-Extra-02-Docker/tree/docs)
-   Zum mitverfolgen: `final`-Branch [hier.](https://github.com/WD-23-D10-A/16-BE-Extra-02-Docker/tree/final)
-   React Docker: `react`-Branch [hier.](https://github.com/WD-23-D10-A/16-BE-Extra-02-Docker/tree/react)

## Warum Docker mit React nutzen?

* Isolierte Umgebung: Docker bietet eine komplett isolierte und reproduzierbare Umgebung, unabhängig von den Abhängigkeiten und Konfigurationen des Host-Systems. Dies bedeutet, dass die Anwendung in einer konsistenten Umgebung läuft, egal wo sie gehostet wird (lokal oder in der Cloud).

* Portabilität: Docker-Container können auf verschiedenen Plattformen (lokal, auf Servern oder in der Cloud) einfach deployed werden. Ein einmal erstelltes Image kann überall laufen, was die Flexibilität erhöht.

* Einfacher Build-Prozess: Mit Docker kannst du den gesamten Build-Prozess für deine React-App kapseln, sodass alle Abhängigkeiten und Konfigurationen an einem Ort verwaltet werden. Dies vermeidet Probleme wie "es funktioniert auf meinem Computer" (funktioniert aber nicht auf dem Server).

* Optimierte Produktionsumgebung: Im zweiten Teil des Dockerfiles wird ein Nginx-Webserver verwendet, um die statischen Dateien zu hosten. Dies ist optimal für Produktions-Deployments, da Nginx sehr effizient im Umgang mit statischen Dateien ist und zusätzlich als Reverse Proxy verwendet werden kann.

* Skalierbarkeit: Docker-Container sind leicht skalierbar. Du kannst leicht mehrere Instanzen deiner React-App in verschiedenen Containern laufen lassen, um den Traffic zu bewältigen, indem du Load Balancing verwendest.

* Einfaches Deployment: Mit Docker kann das Deployment von React-Apps vereinfacht werden. Entwickler müssen lediglich das Docker-Image auf den Produktionsserver hochladen und ausführen, ohne sich um Abhängigkeiten, Konfigurationen oder unterschiedliche Systemumgebungen zu kümmern.

## Erstelle eine Dockerfile für die React-App

```Dockerfile

# Verwende das offizielle Node.js-Image als Basis-Image
FROM node:14

# Setze das Arbeitsverzeichnis innerhalb des Containers
WORKDIR /app

# Kopiere package.json und package-lock.json ins Arbeitsverzeichnis
COPY package*.json ./

# Installiere die Abhängigkeiten
RUN npm install

# Kopiere den Rest des Anwendungscodes ins Arbeitsverzeichnis
COPY . .

# Baue die App für die Produktion
RUN npm run build

# Verwende einen leichten Webserver, um die statischen Dateien zu servieren
FROM nginx:alpine

# Kopiere die erstellte React-App in den Nginx-Container
COPY --from=0 /app/build /usr/share/nginx/html

# Exponiere den Port 80
EXPOSE 80

# Starte den Nginx-Server
CMD ["nginx", "-g", "daemon off;"]

```

```bash
docker build -t simple-react-app .
```

```bash
docker run -p 8080:80 simple-react-app
```

## Docker für backend und frontend gleichzeitig

Es ist möglich, sowohl das Backend als auch das Frontend gleichzeitig mit Docker zu starten, ohne eines der beiden manuell zuerst zu starten. Dies lässt sich durch die Verwendung von Docker Compose erreichen. Docker Compose ermöglicht es dir, mehrere Docker-Container gleichzeitig zu orchestrieren und ihre Dienste zusammen zu starten.

## Ordnerstruktur

```plaintext
root
│
├── backend
│   ├── Dockerfile
│   ├── package.json
│   └── (weitere Backend Dateien und Ordner)
│
├── frontend
│   ├── Dockerfile
│   ├── package.json
│   └── (weitere Frontend Dateien und Ordner)
│
└── docker-compose.yml
```

1. Erstelle Dockerfile für das Backend und das Frontend(beispiele habt Ihr schon)

2. Erstelle eine `docker-compose.yml`-Datei, um beide Container zu definieren und zu starten

```yml
version: '3'
services:
  backend:
    build:
      context: ./backend
    ports:
      - "5000:5000"
    volumes:
      - ./backend:/app
    environment:
      - NODE_ENV=development
      - PORT=5000

  frontend:
    build:
      context: ./frontend
    ports:
      - "3000:80"
    volumes:
      - ./frontend:/app
    environment:
      - NODE_ENV=production
```

3. Beide Services gleichzeitig starten

Du kannst nun Docker Compose verwenden, um sowohl das Backend als auch das Frontend gleichzeitig zu starten. Navigiere zum Stammverzeichnis, in dem sich die docker-compose.yml befindet, und führe folgenden Befehl aus:

```bash
docker-compose up --build
```

4. Zugriff auf die Anwendungen

* Frontend: Du kannst deine React-Anwendung nun unter http://localhost:3000 erreichen.

* Backend: Das Backend läuft unter http://localhost:5000.