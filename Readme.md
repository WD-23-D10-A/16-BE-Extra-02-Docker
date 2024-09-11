# 16-BE-Extra-02-Docker

-   Docs: `docs`-Branch [hier.](https://github.com/WD-23-D10-A/16-BE-Extra-02-Docker/tree/docs)
-   Zum mitverfolgen: `final`-Branch [hier.](https://github.com/WD-23-D10-A/16-BE-Extra-02-Docker/tree/final)
-   React Docker: `react`-Branch [hier.](https://github.com/WD-23-D10-A/16-BE-Extra-02-Docker/tree/react)

# Was ist Docker?

Docker ist eine Plattform, die es ermöglicht, die Bereitstellung, Skalierung und Verwaltung von Anwendungen mithilfe von Containerisierung zu automatisieren. Ein Container verpackt die Anwendung und ihre Abhängigkeiten zusammen, was es einfacher macht, sie in verschiedenen Umgebungen auszuführen, ohne sich über Kompatibilitätsprobleme Gedanken machen zu müssen. Im Gegensatz zu virtuellen Maschinen teilen Container den Kernel des Hostsystems, was sie leichtgewichtig und schneller startbar macht.

## Warum sollten wir Docker verwenden?

1. Konsistenz über Umgebungen hinweg: Docker stellt sicher, dass Ihre Anwendung in jeder Umgebung (Entwicklung, Staging, Produktion) gleich läuft. Sie müssen sich keine Sorgen mehr über "Es funktioniert auf meinem Rechner!"-Probleme machen.

1. Isolierung: Docker isoliert Anwendungen, das heißt, jeder Container läuft unabhängig mit seinem eigenen Satz von Abhängigkeiten. Dies verringert das Risiko von Versionskonflikten zwischen Bibliotheken.

1. Portabilität: Da Container die gesamte Laufzeitumgebung (Anwendung, Abhängigkeiten, Konfigurationen) kapseln, können Sie sie problemlos zwischen verschiedenen Umgebungen verschieben oder mit anderen teilen.

1. Skalierbarkeit: Docker erleichtert das Skalieren von Anwendungen, insbesondere in Cloud-Umgebungen wie AWS oder Kubernetes.

1. Effizienz: Container sind im Vergleich zu traditionellen virtuellen Maschinen leichtgewichtig, da sie den Kernel des Host-Betriebssystems gemeinsam nutzen, was zu schnelleren Startzeiten und geringerem Overhead führt.

Docker Grundlagen hier: [Grundlagen von Docker](./Grundlagen.md)

Docker Syntax hier: [Docker Syntax](./Docker-Syntax.md)