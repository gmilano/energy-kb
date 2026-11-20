---
industry: energy
region: Global
updated: 2026-11-20
---

# 📈 Agentes trending — energy

> **Archivo APPEND-ONLY.** Cada pase añade una sección fechada arriba y conserva el historial
> debajo. No reescribir: el valor de este archivo es la serie temporal.

## 2026-11-20 — pase 10 (la cola larga agéntica tiene número: 33 repos en siete semanas, el mejor con 7 estrellas y sin licencia)

**Titular del pase: este pase no encontró ningún agente energético nuevo proponible, y por primera
vez puede decir cuántos hay y de qué tamaño.** La consulta `agent energy grid in:name,description
created:>2026-10-01` devuelve **33 repos creados en las últimas siete semanas**. El mejor tiene
**7 ★ y licencia `NOASSERTION`**; los cinco siguientes tienen **1, 0, 0, 0 y 0 estrellas** y
**ninguno tiene licencia**:

| Repo | Licencia | ★ | Push | Qué dice ser |
|------|----------|---|------|--------------|
| `arhamshah08/energy-hack` | ⚠️ NOASSERTION | 7 | 2026-11-16 | Pack de recursos "agent-ready" para un hack day de energía |
| `xvbohan92-ai/gridnote-energy-agent` | ⚠️ **sin licencia** | 0 | 2026-10-26 | Agente de análisis energético "evidence-backed" con **LangGraph**, sólo lectura |
| `tarrini/renewable-grid-agent` | ⚠️ **sin licencia** | 0 | 2026-10-11 | Despacho simulado de corredor renovable |
| `Likhitha-B-Y/smart-grid-energy-arbitrage-agent` | ⚠️ **sin licencia** | 0 | 2026-10-09 | Arbitraje de energía |
| `ssblip/gridmind` | ⚠️ **sin licencia** | 0 | 2026-10-11 | Multi-agente para gestión autónoma de red renovable |

Y en MCP, `mcp energy grid in:name,description created:>2026-09-01` devuelve **4 repos, los cuatro
con 0 estrellas** (`pipeworx-io/mcp-georgia-energy` y `azmartone67/dchub-claude-plugin` ya estaban
catalogados; `sohamshindework/gridpulse` se creó **hoy**).

**Lo que esto cambia, que no es poco:** hasta este pase, "no hay agente de operación de red
proponible" era una ausencia. Ahora es una **distribución medida**: hay actividad —33 repos en siete
semanas, nombres que prometen despacho autónomo y arbitraje— y **toda ella está por debajo del umbral
de proponible, y mayoritariamente sin licencia**. Es el **sexto cero consecutivo** en operación de
red, y el primero con la forma del cero descrita. Un cliente que pregunte "¿no hay ya agentes de red
open source?" tiene ahora una respuesta con número: los hay, son de una semana, de una persona y de
cero estrellas.

`gridnote-energy-agent` merece una nota aparte porque **acierta en el diseño**: LangGraph,
*evidence-backed*, y explícitamente **sólo lectura**. Es la regla de arquitectura de esta KB y la
postura de `OpenVigil` (pase 9), en un repo de cero estrellas sin licencia. **La idea correcta está
circulando; la base utilizable no.**

### Lo que sí aportó este pase a la capa agéntica: el banco de pruebas que un agente de red necesitaría

El hallazgo principal del pase 10 son dos organizaciones institucionales norteamericanas (EPRI y
Grid Protection Alliance, ~125 repos — ver `repos/trending.md`). **Ninguno de esos repos es un
agente, y conviene decirlo sin adornos.** Pero dos piezas son precondición directa de la capa
agéntica, y esta KB no las tenía:

| Repo | Licencia | ★ | Forks | Push | Por qué importa para un agente |
|------|----------|---|-------|------|-------------------------------|
| [epri-dev/Universal-Semantic-Standard-Test-Harness](https://github.com/epri-dev/Universal-Semantic-Standard-Test-Harness) | **BSD-3-Clause** | **0** | 1 | 2026-08-18 | Banco de pruebas de **interoperabilidad semántica**. Un agente que actúa sobre la red necesita exactamente esto: un arnés que compruebe que lo que entendió es lo que el modelo dice |
| [Haigutus/cim-bench](https://github.com/Haigutus/cim-bench) | **MIT** | 10 | 5 | 2026-07-16 | **Benchmarking de herramientas CIM**. Comparar implementaciones es el paso previo a dejar que un modelo elija entre ellas |
| [GridProtectionAlliance/openECA](https://github.com/GridProtectionAlliance/openECA) | **MIT** | 16 | 8 | 2026-11-15 | *Extensible Control & Analytics*: el punto de inserción de analítica en el lazo operativo. ⚠️ **20 issues abiertas** |

El patrón que esta KB viene registrando desde el pase 4 se repite con otro signo: **la capa de
evaluación llega antes que la capa de agente, y llega de las instituciones.** `PowerAgentBench` y
`PowerFM` (pase 4-5) venían de la academia; el arnés semántico de EPRI tiene **cero estrellas y tres
meses**. Cuando exista un agente de operación de red proponible, el arnés para auditarlo ya estará
escrito, en BSD-3, y nadie lo habrá mirado.

### Nota de método que afecta al descubrimiento de agentes

El pase 9 estableció "buscar la norma, no el buzzword". Este pase encontró el límite de esa regla, y
es el motivo por el que nueve pases no vieron 125 repos institucionales: **las instituciones no
nombran sus herramientas por la categoría ni por la norma, sino por el acrónimo interno del método**.
`StorageVET`, `DER-VET`, `QuESt`, `openMIC`, `openXDA`, `ProGRESS`, `SPI-Tool`. Ninguno contiene el
término de su categoría. La consulta que los encuentra es `org:epri-dev` y
`org:GridProtectionAlliance` — es decir: **cuando la oferta esperable es de investigación aplicada,
buscar la institución, no la cosa.** Ver **T47**.

Para la caza de agentes esto tiene una consecuencia directa y comprobable en el próximo pase:
conviene barrer por organización los laboratorios e institutos que ya aparecen en esta KB
(`pnnl`, `argonne-*`, `lbl-srg`, `NatLabRockies`, `equinor`, `statnett`, `alliander-opensource`,
`entsoe`) antes de volver a barrer por buzzword agéntico.

## 2026-11-20 — pase 9 (el agente que opera un activo real: 22 agentes, capa de autorización humana, y publica que no está verificado)

**Titular del pase: apareció el primer repo de esta KB que implementa T28 ("la IA asiste, no decide")
como código y no como frase de README — y que publica su propio estado como NO VERIFICADO.**
[`Ninemilo/OpenVigil`](https://github.com/Ninemilo/OpenVigil) (**Apache-2.0** confirmada en `LICENSE`
crudo, 180 ★, 37 forks, creado 2026-09-04, push 2026-11-17, **0 issues abiertas**) es una plataforma
de O&M de parque eólico que encadena monitoreo → alarma → diagnóstico → **aprobación humana** →
orden de trabajo → evidencia de campo → actualización de conocimiento en un flujo auditable.

### Qué tiene dentro, verificado leyendo el repo

| Capa | Implementación |
|------|----------------|
| Agentes | **22 agentes** en tres capas: decisión, revisión, ejecución. Runtime de agentes con **16 tools** |
| Orquestación | **LangGraph** en backend Python + catálogo SQL gobernado con **18 tools** |
| Modelos | **LiteLLM**; proveedores nombrados: SiliconFlow, Alibaba Bailian, DeepSeek (**origen APAC**) |
| Datos | SCADA, CMS, meteorología, alarmas manuales; conectores SCADA / MQTT / HTTPS / **EAM** |
| Backend | FastAPI, PostgreSQL + **TimescaleDB** + **pgvector**, Redis, Dramatiq, MinIO, **Neo4j** |
| Workers | `pyOMA2` (análisis modal estructural) y parser PDF/OCR basado en **Docling** |
| Benchmark | **CARE v6** offline (Fraunhofer IEE): 95 eventos, 36 activos, **CC BY-SA 4.0 y NO incluido** en el repo — lo aporta el operador |
| Frontend | React 19, vinext, Cloudflare Worker + D1 (sólo demo) |

### Por qué es el hallazgo del pase, y qué NO se puede decir de él

Lo valioso es la **postura**, no la precisión: el propio README declara que es una *"production
candidate implementation, not a system already deployed in production"*, y marca **UNVERIFIED** la
exactitud de campo, la calibración real, la operación en sombra y la calificación formal de release.
La salida de la demo proviene de **fixtures deterministas, no de modelos en vivo**, y no hay
releases publicados. Documentación en **ocho idiomas**.

- **Usar como plantilla** del patrón de autorización: la IA propone alternativas, **la persona
  autoriza las acciones de alto riesgo**. Es exactamente la regla de arquitectura de esta KB, ya
  escrita en código y con capa de revisión separada de la de ejecución.
- **No citar ninguna cifra de desempeño**: no publica ninguna. Es un hallazgo de *viabilidad y
  diseño*, no de *ranking*. (Misma disciplina que el pase de automotive aplicó a `drivingbench`.)
- **Riesgos medidos**: 180 ★ y **0 issues abiertas** en 2,5 meses con 63 commits sugieren velocidad
  de autor único; **no nombra ningún protocolo industrial** (ni OPC UA ni IEC 61400-25), y los
  contratos reales de SCADA/CMS/EAM siguen pendientes de pruebas de aceptación conjuntas. El gemelo
  digital es una **vista operativa 2D, no una simulación física**.

**Lectura de patrón, tercera confirmación en esta rotación:** automotive encontró `LionDriver`
publicando 42 defeaters abiertos; automotive encontró `wtfault-scanner` con "never makes anything
up"; energy encuentra `OpenVigil` marcando UNVERIFIED lo que no probó. **Publicar el propio límite
se consolidó como movimiento de credibilidad en industrias reguladas.**

### La capa ISO 15118 / Plug&Charge: esta KB tenía el lado del CSMS y le faltaba el del vehículo

El séptimo pase catalogó la carga de EV como la categoría más grande del open source energético
(T31) con `evcc`, `EVerest`, `steve` y `mobilityhouse/ocpp`. Faltaba el **protocolo
vehículo↔cargador**. Buscando `"ISO 15118"` como término único:

| Repo | Licencia | ★ | Forks | Push | Qué aporta |
|------|----------|---|-------|------|-----------|
| [ecog-io/iso15118](https://github.com/ecog-io/iso15118) | **Apache-2.0** | 250 | 142 | 2026-11-17 | Implementación de ISO 15118 **-2, -20 y -8**. Ratio fork:★ = **0,57**, señal de construcción, no de estrella |
| [SwitchEV/RISE-V2G](https://github.com/SwitchEV/RISE-V2G) | **MIT** | 261 | 95 | ⚠️ 2025-12-19 | La implementación de referencia histórica de la interfaz V2G. **11 meses sin push** |
| [ecog-io/josev](https://github.com/ecog-io/josev) | **Apache-2.0** | 164 | 23 | 2026-11-16 | Versión comunitaria de Josev: "sistema operativo" para estaciones de carga V2G |
| [matth-x/MicroOcpp](https://github.com/matth-x/MicroOcpp) | **MIT** | 547 | 220 | ⚠️ 2025-12-04 | Cliente OCPP 1.6 / 2.0.1 **para microcontroladores**. 135 issues abiertas y casi un año sin push |

**Lectura honesta: la capa de protocolo existe, es permisiva, y la mitad se está quedando vieja.**
`ecog-io/*` es lo vivo (push de noviembre de 2026); `RISE-V2G` y `MicroOcpp` son las piezas más
citadas de la categoría y llevan ~11 meses sin movimiento. Para un SoW: partir de `ecog-io`, usar
`RISE-V2G` como referencia de lectura, y **no** comprometer `MicroOcpp` en firmware sin antes
auditar sus 135 issues.

### EEBus/SPINE: el protocolo de flexibilidad doméstica de EMEA, y un fabricante publicando el stack

| Repo | Licencia | ★ | Forks | Push | Nota |
|------|----------|---|-------|------|------|
| [enbility/eebus-go](https://github.com/enbility/eebus-go) | **MIT** | 123 | 53 | 2026-11-06 | Implementación de EEBUS en Go; la base viva de la categoría |
| [NIBEGroup/openeebus](https://github.com/NIBEGroup/openeebus) | **Apache-2.0** | 68 | 18 | 2026-11-12 | EEBUS (**SHIP y SPINE**) en C, publicado por **NIBE Group**, fabricante sueco de bombas de calor |
| [volschin/eebus-ha-bridge](https://github.com/volschin/eebus-ha-bridge) | **MIT** | 41 | 9 | 2026-11-19 | Puente EEBUS→Home Assistant sobre `eebus-go`, con API gRPC |
| [FlexMeasures/flexmeasures-s2](https://github.com/FlexMeasures/flexmeasures-s2) | **Apache-2.0** | 2 | 0 | 2026-09-21 | Tooling para mensajes **S2** (EN 50491-12-2) dentro de FlexMeasures |

**`NIBEGroup/openeebus` extiende T2 un escalón.** T2 decía que *los operadores de red* se volvieron
proveedores de open source (RTE, Alliander). Aquí el que publica el stack de protocolo es un
**fabricante de equipo**. La consecuencia comercial: en EMEA el integrador ya no necesita licenciar
una pila EEBus propietaria para hablar con una bomba de calor.

Y el dato incómodo del mismo cuadro: **el estándar S2 de flexibilidad tiene tooling, y tiene 2
estrellas.** La norma existe, la comunidad todavía no.

### Dos "resultados de búsqueda" que no eran hallazgos

La búsqueda web de este pase volvió a presentar `DatariusAI/AI-in-Energy` como *"daily-refreshed hub
of the latest AI, ML and data science research and code for energy and utilities"*. La API dice:
**0 ★, 0 forks, sin licencia, creado 2026-10-08** — y el octavo pase **ya lo había catalogado con
esa misma advertencia** en `repos/foundations.md`. Se registra aquí sólo como confirmación
independiente de que el buscador describe el README y no la tracción.

Lo nuevo de este pase en la misma categoría: `ishandutta2007/Awesome-Energy-Utilities-CRM` (**MIT,
0 ★**, creado 2026-10-12), única pista hacia la capa meter-to-cash y sin tracción; y
`AI4Electricity/Awesome-AI-for-Electricity` (**MIT**, 153 ★), que **no tuvo push desde 2025-03-30:
20 meses**.

Los índices vivos siguen siendo los dos que esta KB ya tenía:
[`protontypes/open-sustainable-technology`](https://github.com/protontypes/open-sustainable-technology)
(CC-BY-4.0, 2.586 ★ — aparece en **todas** las consultas de protocolo de este pase, lo que confirma
que es el mapa del espacio) y [`ps-wiki/best-of-ps`](https://github.com/ps-wiki/best-of-ps)
(CC-BY-SA-4.0, 297 ★, push 2026-11-20, ranking semanal).

### Anomalías ★/fork que confirman T19 en esta muestra

- [`Ali-Marandi/grid-resilience`](https://github.com/Ali-Marandi/grid-resilience) — MIT, **108 ★ y 0 forks**.
- `KEV0143/Comparative-analysis-of-hourly-load-forecasting-using-PatchTST-TFT-NHiTS-and-CatBoost` — Apache-2.0, **1.764 ★ y 0 forks**.

Ninguno de los dos se cita como validado por comunidad. Un repo con mil setecientas estrellas y
cero forks no lo usó nadie.

## 2026-11-20 — pase 8 (el método de "buscar la norma local" no generaliza, y la razón es utilizable)

**Titular del pase: la lección que abrió APAC en el pase 7 no se exporta a EMEA ni a LATAM, y el
por qué es una regla de búsqueda, no una conclusión sobre el sector.** El pase 7 dejó cinco
candidatos —`CEI 0-21` (Italia), `VDE-AR-N 4105` (Alemania), `G99` (Reino Unido), `PRODIST`
(Brasil), `NOM-001-SEDE` (México)— con la hipótesis de que nombrar la norma de conexión local
abriría cada región como `CSIP-AUS` e `IEEE 2030.5` abrieron Australia. Las cinco consultas se
corrieron contra `search/repositories`. **Ninguna devolvió un repo institucional con tracción.**

| Término buscado | Resultados | Lo mejor que apareció | Licencia | ★ |
|-----------------|-----------|----------------------|----------|---|
| `VDE-AR-N` (Alemania) | 188 | [KIT-IAI/PIDE](https://github.com/KIT-IAI/PIDE) — simulación de integración de DER y control autónomo de reactiva en redes de distribución | **MIT** (verificada en `LICENSE` crudo: Karlsruhe Institute of Technology, IAI) | 5 |
| `NOM-001-SEDE` (México) | 74 | [jacometoss/PyEWS](https://github.com/jacometoss/PyEWS) — dimensionado de conductores eléctricos | GPL-3.0 | 4 |
| `G99` (Reino Unido) | 24 | [Nero-Engine/spark-pack-mcp](https://github.com/Nero-Engine/spark-pack-mcp) — servidor MCP de cálculo eléctrico con G98/G99 | **sin licencia** | 0 |
| `CEI 0-21` (Italia) | 10 | calculadoras fotovoltaicas italianas de autor individual | MIT / varias | 0 |
| `PRODIST` (Brasil) | 142 | **nada**: colisión de nombres completa | — | — |

**La regla que sale de esto, y vale para cualquier industria de esta KB: buscar el *protocolo*, no
la *norma*.** `IEEE 2030.5` y `CSIP-AUS` son protocolos máquina-a-máquina con implementación
obligatoria: producen librerías, clientes y servidores. `VDE-AR-N 4105`, `CEI 0-21`, `G99` y
`NOM-001-SEDE` son normas documentales de cumplimiento: producen hojas de cálculo y calculadoras de
0 ★. La diferencia no es la madurez eléctrica del país —Alemania e Italia no están detrás de
Australia— sino **si la norma obliga a que dos máquinas se hablen**. Donde obliga, hay código
abierto; donde sólo obliga a entregar un expediente, hay PDF.

⚠️ **`PRODIST` se suma a la lista de términos inutilizables** (`hydrogen`, `AMI`, `utility billing`,
`reservoir`, registrados en pases anteriores): 142 resultados y **ninguno** es el PRODIST de ANEEL.
"ProDist" es, en GitHub, cálculo de distribuciones de probabilidad, un sistema de gestión de
distribuidores y un curso de programación distribuida. Para Brasil hay que volver al vocabulario que
sí funcionó en el pase 6: **el nombre del framework más el país** (`pypsa-meets-brazil`).

**Único rescate institucional del barrido: `KIT-IAI/PIDE` (MIT, 5 ★, push 2026-08-05).** Es del
Institute for Automation and Applied Informatics del KIT, y simula integración de generación
distribuida con control autónomo de potencia reactiva. 5 ★ no es tracción: vale como **referencia de
método verificable** para una propuesta en Alemania, no como dependencia.

### Quinto pase consecutivo sin agente de operación de red — ahora medido también desde fuera de GitHub

La consulta global prescrita (`top open source AI agents energy 2026 github MIT`) devuelve listicles
de agentes de propósito general —OpenClaw, Hermes, OpenCode, OpenHands, CrewAI, Browser Use— **sin
una sola entrada energética**. Las fuentes además se contradicen en estrellas y licencias entre sí.
Eso confirma, desde un canal distinto al conteo de repos, lo que los pases 4-7 midieron: la capa
agéntica energética **es institucional o es de forecasting**, y no de mercado. Lo proponible sigue
siendo `Power-Agent/*` (MIT), `pypsa-mcp` (MIT), `EnergyPlus-MCP` (BSD) y la cadena de forecasting
del pase 7.

### Novedad agéntica real del pase, pequeña y honesta

[`open-energy-transition/gridlens`](https://github.com/open-energy-transition/gridlens) — **MIT**,
1 ★, push **2026-11-19**. Se describe como *"AI-native app to see who's using which energy models,
where, and for what grid decisions"*. Es el primer repo que esta KB registra cuyo objeto es
**observabilidad del propio ecosistema de modelos**: qué modelo usa quién y para qué decisión de red.

⚠️ **Cómo proponerlo:** 1 ★ y un día de vida. **No es una dependencia.** Vale por dos cosas
concretas: (a) confirma que Open Energy Transition —el autor de `pypsa-mcp`— está construyendo la
capa agéntica alrededor de PyPSA, y (b) el problema que nombra (*trazabilidad de qué modelo sostiene
qué decisión*) es exactamente el entregable que un cliente regulado pide y que ningún repo cubría.
Si se vuelve real, es la pieza de governance del stack.

### Correcciones de este pase a afirmaciones de pases anteriores

1. **`CommonGrid` sí tiene repo de código localizable.** `compose/patterns.md` e `intel/trends.md`
   registraron *"buscados en GitHub: sin repo de código localizable"*. Es
   [`TextureHQ/commongrid`](https://github.com/TextureHQ/commongrid) — 14 ★, push 2026-11-19. El
   fallo fue de vocabulario de organización: `user:texture-hq` devuelve HTTP 422 y la organización
   real es `TextureHQ`. **La advertencia de licencia que la KB había hecho se confirma y se
   endurece**: el `LICENSE` crudo dice literalmente *"Open Data Commons Open Database License (ODbL)
   v1.0 — Copyright (c) 2025-2026 Texture, Inc."* Es licencia de **base de datos**, con obligación de
   compartir derivados de la base: utilizable como fuente, **no empotrable** como dataset en un
   entregable cerrado.
2. **El "gap de geotermia" era, en efecto, artefacto de sintaxis** (como el pase 7 sospechó): existe
   [`open-energy-transition/geothermal-modelling`](https://github.com/open-energy-transition/geothermal-modelling)
   — **AGPL-3.0**, 6 ★, push 2026-11-16. Gap cerrado en oferta; abierto en licencia proponible.

## 2026-11-20 — pase 7 (aparece el agente que faltaba, y no es un agente de red: es de forecasting)

**Titular del pase: por primera vez en cuatro pases la capa agéntica energética tiene una novedad
proponible, y llega por el lado del forecasting, no por el de la operación de red.**
[`TimeCopilot/timecopilot`](https://github.com/TimeCopilot/timecopilot) (MIT, 643 ★, 89 forks,
push 2026-11-18) se describe como *"the Agentic Forecasting Framework. Built on LLMs and Time Series
Foundation Models"*. Es la primera pieza que combina las dos capas que esta KB tenía separadas —
razonamiento LLM (pases 1-3) y foundation models (pase 4) — en un solo framework permisivo con
tracción real. No es energético por diseño, pero el forecasting de carga y precio es su caso de uso
canónico, y es la respuesta concreta al gap que los pases 4, 5 y 6 declararon.

**La cadena de forecasting agéntico, toda verificada este pase y toda permisiva:**

| Capa | Repo | Licencia | ★ | Rol |
|------|------|----------|---|-----|
| Orquestación agéntica | [TimeCopilot/timecopilot](https://github.com/TimeCopilot/timecopilot) | MIT | 643 | LLM elige modelo, explica el pronóstico |
| Modelo fundacional de series | [amazon-science/chronos-forecasting](https://github.com/amazon-science/chronos-forecasting) | Apache-2.0 | 6328 | Pre-entrenado, zero-shot |
| Forecasting energético con TSFM | [arnaud-vs/open-predico](https://github.com/arnaud-vs/open-predico) | Apache-2.0 | 54 | Aplica TSFM a energía |
| Línea base corta solar/viento/carga | [williamhobbs/hefty](https://github.com/williamhobbs/hefty) | BSD-3-Clause | 85 | El baseline honesto a batir |
| Pipeline de producción de utility | [OpenSTEF/openstef](https://github.com/OpenSTEF/openstef) | MPL-2.0 | 184 | Ya catalogado; sigue siendo el de operación |

⚠️ **Cómo proponerlo sin exagerar:** `timecopilot` y `chronos` son de propósito general. Lo que esta
KB puede afirmar es que **existe la cadena**, no que esté validada en despacho. `openstef` sigue
siendo la única pieza con operación real en una utility (Alliander, RTE). La receta nueva —
*Receta 25* en `compose/patterns.md` — pone `timecopilot` en la vía de **evaluación**, con `openstef`
como control, y no en la vía de producción.

**Segunda novedad, institucional y pequeña: un TSO escribió un agente sobre su propio modelo de red.**
[`statnett/Talk2PowerSystem`](https://github.com/statnett/Talk2PowerSystem) (Apache-2.0, 17 ★, push
2026-05-15) es de Statnett, el operador de transmisión noruego: *"Talk to the Power System"*, LLM
sobre grafo de conocimiento CIM. Es la primera vez que esta KB registra un **agente de red escrito por
el operador**, no por un laboratorio ni por un consorcio. Son 17 ★ y el último push es de mayo: no es
una base de producto, **es la prueba de que el patrón es el que los TSO quieren**. Para una propuesta
vale más como precedente citable que como dependencia.

**Lo que sigue sin existir, y ahora con medición de industria, no sólo de repos.** Las búsquedas de
agentes energéticos creados después de 2026-08-01 (`energy agent LLM`, `grid OR substation OR utility
agentic`, ambas con `created:>`) devuelven **ruido puro**: extensiones de Chrome, bots de pentest,
asistentes de voz domésticos. Cuarto pase consecutivo sin un agente de operación de red proponible.
La novedad es que ahora hay un número externo que dice lo mismo: una **encuesta de la IEA a operadores
de red de 13 países** encuentra que sólo el **23 % usa IA para operación en tiempo real**, frente a
**~70 % que la usa para mantenimiento de activos y planificación**. El hueco que esta KB medía
contando repos es el mismo que la IEA mide contando operadores. Eso convierte el gap en **argumento de
venta**: el trabajo proponible hoy está en el 70 %, no en el 23 %.

**Confirmación regulatoria que refuerza la tesis human-in-the-loop del pase 3 y 6:** la encuesta de
Grant Thornton 2026 del sector energético reporta que para el **54 %** la incertidumbre regulatoria y
de cumplimiento es la principal preocupación al desplegar IA agéntica, con **38 % en piloto o prueba
de valor** y **32 % que se estanca después de haber sido declarado listo para escalar**. Ese 32 % es
el mercado de Globant: no es un problema de modelo, es de operacionalización y gobernanza.
Guía **CISA/NSA de mayo de 2026** para infraestructura crítica: zero trust, defensa en profundidad y
**mínimo privilegio** — es decir, la arquitectura donde el agente propone y
[`opfab/operatorfabric-core`](https://github.com/opfab/operatorfabric-core) acepta.

## 2026-11-20 — pase 6 (ninguna novedad agéntica pasa la barra, y una confirmación regulatoria que vale más)

**Titular del pase, dicho como corresponde: en la capa de agentes energéticos no hay novedad
proponible esta semana.** La búsqueda global de "mejores agentes AI open source 2026" devuelve
`OpenClaw`, `Hermes`, `OpenHands`, `Browser Use`, `CrewAI` y `LangGraph` — agentes y frameworks de
propósito general, **ninguno energético**. Esto confirma por tercer pase consecutivo el hallazgo del
pase 5: **no existe un "agente energético" open source de propósito general con tracción**, y lo
creíble sigue siendo lo institucional ya catalogado (`PowerMCP`, `PowerSkills`, `EnergyPlus-MCP`,
`idfkit-mcp`, `pypsa-mcp`, la familia `energnn`). Se registra como hueco medido, no como silencio.

**Lo que sí es nuevo y cambia el argumento de venta de la capa agéntica: la NERC dice por escrito que
la IA debe asistir la decisión, no actuar de forma autónoma.** Hasta ahora la tesis
*human-in-the-loop* de esta KB —que `operatorfabric-core` es la pieza sin la cual una demo de red no
es desplegable, establecida en el pase 3— se sostenía en razonamiento de ingeniería. Ahora tiene
respaldo del organismo que fija los estándares de fiabilidad de la red norteamericana. Deja de ser
una opinión de arquitectura y pasa a ser **cumplimiento**: en un encargo con una utility de EE. UU.,
la capa de aceptación humana no es un extra que se negocia, es el requisito.

**Dónde encaja cada pieza, ahora que la obligación es explícita:**

| Capa | Repo | Licencia | Rol bajo la guía de la NERC |
|------|------|----------|------------------------------|
| Razonamiento sobre herramientas | [Power-Agent/PowerMCP](https://github.com/Power-Agent/PowerMCP) | MIT | Propone; **no ejecuta** |
| Recomendación de maniobra | [ainetus/ExpertOp4Grid](https://github.com/ainetus/ExpertOp4Grid) | MPL-2.0 | Propone topología |
| **Aceptación humana trazable** | [opfab/operatorfabric-core](https://github.com/opfab/operatorfabric-core) | MPL-2.0 | **La pieza que satisface el requisito** |
| Ejecución en campo | [VOLTTRON/volttron](https://github.com/VOLTTRON/volttron) | Apache-2.0 | Actúa sólo tras aceptación |

**Novedad regional de contexto, no de repo (ver `intel/market.md` para el detalle):** la Comisión
Europea publicó el **3 de junio de 2026** una *Strategic Roadmap for Digitalisation and AI in the
Energy Sector* con tres pilares, y el **17 de julio de 2026** una propuesta de modificación del
Reglamento del Mercado Eléctrico. Para la capa agéntica importa una línea concreta: la Comisión
**redactó guías de clasificación de sistemas de IA de alto riesgo según el artículo 6 del AI Act**. Si
un copiloto de operación de red cae en esa clasificación, el *human-in-the-loop* de arriba es
obligatorio también en EMEA, por la misma razón que en North America pero con otra base legal.
⚠️ Todo esto proviene de **fuentes secundarias**: el registro primario de la UE
(`data.consilium.europa.eu`) **no resuelve desde este entorno**, sexto pase consecutivo con esa
limitación. No citar fechas de artículo en una propuesta sin abrir el documento oficial.

## 2026-11-20 — pase 5 (la cohorte LF Energy de septiembre, y una trampa de verificación propia)

**Titular del pase: los cuatro proyectos que LF Energy anunció el 15 de septiembre de 2026 existen,
son localizables y tres de los cuatro son permisivos o MPL — pero ninguno pasa de 34 ★.** El pase 4
cerró diciendo que faltaba el modelo y lo encontró (`gridfm`, `GridSFM`). Este pase cierra el circuito
institucional: el consorcio que publica esos modelos tiene además una **familia agéntica de red**
recién nacida, con gobernanza de la Linux Foundation y convertidores hacia los dos motores que esta
KB ya tenía (`powsybl` y `pandapower`).

**Nuevo esta semana — cohorte LF Energy (anuncio 2026-09-15), verificada repo por repo:**

| Repo | Licencia | ★ | Forks | Issues | Push | Señal |
|------|----------|---|-------|--------|------|-------|
| [energnn/energnn](https://github.com/energnn/energnn) | **MPL-2.0** | 34 | 4 | 15 | 2026-11-16 | GNN para redes de energía **reales**, no sintéticas. Creado 2025-10-16 |
| [assetlife-project/assetlife](https://github.com/assetlife-project/assetlife) | **Apache-2.0** | 7 | 3 | **32** | 2026-11-19 | Modelado estocástico de vida de activo. Creado 2026-09-03: **32 issues sobre 7 ★** |
| [SMART-HEMS-Benchmark/smart-hems-benchmark](https://github.com/SMART-HEMS-Benchmark/smart-hems-benchmark) | **MIT** | 7 | 2 | 0 | 2026-07-09 | Banco de pruebas HEMS; el par de evaluación de `agentic-ai-hems` |
| [energnn/tensio](https://github.com/energnn/tensio) | **MPL-2.0** | 1 | 0 | 0 | 2026-10-19 | Aplicación de EnerGNN a mejora de tensiones |
| [energnn/pypowsybl-to-energnn](https://github.com/energnn/pypowsybl-to-energnn) | **MPL-2.0** | 3 | 2 | 2 | 2026-10-15 | Conversor `pypowsybl` → grafo EnerGNN |
| [energnn/pandapower-to-energnn](https://github.com/energnn/pandapower-to-energnn) | **MPL-2.0** | 0 | 0 | 0 | 2026-09-08 | Conversor `pandapower` → grafo EnerGNN |

**Por qué los conversores importan más que la librería.** `energnn` sola es una librería de GNN con 34 ★:
nada que justifique una propuesta. Los dos conversores la convierten en otra cosa — una capa que lee
el modelo de red que el cliente **ya tiene** en PowSyBl o pandapower y lo entrega como grafo
entrenable. El valor no está en el modelo, está en que no hay que rehacer el modelo de red.

**La señal de `assetlife` es la relación issues/estrellas, no las estrellas.** 32 issues abiertas
sobre 7 ★ y dos meses y medio de vida es desarrollo activo de un equipo, no abandono. El pase 4 de
esta KB estableció la regla de comprobar `forks_count` antes de comprometer alcance; este pase añade
el corolario: **en un repo recién nacido, `open_issues_count` alto es señal positiva**, al revés que
en uno maduro.

### Corrección de método: mi propio verificador se equivocó, y el error era en la dirección peligrosa

Al resolver licencias leyendo el archivo crudo, el detector marcó `energnn/energnn` como **AGPL-3.0**.
La API de GitHub decía **MPL-2.0**. Ganó la API: el texto de la MPL-2.0 **nombra la AGPL en su propia
cláusula 1.12** ("Secondary Licenses" = GPL-2.0, LGPL-2.1, AGPL-3.0), de modo que cualquier detección
por `grep` de la cadena *"GNU Affero"* convierte toda MPL-2.0 en AGPL.

**Consecuencia para esta KB:** la familia europea de LF Energy es MPL-2.0 de forma consistente
(ver nota del tercer pase) — es decir, **toda ella** es vulnerable a este falso positivo. Un pase
futuro que "rescate licencias leyendo el crudo" sin esta precaución reclasificaría media KB a AGPL e
inventaría una obligación de liberar el servicio que no existe. Regla: **ante conflicto entre la API
y un detector de texto sobre una licencia de la familia MPL, gana la API**; el archivo crudo sólo
decide cuando la API dice `null` o `NOASSERTION`.

### La cola larga de agentes LLM energéticos sigue sin ser proponible

Consulta `energy agent LLM in:name,description created:>2026-06-01`, 15 resultados. **Ninguno pasa de
7 ★**; la mayoría son 0 ★ de autor individual (`langgraph-energy-agent` MIT 0 ★,
`energyplus-llm-hvac-agent` MIT 0 ★, `renewable-energy-LLM-agent` sin licencia,
`Knowledge-Orchestrated-LLM-Agent-Workflow` 1 ★ sin licencia). Es el mismo patrón que el pase 3 midió
en LATAM: la demanda se ve, la oferta es personal y sin licencia.

**Lectura:** lo creíble en esta categoría sigue siendo lo institucional que esta KB ya tiene
(`Power-Agent/PowerMCP`, `LBNL-ETA/EnergyPlus-MCP`, `idfkit/idfkit-mcp`,
`open-energy-transition/pypsa-mcp`). **No** hay un "agente energético" open source de propósito
general con tracción. Sigue siendo integración, no instalación.

---

## 2026-11-20 — pase 4 (los foundation models de red, y una trampa de estrellas)

**Titular del pase: apareció la capa que faltaba entre el servidor MCP y el entorno RL — modelos
preentrenados específicos de red, permisivos y con respaldo corporativo.** Los pases 1-3 de hoy
describieron el razonamiento sobre herramientas (`PowerMCP`), el lugar de ejecución (`VOLTTRON`) y la
sala de control (`operatorfabric-core`). Faltaba el modelo.

**Nuevo esta semana — foundation models de red:**

| Repo | Licencia | ★ | Forks | Push | Señal |
|------|----------|---|-------|------|-------|
| [microsoft/GridSFM](https://github.com/microsoft/GridSFM) | MIT | 177 | 41 | 2026-07-15 | Microsoft publica *Small Foundation Models* de red. Creado 2026-04-23; **sin push en 4 meses** |
| [gridfm/gridfm-datakit](https://github.com/gridfm/gridfm-datakit) | Apache-2.0 | 170 | 40 | 2026-11-14 | genera datos de flujo de potencia para entrenar |
| [gridfm/gridfm-graphkit](https://github.com/gridfm/gridfm-graphkit) | Apache-2.0 | 113 | 41 | 2026-11-19 | entrena/fine-tunea el GNN fundacional; par del anterior |
| [emarche/RL2Grid](https://github.com/emarche/RL2Grid) | MIT | 58 | 11 | 2026-09-16 | benchmark estandarizado de agentes RL en red realista |

Relación fork/star de `gridfm-graphkit`: **0.36** — la más alta de la categoría agéntica de esta KB.
Gente lo está bifurcando para entrenar, no sólo marcándolo. Es la señal que distingue una categoría
naciente real de una moda.

**Nuevo esta semana — MCP sobre datos de red en vivo (categoría embrionaria, 0–3 ★):**

`azmartone67/dchub-mcp-server` (MIT, *Data Center Power Index*, 300+ mercados),
`pipeworx-io/mcp-neso` (MIT, operador británico NESO), `pipeworx-io/mcp-georgia-energy` (MIT),
`sohamshindework/gridpulse` (MIT, red DE+US, scheduling carbon-aware, **creado hace dos días**).

Se registran como *prueba de viabilidad del patrón*, no como dependencias. Lo relevante para una
propuesta: conectar el API de un TSO a un agente vía MCP es ya trabajo de días.

**Hallazgo negativo que ahorra un error:** dos repos de forecasting de carga con **1764 ★ / 0 forks** y
**1627 ★ / 0 forks** (misma cuenta, `KEV0143`, cero issues en ambos). Habrían encabezado la tabla de
forecasting de esta KB. Descartados: estrellas de cuatro cifras con relación fork/star de 0.00 no son
adopción. **Regla nueva: ante >1000 ★, verificar `forks_count` e `open_issues_count` antes de escribir
la fila.**

**Categoría confirmada vacía otra vez:** agente de *ejecución* de trading mayorista. Cuarto pase
consecutivo sin encontrarlo. `assume` y `elecsim` siguen siendo simuladores.

**Deuda de verificación del pase 1, cerrada.** El primer pase dejó cinco filas con licencia `?`.
Resueltas todas hoy, y **las cinco son inutilizables** — vale la pena que quede escrito, porque una
licencia desconocida se parece demasiado a una licencia permisiva cuando hay prisa:

| Repo | Veredicto | Evidencia |
|------|-----------|-----------|
| `Basil-Saad/smart-water-grid-ai` | ❌ **"All rights reserved"** | el `LICENSE` dice literalmente *"No permission is granted to copy, modify, redistribute, or use this project"*; publicado *"for academic and portfolio purposes only"* |
| `sariekiriyuu/smartEMS-MultiAgent-Demo` | ❌ **no comercial** | *"Custom License Agreement"*: permiso sólo para uso *personal, educational, and non-commercial* |
| `Marinalizm/BESS-energy-management-system` | ❌ sin licencia | sin archivo en ninguna rama |
| `ArsamAryandoust/awesome-ml-power-systems` | ❌ sin licencia | sin archivo en ninguna rama |
| `Legalagecolouring820/Random-Forest-Model-EMS-...` | ❌ sin licencia | sin archivo en ninguna rama |

**La lección**: `?` en una columna de licencia no es neutral, es **deuda**. De cinco casos, cero
resultaron usables — dos de ellos con prohibición expresa. Ninguna fila con licencia sin resolver
debería sobrevivir a un pase.

⚠️ **Nota de homónimos**: existen **dos** repos `smartEMS-MultiAgent-Demo` distintos
(`sariekiriyuu/`, 3 ★ y `lhg96/`, 6 ★), con la misma descripción. No son el mismo proyecto ni un
renombre: resuelven por separado en la API con contadores distintos. Al citar uno, incluir el owner.

---

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
