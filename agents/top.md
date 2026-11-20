---
industry: energy
region: Global
updated: 2026-11-20
---

# 🎯 Agentes AI — energy

> Agentes y tooling agéntico open source para el sector energético. Foco: MIT / Apache 2.0 / BSD.
> Toda fila verificada contra la GitHub REST API (`search/repositories`, campos `license.spdx_id`,
> `stargazers_count`, `forks_count`, `pushed_at`) el **2026-11-20**. Licencias `NOASSERTION`
> resueltas leyendo el `LICENSE` crudo en `raw.githubusercontent.com`.

## Hallazgo principal de este pase: `Power-Agent` es un stack agéntico completo, todo MIT

No es un repo aislado sino **cinco repos MIT coordinados** (Harvard SEAS Power & AI Initiative) que
cubren el ciclo entero: servidores MCP → skills → workflows → foundation models → benchmark.
Es el punto de partida más fuerte que existe hoy para agentes de sistemas de potencia.

| Nombre | Licencia | Descripción | Stars | Forks | Último push | Región origen |
|--------|----------|-------------|-------|-------|-------------|---------------|
| [Power-Agent/PowerMCP](https://github.com/Power-Agent/PowerMCP) | MIT | Colección de servidores MCP para software de sistemas de potencia (PowerWorld y otros): expone las herramientas de ingeniería al agente | 238 | 67 | 2026-11-17 | North America |
| [LBNL-ETA/EnergyPlus-MCP](https://github.com/LBNL-ETA/EnergyPlus-MCP) | BSD modificada (ver nota) | Servidor MCP con **35 tools** para cargar, validar, modificar, simular y analizar modelos EnergyPlus (IDF). Lawrence Berkeley National Lab | 130 | — | 2026-11-20 | North America |
| [Power-Agent/PowerSkills](https://github.com/Power-Agent/PowerSkills) | MIT | Agent Skills para análisis de sistemas de potencia | 81 | — | 2026-10-24 | North America |
| [open-energy-transition/pypsa-mcp](https://github.com/open-energy-transition/pypsa-mcp) | MIT | Servidor MCP que expone PyPSA a LLMs: modelado energético conversacional | 74 | 10 | 2026-03-20 | EMEA |
| [Power-Agent/PowerFM](https://github.com/Power-Agent/PowerFM) | MIT | Foundation models para el dominio de potencia y energía | 59 | — | 2026-10-24 | North America |
| [Power-Agent/PowerAgentBench](https://github.com/Power-Agent/PowerAgentBench) | MIT | Benchmark para evaluar agentes de sistemas de potencia | 50 | — | 2026-11-02 | North America |
| [Power-Agent/PowerWF](https://github.com/Power-Agent/PowerWF) | MIT | Workflows agénticos para sistemas de potencia | 44 | — | 2026-11-12 | North America |

## Entornos RL / simulación para entrenar y evaluar agentes

| Nombre | Licencia | Descripción | Stars | Forks | Último push | Región origen |
|--------|----------|-------------|-------|-------|-------------|---------------|
| [citylearn-project/CityLearn](https://github.com/citylearn-project/CityLearn) | MIT | Entorno RL oficial para demand response y load shaping en distritos urbanos | 662 | — | 2026-11-19 | North America |
| [Grid2op/grid2op](https://github.com/Grid2op/grid2op) | **MPL-2.0** | Testbed de decisión secuencial en redes eléctricas (RTE Francia); base de la competencia L2RPN | 494 | 155 | 2026-11-13 | EMEA |
| [ugr-sail/sinergym](https://github.com/ugr-sail/sinergym) | MIT | Entorno Gym para simulación y control de edificios sobre EnergyPlus (Univ. de Granada) | 242 | 57 | 2026-11-17 | EMEA |
| [NatLabRockies/PowerGridworld](https://github.com/NatLabRockies/PowerGridworld) | BSD-3-Clause | Framework liviano y modular para RL multi-agente en redes (Alliance for Sustainable Energy / NREL) | 188 | 49 | 2026-11-15 | North America |

## Plataformas de agentes en el borde (hallazgo del segundo pase del 2026-11-20)

La capa agéntica no empieza con los LLM. Existe infraestructura de agentes **ya desplegada en campo**,
con licencia permisiva, que resuelve el problema de "dónde corre el agente cuando está al lado del
equipo y no en la nube":

| Nombre | Licencia | Descripción | Stars | Forks | Último push | Región origen |
|--------|----------|-------------|-------|-------|-------------|---------------|
| [VOLTTRON/volttron](https://github.com/VOLTTRON/volttron) | **Apache-2.0** | Plataforma de control distribuido de PNNL/Battelle: bus de mensajes, aislamiento de agentes y drivers de campo. Despliegue probado en edificios y equipos de red | 504 | 284 | 2026-11-03 | North America |
| [eclipse-volttron/volttron](https://github.com/eclipse-volttron/volttron) | Apache-2.0 | Nuevo hogar del proyecto en la Eclipse Foundation. **Migración en curso, no terminada**: 0 ★ y último push 2026-07-21 | 0 | 1 | 2026-07-21 | North America |
| [idfkit/idfkit-mcp](https://github.com/idfkit/idfkit-mcp) | **MIT** | Servidor MCP para EnergyPlus con **licencia limpia**: la alternativa al de LBNL cuando la revisión legal tiene que ser corta. Joven (14 ★) | 14 | 2 | 2026-11-16 | North America |

**Cómo encaja con `Power-Agent`**: `PowerMCP` y `PowerSkills` dan el *razonamiento* sobre
herramientas de ingeniería; `VOLTTRON` da el *lugar de ejecución* en el borde, con Apache-2.0 y sin
cláusula de red. Es el puente entre la plataforma copyleft de registro y la capa agéntica MIT.

## Simulación de mercados basada en agentes

Categoría que pases anteriores declararon vacía. No lo está — pero es **modelado**, no ejecución:

| Nombre | Licencia | Descripción | Stars | Forks | Último push | Región origen |
|--------|----------|-------------|-------|-------|-------------|---------------|
| [assume-framework/assume](https://github.com/assume-framework/assume) | MIT | **ASSUME**: agentes que representan actores de mercado eléctrico para estudiar su evolución (Fraunhofer IEE / INATECH / TU Dresden). Activo: push 2026-11-19 | 128 | 53 | 2026-11-19 | EMEA |
| [alexanderkell/elecsim](https://github.com/alexanderkell/elecsim) | MIT | Modelo de agentes de mercado a largo plazo: efecto de la política pública sobre decisiones de inversión. ⚠️ **sin actividad desde 2025-12-03** | 61 | 13 | 2025-12-03 | EMEA |

⚠️ **Límite que hay que declarar**: ninguno de los dos coloca ofertas en un mercado real. Son
simuladores. Un agente de *ejecución* de trading mayorista sigue sin equivalente open source.

## Capa agéntica europea bajo LF Energy (añadida en el tercer pase del 2026-11-20)

Hay **dos** stacks agénticos energéticos, no uno. El de arriba (`Power-Agent`, Harvard SEAS) es MIT
y nace en universidad norteamericana. Este nace en **operadores de red europeos** (RTE, Alliander) y
es **MPL-2.0** de forma consistente. Para un encargo con un TSO europeo, es el stack pertinente.

| Nombre | Licencia | Descripción | Stars | Forks | Último push | Región origen |
|--------|----------|-------------|-------|-------|-------------|---------------|
| [opfab/operatorfabric-core](https://github.com/opfab/operatorfabric-core) | **MPL-2.0** | Plataforma LF Energy de **sala de control**: agrega y encamina tarjetas de acción al operador humano. Es donde un agente deposita una recomendación para que una persona la acepte | 42 | 29 | 2026-11-19 | EMEA |
| [ainetus/ExpertOp4Grid](https://github.com/ainetus/ExpertOp4Grid) | **MPL-2.0** | Sistema experto que propone maniobras topológicas de red. Núcleo del asistente AINETUS (AI4REALNET, gobernanza LF Energy) | 12 | 4 | 2026-11-18 | EMEA |
| [PowerGridModel/power-grid-model-ai](https://github.com/PowerGridModel/power-grid-model-ai) | **MPL-2.0** | Agent Skills para `power-grid-model` (Alliander): expone a un LLM el motor de cálculo de red de grado producción | 5 | 2 | 2026-11-17 | EMEA |
| [ainetus/soft_label_gnn](https://github.com/ainetus/soft_label_gnn) | **MPL-2.0** | GNN con etiquetas blandas, del mismo programa de investigación | 4 | 3 | 2026-03-05 | EMEA |
| [ainetus/Expert_op4grid_recommender](https://github.com/ainetus/Expert_op4grid_recommender) | **MPL-2.0** | Recomendador derivado de ExpertOp4Grid | 1 | 3 | 2026-11-18 | EMEA |

**Cifras leídas con honestidad**: entre 1 y 42 ★. No hay comunidad; hay respaldo institucional y
código publicado hace meses. Se registra por **procedencia e integrabilidad**, no por tracción, y
así debe presentarse a un cliente.

**La pieza de arquitectura que faltaba en toda la KB**: `operatorfabric-core`. Había motores de
cálculo, entornos RL y servidores MCP, pero ninguna capa *human-in-the-loop*. Ningún operador de red
deja que un agente ejecute una maniobra: la recomendación tiene que llegar a una sala de control con
trazabilidad y aceptación explícita. Sin ese componente, una demo agéntica de red no es desplegable.

**30 agentes/entornos/modelos reales** (21 de los pases 1-3 + 9 del cuarto pase).
Ninguna fila es ejemplo ni plantilla.

## Foundation models de red: la categoría que esta KB no tenía (cuarto pase, 2026-11-20)

Hasta este pase, `agents/top.md` describía **servidores MCP** (razonamiento sobre herramientas) y
**entornos RL** (dónde entrenar). Faltaba la capa del medio: **modelos preentrenados del dominio
eléctrico**. Ya existe, con licencia permisiva y respaldo corporativo, y cambia el punto de partida
de un encargo: se puede hacer *fine-tuning* en lugar de entrenar desde cero.

| Nombre | Licencia | Descripción | Stars | Forks | Último push | Región origen |
|--------|----------|-------------|-------|-------|-------------|---------------|
| [microsoft/GridSFM](https://github.com/microsoft/GridSFM) | **MIT** | *Small Foundation Models for the Power Grid*. Modelos fundacionales pequeños específicos de red, de Microsoft. Creado 2026-04-23 | 177 | 41 | 2026-07-15 | North America |
| [gridfm/gridfm-datakit](https://github.com/gridfm/gridfm-datakit) | **Apache-2.0** | Generación de datos de flujo de potencia para **entrenar** modelos ML y fundacionales de red. Es el paso previo obligatorio al fine-tuning | 170 | 40 | 2026-11-14 | Global |
| [gridfm/gridfm-graphkit](https://github.com/gridfm/gridfm-graphkit) | **Apache-2.0** | Entrenar, hacer fine-tuning e interactuar con un foundation model de red basado en grafos. Es el par de `gridfm-datakit` | 113 | 41 | 2026-11-19 | Global |
| [emarche/RL2Grid](https://github.com/emarche/RL2Grid) | **MIT** | Benchmark **estandarizado** para agentes RL en entornos de red realistas. Complementa Grid2Op: Grid2Op es el entorno, RL2Grid es la vara de medir | 58 | 11 | 2026-09-16 | EMEA |

**Por qué importa el orden `datakit` → `graphkit`**: son dos repos de la misma organización (`gridfm`,
ambos creados 2025-06-23) y están pensados para usarse en secuencia. `datakit` sintetiza casos de
flujo de potencia a partir de topologías; `graphkit` consume esos datos para entrenar un GNN
fundacional. Citar uno sin el otro deja la receta incompleta.

**Lectura honesta de la tracción**: 58–177 ★. Es una categoría **naciente**, no consolidada.
`GridSFM` no recibe push desde 2026-07-15 (cuatro meses) y tiene 11 issues abiertas — respaldo de
Microsoft no equivale a mantenimiento activo. `gridfm-*` sí está vivo (push de esta semana). Para
una propuesta: presentar como *vía de evaluación técnica*, no como base de producción.

## Entorno RL de V2G a escala

| Nombre | Licencia | Descripción | Stars | Forks | Último push | Región origen |
|--------|----------|-------------|-------|-------|-------------|---------------|
| [StavrosOrf/EV2Gym](https://github.com/StavrosOrf/EV2Gym) | **MIT** | Entorno de simulación V2G para optimización de carga de EV **a gran escala**: flotas, no un vehículo. Cierra el hueco entre `evcc` (un hogar) y `CityLearn` (un distrito) | 248 | 57 | 2026-09-15 | EMEA |

## Servidores MCP de datos de red en vivo (categoría nueva y deliberadamente incómoda)

Aparecieron en 2026 varios servidores MCP que exponen **datos de red reales y en vivo** a un agente.
Es exactamente la pieza que faltaba para un copiloto de operación o de siting. Pero hay que
registrarlos con su tamaño real, porque es diminuto:

| Nombre | Licencia | Descripción | Stars | Forks | Último push | Región origen |
|--------|----------|-------------|-------|-------|-------------|---------------|
| [azmartone67/dchub-mcp-server](https://github.com/azmartone67/dchub-mcp-server) | **MIT** | *Data Center Power Index*: puntaje diario de dónde un datacenter puede conseguir potencia de red, en **300+ mercados**. Expuesto por MCP | 3 | 0 | 2026-11-20 | North America |
| [pipeworx-io/mcp-neso](https://github.com/pipeworx-io/mcp-neso) | **MIT** | MCP sobre los datos abiertos de **NESO** (operador del sistema eléctrico de Gran Bretaña, `api.neso.energy`) | 0 | 0 | 2026-11-09 | EMEA |
| [pipeworx-io/mcp-georgia-energy](https://github.com/pipeworx-io/mcp-georgia-energy) | **MIT** | MCP sobre telemetría de red y estadística del regulador de **Georgia** (el país) | 0 | 0 | 2026-11-09 | EMEA |
| [sohamshindework/gridpulse](https://github.com/sohamshindework/gridpulse) | **MIT** | Datos abiertos de red de **Alemania + EE. UU.**, scheduling carbon-aware y contabilidad verificada; SDK y MCP. Creado 2026-11-18 | 0 | 0 | 2026-11-20 | Global |

⚠️ **Cómo hay que presentar esto a un cliente.** Entre 0 y 3 ★, 0 forks, uno creado hace dos días.
No son productos: son **demostraciones de que el patrón es implementable** y, sobre todo, código de
referencia del que copiar el *wiring* a una API de operador de sistema. El valor para Globant no es
adoptarlos sino que confirman que el camino "datos de TSO → MCP → agente" está trazado y es corto.
Escribir uno propio contra el TSO del cliente es trabajo de días, no de meses, y es facturable.

**La otra lectura, menos obvia**: `dchub-mcp-server` es el único de los cuatro que responde a la
pregunta que de verdad están haciendo los clientes en 2026 — *¿dónde puedo enchufar un datacenter?*
Ese es el cuello de botella descrito en `intel/trends.md`, convertido en una herramienta consultable
por un agente. Categoría a vigilar en el próximo pase.

## Notas de licencia que cambian decisiones

- **`LBNL-ETA/EnergyPlus-MCP`**: la API devuelve `NOASSERTION` y **no hay archivo `LICENSE`**; el
  README declara *"This software is distributed under a modified BSD license"* con el texto en
  `License.txt` (L mayúscula, por eso un fetch de `LICENSE` da 404). Titular: Regents of the
  University of California / LBNL, *"subject to receipt of any required approvals from the U.S.
  Dept. of Energy"*. Versión declarada **0.1.0**. Para uso en cliente: pedir revisión legal del
  `License.txt` y considerar el aviso de U.S. Government Rights. Contacto de IP: IPO@lbl.gov.
- **`Grid2op` es MPL-2.0**, no LGPL-2.1. Pases anteriores de esta KB registraron LGPL-2.1: era
  incorrecto. MPL-2.0 es copyleft por archivo — enlazable sin contaminar el resto del producto.
- **`PowerGridworld` cambió de organización**: `NREL/PowerGridworld` ya **no resuelve**. El repo
  vive en `NatLabRockies/PowerGridworld` (BSD-3-Clause confirmado en `LICENSE` crudo, copyright
  "Alliance for Sustainable Energy, LLC"). Toda URL `NREL/...` registrada antes está rota.
- **`CityLearn` cambió de organización**: `intelligent-environments-lab/CityLearn` ya no resuelve;
  ahora es `citylearn-project/CityLearn`.

### Nota de licencia del tercer pase: MPL-2.0 es la licencia por defecto del sector eléctrico europeo

`Grid2Op`, `PowSyBl`, `openSTEF`, `power-grid-model`, `operatorfabric-core`, `ExpertOp4Grid` y
`power-grid-model-ai` son **todos MPL-2.0**. No es coincidencia: es la licencia que eligieron RTE y
Alliander, y por arrastre LF Energy. Consecuencia práctica que hay que decir al inicio de un
encargo, no al final:

- **Se puede** enlazar desde código propietario y distribuir el producto combinado.
- **Hay que** publicar las modificaciones hechas *a los archivos MPL* que se distribuyan.
- **Por tanto**: entregable de integración, sí. Entregable de marca blanca con el motor modificado y
  cerrado, no — o se asume la publicación de ese delta.

## Correcciones de datos sobre pases anteriores

Los pases de energy de ciclos previos (2026-08-01) sobreestimaron stars de forma sistemática.
Medido de nuevo contra la API el 2026-11-20:

| Repo | Registrado antes | Real hoy | Delta |
|------|------------------|----------|-------|
| CityLearn | ~1.7k ★ | **662 ★** | −2.6× (y org distinta) |
| Grid2Op | ~1.2k ★, LGPL-2.1 | **494 ★, MPL-2.0** | −2.4× + licencia errónea |
| Carbon Aware SDK | ~2.2k ★ | **600 ★** | −3.7× |
| openSTEF | ~500 ★, Apache-2.0 | **183 ★, MPL-2.0** | −2.7× + licencia errónea |
| PowerGridworld | ~430 ★, org NREL | **188 ★, org NatLabRockies** | −2.3× + org rota |
| sinergym | ~310 ★ | **242 ★** | −1.3× |

Causa probable: cifras arrastradas entre pases sin re-consultar la API. Esta tabla existe para que
el próximo pase no las vuelva a propagar.

## Resoluciones de licencia del segundo pase (2026-11-20)

La regla del pase anterior —*"`NOASSERTION` no significa sin licencia: leer el `LICENSE` crudo"*— es
correcta pero incompleta. Hay repos **sin archivo `LICENSE` en ninguna rama** que sí declaran
licencia, mediante un identificador **SPDX** en `pyproject.toml` o en el `README` (estándar REUSE).

**Orden de verificación que esta KB adopta desde hoy:**

1. `LICENSE` / `LICENSE.txt` / `License.txt` / `COPYING` crudo en `raw.githubusercontent.com`.
2. `SPDX-License-Identifier:` en `pyproject.toml`, `setup.py`, `README`.
3. Sólo entonces: declararlo **irresuelto** (y no construir sobre él).

Resueltas así en este pase:

| Repo | API decía | Realidad verificada | Dónde estaba | Veredicto |
|------|-----------|---------------------|--------------|-----------|
| `VOLTTRON/volttron` | NOASSERTION | **Apache-2.0** (Battelle Memorial Institute) | `LICENSE` | ✅ rescatado, 504 ★ |
| `oemof/oemof-solph` | `null` | **MIT** | SPDX en `pyproject.toml` | ✅ rescatado, 430 ★ |
| `pypsa-meets-earth/pypsa-earth` | `null` | **AGPL-3.0-or-later** | SPDX en `README` | ⚠️ **copyleft de red** |
| `e2nIEE/pandapipes` | NOASSERTION | **BSD-3-Clause** (Fraunhofer IEE) | `LICENSE` | ✅ rescatado, 247 ★ |
| `dss-extensions/OpenDSSDirect.py` | NOASSERTION | **BSD-3 + derechos del gobierno de EE. UU.** | `LICENSE` | ⚠️ revisar cláusula gov |
| `gridlab-d/gridlab-d` | NOASSERTION | **licencia propia de Battelle v5.3 (no OSI, no SPDX)** | `LICENSE` | ⚠️ gate de compliance la marcará |
| `idfkit/idfkit-mcp` | MIT | **MIT** confirmada | `LICENSE` | ✅ |
| `u9n/dlms-cosem` | NOASSERTION | **Business Source License 1.1** (re-confirmada) | `LICENSE` | ❌ no permisiva |

**El caso que más caro habría salido**: `pypsa-earth`. Es el único modelo de sistema energético que
cubre LATAM y APAC de fábrica, la API no declara licencia, y la respuesta —AGPL-3.0-or-later— está
en una línea del `README`. Tratarlo como permisivo en un SaaS de cliente habría significado
obligación de liberar el servicio.

## Hallazgos de verificación del cuarto pase (2026-11-20)

### 1. Trampa nueva: repos con estrellas infladas y cero forks

Dos repos de **carga eléctrica** aparecen en el top de cualquier búsqueda de forecasting con cifras
que los pondrían primeros en esta KB. No se incluyen, a propósito:

| Repo | Stars | Forks | Issues | Creado | Veredicto |
|------|-------|-------|--------|--------|-----------|
| `KEV0143/Comparative-analysis-of-hourly-load-forecasting-using-PatchTST-TFT-NHiTS-and-CatBoost` | 1764 | **0** | 0 | 2025-09-15 | ❌ descartado |
| `KEV0143/Adaptive-forecasting-of-electricity-consumption-24-168-720-h-with-load-regime-conditioning` | 1627 | **0** | 0 | 2026-07-20 | ❌ descartado |

Mil setecientas estrellas con **cero forks y cero issues**, dos veces, en la misma cuenta. Un repo
técnico realmente usado genera forks: la relación fork/star del resto de esta KB va de 0.1 a 0.4.
Una relación de **0.00** con estrellas de cuatro cifras no es adopción.

**Regla de método que esta KB adopta**: ante >1000 ★, comprobar `forks_count` y `open_issues_count`
antes de escribir la fila. `stars` es el único campo de la API que se puede comprar; `forks` e
`issues` requieren que alguien use el código. Si la relación fork/star es ≈0, descartar.

### 2. Repos sin licencia: el bloqueo más caro de este pase

`NOASSERTION` se resuelve leyendo el `LICENSE` crudo. **Ausencia total de archivo de licencia** es
distinto y peor: sin concesión expresa, el código está bajo copyright exclusivo del autor y **no es
utilizable** en un entregable, por público que sea el repo.

| Repo | Qué es | Estado de licencia | Consecuencia |
|------|--------|--------------------|--------------|
| `douyimin/GEM` | *Geological Everything Model 3D*: foundation model promptable para subsuelo, zero-shot | **sin archivo de licencia en ninguna rama** | ❌ el único foundation model de subsuelo encontrado, y es inutilizable |
| `xingyuz-phd/Generic-EMT-Modeling-of-Data-Center-Load` | Modelo EMT modular de carga de datacenter con UPS centralizado | **sin licencia** | ❌ no empotrable; citable como referencia académica |
| `ames-market/AMES-V5.0` | Test bed de mercado mayorista tipo RTO/ISO de EE. UU. | `NOASSERTION`, sin licencia localizable | ❌ tratar como no utilizable hasta aclarar |
| `DatariusAI/AI-in-Energy` | Índice diario de investigación y código de IA para energía y utilities | **sin licencia** | ⚠️ útil como *fuente de vigilancia*, no como dependencia |
| `pnoker/iot-dc3` | Runtime IIoT con 36 protocolos, 1273 ★ | **licencia propia**: *"IoT DC3 License Notice, Version 2026.5"* | ⚠️ no OSI, no SPDX: un gate automático de compliance la marcará |

**`douyimin/GEM` es el caso que más duele**: resuelve exactamente lo que un cliente de O&G pediría
—interpretación de subsuelo sin entrenar por campo— y no se puede tocar. Acción concreta y barata:
abrir issue pidiendo licencia explícita. Un repo de 55 ★ y un autor académico suele responder; es la
diferencia entre una categoría bloqueada y una disponible en el próximo pase.

### 3. Licencias rescatadas leyendo el archivo crudo

| Repo | API decía | Realidad verificada | Dónde estaba |
|------|-----------|---------------------|--------------|
| `JuliaEnergy/PowerDynamics.jl` | NOASSERTION | **MIT** | `main/LICENSE` |
| `lbl-srg/modelica-buildings` | `null` (sin `LICENSE` en la raíz) | **BSD-3-Clause** | declarado en `README.md`, texto en `Buildings/legal.html` |
| `OpenLEADR/openleadr-rs` | NOASSERTION | **doble MIT / Apache-2.0** (Stichting ElaadNL) | `LICENSE-MIT` + `LICENSE-APACHE` |
| `sandialabs/quest_planning` | NOASSERTION | **BSD** (Sandia National Laboratories) | `main/LICENSE` |
| `equinor/ecalc` | NOASSERTION | **GPL** | `main/LICENSE` |

`modelica-buildings` amplía la regla del tercer pase: tras `LICENSE*`, `COPYING` y el SPDX en
`pyproject.toml`, hay un cuarto sitio donde mirar — un **`legal.html` dentro del árbol del paquete**,
referenciado sólo desde el README. 363 ★ de LBNL que un gate automático habría descartado.

### 4. Términos de búsqueda inutilizables en GitHub (ahorro de tiempo para el próximo pase)

Cuatro consultas se gastaron en ruido. Quedan registradas para no repetirlas:

| Término | Qué devuelve en realidad | Alternativa que sí funciona |
|---------|--------------------------|-----------------------------|
| `hydrogen` | **Shopify Hydrogen** (storefronts) y la drum machine Hydrogen; ~22 de 25 resultados | buscar el electrolizador o `FESTIM`, o el nombre del proyecto |
| `AMI` | Amiga, Amica, `amazon-eks-ami`, Amiibo | `"smart meter"`, `DLMS`, `COSEM`, `rtlamr` |
| `utility billing` | utilidades de software (PowerToys, lodash, winutil) | `killbill`, `openmeter`, `"meter reading"` |
| `reservoir` | **reservoir computing** (Echo State Networks, ML) | `"reservoir simulation"`, `subsurface`, `petrophysics` |

Confirma la lección del pase de automotive: **buscar el estándar o el protocolo, nunca el
sustantivo del dominio**. Las consultas productivas de este pase fueron `IEC 61850`, `OpenADR`,
`IEEE 2030.5`, `DLMS COSEM`, `DERMS` y `"battery energy storage"`.

---
*Verificado contra GitHub REST API el 2026-11-20. Re-verificar antes de citar en una propuesta.*
