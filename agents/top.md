---
industry: energy
region: Global
updated: 2026-11-24
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
| [statnett/cimsparql](https://github.com/statnett/cimsparql) | **MIT** | Consulta de modelos **CIM** por SPARQL desde Python. Es la **mitad ejecutable** del patrón de arriba, del mismo TSO y con licencia más permisiva: `Talk2PowerSystem` es el plano, `cimsparql` es la dependencia. ⚠️ 9 issues | 10 | 7 | 2026-11-16 | EMEA |

⚠️ **Cómo proponer esta fila sin exagerarla.** `timecopilot` y `chronos` son de propósito general:
lo verificable es que **la cadena existe y es permisiva**, no que esté validada en despacho. La única
pieza con operación real en una utility sigue siendo [`OpenSTEF/openstef`](https://github.com/OpenSTEF/openstef)
(MPL-2.0, 184 ★, Alliander + RTE). `Talk2PowerSystem` tiene 17 ★ y último push en mayo de 2026: vale
como **precedente citable de que un TSO quiere este patrón**, no como dependencia de producto.

🔄 **Corrección del undécimo pase (2026-11-20), y afecta a cómo se vende esta fila.** La frase
anterior —"precedente, no dependencia"— se escribió sin haber leído el repo por dentro, porque su
README se llama `ReadMe.adoc` y la sonda a `README.md` devuelve 404 (ver T52). Leído, contiene una
**N-Shot Tool** de texto-a-SPARQL (recupera las N preguntas más similares del *dataset* de Q&A y las
pasa al modelo con sus plantillas SPARQL), un conector de recuperación vectorial (`connector.rq`) y
una ontología para **GraphDB** (`ontology.trig`). Reclasificación: es una **arquitectura de
referencia copiable**, no sólo un precedente. Lo que **no** cambia: 17 ★, push de mayo de 2026,
`Roadmap.adoc` dice literalmente *"To be addressed"*. El plano se copia; el producto se construye.

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
| ~~[OpenLEADR/openleadr-rs](https://github.com/OpenLEADR/openleadr-rs)~~ — **FILA RETIRADA EN EL PASE 13** | ❌ **El dato era falso.** `Cargo.toml` declara `license = "Apache-2.0 OR MIT"`, y `LICENSE-MIT` + `LICENSE-APACHE` devuelven **200** en `main` **y** en `master` | **Es usable: doble Apache-2.0 / MIT** (Stichting ElaadNL). OpenADR 3.0 **sí** tiene implementación abierta licenciada. Ver el decimotercer pase |
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

## Décimo pase (2026-11-20): cero agentes nuevos proponibles, y por primera vez con la forma del cero medida

**Este pase no añade ninguna fila a las tablas de arriba, y eso es el hallazgo.** La consulta
`agent energy grid in:name,description created:>2026-10-01` devuelve **33 repos creados en siete
semanas**; el mejor tiene **7 ★ y `NOASSERTION`**, y los cinco siguientes tienen **1, 0, 0, 0 y 0
estrellas, ninguno con licencia**. En MCP, `mcp energy grid created:>2026-09-01` devuelve **4 repos,
los cuatro con 0 ★**.

Es el **sexto cero consecutivo** en operación de red, y el primero que puede describirse como
distribución y no como ausencia: **hay actividad intensa y toda está por debajo del umbral de
proponible**. A un cliente que pregunte *"¿no hay ya agentes de red open source?"* se le puede
responder con número: los hay, son de una semana, de una persona y de cero estrellas.

`xvbohan92-ai/gridnote-energy-agent` (0 ★, **sin licencia**) merece mención porque **acierta en el
diseño** —LangGraph, *evidence-backed*, explícitamente **sólo lectura**—, que es la regla de
arquitectura de esta KB y la postura de `OpenVigil`. **La idea correcta circula; la base utilizable
no.**

### La capa de evaluación llega antes que la capa de agente, otra vez

El hallazgo principal del pase son dos organizaciones institucionales (EPRI, 59 repos; Grid
Protection Alliance, 66 — ver `repos/foundations.md`). **Ninguno de esos repos es un agente.** Tres
son precondición directa de uno que actúe sobre la red, y esta KB no los tenía:

| Repo | Licencia | ★ | Forks | Push | Por qué importa para la capa agéntica |
|------|----------|---|-------|------|--------------------------------------|
| [epri-dev/Universal-Semantic-Standard-Test-Harness](https://github.com/epri-dev/Universal-Semantic-Standard-Test-Harness) | **BSD-3-Clause** | 0 | 1 | 2026-08-18 | Arnés de **interoperabilidad semántica**: comprueba que lo que el sistema entendió es lo que el modelo de red dice |
| [GridProtectionAlliance/openECA](https://github.com/GridProtectionAlliance/openECA) | **MIT** | 16 | 8 | 2026-11-15 | *Extensible Control & Analytics*: el punto de inserción de un modelo en el lazo operativo. ⚠️ **20 issues** |
| [Haigutus/cim-bench](https://github.com/Haigutus/cim-bench) | **MIT** | 10 | 5 | 2026-07-16 | **Benchmarking de herramientas CIM**: comparar implementaciones antes de dejar que un modelo elija |

Patrón que esta KB registra desde el pase 4, ahora con otro signo: **cuando exista un agente de
operación de red proponible, el arnés para auditarlo ya estará escrito, en BSD-3, y nadie lo habrá
mirado** — el de EPRI tiene cero estrellas y tres meses.

### Corrección de método para la caza de agentes (ver T47)

El pase 9 estableció "buscar la norma, no el buzzword". Es correcto y **no alcanza**: las
instituciones nombran sus herramientas por el **acrónimo interno del método**, que no contiene ningún
término de categoría (`StorageVET`, `QuESt`, `openMIC`, `openXDA`, `ProGRESS`). Por eso nueve pases
no vieron ~125 repos.

**Instrucción concreta para el próximo pase:** antes de volver a barrer por buzzword agéntico,
barrer por `org:` los laboratorios e institutos que ya aparecen en esta KB — `pnnl`,
`argonne-citadel`, `lbl-srg`, `NatLabRockies`, `entsoe`, `statnett`, `alliander-opensource`,
`equinor`, `eclipse-volttron` — y comprobar si alguno publica ya capa agéntica bajo un nombre que no
dice "agent".

## Duodécimo pase (2026-11-20): el cero de agentes de operación de red se rompe, y lo rompe un TSO

**Titular del pase: después de siete u ocho pases consecutivos registrando "cero agentes de
operación de red" por consulta genérica, hay uno, es real, y no viene de un laboratorio ni de una
universidad: lo publica RTE, el operador de la red de transmisión francesa.
[`powsybl/pypowsybl-mcp`](https://github.com/powsybl/pypowsybl-mcp) (**MPL-2.0**, 7 ★, 2 forks, push
**2026-11-18**) expone pypowsybl por MCP: load flow, análisis de seguridad N-1 y análisis de
sensibilidad como llamadas de herramienta que un agente puede encadenar.**

Esto no es un hallazgo de catálogo: es la confirmación ejecutable de **T2** ("los operadores de red
se volvieron proveedores de open source"). Hasta este pase, T2 se apoyaba en repos de *modelado* y
de *interoperabilidad* publicados por TSOs. Ahora el TSO publica la **capa agéntica** sobre su
propio motor de red.

| Agente | Repo | Licencia | ★ / forks | Push | Qué hace |
|---|---|---|---|---|---|
| **pypowsybl-mcp** | [powsybl/pypowsybl-mcp](https://github.com/powsybl/pypowsybl-mcp) | **MPL-2.0** | 7 / 2 | 2026-11-18 | Servidor MCP de RTE sobre pypowsybl: load flow, seguridad N-1, sensibilidad, diagramas y exportación, como herramientas MCP |
| **PowerMCP** | [Power-Agent/PowerMCP](https://github.com/Power-Agent/PowerMCP) | MIT | 238 / 67 | 2026-11-17 | Colección de servidores MCP sobre PowerWorld, PSS/E y OpenDSS (ya catalogado; **re-medido** este pase) |
| **opendss-mcp-server** | [ahmedelshazly27/opendss-mcp-server](https://github.com/ahmedelshazly27/opendss-mcp-server) | MIT | 4 / 3 | 2025-10-28 | MCP sobre OpenDSS para análisis de distribución; publicado en PyPI |
| **UBEM-MCP** | [TensorBuildLab/UBEM-MCP](https://github.com/TensorBuildLab/UBEM-MCP) | BSD-3-Clause | 1 / 0 | 2026-10-26 | MCP de modelado energético urbano de edificios a escala de ciudad |
| **octavius-energy-lab** | [saptiva-ai/octavius-energy-lab](https://github.com/saptiva-ai/octavius-energy-lab) | Apache-2.0 | 0 / 0 | 2026-11-10 | **Andamiaje**, no producto: banco de evaluación de *agent harnesses*; ver la advertencia abajo |

### Detalle operativo de `pypowsybl-mcp`, que decide si se puede proponer

- **Transporte: streamable HTTP, no stdio.** El servidor PyPowsybl debe estar **ya corriendo** antes
  de que el cliente (Codex, Claude Desktop, Cursor o un agente propio) se conecte. Esto no es un
  detalle de confort: cambia el despliegue, porque obliga a un servicio gestionado con ciclo de vida
  propio en vez de un subproceso del cliente.
- **Sesiones en memoria.** El modelo de red se mantiene en memoria y con el agente sólo se
  intercambian identificadores de sesión y resúmenes filtrados. Dos consecuencias opuestas y las dos
  importan: (1) es la decisión *correcta* de privacidad e de contexto —el modelo de red no se vuelca
  al LLM—; (2) **el estado se pierde al reiniciar el proceso**, así que cualquier estudio largo
  necesita persistencia propia por encima.
- **Autoría y procedencia.** Cabecera `Copyright (c) 2026, RTE`; autores Jérôme Picault y Clément
  Goubet (RTE). Paper de posición: **arXiv 2607.14158**, que lo describe como usado internamente en
  RTE y liberado.
- **Madurez real: baja.** 7 ★ y ~2 forks. PRs recientes abiertos sobre creación/eliminación de
  elementos de red y migración al SDK Python de MCP v2 (`mcp>=2,<3`). Es **un cimiento institucional
  joven**, no una pieza estabilizada: proponerlo exige decir que se va a contribuir a él.
- **MPL-2.0**, no MIT: copyleft por archivo. Se puede enlazar desde código propietario, pero los
  archivos modificados del propio servidor se publican. Coincide con la nota de licencia del tercer
  pase (MPL-2.0 es la licencia por defecto del sector eléctrico europeo).

### La advertencia que evita una propuesta falsa: `octavius-energy-lab` es andamiaje

`saptiva-ai/octavius-energy-lab` (Apache-2.0, Saptiva, México) aparece en búsqueda como lo que esta
KB llevaba pases pidiendo: **un repo agéntico energético de origen LATAM**. Se leyó el README
completo antes de catalogarlo, y la lectura cambia la ficha:

- El propio README dice que **el dominio energético "no está todavía en este árbol"**: CENACE y Low
  Carbon London son los datasets *previstos*, y entran en fases posteriores como plugins MCP.
- **Qwen3-8B** (LLM local) y **TimesFM** (forecasting) están **nombrados, no integrados**. Y anota
  que los pesos de **TimesFM 3.0 son de uso no comercial** — restricción que invalida el camino de
  producción aunque el repo sea Apache-2.0.
- Lo que sí existe y funciona es la **plataforma**: Next.js 15 / React 19, backend FastAPI con
  orquestador de *tool-calling*, MongoDB/Redis/MinIO/Weaviate por Docker Compose, observabilidad
  OpenTelemetry/Prometheus/Grafana/Loki, y `make dev` / `make test`.
- Metodología de evaluación: una sola regla declarada, **"no optimizar el benchmark para que el
  harness parezca bueno"**. El diseño vive en `docs/`, no en el README.
- 0 ★, 0 forks. El README se autodescribe como **"el punto de partida"**.

**Veredicto honesto: no es el agente energético LATAM. Es la declaración de intención de una empresa
mexicana de IA de construirlo, con la plataforma ya montada y el dominio vacío.** Vale como señal de
mercado (hay quien lo está intentando desde la región, con licencia permisiva y con criterio de
evaluación explícito) y **no** vale como cimiento técnico que un engagement pueda reutilizar hoy.
Volver a medirlo el próximo pase: si el dominio energético aterriza, pasa a ser el primer banco de
evaluación agéntico energético de origen LATAM.

### La cola larga de MCP energético, medida entera y con el mismo veredicto que el quinto pase

El quinto pase escribió que "la cola larga de agentes LLM energéticos sigue sin ser proponible". Este
pase la **midió completa** en vez de afirmarlo: ocho servidores MCP energéticos encontrados por
búsqueda, todos verificados por API.

| Repo | Licencia | ★ / forks | Push | Nota |
|---|---|---|---|---|
| [karthikravva/MCP-Energy-Hub](https://github.com/karthikravva/MCP-Energy-Hub) | MIT | 2 / 0 | 2025-12-05 | Red de EEUU vía EIA, orientado a *carbon-aware* |
| [kasathur/energyatit-mcp-server](https://github.com/kasathur/energyatit-mcp-server) | MIT | 1 / 0 | 2026-02-14 | Se autodescribe "first and only energy MCP server" — **es falso**, y el propio repo es de 1 ★ |
| [mattoddie/octopus-mcp](https://github.com/mattoddie/octopus-mcp) | MIT | 1 / 0 | 2026-11-19 | Octopus Energy (GB): consumo, tarifas Agile, facturas; read-only salvo activación |
| [mrksmts/homewizard-mcp-server](https://github.com/mrksmts/homewizard-mcp-server) | MIT | 1 / 0 | 2026-04-26 | API local HomeWizard (contador P1), read-only |
| [TensorBuildLab/UBEM-MCP](https://github.com/TensorBuildLab/UBEM-MCP) | BSD-3-Clause | 1 / 0 | 2026-10-26 | UBEM a escala de ciudad |
| [jalcodev/gridhub-mcp](https://github.com/jalcodev/gridhub-mcp) | MIT | 0 / 0 | 2026-09-27 | 25 zonas de red (ISOs EEUU, UE, GB, AU); **servicio hospedado**, no autoinstalable |
| [szl-holdings/szl-energy-mcp](https://github.com/szl-holdings/szl-energy-mcp) | Apache-2.0 | 0 / 0 | 2026-11-19 | Medición con *receipt-gating* (sha256 por resultado), fail-closed, cero dependencias |
| [ahmedelshazly27/opendss-mcp-server](https://github.com/ahmedelshazly27/opendss-mcp-server) | MIT | 4 / 3 | 2025-10-28 | El único de la cola con forks > 0 |

**Rango completo: 0–4 ★. Ninguno pasa de 4.** La frontera no es la licencia (son casi todos MIT o
Apache-2.0, es decir, el perfil que Globant puede usar) ni la actividad (cinco con push en 2026). La
frontera es que **no hay comunidad detrás de ninguno**: sin forks, sin issues, sin segundo
mantenedor. Para un engagement eso significa que **la cola larga de MCP energético es material de
referencia y de copia de patrón, no dependencia**. El contraste con `pypowsybl-mcp` (7 ★ pero RTE
detrás) y con `Power-Agent/PowerMCP` (238 ★, 67 forks) es el dato: en esta categoría **la procedencia
institucional pesa más que las estrellas**.

### Hallazgos de verificación del duodécimo pase

#### 1. `search/repositories` **excluye los forks**, y por eso un `NOTFOUND` no significa "no existe"

Este es el hallazgo de método más reutilizable del pase, y casi produjo una ficha falsa.

La búsqueda devolvió `CorradoMariaCaminiti/PowerMCP` con una descripción completa y creíble
("colección open source de servidores MCP para PowerWorld, PSSE y OpenDSS"). El verificador de esta
KB —`gh api -X GET search/repositories -f q="repo:owner/name"`— respondió **`NOTFOUND`**. Según la
regla escrita en pases anteriores ("un 404 no es un hallazgo"), ahí había que descartarlo.

Se cruzó con el otro canal antes de descartar:

```
curl -sI https://raw.githubusercontent.com/CorradoMariaCaminiti/PowerMCP/main/README.md  -> 200
```

**El repo existe.** Es un **fork** de [`Power-Agent/PowerMCP`](https://github.com/Power-Agent/PowerMCP)
(MIT, **238 ★**, 67 forks, push 2026-11-17), que esta KB ya tenía catalogado. La API de búsqueda de
GitHub **no indexa forks por defecto**, de modo que el canal de verificación de esta KB es
estructuralmente ciego a ellos.

Las dos consecuencias operativas, y tiran en direcciones opuestas:

1. **`NOTFOUND` del canal de búsqueda ≠ inexistente.** Significa "no existe *como repo fuente
   indexado*". Antes de registrar un gap por esta vía, cruzar con `raw.githubusercontent.com`.
2. **Y al revés, que es el riesgo real: un resultado de búsqueda web puede ser un fork, y el fork se
   cataloga igual de bien que el original.** Si la verificación hubiera sido sólo
   `curl raw.githubusercontent.com` —el canal que esta KB adoptó tras el sexto pase—, este fork de 0 ★
   habría entrado en la tabla como hallazgo, desplazando al upstream de 238 ★. **La defensa es que
   `NOTFOUND` en búsqueda + `200` en raw es la firma exacta de un fork**, y obliga a buscar el
   upstream.

Regla para los próximos pases: **`NOTFOUND` en búsqueda con `200` en raw ⇒ es un fork ⇒ catalogar el
upstream, no el que devolvió la búsqueda.**

#### 2. `NOASSERTION` fuera del laboratorio nacional es un **falso negativo**, no un dato

El quinto pase escribió **T24**: "`NOASSERTION` en un laboratorio nacional no es un defecto de la
API: es el dato correcto". Este pase encontró cuatro repos `NOASSERTION` **fuera** de ese perfil
(TSO europeo y universidad australiana) y los resolvió leyendo el fichero de licencia. **Tres de los
cuatro tenían una licencia OSI perfectamente estándar**, invisible para la API sólo por el formato
del fichero:

| Repo | API dijo | El fichero dice | Por qué falló la detección |
|---|---|---|---|
| [Energinet-SimTools/IMTB](https://github.com/Energinet-SimTools/IMTB) | `NOASSERTION` | **MPL-2.0** | `LICENSE.md` con la MPL **reescrita en Markdown** (`# Mozilla Public License`, `### 1.1.`) — el *matcher* no reconoce el texto reformateado |
| [UNSW-CEEM/NEMOSIS](https://github.com/UNSW-CEEM/NEMOSIS) | `NOASSERTION` | **GPL-3.0-or-later** | Cabecera GPL **indentada y precedida del nombre del programa**, no el texto canónico al inicio del fichero |
| [AlexanderHoogsteyn/ClariGrid](https://github.com/AlexanderHoogsteyn/ClariGrid) | `NOASSERTION` | **Apache-2.0** | Texto Apache íntegro y canónico; falso negativo sin causa aparente |
| [Energinet-SimTools/MTB](https://github.com/Energinet-SimTools/MTB) | `NOASSERTION` | **NO es OSI** (ver §3) | Aquí `NOASSERTION` era correcto, y además hacia el lado peligroso |

**T24 queda cualificada, no derogada:** `NOASSERTION` no es un dato, es **una pregunta sin
responder**. En laboratorio nacional norteamericano suele resolverse en licencia propia (lo que T24
midió). En TSO europeo y universidad, **suele resolverse en licencia OSI estándar mal formateada**.
La única lectura válida en los dos casos es abrir el fichero. Y el coste de no abrirlo es asimétrico:
descartar `NEMOSIS` (113 ★, el repo más estrellado del stack australiano) por "sin licencia" es
perder la pieza central de una región entera; dar por permisivo el `MTB` de Energinet es un riesgo
contractual.

Sondas que hay que probar, en este orden, antes de concluir cualquier cosa:
`LICENSE`, `LICENSE.md`, `LICENSE.txt`, `COPYING`, `LICENCE` × ramas `main`, `master`.

#### 3. Existe la licencia **revocable**, y ningún `grep` de SPDX la detecta

[`Energinet-SimTools/MTB`](https://github.com/Energinet-SimTools/MTB) (**83 ★**, 24 forks, push
2026-11-19) es el repo más estrellado del TSO danés y **no es open source**. Su `LICENSE.md` no
nombra ninguna licencia: es un texto de "consideraciones de uso" propio de Energinet. Lo que
concede y lo que se reserva, verbatim:

- Concede **"a worldwide, non-exclusive, non-payable right to use, modify and distribute the MTB"**,
  entero o en partes.
- **Y se lo puede quitar: "Energinet may withdraw or modify the right to use, modify and
  distribute."**
- **"All intellectual property rights, including copyright to the MTB remains at Energinet."**
- Los resultados son **"indicative and for informational purposes only"**; sólo el ensayo de
  Energinet en su propio entorno es concluyente.
- Uso **"at the facility owners and the users own risk"**, sin responsabilidad por daños.

Un permiso **revocable unilateralmente** es incompatible con la definición de open source (no hay
licencia OSI que permita retirar el derecho ya concedido) y es **incompatible con construir un
entregable de cliente encima**: el riesgo no es de atribución, es de continuidad del derecho de uso.

Y es indetectable por automatismo: no hay cadena SPDX que *grepear*, no hay `MIT`, no hay `Apache`,
no hay `GPL`. Un verificador que busque identificadores de licencia **no encuentra nada y clasifica
el repo como "sin licencia"** — es decir, en la categoría de T20 ("bloqueada, distinta de ausente"),
que es la clasificación práctica correcta aunque por el motivo equivocado. Ver **T33**.

**Cómo usar el MTB de todas formas, porque es útil:** como **especificación de requisitos de
prequalificación de Energinet**, que es lo que de hecho es. Un proyecto de cumplimiento de red en
Dinamarca necesita saber qué comprueba el MTB; eso se lee del repo sin incorporar su código. Lo que
no se puede es empaquetarlo dentro de una herramienta propia y vendérsela a un cliente.

## Decimotercer pase (2026-11-20): la KB tenía la respuesta correcta y la perdió; y aparece la capa de medición

**Titular del pase: el hallazgo no es un repo, es un error de esta KB que habría costado una
decisión de arquitectura en un encargo real.** Durante dos pases la KB afirmó que
[`OpenLEADR/openleadr-rs`](https://github.com/OpenLEADR/openleadr-rs) no tenía licencia y que
**"OpenADR 3.0 no tiene implementación abierta licenciada"** (T45), y recomendaba en consecuencia
entregar sobre 2.0b, negociar licencia durante semanas o reimplementar 3.0 desde la especificación.
**Las tres recomendaciones eran innecesarias.** `Cargo.toml` declara
`license = "Apache-2.0 OR MIT"`, y `LICENSE-MIT` y `LICENSE-APACHE` devuelven **200** en `main` y en
`master`.

### Lo que lo convierte en lección y no en erratum: era una regresión, no un hueco

La parte incómoda es que **esta KB ya lo había resuelto bien**. En `agents/top.md`, en una tabla
titulada *"Licencias rescatadas leyendo el archivo crudo"*, consta desde un pase anterior:

```
| `OpenLEADR/openleadr-rs` | NOASSERTION | doble MIT / Apache-2.0 (Stichting ElaadNL) | `LICENSE-MIT` + `LICENSE-APACHE` |
```

Un pase posterior volvió a medirlo con una lista de sondas más corta (`LICENSE`, `LICENSE.md`,
`LICENSE.txt`, `COPYING`, `LICENCE`), obtuvo 404 en las tres ramas —correctamente, porque ninguno de
esos archivos existe— y **escribió la conclusión contraria sin consultar el registro propio**. El
dato falso se propagó a tres archivos (`agents/top.md`, `compose/patterns.md`, `intel/trends.md`) y
generó una receta entera construida sobre él.

**La regla que sale de aquí, y es la más barata de aplicar de toda esta KB:**

> **Antes de escribir un hallazgo negativo —"sin licencia", "cero repos", "no existe"— buscar la
> entidad en la propia KB.** Si ya hay un registro positivo, el nuevo negativo **tiene que explicar
> la discrepancia**, no sobrescribirla. Un negativo nuevo no gana a un positivo verificado sólo por
> ser más reciente.

El coste asimétrico es evidente: un falso positivo mete un repo malo en una tabla; un falso negativo
**borra una capacidad entera del catálogo** y nadie vuelve a buscarla, porque ya está "medida".

### Lista de sondas de licencia, corregida (ver T46)

Leer **primero el manifiesto del gestor de paquetes**, que declara la licencia como expresión SPDX
del propio autor: `Cargo.toml` (`license =`), `pyproject.toml`, `package.json`, `pom.xml`,
`*.csproj`. Sólo después los archivos: `LICENSE`, `LICENSE.md`, `LICENSE.txt`, **`LICENSE-MIT`**,
**`LICENSE-APACHE`**, `COPYING`, `LICENCE`, × ramas `main`, `master`, `develop`.

Firma diagnóstica a memorizar: **`LICENSE` da 404 en todas las ramas y el repo está vivo y con
tracción** ⇒ no es un repo sin licencia, es un repo cuyo archivo de licencia se llama de otra manera.

## Capa nueva de este pase: modelos de datos de medición y de DER

Hasta este pase la KB cubría el **motor** de red (pypowsybl, pandapower, PyPSA), los **entornos RL**,
los **protocolos de carga** (OCPP, ISO 15118, EEBUS) y la **capa agéntica** (MCP). Faltaba la capa de
abajo: **cómo se leen el medidor y el inversor, y con qué modelo de datos**. Son las piezas que
convierten un piloto de agente en algo que toca hardware real del cliente.

Se abrió con tres términos de protocolo —`SunSpec`, `IEC 62056`, `SAREF`— aplicando la regla del
pase 8 (*buscar el protocolo máquina-a-máquina, no la norma documental*). **Doce repos nuevos,
todos verificados contra `search/repositories` por consulta `repo:` exacta, ninguno archivado.**

### Modelo de datos de DER e inversores (SunSpec)

| Nombre | Licencia | Descripción | Stars | Forks | Último push | Región origen |
|--------|----------|-------------|-------|-------|-------------|---------------|
| [sunspec/models](https://github.com/sunspec/models) | **Apache-2.0** | **Definiciones de modelos SunSpec** publicadas por la propia alianza: es el diccionario de datos normativo de inversores y DER. La pieza de referencia, no una implementación de terceros | 135 | 67 | 2026-08-20 | North America |
| [sunspec/pysunspec2](https://github.com/sunspec/pysunspec2) | **Apache-2.0** | Librería Python oficial para hablar con dispositivos SunSpec (Modbus TCP/RTU) | 76 | 32 | 2026-10-21 | North America |
| [CJNE/ha-sunspec](https://github.com/CJNE/ha-sunspec) | **MIT** | Integración SunSpec/Modbus para Home Assistant: el camino más corto a un banco de pruebas con inversor real | 90 | 27 | 2026-11-19 | EMEA |
| [WillCodeForCats/solaredge-modbus-multi](https://github.com/WillCodeForCats/solaredge-modbus-multi) | **Apache-2.0** | Integración SolarEdge completa por Modbus/TCP, multi-inversor | 343 | 29 | 2026-11-19 | North America |
| [volkszaehler/mbmd](https://github.com/volkszaehler/mbmd) | **BSD-3-Clause** | *ModBus Measurement Daemon*: lectura de medidores e inversores por Modbus, en Go | 281 | 95 | 2026-11-09 | EMEA (Alemania) |

### Lectura de medidores (IEC 62056 / DLMS-COSEM / OBIS)

| Nombre | Licencia | Descripción | Stars | Forks | Último push | Región origen |
|--------|----------|-------------|-------|-------|-------------|---------------|
| [marq24/ha-tibber-pulse-local](https://github.com/marq24/ha-tibber-pulse-local) | **Apache-2.0** | Lectura **local** (sin nube) del Tibber Pulse por LAN. El repo más estrellado y limpio de esta capa: 0 issues abiertas | 297 | 20 | 2026-11-08 | EMEA |
| [pwitab/iec62056-21](https://github.com/pwitab/iec62056-21) | **BSD-3-Clause** | Librería Python de **IEC 62056-21** (antes IEC 1107): lectura local de medidores de energía | 89 | 25 | 2026-04-13 | EMEA (Suecia) |
| [lvzon/dsmr-p1-parser](https://github.com/lvzon/dsmr-p1-parser) | **Apache-2.0** | Parser en C (Ragel) del puerto **P1** DSMR y telegramas IEC 62056-21 asimilables | 60 | 14 | 2026-02-27 | EMEA (Países Bajos) |
| [Apollon77/smartmeter-obis](https://github.com/Apollon77/smartmeter-obis) | **MIT** | Lectura y parseo de protocolos de medidor que siguen la lógica de números **OBIS**, normalizando varios fabricantes | 57 | 20 | 2026-06-04 | EMEA |

### Ontología y grafo semántico de energía (SAREF)

| Nombre | Licencia | Descripción | Stars | Forks | Último push | Región origen |
|--------|----------|-------------|-------|-------|-------------|---------------|
| [JBjoernskov/Twin4Build](https://github.com/JBjoernskov/Twin4Build) | **MIT** | Gemelo digital de edificio: simulación dinámica con modelos diferenciables **integrada con modelos semánticos**. La pieza que une ontología y simulación | 31 | 13 | 2026-11-18 | EMEA (Dinamarca) |
| [NeverBlink-OSS/saref-linkml](https://github.com/NeverBlink-OSS/saref-linkml) | **BSD-3-Clause** | Las ontologías **SAREF** expresadas en **LinkML**: convierte el estándar semántico europeo en esquemas y código generables | 11 | 1 | 2026-11-09 | EMEA |
| [sensorlab/energy-knowledge-graph](https://github.com/sensorlab/energy-knowledge-graph) | **BSD-3-Clause** | Grafo de conocimiento de consumo energético a partir de datasets de medición | 9 | 3 | 2026-08-24 | EMEA (Eslovenia) |
| [open-renewable-energy-systems/gaifare](https://github.com/open-renewable-energy-systems/gaifare) | **Apache-2.0** | *Generative AI For Autonomous Renewable Energy*: andamiaje temprano, se cataloga como **pieza a vigilar**, no como base | 10 | 1 | 2026-09-12 | EMEA |

### Capa OpenADR 3.0, ahora que se sabe que es usable

| Nombre | Licencia | Descripción | Stars | Forks | Último push | Región origen |
|--------|----------|-------------|-------|-------|-------------|---------------|
| [OpenLEADR/openleadr-rs](https://github.com/OpenLEADR/openleadr-rs) | **Apache-2.0 OR MIT** | **VTN + VEN de OpenADR 3.0** en Rust (Stichting ElaadNL). Licencia **rectificada en este pase**: ver T45/T46 | 107 | 30 | 2026-11-20 | EMEA (Países Bajos) |
| [ElaadNL/openadr3-client](https://github.com/ElaadNL/openadr3-client) | **Apache-2.0** | Cliente **BL + VEN** de OpenADR 3.0 en Python, del mismo origen que `openleadr-rs`: permite equipo Python sin salir de la versión 3.0 | 6 | 3 | 2026-11-19 | EMEA (Países Bajos) |
| [eclipse-volttron/volttron-openadr-ven](https://github.com/eclipse-volttron/volttron-openadr-ven) | **Apache-2.0** | Agente **VEN** sobre VOLTTRON: conecta la capa de respuesta a la demanda con el framework de agentes de edificio del PNNL que esta KB ya cataloga | 6 | 6 | 2026-07-21 | North America |

## El hallazgo de riesgo del pase: la capa de medición es donde se concentran las licencias no-OSI

Esta capa es **populosa, viva y engañosa**. De los repos con más tracción del barrido, **cuatro no se
pueden usar en un entregable de cliente**, y ninguno de los cuatro es detectable por *grep* de SPDX:
la API de GitHub informa `NOASSERTION` en todos. El pase 12 descubrió la licencia **revocable**
(Energinet `MTB`, T33); este pase encuentra que no era un caso aislado sino **una familia**.

| Repo | ★ / forks | Lo que dice el archivo | Por qué bloquea |
|------|-----------|------------------------|-----------------|
| [UtilitechAS/amsreader-firmware](https://github.com/UtilitechAS/amsreader-firmware) | **471** / 88 | **Fair Source License 0.9**, con **`Use Limitation: 5 users`** | Permiso con **tope de 5 usuarios**. No es open source y es **incompatible con cualquier despliegue de cliente**: el límite no se negocia con atribución, se negocia con el licenciante |
| [bolagnaise/PowerSync](https://github.com/bolagnaise/PowerSync) | 96 / 24 | **PolyForm Noncommercial 1.0.0** | **Prohíbe el uso comercial.** Un encargo de Globant es uso comercial por definición. Bloqueo total, no condicional |
| [binsentsu/home-assistant-solaredge-modbus](https://github.com/binsentsu/home-assistant-solaredge-modbus) | **420** / 91 | **Ningún archivo de licencia** en ninguna rama probada | 420 ★ sin licencia. Bloqueado por T20; usar `WillCodeForCats/solaredge-modbus-multi` (Apache-2.0, 343 ★) que cubre lo mismo |
| [matthijskooijman/arduino-dsmr](https://github.com/matthijskooijman/arduino-dsmr) | 145 / **123** | **Ningún archivo de licencia**; último push **2023-11-08** | Sin licencia **y** parado tres años, con una proporción fork/★ de 0,85 que indica que se usa copiando código. Usar `lvzon/dsmr-p1-parser` (Apache-2.0) |
| [scs/smartmeter-datacollector](https://github.com/scs/smartmeter-datacollector) | 95 / 34 | **GPL-2.0-only** (SPDX explícito en el archivo) | OSI, pero **copyleft fuerte**: utilizable como servicio separado, **no** enlazable dentro de un producto propietario del cliente. Decisión de arquitectura, no bloqueo |

Y el matiz que evita el error inverso: **"no-OSI" no significa automáticamente "bloqueado"**.
[`universaldevices/oadr30`](https://github.com/universaldevices/oadr30) (10 ★) trae una *"Universal
Devices Free/MIT License"* de redacción propia que concede *"free to use/distribute/share/modify with
no attribution"* — **permisiva en sustancia** aunque no sea un identificador OSI. Requiere lectura
legal, no descarte. La conclusión correcta sobre un archivo de licencia no estándar es siempre
**"hay que leerlo"**, en los dos sentidos.

**Lo que esto cambia en una propuesta:** si un cliente pide "leer sus medidores y sus inversores", la
capa existe y es rica, pero **el filtro de licencia hay que correrlo repo por repo y leyendo el
archivo**, porque es la capa de la KB con mayor densidad de licencias raras. El subconjunto limpio y
proponible de este pase son las **16 filas de las cuatro tablas de arriba**; las 5 de esta tabla son
las que hay que saber descartar antes de que aparezcan en un diagrama.

## Términos de búsqueda inutilizables añadidos en este pase

Se suman a la lista acumulada (`hydrogen`, `AMI`, `utility billing`, `reservoir`, `PRODIST`):

| Término | Resultados | Qué devuelve en realidad | Lección |
|---------|-----------|--------------------------|---------|
| `IEEE 1547` | 460 | `PENTESTING-BIBLE` (14.028 ★), redes de recomendación con GNN, *optical flow*, listas de papers de ICRA | **Un número de norma a secas no es un término de búsqueda.** "1547" coincide con cualquier cita bibliográfica, número de línea o identificador. Hay que pegarle una palabra de dominio (`IEEE 1547 interconnection DER`) o usar el protocolo que la implementa (**IEEE 2030.5**), que sí es buscable |
| `virtual power plant DER aggregation` | 96 | diseño de proteínas con deep learning, *conformal prediction*, Segment Anything, herramientas Hi-C | **Una frase genérica larga en inglés ya no discrimina: coincide con `awesome-*`.** Las listas curadas contienen todo el vocabulario técnico del mundo, así que cuanto más genérica la frase, más listas devuelve y menos repos de dominio |

Corolario de método, que vale para toda la rotación: los dos fallos tienen la **misma causa** —el
término no es *específico del dominio*, sino *frecuente en todo el corpus*. El discriminador bueno es
siempre el **nombre propio de un artefacto técnico**: un protocolo (`IEC 62056`, `SunSpec`,
`OpenADR 3.0`), una ontología (`SAREF`), un formato (`OBIS`, `P1 DSMR`) o una organización (`org:sunspec`).

*Verificado contra la GitHub REST API (`search/repositories`, consulta `repo:` exacta) y contra
`raw.githubusercontent.com` el 2026-11-20 (decimotercer pase). Re-verificar antes de citar en una propuesta.*

## Decimocuarto pase (2026-11-21): la NERC escribió la restricción de arquitectura que esta KB ya exigía, y el "cero de cumplimiento" era falso

**El hallazgo de agentes de este pase no es un repo: es que el regulador de referencia de NA
publicó la regla de diseño.** La guía de **NERC** sobre IA en el sistema eléctrico establece que la
IA debe ser **herramienta de apoyo a la decisión, no controlador autónomo**.

Esa es, literalmente, la restricción que las recetas de esta KB ya imponían (*"el texto de
razonamiento nunca llega al actuador"*). Lo que cambia es **el estatus del argumento**:

| Antes de este pase | Después |
|--------------------|---------|
| *Human-in-the-loop* = buena práctica de ingeniería defendida por el proveedor | *Human-in-the-loop* = **lectura publicada del regulador de referencia** |
| "Conviene no escribir en el lazo de control" | "Escribir en el lazo de control es **contrario a la guía de NERC**" |

**Consecuencia para el catálogo de agentes:** el techo de los agentes energéticos en NA **no es
técnico ni de licencia, es regulatorio**, y está donde esta KB ya lo había puesto. Todo agente de
las tablas de este archivo se propone como **copiloto de sala de control o de ingeniería**, nunca
como actuador — y ahora eso se puede justificar citando a NERC en lugar de argumentándolo.

> **Dato que cierra el círculo:** la IEA, citada por el ADB (jun-2026), afirma que **la adopción de
> IA sigue siendo limitada en la operación de red crítica para el sistema** incluso donde el valor es
> claro. Esta KB midió ese mismo cero **siete u ocho pases seguidos contando repos**. Ahora hay
> **dos mediciones independientes** —una de oferta (GitHub) y una de demanda (IEA)— que coinciden.
> Un cero medido dos veces por canales distintos deja de ser un límite del método y pasa a ser un
> hecho del sector, y se puede escribir así en una propuesta.

### La capa de cumplimiento: el "cero de NERC CIP" era falso, pero la conclusión comercial casi no cambia

El registro decía *"**cero** herramientas del sector frente al plazo de diciembre de 2026"*. Era un
cero del instrumento: la consulta corta `topic:nerc-cip` devuelve **21 repos**. Pero medido con
honestidad, **lo que hay son plantillas, no herramientas**:

| Pieza | Licencia | Qué es realmente | ★ / forks / issues | Push |
|-------|----------|------------------|--------------------|------|
| [ynotbhatc/rego_policy_libraries](https://github.com/ynotbhatc/rego_policy_libraries) | **Apache-2.0** | **Política ejecutable en OPA Rego v1** (CIS, DISA STIG, NIST, incluye NERC). Lo único *ejecutable* del grupo, y **no es específico de energía** | 23 / 2 / **17** | 2026-11-20 |
| [mizcausevic-dev/nerc-cip-readiness-evidence-bundle](https://github.com/mizcausevic-dev/nerc-cip-readiness-evidence-bundle) | **MIT** | Perfil de *evidence bundle* CIP-002→CIP-014 + TSA SD-2021-02C | 1 / — / — | 2026-05-31 |
| [gridsafetechnology-tech/nerc-cip-checklists](https://github.com/gridsafetechnology-tech/nerc-cip-checklists) | **MIT** | Checklists en **YAML** (CIP-002, CIP-003-9 *low impact*, CIP-010) | 0 / — / — | 2026-11-07 |
| [mizcausevic-dev/grid-decision-record-audit-stream](https://github.com/mizcausevic-dev/grid-decision-record-audit-stream) | **MIT** | **Eventos de decisión de IA encadenados por hash** para auditoría NERC | 0 / — / — | 2026-10-31 |

**El último merece atención aparte** aunque tenga 0 ★, porque describe **exactamente el entregable
que la guía de NERC vuelve obligatorio**: si la IA es apoyo a la decisión, hay que **poder demostrar
qué decidió, cuándo y con qué datos**. Un registro de decisiones encadenado por hash es la forma
canónica de eso. **No se recomienda el repo** (0 ★, un autor, un mes) — se recomienda **el patrón**,
y construirlo es trabajo facturable.

> **La frase honesta para una propuesta:** *"existen al menos ocho proyectos abiertos de cumplimiento
> NERC CIP con licencia permisiva; ninguno pasa de 23 ★ y los específicos del estándar son plantillas
> y checklists, no herramientas ejecutables. Hay material de arranque; no hay producto."* Es un hueco
> de **producto**, no de búsqueda, y ahora está **cuantificado** en lugar de afirmado.

### Precisión de licencia que afecta a cómo se compone un agente sobre un EMS

`OpenEMS` **no es AGPL-3.0 a secas**: Edge y Backend son **EPL-2.0** y sólo la UI es AGPL-3.0
(byte-read de los dos archivos; ver `verticals/solutions.md` y T55 en `intel/trends.md`). Para la
capa agéntica eso significa que **un agente MIT puede integrarse con el Backend de `OpenEMS` sin
que la cláusula de red entre en juego**, lo que hasta este pase esta KB daba por imposible.

---

## Pase 15 (2026-11-21) — cuatro agentes nuevos, y el incipit de MIT deja de servir como identificador

Las cuatro filas siguientes se añaden con **licencia leída byte a byte** (no por campo SPDX de la
API) y con estrellas/forks fijados **todos con el índice de búsqueda de `gh`** en la misma hora.

| Nombre | Licencia | Descripción | Stars | Forks | Último push | Región origen |
|--------|----------|-------------|-------|-------|-------------|---------------|
| [RedaElMakroum/agentic-ai-hems](https://github.com/RedaElMakroum/agentic-ai-hems) | MIT (leída, 1.071 B) | *Agentic AI Home Energy Management System*: framework de LLM para gestión energética residencial. Primer agente **doméstico** explícito de la KB | 18 | 4 | 2025-11-05 | EMEA |
| [IBM/OpenDsStar](https://github.com/IBM/OpenDsStar) | Apache-2.0 (leída, 11.356 B) | Implementación abierta del agente **DS-Star**: sustituye el paso por archivos del agente de ciencia de datos. Capa de análisis sobre datos de red | 25 | 3 | 2026-05-10 | North America |
| [maxoliverbr/eia-api-ts](https://github.com/maxoliverbr/eia-api-ts) | MIT (leída, 1.066 B) | Wrapper tipado de la **EIA API v2** construido **explícitamente para uso agéntico**; acceso al dato público federal de EE. UU. | 11 | 2 | 2026-11-19 | North America |
| [TU-Delft-AI-Energy-Lab/MARL-iDR](https://github.com/TU-Delft-AI-Energy-Lab/MARL-iDR-Multi-Agent-Reinforcement-Learning-for-Incentive-based-Residential-Demand-Response) | MIT (leída, 1.078 B) | RL multiagente para respuesta a la demanda residencial **basada en incentivos**; paper + código. ⚠️ Sin push desde 2023: referencia del esquema, no base de producto | 50 | 9 | 2023-08-02 | EMEA |

**Son cuatro, y se dicen cuatro.** De 120 candidatos únicos en 18 consultas, éstos son los que
pasaron el filtro de licencia **y** el de pertinencia agéntica. El resto de los 76 repos nuevos del
pase es infraestructura, no agentes, y está en `repos/trending.md`.

### El dato de adopción que ordena la propuesta agéntica en APAC

**23% de los operadores de red de Asia Oriental usa IA en operación en tiempo real; 54% la usa en
planificación del desarrollo de red** (IEA, *Energy and AI in East Asia*, abril 2026; ⚠️ por snippet
—`iea.blob.core.windows.net` no resuelve desde este entorno). La IEA atribuye la brecha a
**fiabilidad**: el rechazo al tiempo real es **deliberado**.

Es la tercera confirmación independiente de la restricción de arquitectura de esta KB, y la primera
**cuantificada desde el lado de la demanda**: receta propia → guía de NERC (pase 14) → 23%/54% +
guía de práctica de NA (este pase). Para una propuesta: **agente de planificación y estudio, no de
control**; y el 23% no es inmadurez a vencer, es **política de riesgo del cliente**.

### Exclusiones por licencia — las tres llegaron como `NOASSERTION` y las tres tienen tracción

| Repo | ★ | La API dice | El archivo dice | Veredicto |
|------|---|-------------|-----------------|-----------|
| [Zara-Toorox/Solar-Forecast-ML](https://github.com/Zara-Toorox/Solar-Forecast-ML) | 318 | `NOASSERTION` | `PROPRIETARY AND NON-COMMERCIAL LICENSE` (2.646 B) — **contiene la frase literal de MIT** en su cláusula de concesión, y prohíbe uso comercial **y entrenamiento de IA** | ❌ Exclusión dura |
| [u9n/dlms-cosem](https://github.com/u9n/dlms-cosem) | 124 | `NOASSERTION` | **Business Source License 1.1** (`pyproject.toml`) + `License :: Other/Proprietary`; el *Additional Use Grant* veta "exponer las API del Licensed Work" | ❌ No es open source |
| [GreatTM/PowerBiMIP](https://github.com/GreatTM/PowerBiMIP) | 42 | `NOASSERTION` | Aviso de 1.067 B: "academic and non-commercial research only", Southeast University | ❌ No utilizable |
| [ValentinRigoni/Open-DSOPF](https://github.com/ValentinRigoni/Open-DSOPF) | 80 | `NOASSERTION` | **Ningún artefacto** de licencia (6 nombres × 3 ramas) | ❌ Sin concesión expresa |

> **T56 — el incipit de MIT no identifica una licencia.** *"Permission is hereby granted, free of
> charge…"* puede aparecer dentro de una licencia propietaria. Discriminadores de coste cero, en
> este orden: **(1) la primera línea no vacía del archivo; (2) el tamaño** (MIT real mide
> ~1,05–1,09 kB; el impostor medía 2.646 B). Nunca buscar la frase de concesión en todo el archivo.
>
> **T57 — cláusula de prohibición de entrenamiento de IA: clase nueva.** Prohíbe usar el código para
> entrenar o afinar LLM. Afecta al **uso interno de un estudio de IA**, no sólo a la redistribución,
> y **ningún campo SPDX la expresa**.

## Pase 16 (2026-11-24): el primer servidor MCP **oficial de un operador de sistema**, y es Apache-2.0

Todo lo verificado el **2026-11-24** con `gh api search/repositories` (campos `license.spdx_id`,
`stargazers_count`, `pushed_at`), liveness con `git ls-remote`, y **licencias leídas byte a byte** en
`raw.githubusercontent.com` (primera línea no vacía + tamaño) en todos los casos.

| Nombre | Licencia | Descripción | Stars | Último push | Región origen |
|--------|----------|-------------|-------|-------------|---------------|
| [ONSBR/TIAGO-Dados-Abertos](https://github.com/ONSBR/TIAGO-Dados-Abertos) | **Apache-2.0** (11.357 B) | **Servidor MCP oficial de `dados.ons.org.br`**, el portal de datos abiertos del ONS brasileño. Capa semántica en YAML (**ODCS v3.1.0**) declara schema, unidades y agregaciones válidas; el servidor rutea/valida/ejecuta y **el modelo del cliente escribe el SQL**. Motor DuckDB. Publicado en PyPI (`mcp-tiago-dados-abertos`) | 29 | 2026-11-20 | **LATAM** |
| [cyanheads/eia-energy-mcp-server](https://github.com/cyanheads/eia-energy-mcp-server) | **Apache-2.0** (10.846 B) | MCP sobre la **EIA API v2** de EE. UU. `NOASSERTION` por API, Apache por byte-read | 3 | 2026-11-15 | North America |
| [HPML6998-S26-Team13/hpml-assetopsbench-smart-grid-mcp](https://github.com/HPML6998-S26-Team13/hpml-assetopsbench-smart-grid-mcp) | **MIT** (1.111 B) | **SmartGridBench**: benchmark de mantenimiento de transformadores con *tool-calling*. Categoría nueva en esta KB: banco de pruebas agéntico sectorial | 1 | 2026-07-01 | North America |
| [lubosstrejcek/victron-tcp](https://github.com/lubosstrejcek/victron-tcp) | **MIT** (1.070 B) | MCP sobre dispositivos **Victron GX** en tiempo real: solar, batería, red | 7 | 2026-11-02 | EMEA |
| [lubosstrejcek/victron-vrm-mcp](https://github.com/lubosstrejcek/victron-vrm-mcp) | **MIT** | MCP sobre la API cloud **Victron VRM**: acceso remoto a solar y batería | 5 | 2026-11-13 | EMEA |
| [KoshiirRa/midgley](https://github.com/KoshiirRa/midgley) | **Apache-2.0** (10.172 B) | Multi-agente LLM de pronóstico de precio de combustible (RBOB mayorista y retail) | 2 | 2026-11-23 | North America |
| [alanmossinger/ai-enablement-proof](https://github.com/alanmossinger/ai-enablement-proof) | **MIT** (1.071 B) | Agente autónomo **«gobernado»** para fiabilidad de red en EE. UU. Vale por el encuadre de gobernanza, no por el código (1 ★) | 1 | 2026-11-11 | North America |

### Por qué `TIAGO-Dados-Abertos` es la fila más importante de este archivo

No por las estrellas —29— sino porque **es la primera vez que esta KB registra un servidor MCP
publicado por el operador de un sistema eléctrico nacional**, y porque su arquitectura resuelve, en
producción, la restricción que atraviesa todas las recetas de esta KB:

- **Ningún LLM corre en el servidor.** Entrega catálogo y contratos, valida y ejecuta SQL, y
  *«tudo o que devolve é determinístico e rastreável ao contrato»*.
- **Cuando no puede probar un dato, declara desconocido en vez de deducir.**
- Cada respuesta trae **unidad y fuente probadas por el contrato** ODCS.

Esto es la **receta 49** de esta KB (compuerta de validación sobre el esquema del propio sector),
implementada con ODCS en vez de SHACL y DuckDB como motor, por un TSO. Es la **séptima confirmación
independiente** de la restricción de arquitectura de esta KB y **la primera embarcada en un producto**
y no en un análisis, una norma o un paper. Generalizada en la **receta 53**.

⚠️ **Cómo proponerlo sin exagerarlo.** Es un servidor de **consulta de datos abiertos**, no de
operación: su alcance es el portal público del ONS, no el SIN ni el despacho. Lo citable es
**el patrón y la autoría institucional**, más el hecho de que el propio ONS publique su advertencia
de que la herramienta generativa puede producir imprecisiones y que para posición institucional hay
que usar los canales oficiales. Esa advertencia es un **activo** en una conversación con cliente:
el operador ya escribió la frontera que el cliente va a querer oír.

### Exclusiones de este pase

- ⛔ [`lhg96/smartEMS-MultiAgent-Demo`](https://github.com/lhg96/smartEMS-MultiAgent-Demo) (6 ★,
  origen Corea): `LICENSE` de 2.699 B titulado **`Custom License Agreement`** — no comercial, con
  licencia comercial separada de pago. Prohíbe explícitamente integración en productos comerciales,
  uso en producción y despliegue en actividades generadoras de ingresos. **Inutilizable.**
- ⛔ [`d2rojas/LLMs-Agents-For-SmartGrids-Code`](https://github.com/d2rojas/LLMs-Agents-For-SmartGrids-Code)
  (5 ★): **sin artefacto de licencia** (probados `main`/`master`/`develop` × 4 nombres). Citable como
  paper, no incorporable.
- ⛔ [`emporiaenergy/emporia-mcp`](https://github.com/emporiaenergy/emporia-mcp): MCP de fabricante
  **sin licencia**. Se registra porque la categoría «MCP de dispositivo de fabricante» es nueva y
  Victron sí es MIT.

### Nota de saturación

Los barridos agénticos de este pase (cuatro consultas con filtro de recencia, `pushed:>2026-06-01` a
`>2026-09-01`) devolvieron como ancla **exclusivamente repos ya inventariados**: `Power-Agent/PowerMCP`
(242 ★, +4 desde el pase 15), `Power-Agent/PowerFM`, `LBNL-ETA/EnergyPlus-MCP` (132 ★),
`TimeCopilot/timecopilot` (643 ★), `idfkit/idfkit-mcp`. **El techo agéntico global de esta KB es
real.** Lo que no era real era el cero regional de LATAM, y lo rompió una consulta de cuatro palabras
en portugués (T63, ver `agents/trending.md`).

## Pase 17 (2026-11-24): el puente ML→optimización, que es la compuerta de esta KB escrita en código

Dos piezas nuevas, ambas verificadas vivas y con licencia **leída byte a byte**. Ninguna es un
«agente de operación de red»: ese cero sigue en pie por sexto pase consecutivo y este pase lo
explica por **demanda del mercado**, no por fallo del instrumento (ver `agents/trending.md`).

| Pieza | Repo | Licencia (byte-read) | ★ | Push | Origen | Papel en una arquitectura agéntica |
|-------|------|----------------------|---|------|--------|-------------------------------------|
| **MathOptAI.jl** | [lanl-ansi/MathOptAI.jl](https://github.com/lanl-ansi/MathOptAI.jl) | ⚠️ BSD-3 + reserva de derechos del Gobierno de EE. UU. (2.293 B; **sin indemnidad, sin deber de marcado** — la variante más limpia de `lanl-ansi`) | 90 | 2026-08-27 | North America | **La compuerta, en la misma formulación matemática.** Empotra un predictor de ML entrenado dentro de un problema JuMP/ExaModels: el modelo aprendido es **una restricción más**, no un actuador. El *solver* lo satisface o declara infactible |
| **Agentes generativos con LLM local sobre Setonix** | [csiro-energy-systems/gen_agents_localLLM_on_Setonix](https://github.com/csiro-energy-systems/gen_agents_localLLM_on_Setonix) | **Apache-2.0** (11.334 B) | 2 | 2025-04-24 | APAC | Agentes generativos con **LLM local** en el supercomputador **Setonix** (Pawsey). Primer repo agéntico de una **agencia científica nacional** en esta KB; patrón de **soberanía de datos**: el modelo no sale de la infraestructura nacional |

**Por qué `MathOptAI.jl` es la entrada más importante de este pase pese a tener 90 ★.** Esta KB
tiene dieciséis pases de confirmaciones externas de que el sector **no comprará control autónomo**
(criterio propio → NERC, *decision-support* → IEA, 23 % en tiempo real vs 54 % en planificación →
NIST, borrador de perfil de infraestructura crítica → ONS, producto embarcado → PSR). Todas dicen
**qué no vender**. `MathOptAI.jl` es la primera pieza inventariada que dice **cómo construir lo que
sí se vende**, y en el lenguaje que el sector ya audita: restricciones en un problema de
optimización. El argumento de *engagement* pasa de «pondremos una validación delante del modelo» a
**«el modelo no puede proponer un punto infactible, porque vive dentro del despacho»**.

⚠️ **Condición de uso, no decorativa.** `MathOptAI.jl` se propone **con JuMP directamente**. Si se
acopla a la familia `PowerModels.jl`, arrastra `InfrastructureModels.jl`, que **impone indemnidad
al licenciatario** (T73/T74): entonces exige revisión legal previa. La frontera no está en el
paquete que se elige sino en **el árbol de dependencias**.

**Nota de alcance, para no inflar la categoría.** `gen_agents_localLLM_on_Setonix` tiene 2 ★ y su
último *push* es de abril de 2025: se inventaría por **patrón y procedencia institucional** (LLM
local en infraestructura nacional, Apache-2.0), **no** como componente maduro. No proponerlo como
base de producto.

## Pase 18 (2026-11-24): la capa de modelo meteorológico es de clase mundial y **no tiene agentes**, y el cero está medido

Este pase abrió la capa que alimenta todo pronóstico renovable (ver `repos/foundations.md` §1–§5):
`anemoi` de ECMWF, `graphcast`, `neuralgcm`, `physicsnemo`, `earth2studio`, `weatherbench2`. Miles
de estrellas, licencias permisivas, servicios meteorológicos nacionales trabajando dentro de los
repos. **Encima de todo eso no hay nada agéntico de grado institucional**, y ésa es la conclusión
útil del pase.

### Lo que sí existe, con su medida

| Pieza | Repo | Licencia (byte-read) | ★ | Push | Origen | Papel real |
|-------|------|----------------------|---|------|--------|------------|
| **Agente de pronóstico + *trading*** | [PredictionMarketTrader/openthomas](https://github.com/PredictionMarketTrader/openthomas) | **MIT** | 25 | 2026-09-12 | North America | Agente de pronóstico meteorológico **que se auto-mejora** y opera en mercados de predicción. El único agente de esta capa con una **función objetivo medible** (P&L), no una demo |
| **Servidor MCP meteorológico más traccionado** | [weather-mcp/weather-mcp](https://github.com/weather-mcp/weather-mcp) | **MIT** | 58 | **2026-11-24** | Global | 17 *tools* meteorológicas: resumen de una llamada + pronósticos. *Push* del día. ⚠️ Envuelve APIs de terceros |
| **MCP sobre `open-meteo`** | [cyanheads/open-meteo-mcp-server](https://github.com/cyanheads/open-meteo-mcp-server) | **Apache-2.0** | 14 | 2026-11-18 | Global | Geocodificación + pronóstico + clima histórico + marino + calidad de aire. ⚠️ **Ver advertencia de licencia abajo: es el caso más instructivo del pase** |
| **MCP de estaciones meteorológicas** | [WeatherXM/weatherxm-pro-mcp](https://github.com/WeatherXM/weatherxm-pro-mcp) | **MIT** | 7 | 2025-04-30 | EMEA | Expone las APIs WeatherXM PRO como *tools*: datos de **estación física**, no de modelo |

### El cero, con su forma medida (no un silencio)

| Consulta | Resultados | Techo de estrellas | Qué hay realmente |
|----------|-----------|--------------------|-------------------|
| `agent weather forecasting llm` | 69 | **25 ★** (`openthomas`) | Tras el primero: 5 ★, 4 ★, 2 ★, 0 ★… Demos de *tool calling* sobre OpenWeather |
| `agentic climate data analysis` | 21 | **2 ★** | Notebooks de análisis CMIP6; uno (`JGrassi97/climagent`, AGPL-3.0) ya **archivado** |
| `mcp server weather forecast` | 276 | **58 ★** | Cola larga de envoltorios de API comercial |
| `mcp server energy grid` | 12 | **7 ★** | Ya cubierto en el pase 12; sin novedad institucional |

**La lectura, y es una oportunidad, no una queja.** En esta capa **el modelo físico ya está
construido, abierto y validado por el productor** (ECMWF publica incluso el nivel de madurez por
repo, ver T82). Lo que no existe es **la orquestación**: nadie ha publicado un agente que decida
qué modelo correr, con qué condiciones iniciales, cuándo el conjunto está demasiado disperso para
emitir una recomendación, y cómo entregar eso a un EMS. En todas las demás capas de esta KB el
problema era el contrario — agentes de sobra, componente físico ausente. **Aquí el componente duro
está hecho y la integración está vacía: es exactamente la forma de trabajo que un estudio vende.**
La receta concreta está en `compose/patterns.md`, Receta 60.

⚠️ **El caso `open-meteo-mcp-server` y el patrón de «lavado de licencia» por envoltura.** El
servidor MCP es **Apache-2.0** y su código se puede usar sin reservas. Lo que llama es
`api.open-meteo.com`, cuyo servicio público es *free for non-commercial use* y cuyo servidor es
**AGPL-3.0** — el riesgo que esta KB viene señalando desde el pase 5. **Envolver una fuente
restringida en un componente permisivo cambia la licencia del envoltorio y no cambia los términos
de la fuente.** Un piloto que instala este MCP ve `Apache-2.0` en su inventario de dependencias y
no ve la restricción que realmente aplica. El sustituto correcto está inventariado y es permisivo:
[ecmwf/ecmwf-opendata](https://github.com/ecmwf/ecmwf-opendata) (Apache-2.0, 342 ★) o
[blaylockbk/Herbie](https://github.com/blaylockbk/Herbie) (MIT, 801 ★) según la región.

### Lo que este pase **no** propone, y por qué

- **Ninguno de los cuatro grandes modelos de IA meteorológica es un agente**, y proponerlos como tal
  sería un error de categoría. Son componentes de inferencia. Su papel en una arquitectura agéntica
  es ser **el *tool* que el agente llama**, nunca el que decide.
- **`microsoft/aurora` no se propone como componente de producto** pese a ser MIT y tener 1.049 ★.
  Su propio README nombra *«critical infrastructure operations»* entre los riesgos de uso
  consecuente y declara que el código *«has not been developed nor tested for non-academic
  purposes»*. Cuando el fabricante escribe que no es apto para el uso que propondríamos, la licencia
  permisiva no es el dato relevante (T80).
- **`198808xc/Pangu-Weather` queda excluido** (1.402 ★, el más traccionado de origen APAC): sus pesos
  son CC BY-NC-SA 4.0 y su README dice, en negrita, *«The commercial use of these models is
  forbidden.»* No hay fichero de licencia en el repo.

## La organización detrás de AINETUS, enumerada repo por repo (pase 19, 2026-11-24)

El pase 12 cerró el hueco *«AINETUS: anunciado en prensa, código no localizado»* localizando
`ainetus/ExpertOp4Grid` (MPL-2.0). Lo que **no** se había hecho es enumerar la organización
`AI4REALNET` —el proyecto europeo de investigación del que AINETUS procede— y el resultado cambia
cómo se cita el conjunto.

**16 repositorios medidos** (`gh api search/repositories -f q='org:AI4REALNET'`). **5 llevan
licencia utilizable; 11 no llevan ninguna** (`NONE`) o declaran `NOASSERTION`.

| Nombre | Licencia | Descripción | ★ | Forks | Último push | Región origen |
|--------|----------|-------------|---|-------|-------------|---------------|
| [AI4REALNET/grid2evaluate](https://github.com/AI4REALNET/grid2evaluate) | **MPL-2.0** | Evaluación de agentes sobre `Grid2Op`. El más reciente de la organización y el de encaje más directo: es el arnés con el que se mide un agente de red antes de proponerlo | 0 | 0 | **2026-11-03** | EMEA |
| [AI4REALNET/XLLM](https://github.com/AI4REALNET/XLLM) | **MPL-2.0** | *«Bridging Optimization and Operator Insight»*: LLM asistiendo el acoplamiento entre optimización y criterio del operador. Es la pieza **LLM** de la familia, frente al resto que es RL | 1 | 0 | 2026-05-24 | EMEA |
| [AI4REALNET/distributed-rl-gnn](https://github.com/AI4REALNET/distributed-rl-gnn) | **MIT** | RL distribuido con redes neuronales de grafo sobre la topología de red. La licencia más permisiva de la organización | 0 | 0 | 2026-10-30 | EMEA |
| [AI4REALNET/distributed_rl](https://github.com/AI4REALNET/distributed_rl) | **MPL-2.0** | Entregable D2.2, Politecnico di Milano: RL distribuido para operación de red | 0 | 1 | 2026-04-14 | EMEA |
| [AI4REALNET/T2.3_explaining_action_alternatives](https://github.com/AI4REALNET/T2.3_explaining_action_alternatives) | **MPL-2.0** | Explicabilidad: por qué el agente propone una maniobra y no otra. Es la mitad *exigible por el regulador* del patrón de operación asistida | 0 | 0 | 2026-02-20 | EMEA |

⚠️ **Cómo citar esto sin sobrevenderlo, y es un patrón nuevo que conviene nombrar.** En un consorcio
financiado por la UE **la licencia se aplica por repositorio-entregable, no por organización**: las
mismas siglas cubren `risk-sensitive-inverse-rl`, `network-distributed-q-learning`, `Tokener`,
`flatland-commnet` y `T3.3-3.4-HMI`, todos **sin fichero de licencia**, y `Human-Assessment-Module`
y `flatland-blackbox` con `NOASSERTION`. «Está en LF Energy» **no** convierte los repos de paquete
de trabajo en dependencias utilizables. Las cinco filas de arriba son las utilizables; las otras
once son **registro de investigación citable**, no software proponible. Ver **T87**.

⚠️ **Y el techo de tracción es real:** ninguna de las cinco pasa de **1 estrella**. Se inventarían
porque son el arnés y la explicabilidad de una pila —`Grid2Op` + `ExpertOp4Grid` + `OperatorFabric`—
que esta KB ya tiene y que **sí** tiene autoría de operador. Son complemento de esa pila, nunca su
punto de partida.

## El motor ABM de mercados que vivía en otra forja (pase 19, 2026-11-24)

Esta sección existe para prevenir un error de categoría, no para añadir un agente. **AMIRIS**
(Apache-2.0, DLR) y el marco **FAME** sobre el que corre son **modelos basados en agentes**: agentes
económicos que pujan bajo reglas regulatorias, sin LLM en el lazo. Se inventarían en
`repos/foundations.md`, no aquí, y se proponen como **motor de escenario de mercado** —el papel que
`assume-framework/assume` ya cumple en esta KB— nunca como «agente de IA». La novedad verificable
del pase es que vivían en `gitlab.com` y por eso faltaban: ver **T83** y la tabla del plano de forja.
