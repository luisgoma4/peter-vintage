# Seguridad: revisión del 2026-10-31

Contexto: revisión de seguridad de todos los repos tras el «octubre negro» (la IA abarata el ataque: se asume que todo repo, endpoint y clave se escanea en minutos). Este documento recoge lo aplicado a este repo y lo que queda pendiente; el estado vive en `docs/`, no en la conversación.

> Repo **público**: los pendientes se describen por categoría y acción, sin detalles explotables.

## Cambios aplicados

Ninguno en esta tanda.

## Pendientes

- [ ] **Baja** · Ficheros de trabajo de copy en la raíz (PV-02): Mover los ficheros de trabajo fuera del repo público y comprobar que las reseñas son reales y citables.
- [ ] **Info** · `package-lock.json` (PV-03): Regenerar el lockfile (el `npm audit` falló por lockfile inválido) y auditar; riesgo bajo, solo herramienta de build.
- [ ] **Baja** · `.gitignore` (E-28): Añadir regla `.env*`.
- [ ] **Info** · Metadatos de commit (E-03): Email `noreply` de GitHub en commits futuros.

## Reglas nuevas para agentes de este repo

- .gitignore base: `.env*`, `*.pem`, `*.key`, `*.sqlite*`, `*.db`, `.wrangler/`, y `*.xlsx`/`*.docx`/`*.pdf` en repos con material de cliente. Ejecutar `gitleaks detect --log-opts=--all` antes de hacer público un repo.
- En repos públicos, commits con el email `noreply` de GitHub.
- Dependabot (npm y github-actions) y alertas de seguridad activas, incluso en repos estáticos.
- Sitio estático sin terceros: mantenerlo así; si se añade un formulario o script externo, CSP y SRI desde el primer día.
