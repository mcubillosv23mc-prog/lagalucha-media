# Plan Auto Eléctrico

Proyecto para cambiar el Peugeot 301 diésel por un auto eléctrico. Incluye una app Android (Plan Auto).

## Fuente de verdad
- `docs/ESTADO_PROYECTO.md` es la **fuente de verdad compartida** entre la sesión principal y todos los subagentes. Léelo antes de trabajar.
- Cada frente tiene su bloque (`### Frente: …`, entre `<!-- INICIO:x -->` y `<!-- FIN:x -->`). Cada subagente edita **solo su bloque** usando Edit, nunca Write.
- Los subagentes anotan sus avances en "Notas para el log" de su bloque. La sesión principal los pasa al "Registro de avances".
- Las "Decisiones tomadas" no se vuelven a discutir sin que el usuario lo pida.

## Subagentes (`.claude/agents/`)
finanzas-planner (sonnet) · app-developer (sonnet) · datos-extractor (haiku) · ev-researcher (haiku) · rutas-energia (haiku). Cada uno responde con 5–7 viñetas como máximo.

## Privacidad
En el repo no van montos personales exactos, RUT, números de cuenta ni nombres de terceros. Los datos exactos van solo en `datos.json`, que no se versiona.

## App
- Web: `app/web/index.html` (un solo archivo).
- Android: `app/android/`.
- El APK lo compila `.github/workflows/plan-auto-apk.yml` (en la raíz del repo) y lo publica en el release `plan-auto-latest`.
- Responde al usuario en español de Chile, sin tecnicismos.
