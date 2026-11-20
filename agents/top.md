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

## Forecasting agéntico: la categoría que los pases 4-6 declararon ausente y el séptimo encontró (2026-11-20)

Durante cuatro pases esta KB registró que no existía un agente energético proponible fuera de lo
institucional. La corrección del séptimo pase es precisa: **no existe para operación de red, y sí
existe para forecasting.** La diferencia importa porque el forecasting es donde la IEA mide la
adopción real (≈70 % de operadores en mantenimiento y planificación, **23 % en tiempo real**).

| Nombre | Licencia | Descripción | Stars | Forks | Último push | Región origen |
|--------|----------|-------------|-------|-------|-------------|---------------|
| [TimeCopilot/timecopilot](https://github.com/TimeCopilot/timecopilot) | MIT | Framework de **forecasting agéntico**: el LLM selecciona y combina modelos de series temporales y foundation models, y explica el pronóstico. No es energético por diseño; carga y precio son su caso canónico | 643 | 89 | 2026-11-18 | North America |
| [amazon-science/chronos-forecasting](https://github.com/amazon-science/chronos-forecasting) | Apache-2.0 | Foundation models pre-entrenados de series temporales (Chronos). Sustrato zero-shot sobre el que corre lo anterior | 6328 | 774 | 2026-10-05 | North America |
| [arnaud-vs/open-predico](https://github.com/arnaud-vs/open-predico) | Apache-2.0 | Forecasting **energético** con time-series foundation models. Pequeño, pero es el puente explícito TSFM→energía | 54 | 4 | 2026-11-15 | EMEA |
| [williamhobbs/hefty](https://github.com/williamhobbs/hefty) | BSD-3-Clause | Herramientas ligeras de forecasting de corto plazo para solar, viento y carga. El *baseline* honesto contra el que medir todo lo anterior | 85 | 13 | 2026-11-13 | North America |
| [statnett/Talk2PowerSystem](https://github.com/statnett/Talk2PowerSystem) | Apache-2.0 | LLM sobre grafo de conocimiento CIM del sistema eléctrico. **Escrito por Statnett**, el TSO noruego: primer agente de red de autoría de un operador que esta KB registra | 17 | 3 | 2026-05-15 | EMEA |

⚠️ **Cómo proponer esta fila sin exagerarla.** `timecopilot` y `chronos` son de propósito general:
lo verificable es que **la cadena existe y es permisiva**, no que esté validada en despacho. La única
pieza con operación real en una utility sigue siendo [`OpenSTEF/openstef`](https://github.com/OpenSTEF/openstef)
(MPL-2.0, 184 ★, Alliander + RTE). `Talk2PowerSystem` tiene 17 ★ y último push en mayo de 2026: vale
como **precedente citable de que un TSO quiere este patrón**, no como dependencia de producto.

## Hallazgos de verificación del séptimo pase (2026-11-20)

### 1. El endpoint de verificación de esta sesión es `search/repositories`, y `repos/{owner}/{repo}` devuelve 403

El pase 6 concluyó que "el método de verificación de URLs prescrito no verifica nada". El séptimo
pase cierra la cuestión nombrando qué canal funciona y qué canal no, con el código exacto:

| Canal | Resultado | Nota |
|-------|-----------|------|
| `gh api -X GET search/repositories -f q='repo:owner/name'` | ✅ **funciona** | Es la REST API: `license.spdx_id`, `stargazers_count`, `forks_count`, `pushed_at`, `archived` son campos de primera mano |
| `gh api repos/{owner}/{repo}` | ❌ **HTTP 403** | *"GitHub access to this repository is not enabled for this session"* — el endpoint directo está limitado a los repos adjuntos a la sesión |
| `curl https://github.com/...` y `curl https://api.github.com/...` | ❌ HTTP 403 | Política del host, registrado desde el pase 5 |
| `curl https://raw.githubusercontent.com/...` | ✅ 200 | Sigue siendo la vía para leer el `LICENSE` crudo |

**Consecuencia operativa para el próximo pase:** verificar con `search/repositories` y una consulta
`repo:` por repo, con `sleep 3` entre llamadas. **51 de 51 repos nuevos resolvieron**, ninguno
archivado. No intentar `gh api repos/...`: falla siempre y parece un 404 del repo cuando es un 403 de
la sesión.

### 2. Un cero de la API de GitHub puede ser un error de sintaxis, no un gap del sector

La consulta `(electrolyzer OR hydrogen OR geothermal OR "small modular reactor") in:name,description`
devolvió **cero filas sin error**. La misma búsqueda reescrita sin paréntesis
(`hydrogen electrolyzer in:name,description,readme`) devolvió dieciséis resultados, entre ellos
`openFuelCell2`, `BattMo`, `MacroEnergy.jl`, `openTEPES` y `FINE`.

**Regla para el próximo pase:** los paréntesis agrupando `OR` dentro de un calificador `in:` hacen
que la búsqueda falle en silencio. Antes de declarar un gap, reescribir la consulta sin paréntesis.
Los "gaps" de hidrógeno, geotermia y nuclear registrados en pases anteriores deben considerarse
**sospechosos de ser artefactos de sintaxis** hasta que se reconsulten así.

### 3. Buscar el instrumento regulatorio local abre las regiones que "no tienen repos"

APAC estaba registrado como delgado. No lo era: faltaba el término. `CSIP-AUS`, `IEEE 2030.5` y `NEM`
devuelven repos australianos reales y permisivos (`open-dynamic-export` MIT, `sep2_client` Apache-2.0,
`NEMSEER` y `NEMO` GPL-3.0). Es la misma lección que el pase 6 aprendió en LATAM, generalizada:
**el término que abre una región es el nombre de su norma de conexión o de su mercado, no el nombre de
la región.** Candidatos sin explorar para el próximo pase: `CEI 0-21` (Italia), `VDE-AR-N 4105`
(Alemania), `G99` (Reino Unido), `PRODIST` (Brasil), `NOM-001-SEDE` (México).

### 4. Cuarto pase consecutivo sin agente de operación de red, ahora con medición externa

`energy agent LLM in:name,description created:>2026-09-01` y `grid OR substation OR utility agentic
... created:>2026-08-01` devuelven ruido puro (extensiones de navegador, bots de pentest, asistentes
de voz). Lo que cambia es que el hueco ya no se apoya sólo en el conteo de repos de esta KB: la
**encuesta de la IEA a operadores de red de 13 países** reporta **23 %** de uso de IA en operación en
tiempo real frente a **~70 %** en mantenimiento de activos y planificación. Dos métodos
independientes miden el mismo hueco.

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

## Cohorte LF Energy de septiembre de 2026: GNN de red y gestión de activos (quinto pase)

El 15 de septiembre de 2026 LF Energy anunció cuatro proyectos nuevos. Los cuatro existen y son
localizables; **ninguno pasa de 34 ★**. Se registran por procedencia e integrabilidad, igual que la
capa europea de arriba, y así deben presentarse.

| Nombre | Licencia | Descripción | Stars | Forks | Último push | Región origen |
|--------|----------|-------------|-------|-------|-------------|---------------|
| [energnn/energnn](https://github.com/energnn/energnn) | **MPL-2.0** | Librería de **GNN para redes de energía reales** (no sintéticas). 15 issues abiertas; creado 2025-10-16 | 34 | 4 | 2026-11-16 | EMEA |
| [assetlife-project/assetlife](https://github.com/assetlife-project/assetlife) | **Apache-2.0** | Modelado estocástico de vida de activo para decisiones de gestión de parque. **32 issues abiertas sobre 7 ★** | 7 | 3 | 2026-11-19 | EMEA |
| [SMART-HEMS-Benchmark/smart-hems-benchmark](https://github.com/SMART-HEMS-Benchmark/smart-hems-benchmark) | **MIT** | Banco de pruebas de gestión energética doméstica; el par de evaluación que le faltaba a `agentic-ai-hems` | 7 | 2 | 2026-07-09 | EMEA |
| [energnn/pypowsybl-to-energnn](https://github.com/energnn/pypowsybl-to-energnn) | **MPL-2.0** | Conversor de redes `pypowsybl` → grafo EnerGNN | 3 | 2 | 2026-10-15 | EMEA |
| [energnn/tensio](https://github.com/energnn/tensio) | **MPL-2.0** | Aplicación de EnerGNN a mejora de tensiones en redes reales | 1 | 0 | 2026-10-19 | EMEA |
| [energnn/pandapower-to-energnn](https://github.com/energnn/pandapower-to-energnn) | **MPL-2.0** | Conversor de redes `pandapower` → grafo EnerGNN | 0 | 0 | 2026-09-08 | EMEA |

**Los conversores valen más que la librería.** `energnn` sola es una librería de GNN con 34 ★: nada
que sostenga una propuesta. Los dos conversores la convierten en una capa que lee el modelo de red
que el cliente **ya tiene** en PowSyBl o en pandapower —los dos motores que esta KB ya cataloga— y lo
entrega como grafo entrenable. El valor no es el modelo: es no rehacer el modelo de red.

**Regla nueva sobre `open_issues_count`.** El cuarto pase estableció comprobar `forks_count` antes de
comprometer alcance sobre un repo de muchas estrellas. Corolario de este pase: en un repo **recién
nacido**, muchas issues abiertas son señal **positiva**. `assetlife` tiene 32 issues sobre 7 ★ y dos
meses y medio de vida: eso es un equipo trabajando, no abandono. La misma cifra en un repo de 2016
significaría lo contrario.

## Hallazgos de verificación del quinto pase (2026-11-20)

### 1. El verificador de esta KB se equivocó, y hacia el lado peligroso

Al resolver licencias leyendo el archivo crudo, el detector marcó `energnn/energnn` como **AGPL-3.0**;
la API de GitHub decía **MPL-2.0**. **Ganó la API.** El texto de la MPL-2.0 nombra la AGPL en su
propia cláusula 1.12 ("Secondary Licenses" = GPL-2.0, LGPL-2.1, AGPL-3.0), así que cualquier
detección por `grep` de *"GNU Affero"* sobre un archivo MPL produce un falso positivo de AGPL.

**Por qué importa aquí más que en otra KB:** el tercer pase estableció que MPL-2.0 es la licencia por
defecto del sector eléctrico europeo (`Grid2Op`, `PowSyBl`, `operatorfabric-core`, `ExpertOp4Grid`,
`power-grid-model-ai`, y ahora toda la familia `energnn`). Un pase futuro que "rescate licencias
leyendo el crudo" sin esta precaución **reclasificaría media KB a AGPL** e inventaría una obligación
de liberar el servicio que no existe.

**Regla:** ante conflicto entre la API y un detector de texto sobre una licencia de la familia MPL,
**gana la API**. El archivo crudo decide sólo cuando la API dice `null` o `NOASSERTION`.

### 2. Las licencias de laboratorio nacional no son BSD, y `NOASSERTION` era correcto

El cuarto pase trataba `NOASSERTION` como un defecto de la API a corregir leyendo el crudo. En los
repos de laboratorio nacional **`NOASSERTION` es exacto**: no son licencias OSI.

| Repo | La API dice | El archivo dice | Lo que cambia |
|------|-------------|-----------------|---------------|
| `NatLabRockies/resstock` | `NOASSERTION` | BSD-3 + **copyleft condicionado al tipo de redistribuidor** + marca ResStock™ | Si el cliente es universidad, laboratorio o ONG, **hay que publicar el código de la redistribución** |
| `NatLabRockies/REopt_API` | `NOASSERTION` | BSD-3 + cláusula de **designación REopt®** + no-endoso DOE | Una versión modificada no puede llamarse REopt® y debe citar el original |
| `NatLabRockies/OpenStudio` | `NOASSERTION` | BSD-3 + marca **OpenStudio®** | Igual que `EnergyPlus`: el nombre no puede ir en producto ni promoción |
| `richard-weinhold/pomato` | `NOASSERTION` | **LGPL-3.0** declarada | Copyleft de biblioteca; además sin push desde 2025-08-12 |
| `NatLabRockies/electrolyzer` | `NOASSERTION` | **Apache-2.0** limpia | Rescatada: usable sin reservas |

La cláusula de `resstock` es de un tipo que esta KB no tenía catalogado: **se activa por quién es el
cliente**, no por lo que se hace con el código.

### 3. La cola larga de agentes LLM energéticos sigue sin ser proponible

Consulta `energy agent LLM in:name,description created:>2026-06-01`: 15 resultados, **ninguno pasa de
7 ★**, la mayoría 0 ★ de autor individual y buena parte sin licencia. Lo creíble en esta categoría
sigue siendo lo institucional que ya está arriba (`PowerMCP`, `EnergyPlus-MCP`, `idfkit-mcp`,
`pypsa-mcp`). **No existe un "agente energético" open source de propósito general con tracción.**

### 4. Término de búsqueda inutilizable, añadido a la lista del cuarto pase

**`hydrogen`** no es un término energético en GitHub. `hydrogen in:name stars:>50` devuelve
`Shopify/hydrogen` (framework de comercio, 2.183 ★), `nteract/hydrogen` (plugin de Jupyter, 4.018 ★)
y `hydrogen-music/hydrogen` (caja de ritmos, 1.357 ★): **ni un resultado energético en quince**.
Lo que funciona es `electrolyzer`, `fuel cell`, `PEMFC` y la búsqueda por organización.

## Hallazgos de verificación del sexto pase (2026-11-20)

### 1. El método de verificación de URLs que esta KB tenía prescrito no verifica nada

La instrucción de ingesta dice *"verificar toda URL antes de escribirla (`curl -sI`)"*. **En este
entorno esa comprobación siempre pasa, incluso cuando el archivo no existe.** El proxy responde al
`CONNECT` con `HTTP/1.1 200 Connection Established` y `curl -sI` imprime esa línea como si fuera el
estado del recurso.

Comprobación directa, con un path inventado a propósito:

| URL | Lo que imprime `curl -sI` | Código real (`-o /dev/null -w "%{http_code}"`) |
|-----|---------------------------|------------------------------------------------|
| `raw.githubusercontent.com/PyPSA/pypsa-eur/master/LICENSE` | `200 Connection Established` | **404** |
| `raw.githubusercontent.com/PyPSA/pypsa-eur/master/LICENSES/MIT.txt` | `200 Connection Established` | 200 |
| `raw.githubusercontent.com/PyPSA/pypsa-eur/master/NONEXISTENT-FILE-XYZ` | `200 Connection Established` | **404** |

**Un 404 pasa la verificación.** Cualquier fila de cualquier pase anterior "verificada con `curl -sI`"
está verificada sólo en apariencia.

**Recetas correctas, y son dos distintas según el host:**

- Archivos en `raw.githubusercontent.com`: `curl -s -o /dev/null -w "%{http_code}" <url>`.
- **URLs de repo en `github.com`: no se pueden verificar con `curl` desde aquí.** El host devuelve
  **403** a todo por política de red, con o sin `-I`, para repos que existen. La verificación válida
  es `gh api -X GET search/repositories -f q="repo:owner/name"`, que es la API REST de GitHub y
  devuelve `license.spdx_id`, `stargazers_count`, `forks_count` y `pushed_at` de primera mano.

Esto refina el hallazgo del pase 5 (`curl github.com` = 403): el problema no es sólo que GitHub esté
bloqueado, es que **el comando devuelve éxito igualmente** y eso es peor que un fallo limpio.

### 2. `pypsa-eur` no tiene una licencia: tiene cuatro, y el `grep` de SPDX elige la equivocada

El pase 2 estableció la escalera de resolución de licencias (archivo crudo → SPDX en
`pyproject.toml`/`README` → irresuelto) y el pase 4 le añadió un cuarto sitio (`legal.html` dentro del
paquete). **`PyPSA/pypsa-eur` necesita un quinto sitio donde mirar.** El pase 5 ya había anotado este
repo como "MIT+CC-BY-4.0" en `compose/patterns.md`: la intuición era correcta y la lectura incompleta
—son **cuatro** licencias por tipo de archivo, declaradas vía REUSE— y el `README`, que es donde un
verificador miraría, da la respuesta equivocada.

| Qué se preguntó | Respuesta |
|-----------------|-----------|
| API de GitHub (`license.spdx_id`) | `null` |
| `LICENSE` en la raíz | **404** (no existe) |
| `grep SPDX` en el `README` | **`CC-BY-4.0`** ← *la licencia del propio README, no del proyecto* |
| `doc/licenses.md` + `REUSE.toml` (REUSE de la FSFE) | **código MIT**, documentación CC-BY-4.0, configuración CC0-1.0, datos CC-BY-4.0 |

**Por qué es la trampa más cara de este pase**: `pypsa-eur` es el modelo sectorial europeo más usado
de esta KB (640 ★, 494 forks). Un gate automático que leyera el SPDX del `README` lo clasificaría como
**CC-BY-4.0** —una licencia de contenido con obligación de atribución— en lugar de **MIT**. El error
va en la dirección conservadora (bloquearía un repo usable), al revés que el falso positivo de AGPL
del pase 5, pero el resultado es el mismo: una decisión de arquitectura tomada sobre un dato falso.

**Regla que se añade a la escalera**: si el repo contiene un directorio `LICENSES/` o un `REUSE.toml`,
**el proyecto es multi-licencia por tipo de archivo** y hay que leer `REUSE.toml` o `doc/licenses.md`.
Ningún `grep` de un solo archivo da la respuesta correcta en un repo REUSE. Nota práctica: el código
es MIT, así que el veredicto operativo de `pypsa-eur` **no cambia** — lo que cambia es que ahora está
justificado.

### 3. La rama por defecto no siempre es `main`, y eso produce falsos "sin licencia"

`BrandolRuizOlmeda/pypsa-mexico_base` no tiene `LICENSE` en `main` (**404**) y **sí** lo tiene en
`master` (200, MIT). Un verificador que consulte sólo `main` lo habría registrado como repo sin
licencia y lo habría descartado — el mismo veredicto que `pypsa-meets-brazil`, que sí está sin
licencia en las dos ramas. **Regla: antes de declarar "sin licencia", probar `main` y `master`.**

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

## Octavo pase (2026-11-20): observabilidad del propio stack de modelos, y el quinto cero consecutivo en operación de red

### La única novedad agéntica del pase, registrada con su tamaño real

| Nombre | Licencia | Descripción | Stars | Push | Región origen |
|--------|----------|-------------|-------|------|---------------|
| [open-energy-transition/gridlens](https://github.com/open-energy-transition/gridlens) | MIT | App *AI-native* para ver **qué modelo energético usa quién, dónde y para qué decisión de red** | 1 | 2026-11-19 | EMEA |

⚠️ **Un día de vida y 1 ★: no es una dependencia.** Se cataloga por dos razones concretas. (a) Confirma
que **Open Energy Transition** —autora de `pypsa-mcp` (MIT, 74 ★)— está construyendo deliberadamente
la capa agéntica alrededor de PyPSA, lo que convierte a esa organización en el proveedor abierto más
probable de este vertical. (b) El problema que nombra —**trazabilidad de qué modelo sostiene qué
decisión**— es el entregable que un cliente regulado pide en la primera reunión de gobernanza y que
ningún repo de esta KB cubría. Vigilar en el próximo pase; proponer sólo como patrón, no como
componente.

### Quinto pase consecutivo sin agente de operación de red, ahora medido por un canal distinto

Los pases 4-7 midieron este cero contando repos. El octavo lo midió **fuera de GitHub**: la consulta
global prescrita (`top open source AI agents energy 2026 github MIT`) devuelve exclusivamente agentes
de propósito general —OpenClaw, Hermes, OpenCode, OpenHands, CrewAI, Browser Use— **sin una sola
entrada energética**, y las fuentes se contradicen entre sí en estrellas y en licencia. Dos canales
independientes miden lo mismo, y conviene decirlo en una propuesta con esas palabras:

> La capa agéntica energética abierta hoy es **institucional** (`Power-Agent/*` MIT, `PowerMCP`,
> `EnergyPlus-MCP` BSD, `Talk2PowerSystem` Apache-2.0 de Statnett) o es **de forecasting**
> (`timecopilot` MIT, `chronos` Apache-2.0). No hay agente de operación de red con tracción de
> mercado. Quien lo necesite, lo construye — y eso es trabajo facturable, no un riesgo.

### Lo que el barrido de normas de conexión devolvió en la capa agéntica

Una sola pieza, y no es proponible: [`Nero-Engine/spark-pack-mcp`](https://github.com/Nero-Engine/spark-pack-mcp)
— servidor MCP de herramientas de cálculo eléctrico para electricistas del Reino Unido (dimensionado
de cable, Part P, verificación de certificados, **G98/G99**), **0 ★ y sin archivo de licencia**. Sin
concesión expresa es copyright exclusivo del autor. Se registra porque demuestra que **el patrón
"MCP sobre norma de conexión local" ya se le ocurrió a alguien**, y está libre: es un hueco de
producto, no un competidor.


## Hallazgos del noveno pase (2026-11-20): el agente que opera un activo, y la capa de protocolo del vehículo

### `OpenVigil`: primer agente de esta KB que implementa la autorización humana como código

| Nombre | Licencia | Descripción | ★ | Forks | Push | Región origen |
|--------|----------|-------------|---|-------|------|---------------|
| [Ninemilo/OpenVigil](https://github.com/Ninemilo/OpenVigil) | **Apache-2.0** (verificada en `LICENSE` crudo) | O&M de parque eólico de extremo a extremo: **22 agentes** en capas de decisión / revisión / ejecución, runtime de 16 tools, LangGraph + catálogo SQL gobernado de 18 tools, conectores SCADA/MQTT/HTTPS/EAM. La IA propone, **la persona autoriza lo de alto riesgo** | 180 | 37 | 2026-11-17 | **APAC** (LiteLLM → SiliconFlow / Alibaba Bailian / DeepSeek) |

**Cómo usarlo y cómo no.** Es la **plantilla** del patrón de autorización que la regla de
arquitectura de esta KB exige, ya escrita en código y con la capa de revisión separada de la de
ejecución. Pero su propio README marca **UNVERIFIED** la exactitud de campo, la calibración real, la
operación en sombra y la calificación de release; la demo sale de **fixtures deterministas, no de
modelos en vivo**; no hay releases publicados; y **no nombra ningún protocolo industrial** (ni OPC
UA ni IEC 61400-25). Benchmark **CARE v6** de Fraunhofer IEE (95 eventos, 36 activos) **no incluido**
en el repo y bajo CC BY-SA 4.0: lo aporta el operador.

→ Hallazgo de **viabilidad y diseño**, no de ranking. **No citar cifras de desempeño: no publica
ninguna.** Y verificar mantenimiento antes de depender: 180 ★ con **0 issues abiertas** en 2,5 meses
es perfil de autor único.

### Agentes y tooling agéntico: filas nuevas verificadas

| Nombre | Licencia | Descripción | ★ | Forks | Push | Región origen |
|--------|----------|-------------|---|-------|------|---------------|
| [ecog-io/iso15118](https://github.com/ecog-io/iso15118) | **Apache-2.0** | Implementación de **ISO 15118 -2, -20 y -8** (Plug & Charge). Ratio fork:★ de **0,57** = se construye sobre él | 250 | 142 | 2026-11-17 | EMEA |
| [ecog-io/josev](https://github.com/ecog-io/josev) | **Apache-2.0** | Versión comunitaria de Josev: sistema operativo para estaciones de carga V2G | 164 | 23 | 2026-11-16 | EMEA |
| [enbility/eebus-go](https://github.com/enbility/eebus-go) | **MIT** | Implementación de **EEBUS** en Go: el protocolo de flexibilidad doméstica de EMEA | 123 | 53 | 2026-11-06 | EMEA |
| [NIBEGroup/openeebus](https://github.com/NIBEGroup/openeebus) | **Apache-2.0** | EEBUS (**SHIP y SPINE**) en C, publicado por un **fabricante de bombas de calor** (NIBE Group) | 68 | 18 | 2026-11-12 | EMEA (Suecia) |
| [vinerya/virtual-power-plant](https://github.com/vinerya/virtual-power-plant) | **MIT** | Librería de gestión, simulación e investigación de **planta virtual (VPP)** | 96 | 26 | 2026-11-16 | Global |
| [jeslago/epftoolbox](https://github.com/jeslago/epftoolbox) | **Apache-2.0** | Benchmark y toolbox de **forecasting de precio eléctrico**: la vara de medir antes de prometer un modelo propio | 417 | 115 | 2026-05-18 | EMEA (España) |
| [alliander-opensource/s4casting](https://github.com/alliander-opensource/s4casting) | **MPL-2.0** | **Time series foundation models** para forecasting energético, publicado por el DSO **Alliander** | 12 | 2 | **2026-11-20** | EMEA (Países Bajos) |

### Piezas que NO se pueden proponer, y por qué

| Pieza | Problema | Consecuencia |
|-------|----------|--------------|
| [OpenLEADR/openleadr-rs](https://github.com/OpenLEADR/openleadr-rs) | **Ningún archivo de licencia** en `main`, `master` ni `develop` (107 ★, 30 forks, push 2026-11-20) | Es la **única implementación de OpenADR 3.0** encontrada y es legalmente inusable. `openleadr-python` (Apache-2.0, 161 ★) sólo cubre **2.0b** → **OpenADR 3.0 no tiene implementación abierta licenciada** |
| [runyao-yu/PriceFM](https://github.com/runyao-yu/PriceFM) | Sin licencia (158 ★) | Foundation model de precio, bloqueado |
| [california-energy-commission/MIDAS](https://github.com/california-energy-commission/MIDAS) | Sin licencia (9 ★) | Dato tarifario **oficial** de la California Energy Commission, no redistribuible |
| `pnoker/iot-dc3` *(ya en esta tabla desde un pase previo)* | `LICENSE.txt` crudo = **"IoT DC3 License Notice, Version: 2026.5"**, licencia **propia** | No es licencia estándar: revisión legal obligatoria antes de cualquier uso. La API lo informa como `NOASSERTION` |
| [matth-x/MicroOcpp](https://github.com/matth-x/MicroOcpp) | MIT pero **push 2025-12-04** y 135 issues abiertas | La pieza OCPP para microcontroladores más citada está parada: no comprometerla en firmware sin auditoría |
| [SwitchEV/RISE-V2G](https://github.com/SwitchEV/RISE-V2G) | MIT pero **push 2025-12-19** | Referencia de lectura, no base de producto |

### Confirmación independiente de las correcciones del octavo pase

Este pase re-consultó por su cuenta `CityLearn`, `Grid2Op`, `openSTEF`, `PowerGridworld`, `sinergym`
y `carbon-aware-sdk` sin mirar primero la tabla de correcciones del octavo pase, y **obtuvo los
mismos valores** que esa tabla ya registra (662 ★; 494 ★ MPL-2.0; 183-184 ★ MPL-2.0; 188 ★;
242 ★; 600 ★). No es un hallazgo nuevo: es la verificación de que la corrección del octavo pase
es correcta y reproducible. Dos licencias más quedaron confirmadas contra `LICENSE` crudo:
**`e2nIEE/pandapower` es BSD-3-Clause** (Univ. de Kassel + Fraunhofer IEE) y **`Akkudoktor-EOS/EOS`
es Apache-2.0**, pese a que la API informa `NOASSERTION` en ambos — otra instancia de T39.

---
*Verificado contra GitHub REST API el 2026-11-20 (noveno pase). Re-verificar antes de citar en una propuesta.*
