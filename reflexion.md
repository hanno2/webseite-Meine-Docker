# Reflexion

## Multi-Stage Build

**Vorteil:** Trennung von Build und Runtime → kleineres, sicheres Image.

**node_modules:** Wird nur im Build verwendet, nicht ins finale Image übernommen.

**Caching:** COPY package\*.json ermöglicht Wiederverwendung der Layer bei unveränderten Abhängigkeiten.

## 🌐 Webserver & Anwendung

**Finales Image:** Enthält nur statische Dateien (dist), kein Quellcode.

**Nginx:** Liefert die Dateien aus, kann für SPAs mit Fallback konfiguriert werden.

**Kein npm run dev:** Das ist nur für lokale Entwicklung gedacht.

## 📦 Containerisierung & Betrieb

**Vorteile:**

- **Portabilität:** Läuft überall gleich.
- **Isolation:** Keine Abhängigkeit vom Host-System.
- **Reproduzierbarkeit:** Dockerfile ist wie ein Rezept.

**HEALTHCHECK:** Prüft, ob die App erreichbar ist → wichtig für automatische Neustarts oder Load Balancing.

## 📁 .gitignore vs. .dockerignore

**.gitignore:** beeinflusst, was in Git gespeichert wird.

**.dockerignore:** beeinflusst, was in den Docker-Build gelangt.
