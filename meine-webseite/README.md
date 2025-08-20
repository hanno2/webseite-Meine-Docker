# React + Vite

This template provides a minimal setup to get React working in Vite with HMR and some ESLint rules.

Currently, two official plugins are available:

- [@vitejs/plugin-react](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react) uses [Babel](https://babeljs.io/) for Fast Refresh
- [@vitejs/plugin-react-swc](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react-swc) uses [SWC](https://swc.rs/) for Fast Refresh

## Expanding the ESLint configuration

If you are developing a production application, we recommend using TypeScript with type-aware lint rules enabled. Check out the [TS template](https://github.com/vitejs/vite/tree/main/packages/create-vite/template-react-ts) for information on how to integrate TypeScript and [`typescript-eslint`](https://typescript-eslint.io) in your project.

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
