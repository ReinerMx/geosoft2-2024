# Containerisierung mit Docker
Autoren: [@Lukas Ahlert](https://github.com/LukasAhl) und [@Maximilian Reiner](https://github.com/ReinerMx)


## 1. Was ist Containerisierung? 

- **Definition**: 
  - Containerisierung ist eine leichte Form der Virtualisierung, bei der eine Anwendung und ihre Abhängigkeiten in einen Container gepackt werden.
  - Diese Container können konsistent in verschiedenen Umgebungen laufen.
  
- **Wesentliche Merkmale**:
  - **Isolierte Umgebung**: Jeder Container läuft in einer isolierten Umgebung mit eigenem Dateisystem, Prozessen und Netzwerk-Stack.
  - **Leichtgewichtig**: Container teilen sich den Kernel des Host-Betriebssystems, was sie effizienter als virtuelle Maschinen (VMs) macht.

- **Analogie**: 
  - Vergleiche die Containerisierung mit "Schiffscontainern" in der Logistik – standardisierte, portable Einheiten, die überall hin transportiert werden können, unabhängig davon, was sich darin befindet.

---

## 2. Warum ist Containerisierung wichtig? 

- **Konsistenz zwischen Umgebungen**: 
  - Container stellen sicher, dass dieselbe Anwendung in Entwicklungs-, Test- und Produktionsumgebungen ohne das Problem "Es funktioniert auf meinem Rechner" läuft.

- **Vorteile**:
  - **Portabilität**: Container können auf mehreren Plattformen (z. B. lokal, Cloud) betrieben werden.
  - **Skalierbarkeit**: Containerisierte Anwendungen können einfach über Cluster skaliert werden.
  - **Effizienz**: Effizienter als VMs, da Container sich den Betriebssystem-Kernel teilen.
  - **Geschwindigkeit**: Schnellere Start- und Herunterfahrzeiten im Vergleich zu VMs.

- **Echte Anwendungen**:
  - Von Unternehmen in Bereichen wie Microservices-Architekturen, cloud-nativen Anwendungen und CI/CD-Pipelines übernommen.

---

## 3. Wann sollte man Containerisierung einsetzen (oder nicht)?

- **Geeignete Anwendungsfälle**:
  - **Microservices**: Aufteilen großer Anwendungen in unabhängige Dienste.
  - **CI/CD-Pipelines**: Automatisierte Tests und Deployments in verschiedenen Umgebungen.
  - **Entwicklungsumgebungen**: Einheitliche Entwicklungs- und Produktionsumgebungen schaffen.

- **Wann Containerisierung weniger sinnvoll ist**:
  - **Komplexe monolithische Anwendungen**: Wenn spezifische Hardware oder Umgebungskonfigurationen notwendig sind.
  - **Ressourcenintensive Anwendungen**: Anwendungen, die strikte Kontrolle über CPU und RAM benötigen, könnten von Containerisierung beeinträchtigt werden.
  - **Altsysteme**: Ältere Systeme, die schwer in Container zu migrieren sind.


## 4. Einführung in Docker 

- **Was ist Docker?**:
  - Docker ist eine Open-Source-Plattform, die die Bereitstellung, Skalierung und Verwaltung von Anwendungen in Containern automatisiert.
  
- **Docker-Komponenten**:
  - **Docker Engine**: Kernkomponente zum Ausführen von Containern.
  - **Docker Hub**: Ein Register für Docker-Images.
  - **Docker Compose**: Tool zum Definieren und Ausführen von Multi-Container-Anwendungen.

- **Wie Docker die Entwicklung verändert hat**:
  - Vereinfachte die Erstellung und Verwaltung von Containern.
  - Bietet einen Standard für Containerisierung.

- **Wichtige Begriffe**:
  - Dockerfile: <br>
    - Textdatei mit Anweisungen zur Erstellung des Docker-Images <br>
    - “Rezept” für den Container
  - Image: <br>
     - “Blaupause” eines Containers, der aus Dockerfile gebaut wird <br>
     - Enthält alle notwendigen Dateien und Abhängigkeiten (Betriebssystem, Programmbibliotheken, Anwendungscode, etc.) <br>
     - Grundlage für weitere Containerstarts
  - Volumes: Persistente Speicherung von Daten unabhängig von Containern
 
---

## 5. Wie containerisiert man eine Anwendung mit Docker? 

### Schritte zur Containerisierung einer einfachen Anwendung:

1. **Schritt 1**: Docker installieren  
   - Stelle sicher, dass Docker auf deinem Rechner installiert ist.

2. **Schritt 2**: Erstellen einer `Dockerfile`  
   - Eine `Dockerfile` ist eine Textdatei, die Anweisungen für den Bau des Docker-Images enthält.
   - Beispiel für eine Node.js-Anwendung:
     ```dockerfile
     # Schritt 1: Basis-Image
     FROM node:14

     # Schritt 2: Arbeitsverzeichnis festlegen
     WORKDIR /usr/src/app

     # Schritt 3: Anwendungscode kopieren
     COPY . .

     # Schritt 4: Abhängigkeiten installieren
     RUN npm install

     # Schritt 5: Anwendung starten
     CMD ["node", "app.js"]

     # Schritt 6: Port freigeben
     EXPOSE 3000
     ```

3. **Schritt 3**: Docker-Image bauen  
   - Befehl: `docker build -t my-app .`

4. **Schritt 4**: Container starten  
   - Befehl: `docker run -p 3000:3000 my-app`

5. **Schritt 5**: Volumes einbinden, um Daten persistent zu speichern (optiional)  
   - Beispiel-Befehl für eine MongoDB: `docker run -v /mein/host/pfad:/data/db --name mongo-container mongo`

6. **Schritt 6**: In Docker Hub hochladen (optional)
   - Befehl: `docker push benutzername/app-name`

---

## 6. Zusammenfassung & Fazit 

- **Wichtige Erkenntnisse**:
  - Containerisierung macht Anwendungen portabel, skalierbar und effizient.
  - Docker vereinfacht die Erstellung und Verwaltung von Containern.
  - Nutze Docker, wenn du skalierbare und portable Anwendungen baust, aber beachte auch die Grenzen.

- **Abschließende Bemerkung**: 
  - Containerisierung ist ein entscheidender Teil der modernen Softwareentwicklung und -bereitstellung, und Docker hat sich als das Standard-Tool dafür etabliert.


---
## 7. Quellen

- [Docker-Dokumentation](https://docs.docker.com/)
- [Docker-Logos](https://www.docker.com/company/newsroom/media-resources/)
- [Kubernetes und Container-Orchestrierung](https://kubernetes.io/)
- [RedHat](https://www.redhat.com/de/topics/cloud-native-apps/what-is-containerization)
- [OPC Router](https://www.opc-router.de/was-ist-docker/)
