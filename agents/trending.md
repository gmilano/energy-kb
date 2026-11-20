---
industry: energy
region: Global
updated: 2026-11-20
---

# 📈 Agentes trending — energy

> **Archivo APPEND-ONLY.** Cada pase añade una sección fechada arriba y conserva el historial
> debajo. No reescribir: el valor de este archivo es la serie temporal.

## 2026-11-20 — pase 3 (la capa agéntica europea y su licencia)

**Titular del pase: existen DOS stacks agénticos energéticos, no uno, y se distinguen por licencia.
El norteamericano (`Power-Agent`, Harvard SEAS) es MIT. El europeo, que esta KB no tenía registrado,
se está consolidando bajo LF Energy y es MPL-2.0 — copyleft de archivo, no permisivo.**

Los dos pases anteriores de hoy registraron el stack MIT y lo declararon "el punto de partida más
fuerte que existe". Sigue siendo cierto para North America. Pero para un encargo con un TSO europeo
la respuesta es otra, y es la que faltaba.

### El hallazgo que cierra una pregunta abierta: la organización `ainetus` existe

El pase anterior registró AINETUS a partir de prensa (Enlit, LF Energy) **sin localizar el código**.
Está en GitHub, bajo la organización `ainetus`, activa esta semana:

| Nombre | Licencia | Descripción | Stars | Forks | Último push | Región origen |
|--------|----------|-------------|-------|-------|-------------|---------------|
| [ainetus/ExpertOp4Grid](https://github.com/ainetus/ExpertOp4Grid) | **MPL-2.0** | Sistema experto que **opera** una red eléctrica: motor de recomendación de maniobras topológicas. Núcleo del asistente de operación AINETUS (proyecto AI4REALNET, gobernanza LF Energy) | 12 | 4 | 2026-11-18 | EMEA |
| [ainetus/Expert_op4grid_recommender](https://github.com/ainetus/Expert_op4grid_recommender) | **MPL-2.0** | Recomendador basado en los principios de ExpertOp4Grid: analiza y propone acciones al operador | 1 | 3 | 2026-11-18 | EMEA |
| [ainetus/soft_label_gnn](https://github.com/ainetus/soft_label_gnn) | **MPL-2.0** | GNN con etiquetas blandas para el mismo programa de investigación | 4 | 3 | 2026-03-05 | EMEA |
| [ainetus/Grid2Op_MORL](https://github.com/ainetus/Grid2Op_MORL) | **MPL-2.0** | RL multi-objetivo sobre Grid2Op | 0 | 2 | 2026-06-11 | EMEA |

**Lectura honesta de las cifras**: 12 ★ es *muy* poco. No es un proyecto con comunidad; es código de
investigación con respaldo institucional (RTE, AI4REALNET, LF Energy) publicado hace ~6 meses. Su
valor no está en la tracción sino en **de quién viene y con qué se integra**.

### La pieza que faltaba entre el agente y la sala de control

| Nombre | Licencia | Descripción | Stars | Forks | Último push | Región origen |
|--------|----------|-------------|-------|-------|-------------|---------------|
| [opfab/operatorfabric-core](https://github.com/opfab/operatorfabric-core) | **MPL-2.0** | Plataforma LF Energy de **sala de control**: agrega, prioriza y encamina notificaciones y tarjetas de acción a los operadores. Es el sitio donde un agente deposita una recomendación para que un humano la vea y la acepte | 42 | 29 | 2026-11-19 | EMEA |
| [PowerGridModel/power-grid-model-ai](https://github.com/PowerGridModel/power-grid-model-ai) | **MPL-2.0** | **Agent Skills** para `power-grid-model` (LF Energy / Alliander): da al LLM acceso al motor de cálculo de red de grado producción | 5 | 2 | 2026-11-17 | EMEA |

`operatorfabric-core` es el hallazgo de arquitectura del pase. Esta KB ya registraba motores de
cálculo, entornos RL y servidores MCP, pero **ninguna pieza de "human-in-the-loop"**. En operación de
red eso no es un detalle: ningún TSO deja que un agente ejecute una maniobra. La recomendación tiene
que llegar a una sala de control, con trazabilidad y aceptación explícita. Ese es el componente.

### Lo que esto cambia en una decisión concreta

- **Un encargo europeo de operación de red no se arma con `Power-Agent`.** Se arma con
  `Grid2Op` (MPL-2.0) + `ExpertOp4Grid` (MPL-2.0) + `operatorfabric-core` (MPL-2.0), que ya están
  diseñados para integrarse entre sí y comparten gobernanza.
- **MPL-2.0 no es un bloqueo, pero no es MIT.** El copyleft es **por archivo**: se puede enlazar
  desde código propietario y distribuir el conjunto, pero las modificaciones *a los archivos MPL*
  deben publicarse. Para un entregable de cliente eso es manejable; para uno de marca blanca donde
  el cliente quiere el motor modificado y cerrado, no lo es. Hay que decidirlo al inicio, no al final.
- **El patrón de licencia tiene geografía.** No es casualidad: la capa americana nace en universidad
  (Harvard → MIT) y la europea en operadores de red (RTE/Alliander → MPL, la licencia de PowSyBl y
  Grid2Op). Conviene anticiparlo al estimar cualquier encargo transatlántico.

## 2026-11-20 — pase 2 (barrido de huecos declarados)

**Titular del pase: la categoría agéntica energética no se agota en `Power-Agent`. Apareció una
plataforma de control distribuido con 504 ★ cuya licencia esta KB nunca había resuelto, y un
segundo servidor MCP de EnergyPlus que sí es MIT.**

Este pase no buscó novedades por buzzword: atacó uno por uno los **gaps declarados** del pase
anterior de hoy. Tres de ellos ya no son gaps.

| Nombre | Licencia | Descripción | Stars | Forks | Último push | Región origen |
|--------|----------|-------------|-------|-------|-------------|---------------|
| [VOLTTRON/volttron](https://github.com/VOLTTRON/volttron) | **Apache-2.0** (resuelta; la API dice `NOASSERTION`) | Plataforma de control distribuido de PNNL/Battelle: bus de mensajes + agentes desplegables en edificios y equipos de red. Es **infraestructura de agentes**, anterior a los LLM y ya desplegada en campo | 504 | 284 | 2026-11-03 | North America |
| [eclipse-volttron/volttron](https://github.com/eclipse-volttron/volttron) | Apache-2.0 | **Nuevo hogar en la Eclipse Foundation.** Hoy tiene 0 ★ y un último push del 2026-07-21: la migración está empezada, no terminada | 0 | 1 | 2026-07-21 | North America |
| [idfkit/idfkit-mcp](https://github.com/idfkit/idfkit-mcp) | **MIT** (verificada en `LICENSE` crudo) | Segundo servidor MCP para EnergyPlus. **Licencia limpia**, al contrario que el de LBNL | 14 | 2 | 2026-11-16 | North America |
| [assume-framework/assume](https://github.com/assume-framework/assume) | MIT | Simulación **basada en agentes de mercados eléctricos** (Fraunhofer IEE / INATECH / TU Dresden). Rompe el gap "cero repos de mercados" | 128 | 53 | 2026-11-19 | EMEA |

### Lo que esto cambia en una decisión concreta

- **`EnergyPlus-MCP` (LBNL, 130 ★) ya no es la única puerta a EnergyPlus por MCP.** El pase anterior
  advirtió —con razón— que su licencia es una BSD modificada sin archivo `LICENSE`, con derechos del
  gobierno de EE. UU. y contacto de IP en LBNL. `idfkit-mcp` es **MIT verificada**, con el coste de
  ser mucho más joven (14 ★, v. inicial). Para un entregable de marca blanca con revisión legal
  corta, `idfkit-mcp` es el camino; para cobertura funcional (35 tools), el de LBNL.
- **`VOLTTRON` es Apache-2.0 y lleva años en edificios reales.** Es la pieza que faltaba entre "la
  plataforma copyleft de registro" y "la capa agéntica MIT": permite ejecutar agentes **en el borde**,
  junto al equipo, sin AGPL. Que esté migrando a Eclipse es una señal de gobernanza, pero
  **la org nueva todavía no es la fuente de verdad** — hoy el código vivo está en `VOLTTRON/volttron`.

### Advertencia de método que cambió este pase

El pase anterior fijó la regla "`NOASSERTION` ≠ sin licencia: leer el `LICENSE` crudo". Esa regla es
necesaria pero **insuficiente**: `oemof/oemof-solph` (430 ★) y `pypsa-meets-earth/pypsa-earth`
(384 ★) **no tienen archivo `LICENSE` en ninguna rama** y sin embargo sí declaran licencia, en un
identificador **SPDX dentro de `pyproject.toml` / `README`** (estándar REUSE):

- `oemof-solph` → `SPDX-License-Identifier: MIT` en `pyproject.toml` (+ `LICENSES/MIT.txt`).
- `pypsa-earth` → `SPDX-License-Identifier: AGPL-3.0-or-later` en el `README`.

Regla nueva, en orden: **(1) `LICENSE` crudo → (2) SPDX en `pyproject.toml`/`README` → (3) sólo
entonces declararlo irresuelto.** Saltarse el paso 2 habría costado descartar un repo MIT de 430 ★ y,
peor, **haber tratado como permisivo un AGPL de 384 ★**.

### Canales de verificación de este pase (cambiaron respecto del anterior)

| Canal | Pase anterior | Hoy |
|-------|---------------|-----|
| `api.github.com` / `github.com` vía curl | HTTP 403 (política de host) | **HTTP 200** |
| `gh api search/repositories` con `q=repo:owner/name` | funciona | funciona (único camino fiable) |
| `gh api repos/{owner}/{repo}` | no registrado | **403**: la sesión sólo alcanza sus repos configurados |
| `raw.githubusercontent.com` | 200 | 200 |
| `huggingface.co` | "no resuelve" | **403 del proxy** — es política de red, no DNS |
| `gitee.com` | no probado | **403 del proxy** → la hipótesis "los repos chinos están en Gitee" **no se puede testear desde aquí** |
| `eur-lex.europa.eu` | no probado | **403 del proxy** → la verificación del AI Act contra el Diario Oficial que pidió el pase anterior **es imposible en este entorno** |
| Fetch directo de páginas (arxiv.org, oati.com, twobirds.com) | no registrado | **falla DNS/allowlist** → todo dato de prensa de este pase es de **snippet de búsqueda, no de fuente primaria** |

**Consecuencia honesta**: en esta KB, sólo lo verificado contra GitHub es dato de primera mano.
Todo lo regulatorio y de mercado es secundario, y está marcado como tal.

---

## 2026-11-20 — pase 1 (verificación del stack agéntico)

**Titular del pase: apareció un stack agéntico energético completo, todo MIT, y un servidor MCP de
laboratorio nacional.** Verificado contra la GitHub REST API.

| Nombre | Licencia | Descripción | Stars | Último push |
|--------|----------|-------------|-------|-------------|
| [Power-Agent/PowerMCP](https://github.com/Power-Agent/PowerMCP) | MIT | Servidores MCP para software de sistemas de potencia (PowerWorld y otros) | 238 | 2026-11-17 |
| [LBNL-ETA/EnergyPlus-MCP](https://github.com/LBNL-ETA/EnergyPlus-MCP) | BSD modificada | Primer servidor MCP open source para EnergyPlus: 35 tools sobre modelos IDF (LBNL) | 130 | 2026-11-20 |
| [Power-Agent/PowerSkills](https://github.com/Power-Agent/PowerSkills) | MIT | Agent Skills para análisis de sistemas de potencia | 81 | 2026-10-24 |
| [open-energy-transition/pypsa-mcp](https://github.com/open-energy-transition/pypsa-mcp) | MIT | PyPSA expuesto a LLMs vía MCP | 74 | 2026-03-20 |
| [Power-Agent/PowerFM](https://github.com/Power-Agent/PowerFM) | MIT | Foundation models para potencia y energía | 59 | 2026-10-24 |
| [Power-Agent/PowerAgentBench](https://github.com/Power-Agent/PowerAgentBench) | MIT | Benchmark de agentes de sistemas de potencia | 50 | 2026-11-02 |
| [Power-Agent/PowerWF](https://github.com/Power-Agent/PowerWF) | MIT | Workflows agénticos para sistemas de potencia | 44 | 2026-11-12 |

**Qué cambió respecto del pase de 2026-08-01**: ese pase registró `X-GridAgent`, `GridMind` y
`PowerAgent` como *papers* (arXiv, Argonne, Harvard). Hoy `Power-Agent` es **código MIT publicado y
versionado** en cinco repos, con benchmark propio. La categoría pasó de literatura a software
instalable en ~3 meses.

**Señal de madurez a vigilar**: que `PowerAgentBench` exista antes que la adopción masiva. Igual que
en automotive, publicar el propio benchmark/defeater count se volvió movida de credibilidad.

**Advertencia sobre `EnergyPlus-MCP`**: no tiene archivo `LICENSE`; el README declara BSD modificada
con texto en `License.txt`. Versión **0.1.0**. No asumir licencia desde la API (devuelve
`NOASSERTION`).

---

## Historial

### 2026-07-02 — pase automático (datos NO verificados)

⚠️ **Advertencia añadida 2026-11-20**: las filas de abajo provienen de un pipeline de keyword-match
sin verificación. Al menos una (`mtd`, conversor de Markdown a DOCX) **no pertenece al dominio
energético**, y varias tienen 0–2 stars. Se conservan por la regla append-only, **no** como
hallazgos curados. No usar en una propuesta.
Re-verificadas el 2026-11-20 contra la API: **3 de 10 URLs ya no resuelven** (`Hartblack356/mtd` y `Legalagecolouring820/Random-Forest-Model-...` fueron borradas; `openremote/openremote` fue renombrada a `openremote/core`). Ese 30 % de link-rot en 4 meses es la razón por la que cada pase debe re-verificar y no arrastrar filas.


> Última actualización: 2026-07-02

| Nombre | Licencia | Descripción | Stars |
|--------|----------|-------------|-------|
| [smart-water-grid-ai](https://github.com/Basil-Saad/smart-water-grid-ai) | ? | AI-powered IoT smart water grid management system, Firebase, XGBoost, and Digita | 1 |
| [oscp-go](https://github.com/ChargePi/oscp-go) | MIT | Open Smart Charging Protocol SDK for Go | 3 |
| [BESS-energy-management-system](https://github.com/Marinalizm/BESS-energy-management-system) | ? | ⚡ Monitor and control your 300MW Battery Energy Storage System (BESS) in real-ti | 2 |
| [smartEMS-MultiAgent-Demo](https://github.com/sariekiriyuu/smartEMS-MultiAgent-Demo) | NOASSERTION | ⚡ Simulate and visualize energy management with a multi-agent AI framework for r | 2 |
| [mtd](https://github.com/Hartblack356/mtd) | MIT | Convert Markdown to DOCX and ODT with themes, YAML frontmatter, and CLI, SDK, or | 0 |
| [pyiec61850-ng](https://github.com/f0rw4rd/pyiec61850-ng) | GPL-3.0 | Python bindings for libiec61850, packaged as a Python wheel based on libiec61850 | 6 |
| [grid-gym](https://github.com/pt9912/grid-gym) | NOASSERTION | grid-gym is an open-source platform for deterministic simulation and validation  | 2 |
| [awesome-ml-power-systems](https://github.com/ArsamAryandoust/awesome-ml-power-systems) | ? | A curated collection of papers, datasets, software, benchmarks, and resources at | 1 |
| [openremote](https://github.com/openremote/openremote) | NOASSERTION | 100% open-source IoT Platform - Integrate your devices, add intelligence, build  | 1.8k |
| [Random-Forest-Model-EMS-system-data-machine-learning-early-warning](https://github.com/Legalagecolouring820/Random-Forest-Model-EMS-system-data-machine-learning-early-warning) | ? | Predict EMS data with random forest to flag machine issues early and improve ene | 0 |

---
*Pipeline automático — se actualiza cada hora.*
---
