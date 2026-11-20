# Estado del Proyecto: Plan Auto Eléctrico

> **Fuente de verdad compartida** entre la sesión principal y todos los subagentes.
> Lee el archivo completo antes de trabajar. Edita **solo tu bloque**, entre sus marcas `INICIO`/`FIN`, y usa siempre Edit, nunca Write.
> Aquí no van montos personales exactos. Los datos exactos viven en `datos.json`, en el teléfono del usuario o en el scratchpad, y nunca se suben al repo.

## 1. Objetivo general
Cambiar el Peugeot 301 diésel 2021 por un auto eléctrico sin desordenar las finanzas, y mantener una app Android (APK) donde el usuario ingresa sus datos y ve si el cambio es factible y cuándo.

## 2. Decisiones tomadas (no se vuelven a discutir)
- Primero se terminan las tarjetas y después se cambia el auto. **Fecha objetivo: marzo–abril de 2027.**
- **No tomar** el crédito de consumo de Falabella (~$22M) ni el Súper Avance de la CMR (~$22M).
- La CMR se usa solo para emergencias hasta su última cuota (marzo de 2027). Cada compra nueva en cuotas atrasa la fecha.
- La tarjeta Cencosud la paga un colega. **No es gasto del usuario.** Termina en nov 2026 y no se vuelve a prestar. Lo ideal es cerrarla o bajarle el cupo.
- Presupuesto para el eléctrico: **$12–15M**, con el 301 como pie (~$7M, por confirmar).
- Autonomía real **≥ 300 km**, porque recorre ~185–200 km por día de trabajo. Cargará en casa.
- Candidato preferido: **BYD Dolphin usado 2024–2025**, con informe de batería (SOH) **> 90%**. Descartado: Nissan Leaf antiguo.
- El aporte de la otra persona del hogar es el **50% de los gastos de la casa**. En la app se marcan los gastos "Casa".
- App: un HTML local dentro de un WebView Android. El APK lo compila GitHub Actions. Rutas con OpenStreetMap/OSRM (sin API key), enlaces a Google Maps e importación de la cronología de Google Maps.
- Proyecto aislado en la carpeta `plan-auto/`. Lo ideal es moverlo a su propio repo privado.

## 3. Resumen financiero (cifras redondeadas)
| Concepto | Mensual aprox. |
|---|---|
| Ingresos (sueldo + aporte 50% de la casa) | ~$1,70M |
| Gastos (dividendo ~$370k, 2 luces, agua, internet, supermercado ~$250k, celular, TAG, suscripciones) | ~$0,93M |
| CMR (nov $233k → dic $171k → ene $116k → feb $41k → mar $16k) | baja cada mes |
| Auto actual (diésel ~$260k + mantención y permiso) | ~$305k |
| **Sobrante actual** | **~$230k** |
| Con eléctrico de ~$14,5M (cuota ~$225k a 48 meses) | ~$330k libres |

---

### Frente: Finanzas y Deudas
<!-- INICIO:finanzas -->
**Responsable:** `finanzas-planner` (sonnet)
**Estado:** Plan definido. Falta hacer el seguimiento mensual.
**Hecho:** Análisis de cartolas BancoEstado (dividendo, cuota 21 de 300), CMR, Cencosud y Servipag (may–nov 2026). Calendario de cuotas de la CMR. Proyección de 18 meses.
**Pendiente:**
- Confirmar cada mes que la CMR baja y que no hay compras nuevas.
- Revisar por qué la luz de la segunda propiedad (CGE) cuesta ~$105k.
- Revisar los cobros repetidos de YouTube/Google Play (~$27k/mes).
- Revisar el aviso de convenio de pago de Esval.
**Notas para el log:**
<!-- FIN:finanzas -->

### Frente: Extracción de Datos (correos y documentos)
<!-- INICIO:datos -->
**Responsable:** `datos-extractor` (haiku)
**Estado:** Extracción inicial lista.
**Fuentes:**
- Hotmail: bancos, tarjetas, Servipag, CGE, Movistar y Entel.
- Gmail: solo Tenpo.
- Drive: nada financiero.
- Capturas que manda el usuario.
- Cartolas BancoEstado: PDF con clave (la clave la indica el banco en el correo).
**Pendiente:** Extraer cada mes los estados de cuenta nuevos (CMR, Cencosud) y las boletas, y entregarlos al frente Finanzas.
**Notas para el log:**
<!-- FIN:datos -->

### Frente: App Plan Auto (web + APK)
<!-- INICIO:app -->
**Responsable:** `app-developer` (sonnet)
**Estado:** v2.0. Pestañas Inicio (semáforo, gráfico de 18 meses, hoja de ruta), Plata (gastos casa/personal + aporte), Deudas (calendario de cuotas), Rutas (mapa, rutas OSRM, enlace a Google Maps, cronología de Google Maps, cargas de diésel) y Autos (comparador de eléctricos con autonomía). Respaldo con archivo o texto.
**Archivos:** `plan-auto/app/web/index.html`, `plan-auto/app/android/**`, `.github/workflows/plan-auto-apk.yml`
**Build:** GitHub Actions → release `plan-auto-latest` → `PlanAuto.apk`.
**Ideas pendientes:** recordatorio mensual de pago, exportar resumen como imagen, modo offline del mapa.
**Notas para el log:**
<!-- FIN:app -->

### Frente: Investigación de Autos Eléctricos
<!-- INICIO:autos -->
**Responsable:** `ev-researcher` (haiku)
**Estado:** Primera búsqueda hecha (nov 2026).
**Lista corta:**
- Dolphin usado 2024–25: ~$14,5M
- Dolphin Mini usado 2025: ~$12,6M (autonomía justa)
- MG4 usado 2024: ~$17,3M (se pasa del presupuesto)
- Changan Lumin nuevo: ~$14M (no le alcanza la autonomía)
**Pendiente:** Confirmar la autonomía real de cada uno. Tasar el 301 2021 en Chileautos. Volver a revisar precios en feb 2027.
**Notas para el log:**
<!-- FIN:autos -->

### Frente: Trayectos y Energía
<!-- INICIO:trayectos -->
**Responsable:** `rutas-energia` (haiku)
**Estado:** Estimación hecha a partir del gasto en diésel (~$60k/semana → ~4.400 km/mes, 5–6 días por semana).
**Pendiente:**
- Conocer el origen y destino del trabajo para calcular la ruta exacta.
- Medir el km/L real con la bitácora de cargas de la app.
- Confirmar el precio del kWh en la boleta de Energía Casablanca.
- Opcional: importar la cronología de Google Maps.
**Notas para el log:**
<!-- FIN:trayectos -->

---

## 4. Registro de avances (Log)
> Los subagentes escriben en "Notas para el log" de su propio bloque. La sesión principal pasa esas notas aquí.
- [2026-11-19] Sesión principal: creó la app v1 y el APK (CI) y la publicó como Artifact.
- [2026-11-19] Sesión principal: analizó Hotmail, cartolas BancoEstado, CMR, Cencosud y Servipag. Generó `datos.json` local (fuera del repo).
- [2026-11-19] Sesión principal: hizo la primera búsqueda de eléctricos en Chile y envió el APK v1.
- [2026-11-20] Sesión principal: movió el proyecto a `plan-auto/`. Creó este archivo, los subagentes y `CLAUDE.md`. Rehízo la app (v2) con mapa, rutas, cronología de Google Maps, cargas de diésel, comparador de eléctricos y proyección.

## 5. Bloqueos y dudas abiertas
- Valor real de venta del 301 2021 (km y versión).
- Origen y destino del trayecto diario.
- Por qué la luz de la segunda propiedad es tan alta, y quién la usa.
- Que el colega pague la Cencosud de noviembre (vence el 24/11).
- Mover `plan-auto/` a un repo privado propio (lo crea el usuario en GitHub).
