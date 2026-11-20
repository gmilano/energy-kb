---
industry: energy
region: Global
updated: 2026-11-20
---

# 📈 Repos trending — energy

> **Archivo APPEND-ONLY.** Cada pase añade una sección fechada arriba y conserva el historial
> debajo. No reescribir: el valor de este archivo es la serie temporal.

## 2026-11-20 — pase 9 (tres gaps medidos con número, y la frontera exacta del canal de verificación)

**Titular del pase: la oferta nueva está en las capas de protocolo (ISO 15118, EEBus, IEC 61850-6) y
la escasez está donde esta KB ya tiene recetas escritas — almacenamiento, medición y cumplimiento.**
Las tres se midieron con consulta y número, no se dedujeron.

### Gap 1 — Optimización de baterías: la oferta abierta es **un** repo

| Consulta | Resultados | Lo real |
|----------|-----------|---------|
| `"battery energy storage" in:name,description stars:>25` | **total = 1** | [`BigdogManLuo/DBESS-Arbitrage`](https://github.com/BigdogManLuo/DBESS-Arbitrage) (Apache-2.0, 26 ★, push 2025-11-19) |
| `BESS in:name,description stars:>25` | 22 | **colisión total de nombres**: un switch de Berkeley (333 ★), una herramienta de overclock de GPU Snapdragon (1.803 ★) y funciones de Bessel (91 ★) |

El único optimizador sectorial con tracción es
[`FlexPwr/bess-optimizer`](https://github.com/FlexPwr/bess-optimizer) (118 ★, 27 forks): modelo de
tres mercados en `pyomo` de CF Flex Power GmbH — y tiene **dos problemas**: la API dice
`NOASSERTION` y el `LICENSE` crudo abre con *"This program is free software: you can redistribute it
and/or modify"*, es decir **copyleft de familia GPL**, no permisivo; y su último push es
**2025-10-02, trece meses**.

**Consecuencia directa para esta KB:** la *Receta 13 — Dimensionamiento y garantía de vida de un
BESS* se apoya en una base de oferta de un repo. Presupuestarla como **ingeniería de modelo**, no
como integración de producto, y no prometer un acelerador reutilizable que no existe.

### Gap 2 — Medición y facturación: confirmación cuantificada de lo que el octavo pase ya había acotado

**Esto no es un hallazgo nuevo: `verticals/solutions.md` ya tiene la capa meter-to-cash resuelta**
por el octavo pase (`killbill` Apache-2.0 5.859 ★ como motor genérico, `navariltd/utility-billing`
AGPL-3.0 sobre ERPNext como única app sectorial, más la trampa de término *MDM = mobile device
management*). Lo que este pase añade son **los números de la escasez**, que antes no estaban:

| Consulta | Resultados | Lo mejor que aparece |
|----------|-----------|---------------------|
| `"meter data management" in:name,description,readme` | 155 | [`aws-solutions-library-samples/guidance-for-meter-data-analytics-on-aws`](https://github.com/aws-solutions-library-samples/guidance-for-meter-data-analytics-on-aws) — Apache-2.0, **7 ★**, push 2024-08-09 |
| `utility billing in:name,description stars:>30` | **5** | `navariltd/utility-billing` (AGPL-3.0, 70 ★) es el único sectorial; el resto son facturación genérica o falsos positivos |

Con el término correcto (`"meter data management"`, no `MDM`) la búsqueda devuelve 155 repos y el
mejor tiene **7 estrellas y dos años sin push**. Queda medido: **no hay plataforma MDM abierta**, y
la conclusión de producto del octavo pase (ERPNext+AGPL o Kill Bill+Apache con el modelo de datos
energético por construir) es la correcta por ausencia de alternativa, no por preferencia.

### Gap 3 — NERC CIP: 573 resultados, cero herramientas del sector

`"NERC CIP" in:name,description,readme` → **573 resultados y ninguno energético**. Lo que aparece
arriba son listas genéricas de cumplimiento: `awesome-opa` (905 ★), `awesome-compliance` (111 ★),
`aws-guard-rules-registry` (146 ★, muerto desde 2024).

Esto importa porque esta KB ya tiene la *Receta 29 — Programa de cumplimiento NERC para carga de
datacenter* apuntada contra el plazo de **diciembre de 2026** de los estándares de carga
computacional. **La oferta abierta contra ese plazo es cero**: el expediente es trabajo de
consultoría, no un repo que forkear. Único hallazgo adyacente real:
[`argonne-citadel/grid-stix`](https://github.com/argonne-citadel/grid-stix) (GPL-3.0, 2 ★, push
2026-08-19), de **Argonne National Laboratory**, que lleva inteligencia de amenazas en formato STIX
al dominio de red. Dos estrellas: es una señal de dirección, no una base.

### Oferta nueva verificada este pase

**Ingeniería IEC 61850 (no el runtime, la configuración):**

| Repo | Licencia | ★ | Forks | Push | Nota |
|------|----------|---|-------|------|------|
| [openscd/open-scd](https://github.com/openscd/open-scd) | **Apache-2.0** | 145 | 53 | ⚠️ 2026-01-12 | Editor de **SCL (IEC 61850-6 Ed2)**: la configuración de subestación. **10 meses sin push y 229 issues abiertas** |

El perfil de licencia del stack 61850 **se parte en dos**: el runtime
([`mz-automation/libiec61850`](https://github.com/mz-automation/libiec61850), **GPL-3.0**, 1.254 ★)
y la ingeniería (`open-scd`, **Apache-2.0**). Para un producto, la pieza enlazable es la de
ingeniería; la de runtime obliga al límite de proceso que ya fija la regla de arquitectura.

**Forecasting de precio: hay benchmark permisivo, y los foundation models están bloqueados o vacíos:**

| Repo | Licencia | ★ | Forks | Push | Nota |
|------|----------|---|-------|------|------|
| [jeslago/epftoolbox](https://github.com/jeslago/epftoolbox) | **Apache-2.0** | 417 | 115 | 2026-05-18 | Benchmark y toolbox de **electricity price forecasting**: la vara académica de la categoría |
| [runyao-yu/PriceFM](https://github.com/runyao-yu/PriceFM) | ⚠️ **sin licencia** | 158 | 13 | 2026-10-25 | Foundation model probabilístico de precio. 158 ★ y legalmente inusable |
| [alliander-opensource/s4casting](https://github.com/alliander-opensource/s4casting) | **MPL-2.0** | 12 | 2 | **2026-11-20** | Time series foundation models para forecasting energético, de **Alliander** |

`s4casting` con 12 ★ es la tercera aparición de Alliander en esta KB (`power-grid-model`,
`openstef`, ahora `s4casting`): **T2 sigue siendo el hallazgo estructural más rentable de esta KB**,
y la pieza recién publicada por un DSO vale más que un repo de 1.000 ★ sin dueño institucional.

**Geotermia: T26 decía "un solo repo usable" y son tres (corrección):**

| Repo | Licencia | ★ | Forks | Push |
|------|----------|---|-------|------|
| [MassimoCimmino/pygfunction](https://github.com/MassimoCimmino/pygfunction) | **BSD-3-Clause** | 75 | 26 | 2026-09-12 |
| [waiwera/waiwera](https://github.com/waiwera/waiwera) | LGPL-3.0 | 62 | 16 | **2026-11-20** |
| `NatLabRockies/GEOPHIRES-X` *(ya catalogado)* | MIT | 67 | 49 | 2026-11-19 |

`pygfunction` (factores de respuesta térmica de intercambiadores geotérmicos) es **más permisivo y
más estrellado que GEOPHIRES-X**, y T26 no lo tenía. `waiwera` es un simulador paralelo de flujo
geotérmico con push de hoy. El veredicto de T26 ("base para estudio técnico-económico, no
ecosistema para plataforma") **se mantiene**; la corrección es de inventario, no de tesis.

**Eólica, piezas de recurso y modelo que faltaban:**

| Repo | Licencia | ★ | Forks | Push | Nota |
|------|----------|---|-------|------|------|
| [IEAWindSystems/IEA-15-240-RWT](https://github.com/IEAWindSystems/IEA-15-240-RWT) | **Apache-2.0** | 314 | 161 | 2026-10-21 | Turbina de referencia de **15 MW** de IEA Wind: el activo de referencia para dimensionar |
| [ebranlard/welib](https://github.com/ebranlard/welib) | **MIT** | 120 | 43 | 2026-11-10 | Librería de energía eólica (Python/Matlab) para análisis de turbinas |

**Carbono y señal de red:**

| Repo | Licencia | ★ | Forks | Push | Nota |
|------|----------|---|-------|------|------|
| [thegreenwebfoundation/grid-intensity-go](https://github.com/thegreenwebfoundation/grid-intensity-go) | **Apache-2.0** | 84 | 10 | 2026-05-11 | Intensidad de carbono como factor de decisión de *dónde y cuándo* correr cómputo, en Go |
| [JamesTwallin/GridSeis](https://github.com/JamesTwallin/GridSeis) | **MIT** | 31 | 1 | 2026-11-04 | Predice intensidad de carbono a partir de **frecuencia de red** (FFT + gradient boosting) |

**Semántica y protocolo industrial:**

| Repo | Licencia | ★ | Forks | Push | Nota |
|------|----------|---|-------|------|------|
| [DataTreehouse/maplib](https://github.com/DataTreehouse/maplib) | **Apache-2.0** | 192 | 14 | **2026-11-20** | Mapeo a grafos RDF; la pieza que falta entre CIM/CGMES y una capa semántica consultable |
| [rsmusllp/termineter](https://github.com/rsmusllp/termineter) | **BSD-3-Clause** | 281 | 106 | 2026-03-17 | Framework de **pruebas de seguridad de medidores inteligentes** |
| [WillCodeForCats/solaredge-modbus-multi](https://github.com/WillCodeForCats/solaredge-modbus-multi) | **Apache-2.0** | 343 | 29 | 2026-11-19 | Integración Modbus/TCP completa de inversores SolarEdge |
| [vinerya/virtual-power-plant](https://github.com/vinerya/virtual-power-plant) | **MIT** | 96 | 26 | 2026-11-16 | Librería de gestión y simulación de **planta virtual** |

**Dato público de EE.UU. con problema de licencia:**
[`california-energy-commission/MIDAS`](https://github.com/california-energy-commission/MIDAS) —
repo oficial de la **California Energy Commission** (servidor de datos de tarifa para automatización
de demanda), **9 ★, 5 forks, sin archivo de licencia**. Organismo público, dato autoritativo,
licencia ausente: entra en la categoría bloqueada de T20, no en la de dato reutilizable.

## 2026-11-20 — pase 8 (había una organización entera de ~30 repos permisivos catalogada en uno solo)

**Titular del pase: esta KB tenía a Open Energy Transition catalogada por un repo (`pypsa-mcp`) y la
organización tiene alrededor de treinta, la mayoría MIT y casi todos con push de noviembre de
2026.** Es la adición de oferta más grande de cualquier pase de esta KB, y no vino de una búsqueda
por dominio: vino de consultar `org:open-energy-transition` después de que la organización apareciera
de pasada en un resultado de búsqueda web.

### El clúster Open Energy Transition, verificado repo por repo (`search/repositories`, 2026-11-20)

| Repo | Licencia | ★ | Push | Qué aporta |
|------|----------|---|------|-----------|
| [grid2poster](https://github.com/open-energy-transition/grid2poster) | MIT | 272 | 2026-10-23 | Genera pósters de la red eléctrica de un país. Suena cosmético: es renderizado de topología de red a partir de datos abiertos |
| [Awesome-Electrical-Grid-Mapping](https://github.com/open-energy-transition/Awesome-Electrical-Grid-Mapping) | CC0-1.0 | 171 | 2026-11-17 | Dataset curado de mapas y datasets de red eléctrica globales. **CC0** = dominio público, sin fricción |
| [MapYourGrid](https://github.com/open-energy-transition/MapYourGrid) | CC-BY-4.0 | 103 | 2026-10-01 | Iniciativa y tooling para mapear la red eléctrica por país en OpenStreetMap |
| [Awesome-Grid-Model-Data](https://github.com/open-energy-transition/Awesome-Grid-Model-Data) | ⚠️ **sin licencia** | 80 | 2025-07-24 | Catálogo abierto de datasets de red para probar interoperabilidad y reproducibilidad |
| [solver-benchmark](https://github.com/open-energy-transition/solver-benchmark) | ⚠️ AGPL-3.0 | 78 | 2026-11-19 | Benchmark de solvers (MI)LP sobre problemas de modelado energético |
| [pypsa-mcp](https://github.com/open-energy-transition/pypsa-mcp) | MIT | 74 | 2026-03-20 | *(ya catalogado)* Servidor MCP que expone PyPSA a LLMs |
| [Awesome-Electricity-Demand](https://github.com/open-energy-transition/Awesome-Electricity-Demand) | MIT | 74 | 2026-11-19 | *(ya catalogado como fuente)* Recursos de demanda eléctrica horaria y sub-horaria |
| [demandcast](https://github.com/open-energy-transition/demandcast) | ⚠️ AGPL-3.0 | 47 | 2026-11-19 | Descarga demanda histórica + clima + socioeconómicos y genera demanda sintética futura |
| [earthpv](https://github.com/open-energy-transition/earthpv) | MIT | 22 | 2026-11-20 | Mapeo de solar en tejado a partir de imagen satelital gratuita |
| [PyPSA-Explorer](https://github.com/open-energy-transition/PyPSA-Explorer) | MIT | 18 | 2026-09-03 | Explorador interactivo de redes PyPSA |
| [deckGlDashboard](https://github.com/open-energy-transition/deckGlDashboard) | MIT | 15 | 2025-06-27 | Dashboard de visualización de PyPSA-Earth (deck.gl) |
| [grid-mapping-starter-kit](https://github.com/open-energy-transition/grid-mapping-starter-kit) | CC0-1.0 ⚠️ **archivado** | 14 | 2025-06-16 | Kit de arranque para mapear red de transmisión en OpenStreetMap |
| [osm-powerplants](https://github.com/open-energy-transition/osm-powerplants) | MIT | 11 | 2026-07-01 | Extrae y procesa datos de centrales eléctricas de OpenStreetMap |
| [pypsa-ppa](https://github.com/open-energy-transition/pypsa-ppa) | MIT | 8 | 2026-11-09 | **Toolkit PyPSA para simular y optimizar PPAs bajo distintos escenarios** |
| [rooftopsenti](https://github.com/open-energy-transition/rooftopsenti) | MIT ⚠️ **archivado** | 7 | 2026-07-05 | Detecta instalaciones grandes de solar en tejado con Sentinel-2 a escala país/estado |
| [openmod-features](https://github.com/open-energy-transition/openmod-features) | MIT | 6 | 2026-11-01 | Inventario de capacidades de las herramientas de modelado energético abierto |
| [geothermal-modelling](https://github.com/open-energy-transition/geothermal-modelling) | ⚠️ AGPL-3.0 | 6 | 2026-11-16 | Modelado geotérmico. **Cierra el "gap de geotermia"** que el pase 7 marcó como sospechoso de sintaxis |
| [geodiff-tool](https://github.com/open-energy-transition/geodiff-tool) | MIT | 4 | 2026-10-11 | Diff entre dos datasets geoespaciales |
| [osm-wikidata-toolset](https://github.com/open-energy-transition/osm-wikidata-toolset) | CC0-1.0 | 4 | 2026-11-15 | Extrae y analiza elementos eléctricos de Wikidata |
| [efuels-supply-potentials](https://github.com/open-energy-transition/efuels-supply-potentials) | ⚠️ AGPL-3.0 | 4 | 2026-07-08 | Modelado de red para potencial de suministro de electrocombustibles |
| [gridlens](https://github.com/open-energy-transition/gridlens) | MIT | 1 | 2026-11-19 | App AI-native: qué modelo energético usa quién, dónde y para qué decisión de red |

⚠️ **La advertencia de licencia más útil de este pase, y es contraintuitiva: una organización
confiable no es una licencia.** Dentro de esta misma organización, MIT domina **pero cuatro repos son
AGPL-3.0** (`solver-benchmark`, `demandcast`, `geothermal-modelling`, `efuels-supply-potentials`) y
al menos tres **no tienen licencia** (`Awesome-Grid-Model-Data` con 80 ★, `pypsa-moon`,
`pypsa-training-sessions`). `demandcast` es el caso que más muerde: es exactamente la pieza que uno
querría para un producto de forecasting de demanda, y su AGPL-3.0 obliga a liberar el servicio
derivado. **Verificar repo por repo, incluso dentro de una organización ya aprobada.**

**Las dos piezas de este clúster que cambian una propuesta hoy:**

1. **[`pypsa-ppa`](https://github.com/open-energy-transition/pypsa-ppa) (MIT, 8 ★, push 2026-11-09)**
   — simulación y optimización de **Power Purchase Agreements**. Esta KB tenía registrado el dato de
   mercado de que LATAM firma PPAs a menos de 0,06 USD/kWh y que Equinix contrató eólica y solar con
   Auren en Brasil, **y no tenía ninguna herramienta abierta de PPA**. 8 ★ es poca tracción, pero es
   MIT y resuelve el artefacto que un cliente corporativo pide primero: *¿a qué precio y con qué
   riesgo firmo?*
2. **[`earthpv`](https://github.com/open-energy-transition/earthpv) (MIT, 22 ★, push 2026-11-20) +
   [`rooftopsenti`](https://github.com/open-energy-transition/rooftopsenti) (MIT, 7 ★, ⚠️ **archivado**)** — detección
   de solar en tejado desde satélite gratuito. Es el insumo de la *generación distribuida invisible*:
   el problema real de una distribuidora que no sabe cuánta DER tiene conectada.

### Segunda adición: la capa de datos de utilities de EE. UU. que faltaba

| Repo | Licencia | ★ | Push | Qué aporta |
|------|----------|---|------|-----------|
| [catalyst-cooperative/pudl](https://github.com/catalyst-cooperative/pudl) | MIT | 621 | 2026-11-20 | **Public Utility Data Liberation**: datos del sistema energético de EE. UU. (FERC, EIA, EPA) limpiados y listos para análisis |
| [TextureHQ/commongrid](https://github.com/TextureHQ/commongrid) | ⚠️ **ODbL-1.0** (verificada en `LICENSE` crudo) | 14 | 2026-11-19 | Registro abierto de la red eléctrica de EE. UU. (iniciativa de Texture) |

`pudl` con 621 ★ y push del mismo día es el repo más grande que esta KB no tenía. Es **MIT** y es el
atajo que convierte los formularios de FERC y EIA en tablas analizables — precisamente el trabajo
sucio que precede a cualquier analítica de cola de interconexión (*Receta 21*).

### Tercera adición: el ecosistema alrededor de los frameworks de planificación

El pase 7 mandó generalizar el hallazgo del pase 6 (`pypsa-` + país) al resto de frameworks. Se hizo,
y **el resultado es mixto de una forma que conviene precisar**: la generalización funciona, pero lo
que destapa es sobre todo **tooling de ecosistema** y **modelos de tesis de 0 ★**, no instancias
nacionales institucionales como las de PyPSA.

| Repo | Licencia | ★ | Push | Qué aporta |
|------|----------|---|------|-----------|
| [OSeMOSYS/otoole](https://github.com/OSeMOSYS/otoole) | MIT | 33 | 2024-11-18 | Conversión de datos de entrada/salida de OSeMOSYS. ⚠️ Sin push desde nov-2024 |
| [EAPD-DRB/MUIOGO](https://github.com/EAPD-DRB/MUIOGO) | Apache-2.0 | 26 | 2026-10-31 | Interfaz de usuario de modelado para OG-Core y OSeMOSYS |
| [OSeMOSYS/MUIO](https://github.com/OSeMOSYS/MUIO) | Apache-2.0 | 22 | 2026-10-01 | Interfaz de usuario de modelado de OSeMOSYS |
| [transition-zero/tz-osemosys](https://github.com/transition-zero/tz-osemosys) | ⚠️ AGPL-3.0 | 46 | 2026-11-02 | Reimplementación moderna de OSeMOSYS por TransitionZero |
| [OSeMOSYS/osemosys_global](https://github.com/OSeMOSYS/osemosys_global) | ⚠️ AGPL-3.0 | 46 | 2026-06-22 | Generador de modelos de sistema eléctrico **global** |
| [MAHTEP/TEMOA-Italy](https://github.com/MAHTEP/TEMOA-Italy) | **MIT (código) + CC-BY-4.0 (datos)** — ver nota | 13 | 2026-11-16 | Modelo del sistema energético italiano 2006-2050. Politecnico di Torino, grupo MAHTEP |
| [MAHTEP/TEMOA-Europe](https://github.com/MAHTEP/TEMOA-Europe) | **MIT (código) + CC-BY-4.0 (datos)** | 4 | 2026-10-25 | Modelo europeo de región única con base de datos abierta hasta 2050 |
| [CANOE-main/canoe-electricity](https://github.com/CANOE-main/canoe-electricity) | MIT | 3 | 2026-09-10 | Sector eléctrico canadiense para el modelo CANOE (datasets Temoa) |
| [CANOE-main/canoe-transportation](https://github.com/CANOE-main/canoe-transportation) | MIT | 3 | 2026-11-18 | Sector transporte canadiense del modelo CANOE |
| [CANOE-main/canoe-industry](https://github.com/CANOE-main/canoe-industry) | MIT | 2 | 2026-09-04 | Sector industrial canadiense del modelo CANOE |
| [calliope-project/ec_modules](https://github.com/calliope-project/ec_modules) | MIT ⚠️ **archivado** | 4 | 2026-04-02 | Módulos reutilizables de workflow para modelos Calliope |
| [NetZeroAtlantic/ACES-Temoa](https://github.com/NetZeroAtlantic/ACES-Temoa) | ⚠️ GPL-2.0 | 1 | 2026-09-02 | Modelo del sistema energético del Atlántico canadiense |
| [DavidLikesLearning/temoa-dataCenter-3Pillars](https://github.com/DavidLikesLearning/temoa-dataCenter-3Pillars) | BSD-3-Clause | 0 | 2026-11-12 | Temoa de EE. UU. midiendo regulación de energía limpia **para datacenters** |

⚠️ **Nuevo patrón de licencia, y es el quinto sitio donde hay que mirar.** La KB ya registraba cuatro
lugares (`LICENSE*`, `COPYING`, el SPDX de `pyproject.toml`, un `legal.html` dentro del árbol).
`MAHTEP/TEMOA-Italy` añade un quinto caso: **un único `LICENSE` que se parte por tipo de contenido**.
La API de GitHub lo reporta `NOASSERTION`; el texto crudo dice, literalmente, *"TEMOA-Italy is
released under two licenses, according to the type of content"* — **CC-BY-4.0** para bases de datos
(`*.sql`, `*.zip`), documentación y figuras, y **MIT** para todo el código (`*.py`). Un gate
automático lo habría descartado, y es un modelo nacional europeo completo de una universidad
politécnica. **Regla: `NOASSERTION` en un modelo energético nacional casi siempre significa licencia
dual, no ausencia de licencia.**

**Nota honesta sobre el alcance de esta generalización.** Con `pypsa-` + país el pase 6 encontró
modelos nacionales institucionales. Con `temoa-`, `calliope-` y `osemosys-` lo que aparece es:
instrumentación del ecosistema (`otoole`, `MUIO`, `ec_modules`, `openmod-features`), dos familias
institucionales reales (**MAHTEP** en Italia/Europa y **CANOE** en Canadá) y una cola larga de
modelos de tesis de 0 ★ (`Calliope-Morocco`, `cumplido2025-thesis-sisol-amazonbr-calliope`,
`Thesis-model`, `OutwithEnergy`). **El patrón "framework + país" es real pero su rendimiento depende
del framework**: PyPSA tiene comunidad nacional, Temoa y Calliope tienen comunidad académica.

### Fuentes de descubrimiento nuevas (y una con reserva)

| Repo | Licencia | ★ | Push | Nota |
|------|----------|---|------|------|
| [martymcenroe/best-of-pes-ai](https://github.com/martymcenroe/best-of-pes-ai) | CC-BY-SA-4.0 | 3 | 2026-11-14 | Ranking de proyectos open source de IA/ML para los dominios de la IEEE Power & Energy Society. Complementa `best-of-ps` con el eje de IA |
| [DatariusAI/AI-in-Energy](https://github.com/DatariusAI/AI-in-Energy) | ⚠️ **sin licencia** | 0 | 2026-11-20 | Hub de investigación y código de IA para energía, refrescado a diario. Útil como *feed*; sin licencia, nada de ahí se cita como dependencia |

⚠️ Ambas son de 0-3 ★. Se registran como **fuentes de descubrimiento para el próximo pase**, no como
hallazgos de contenido: su valor es que reducen el coste de encontrar, no que aporten código.

### Buscado y no encontrado en este pase (para no repetirlo)

- **CIS / MDM de utility open source permisivo**: no existe. Buscado por `utility billing`, `CIS`,
  `MDM`, `meter data management`. Lo que aparece es (a) producto comercial (Fluentgrid, SMART360) y
  (b) facturación genérica no energética: `killbill` (Apache-2.0) y `openmeter` (Apache-2.0) sí son
  permisivos y sí sirven como sustrato, pero **no conocen una tarifa eléctrica**. "MDM" en GitHub es,
  casi siempre, *mobile device management*. Ver `verticals/solutions.md` para el detalle.
- **`user:texture-hq`**: devuelve HTTP 422 ("los usuarios y repositorios listados no se pueden
  buscar"). La organización es `TextureHQ`, sin guion. Un 422 de `search/repositories` es un error de
  nombre de organización, **no** la inexistencia de la organización.

### Hallazgos de la pasada de verificación de este pase (50 URLs, `search/repositories`)

Se verificaron **las 50 URLs** escritas en este pase. 48 resolvieron; las dos que no, y los tres
repos archivados, son lecciones de método:

1. **`repo:NREL/EnergyPlus` y `repo:NREL/floris` devuelven HTTP 422, no 404.** La organización NREL
   **se renombró a `NatLabRockies`** —algo que el pase 1 de esta KB ya había registrado— y las
   recetas nuevas de este pase se habían escrito con el nombre viejo. Corregido a
   [`NatLabRockies/EnergyPlus`](https://github.com/NatLabRockies/EnergyPlus) (1.626 ★, push
   2026-11-19) y [`NatLabRockies/floris`](https://github.com/NatLabRockies/floris) (BSD-3-Clause,
   302 ★, push 2026-11-18). **Un 422 de `search/repositories` significa casi siempre nombre de
   organización equivocado o renombrado, nunca "el repo no existe".** Es el mismo diagnóstico que
   `user:texture-hq`, y apareció dos veces en el mismo pase.
2. **Tres repos están ARCHIVADOS y ninguna búsqueda lo advierte en el título**:
   `open-energy-transition/rooftopsenti` (MIT, 7 ★), `open-energy-transition/grid-mapping-starter-kit`
   (CC0-1.0, 14 ★) y `calliope-project/ec_modules` (MIT, 4 ★). Están marcados como tales en todas las
   tablas de esta KB. Un repo archivado sigue siendo legible y forkeable y su licencia sigue valiendo,
   pero **no recibirá arreglos**: se vendoriza como referencia, no se declara como dependencia.
   **El campo `archived` de la API es obligatorio en la verificación**, no opcional.
3. **`powsybl/powsybl-core` es MPL-2.0**, confirmado en este pase (196 ★, push 2026-11-20). Copyleft
   débil por archivo: enlazable en un producto propietario, pero las modificaciones **al propio
   powsybl** se publican. Importa porque es el motor de la *Receta 31*.

## 2026-11-20 — pase 7 (la categoría más grande del open source energético estaba catalogada al 30 %: carga de EV, y la capa CIM que la red europea ya habla)

**Titular del pase: el propio trend T7 de esta KB dice desde el pase 2 que "movilidad eléctrica es
donde está la masa crítica real de la comunidad" — y la KB tenía cuatro repos de esa categoría.**
Buscando por el protocolo (`OCPP`, `OCPI`) en vez de por el sector aparecen **once más**, nueve de
ellos permisivos, con un rango de 48 a 602 ★ y todos con push de noviembre de 2026. No es una cola
larga: es un stack completo y probable — CSMS, emulador, simulador, firmware embarcado y roaming.

**Carga de EV: lo nuevo, verificado repo por repo por `repo:owner/name`:**

| Repo | Licencia | ★ / forks | Capa | Por qué importa |
|------|----------|-----------|------|-----------------|
| [EVerest/EVerest](https://github.com/EVerest/EVerest) | Apache-2.0 | 298 / 215 | Stack completo de carga | Proyecto **LF Energy**; gobernanza de fundación, no de vendor |
| [citrineos/citrineos-core](https://github.com/citrineos/citrineos-core) | Apache-2.0 | 309 / 175 | CSMS **OCPP 2.0.1** | El CSMS permisivo que faltaba frente al GPL de SteVe |
| [lbbrhzn/ocpp](https://github.com/lbbrhzn/ocpp) | MIT | 415 / 177 | Integración Home Assistant | La vía de piloto residencial sin hardware de utility |
| [ocpi/ocpi](https://github.com/ocpi/ocpi) | ⚠️ NOASSERTION | 602 / 230 | **Roaming** entre operadores | Especificación clave, licencia **no resuelta** |
| [SAP/e-mobility-charging-stations-simulator](https://github.com/SAP/e-mobility-charging-stations-simulator) | Apache-2.0 | 231 / 102 | Simulador de estaciones OCPP-J | Carga sintética a escala; autoría SAP |
| [monta-app/ocpp-emulator](https://github.com/monta-app/ocpp-emulator) | Apache-2.0 | 182 / 29 | Emulador de punto de carga | Kotlin Multiplatform; corre en escritorio |
| [tommymalmqvist/rust-ocpp](https://github.com/tommymalmqvist/rust-ocpp) | Apache-2.0 | 106 / 35 | Librerías 1.6 / 2.0.1 / **2.1** | La única que ya cubre **OCPP 2.1** |
| [ChargeLab/OpenOCPP](https://github.com/ChargeLab/OpenOCPP) | Apache-2.0 | 92 / 47 | Firmware embarcado | Lado estación, multiplataforma |
| [shiv3/ocpp-cp-simulator](https://github.com/shiv3/ocpp-cp-simulator) | Apache-2.0 | 48 / 22 | Simulador **para pruebas de agentes** | Se declara *"for AI agent testing & CSMS development"* |
| [dallmann-consulting/OCPP.Core](https://github.com/dallmann-consulting/OCPP.Core) | ⚠️ GPL-3.0 | 304 / 126 | Servidor + UI .NET | Copyleft: no integrar en producto cerrado |
| [juherr/awesome-ev-charging](https://github.com/juherr/awesome-ev-charging) | CC0-1.0 | 185 / 29 | Índice de la categoría | Punto de partida del próximo pase |

**Segundo hallazgo, y el que más cambia una propuesta en EMEA: la capa CIM / CGMES.** Esta KB tenía
`powsybl-core`, `entsoe/application-profiles-library` y `ReliCapGrid`, y no tenía el resto del
ecosistema que convierte el modelo de red europeo en algo programable. El motivo por el que importa
**ahora** es que la hoja de ruta de la Comisión Europea (COM/2026/501, 3 de junio de 2026) financia
**foundation models para gestión y planificación de red** con 30 M€ en 2026 y 20 M€ en 2027 — y esos
modelos consumirán CGMES. Quien tenga la tubería de datos CGMES tiene el acceso al dato.

| Repo | Licencia | ★ | Rol en la tubería CGMES |
|------|----------|---|--------------------------|
| [eliagroup/ToOp](https://github.com/eliagroup/ToOp) | MPL-2.0 | 76 | Optimización de **topología** del Elia Group: DC load flow en **GPU**, validación AC |
| [powsybl/pypowsybl](https://github.com/powsybl/pypowsybl) | MPL-2.0 | 106 | Acceso Python al motor PowSyBl (GraalVM) |
| [powsybl/powsybl-diagram](https://github.com/powsybl/powsybl-diagram) | MPL-2.0 | 136 | Unifilares y diagramas de red en SVG |
| [PNNL-CIM-Tools/CIM-Graph](https://github.com/PNNL-CIM-Tools/CIM-Graph) | BSD-3-Clause | 31 | CIM como grafo de propiedades en memoria (PNNL) |
| [sogno-platform/libcimpp](https://github.com/sogno-platform/libcimpp) | Apache-2.0 | 27 | Import/export CGMES en C++ |
| [sogno-platform/cimgen](https://github.com/sogno-platform/cimgen) | Apache-2.0 | 25 | Genera código desde el modelo CIM |
| [alliander-opensource/pycgmes](https://github.com/alliander-opensource/pycgmes) | Apache-2.0 | 19 | Dataclasses CGMES 3 + RDFS + SHACL (DSO Alliander) |
| [SOPTIM/OpenCGMES](https://github.com/SOPTIM/OpenCGMES) | Apache-2.0 | 9 | Suite RDFS / SHACL / CIMXML |
| [SOPTIM/RDFArchitect](https://github.com/SOPTIM/RDFArchitect) | Apache-2.0 | 30 | Editor web de esquemas RDFS con extensiones CIM |
| [eigenergy/powerio](https://github.com/eigenergy/powerio) | Apache-2.0 | 39 | *"Power system compiler infrastructure"* |
| [Welthulk/Sparlectra.jl](https://github.com/Welthulk/Sparlectra.jl) | Apache-2.0 | 17 | Flujo AC, corto IEC 60909, N-1 y N-2 en Julia |

**Tercer hallazgo: APAC deja de ser un gap de vocabulario.** Los pases anteriores registraron APAC
como delgado. El término que lo abre no es "APAC": es el **instrumento regulatorio local**. Buscando
`CSIP-AUS` / `IEEE 2030.5` y `NEM` aparecen repos de origen australiano, reales y permisivos:

- [`longzheng/open-dynamic-export`](https://github.com/longzheng/open-dynamic-export) — **MIT**, 57 ★.
  Control dinámico de exportación y curtailment de inversores bajo **CSIP-AUS / SEP2 / IEEE 2030.5**.
  Es exactamente el régimen de conexión obligatorio en Australia.
- [`ethanndickson/sep2_client`](https://github.com/ethanndickson/sep2_client) — **Apache-2.0**, 24 ★,
  y `sep2_common` (Apache-2.0, 14 ★): cliente IEEE 2030.5 en Rust.
- [`UNSW-CEEM/NEMSEER`](https://github.com/UNSW-CEEM/NEMSEER) — GPL-3.0, 39 ★. Pronósticos del
  **AEMO** para el National Electricity Market, de la UNSW.
- [`bje-/NEMO`](https://github.com/bje-/NEMO) — GPL-3.0, 55 ★. Optimizador del NEM.

⚠️ Los dos últimos son **GPL-3.0**: sirven de referencia y de validación, no de base de producto.

**Cuarto: modelos de sistema energético y electroquímica, los que el pase 5 dejó a medias.**
[`macroenergy/MacroEnergy.jl`](https://github.com/macroenergy/MacroEnergy.jl) (**MIT**, 57 ★) es
multi-sector y permisivo — el perfil que faltaba frente a GenX (GPL-2.0) y openTEPES (AGPL-3.0, 57 ★).
[`FZJ-IEK3-VSA/FINE`](https://github.com/FZJ-IEK3-VSA/FINE) (⚠️ NOASSERTION, 102 ★, ETHOS.FINE, Jülich).
En electroquímica: [`BattMoTeam/BattMo`](https://github.com/BattMoTeam/BattMo) (GPL-3.0, 62 ★) y
[`openFuelCell2/openFuelCell2`](https://github.com/openFuelCell2/openFuelCell2) (GPL-3.0, 64 ★) —
ambos copyleft, ambos válidos como motor de estudio, ninguno como librería embebida.

**Quinto: la capa de campo y gemelo digital que no es del sector pero se usa en el sector.**
[`thingsboard/thingsboard-gateway`](https://github.com/thingsboard/thingsboard-gateway) (Apache-2.0,
**2204 ★**, 1008 forks) es el gateway IoT multiprotocolo con más tracción del conjunto completo de este
pase; [`eclipse-ditto/ditto`](https://github.com/eclipse-ditto/ditto) (EPL-2.0, 953 ★) es el framework
de gemelo digital de Eclipse IoT; [`syzygyhack/open-foundry`](https://github.com/syzygyhack/open-foundry)
(Apache-2.0, 137 ★) es una plataforma de ontología para gemelos operativos;
[`VILLASframework/node`](https://github.com/VILLASframework/node) (Apache-2.0, 22 ★) es gateway
multiprotocolo en tiempo real para co-simulación.
En IEC 61850 aparecen dos implementaciones nuevas:
[`wendy512/iec61850`](https://github.com/wendy512/iec61850) (⚠️ GPL-3.0, 182 ★, Go) y
[`mzaniolo/iec61850`](https://github.com/mzaniolo/iec61850) (**MIT**, 15 ★, Rust) — la segunda es
diminuta pero es la **única MIT** de la familia 61850 que esta KB ha encontrado en siete pases.
Para seguridad OT: [`Orange-Cyberdefense/awesome-industrial-protocols`](https://github.com/Orange-Cyberdefense/awesome-industrial-protocols)
(CC0-1.0, 783 ★).

**Sexto: carbono horario, la pieza que vuelve verificable un compromiso de PPA.**
[`carbonfirst/CarbonCast`](https://github.com/carbonfirst/CarbonCast) (Apache-2.0, 49 ★) predice
intensidad de carbono **horaria** por red con ML; [`bluehands/Carbon-Aware-Computing`](https://github.com/bluehands/Carbon-Aware-Computing)
(MIT, 47 ★) desplaza tareas al momento de mínima intensidad. Complementan al ya catalogado
`carbon-aware-sdk` con la parte de **predicción**, que era la que faltaba.

**Séptimo, y el más útil para vender: LF Energy publicó un marco de coste-beneficio de open source
para operadores de red.** [`lf-energy/lfe-oss-benefit-cost-framework`](https://github.com/lf-energy/lfe-oss-benefit-cost-framework)
(Apache-2.0, creado 2026-09-08) es nuevo y pequeño, y resuelve el problema que ninguna de las 24
recetas de esta KB resolvía: **cómo justificar ante una utility regulada la adopción de open source**.
Acompaña a [`lf-energy/lfenergy-landscape`](https://github.com/lf-energy/lfenergy-landscape)
(Apache-2.0, 45 ★), el mapa vivo del ecosistema.

**Nota de método, para no repetir el error del pase 2 de este archivo:** la consulta
`(electrolyzer OR hydrogen OR geothermal) in:name,description` con paréntesis devolvió **cero filas**
de forma silenciosa, y la misma búsqueda sin paréntesis devolvió dieciséis. **Un cero de la API de
GitHub no es un gap del sector hasta haber reescrito la consulta sin paréntesis.** Dos "gaps" de
hidrógeno y nuclear de pases anteriores pueden ser artefactos de esta sintaxis.

## 2026-11-20 — pase 6 (LATAM deja de ser un gap de oferta: cuatro modelos nacionales, tres MIT)

**Titular del pase: la recomendación con la que cerró el pase 5 era correcta y se cobró.** Ese pase
terminó pidiendo *"buscar `PyPSA-CL`, `PyPSA-MX` y `PyPSA-BR` por nombre"*. Hecho: **existen cuatro
modelos de sistema eléctrico nacional latinoamericano sobre PyPSA, y tres son MIT**. Cinco pases
midieron "cero repos LATAM" buscando por dominio e institución; la consulta que funcionó fue el
nombre del framework más el país.

**Nuevo — cohorte de modelos nacionales LATAM, verificada contra la API REST de GitHub:**

| Repo | Licencia | ★ | Forks | Push | Creado | Qué modela | Región |
|------|----------|---|-------|------|--------|-----------|--------|
| [paredes-vergara/PyPSA-CL](https://github.com/paredes-vergara/PyPSA-CL) | **MIT** | 15 | 2 | 2026-07-27 | — | SEN de **Chile**: inversión a largo plazo + *unit commitment* + despacho económico, con datos del Coordinador Eléctrico Nacional, CNE y Ministerio de Energía | LATAM |
| [sanjaygrr/pypsa-chile](https://github.com/sanjaygrr/pypsa-chile) | **MIT** | 0 | 1 | 2026-11-16 | — | Despacho del **SEN chileno** con datos públicos. Push de esta semana | LATAM |
| [BrandolRuizOlmeda/pypsa-mexico_base](https://github.com/BrandolRuizOlmeda/pypsa-mexico_base) | **MIT** (en `master`) | 0 | 0 | 2026-04-07 | — | **Mercado Eléctrico Mayorista** de México | LATAM |
| [leonardovbonatto/pypsa-meets-brazil](https://github.com/leonardovbonatto/pypsa-meets-brazil) | ❌ **sin licencia** | 0 | 0 | 2026-11-06 | — | **SIN brasileño** nodal con física de hidráulica y valores de agua estocásticos | LATAM |

**La lectura honesta de la tracción: 0–15 ★, 0–2 forks.** No hay comunidad y no debe venderse como
tal. Lo que hay es **topología y datos de operador nacional ya mapeados** a un formato que `linopy`
resuelve — el trabajo caro de las primeras semanas de un encargo de planificación, hecho y público.

**El de Brasil es el bueno y es el inutilizable.** Modela lo específicamente difícil del SIN —el agua
embalsada como batería del sistema, con valores estocásticos— y no tiene `LICENSE` en `main` ni en
`master`. Copyright exclusivo del autor: no empotrable. Mismo final que `douyimin/GEM` en el pase 4.

**Dos correcciones de verificación que afectan a toda la KB, no sólo a estas filas:**

1. **`curl -sI` no verifica nada en este entorno, y hasta hoy era el método prescrito.** A través del
   proxy devuelve `HTTP/1.1 200 Connection Established` —la respuesta del `CONNECT`, no la del
   archivo— para **cualquier** URL, incluidas las que son 404. Comprobado contra un path inventado:
   `curl -sI` dice 200, el código real es 404. La forma correcta es
   `curl -s -o /dev/null -w "%{http_code}"`. Y además `github.com` responde **403** a todo desde
   aquí por política de host, así que la URL de un repo **no se puede** verificar con `curl`: se
   verifica con `gh api search/repositories -f q="repo:owner/name"` y los archivos con
   `raw.githubusercontent.com`.
2. **`PyPSA/pypsa-eur` no tiene una licencia, tiene cuatro.** La API devuelve `null`, no hay `LICENSE`
   en la raíz (404 real), y el repo usa **REUSE de la FSFE**: código **MIT**, documentación
   **CC-BY-4.0**, configuración **CC0-1.0**, datos **CC-BY-4.0**, declarado en `doc/licenses.md` y
   `REUSE.toml`. Un `grep` de SPDX sobre el `README` devuelve **CC-BY-4.0**, que es la licencia *del
   propio README* — y clasificaría el modelo de red europeo más usado de esta KB como material de
   atribución en lugar de código MIT.

**Buscado y no encontrado, para que el próximo pase no lo repita**: la categoría de **cola de
interconexión y siting de datacenter** que el pase 5 marcó como "a vigilar" sigue sin nada proponible.
`interconnection queue in:name,description` y `data center power siting` devuelven, en lo alto del
ranking, simuladores de redes de paquetes y pipelines de datos de Steam; lo único temáticamente
correcto es `selormdzakpasu/gen_interconnection_queues` (compilación de las colas de los siete ISO) con
**1 ★ y sin licencia**. Sigue siendo el patrón de `dchub-mcp-server`: demanda alta, oferta open source
inexistente. Es trabajo a medida, y por eso es facturable.

## 2026-11-20 — pase 5 (la capa de acceso a datos de mercado: lo primero que hace falta y lo último que esta KB tenía)

**Titular del pase: esta KB sabía simular siete mercados eléctricos y no sabía leer ninguno.** Cuatro
pases acumularon 147 repos de modelado, optimización, simulación y control — y la pieza que un
encargo necesita el **primer día** (bajar el precio, la carga y la generación reales del operador)
estaba representada sólo por `API_XM` (Colombia), `OMIEData` (España) y `hass-entso-e` (una
integración de Home Assistant). Las dos librerías canónicas del sector faltaban, y ambas son
permisivas y muy usadas.

**Lo que faltaba — capa de acceso a datos, verificada contra la API REST de GitHub:**

| Repo | Licencia | ★ | Forks | Issues | Push | Cobertura | Región |
|------|----------|---|-------|--------|------|-----------|--------|
| [fboerman/entsoe-py](https://github.com/fboerman/entsoe-py) | **MIT** | **745** | 270 | 11 | 2026-11-17 | Cliente de la API de ENTSO-E: precios, generación, carga, flujos transfronterizos | EMEA |
| [gridstatus/gridstatus](https://github.com/gridstatus/gridstatus) | **BSD-3-Clause** | **456** | 89 | 41 | 2026-11-18 | Los **siete** ISO/RTO de EE. UU.: CAISO, ERCOT, PJM, MISO, SPP, NYISO, ISO-NE | North America |
| [PyPSA/linopy](https://github.com/PyPSA/linopy) | **MIT** | 263 | 95 | 46 | 2026-11-19 | Backend de optimización lineal N-D del ecosistema PyPSA | EMEA |
| [PyPSA/powerplantmatching](https://github.com/PyPSA/powerplantmatching) | **MIT** (SPDX) | 235 | 77 | 30 | 2026-11-19 | Reconcilia múltiples bases de datos de centrales en un registro único | EMEA |
| [singularity-energy/open-grid-emissions](https://github.com/singularity-energy/open-grid-emissions) | **MIT** | 96 | 7 | **97** | 2026-11-19 | Generación y **emisiones horarias** de la red de EE. UU. | North America |
| [gridstatus/gridstatusio](https://github.com/gridstatus/gridstatusio) | **BSD-3-Clause** | 58 | 5 | 6 | 2026-11-16 | Cliente de la API alojada de GridStatus.io | North America |
| [entsoe/application-profiles-library](https://github.com/entsoe/application-profiles-library) | **Apache-2.0** | 29 | 9 | 16 | 2026-10-28 | Artefactos RDFS/SHACL **oficiales** de CGMES. Cuenta `entsoe` institucional | EMEA |
| [entsoe/ReliCapGrid](https://github.com/entsoe/ReliCapGrid) | NOASSERTION | 21 | 6 | 21 | 2026-11-18 | Modelos de prueba CGMES y perfiles CIM de códigos de red | EMEA |
| [jo20ow/Obsyd](https://github.com/jo20ow/Obsyd) | **AGPL-3.0** | 12 | 1 | 0 | 2026-11-11 | "gridstatus para Europa": 37 zonas de oferta, precios *day-ahead* a 15 min | EMEA |

**Por qué `entsoe-py` con 745 ★ es el hallazgo incómodo.** Es el repo con más estrellas que esta KB ha
añadido en cinco pases, es MIT, lleva nueve años vivo (creado 2017-07-12), tiene 270 forks y **11
issues abiertas** — el perfil de un proyecto maduro y mantenido. Que no estuviera sugiere que los
pases anteriores buscaron por *función* (`forecasting`, `optimization`, `DERMS`) y nunca por
*fuente de datos*. El pase 4 ya había diagnosticado que los gaps de esta KB eran gaps de
vocabulario (T10); esto lo confirma en la categoría más básica de todas.

**`open-grid-emissions` y el encaje con lo que ya había.** 97 issues abiertas sobre 96 ★: proyecto
trabajado. Produce la serie horaria de emisiones de la red estadounidense, que es exactamente el
input que `Green-Software-Foundation/carbon-aware-sdk` (ya en la KB) consume y que `scaphandre` y
`ecologits` miden del lado del cómputo. Con `gridstatus` delante, la cadena
**dato de red → emisión horaria → decisión de carga** queda completa y permisiva de punta a punta,
para North America.

### Plataformas de planificación y evaluación técnico-económica — la segunda categoría ausente

La KB tenía modelos de expansión de capacidad académicos (`OSeMOSYS`, `TIMES`, `temoa`, `switch`,
`calliope`, `GenX.jl` GPL-2.0). Faltaban las plataformas de laboratorio nacional y de industria:

| Repo | Licencia | ★ | Forks | Issues | Push | Qué hace | Región |
|------|----------|---|-------|--------|------|----------|--------|
| [NatLabRockies/ROSCO](https://github.com/NatLabRockies/ROSCO) | **Apache-2.0** | 182 | 125 | 17 | 2026-09-29 | Controlador de referencia de aerogenerador. **125 forks sobre 182 ★** | Global |
| [NatLabRockies/ReEDS-2.0](https://github.com/NatLabRockies/ReEDS-2.0) | **BSD-3-Clause** | 176 | 79 | 7 | 2026-04-22 | Expansión de capacidad del sistema eléctrico de EE. UU. | North America |
| [grid-parity-exchange/Egret](https://github.com/grid-parity-exchange/Egret) | **BSD-3-Clause** (crudo) | 173 | 72 | 57 | 2026-11-08 | Bloques para construir problemas de optimización de sistemas de potencia | North America |
| [NatLabRockies/pysam](https://github.com/NatLabRockies/pysam) | **BSD-3-Clause** | 157 | 87 | 17 | 2026-09-27 | Envoltorio Python de SAM (modelo técnico-financiero) | Global |
| [sylvan-energy/gridpath](https://github.com/sylvan-energy/gridpath) | **Apache-2.0** | 138 | 71 | 58 | 2026-11-19 | Plataforma de planificación **y** operación en un solo modelo | Global |
| [NatLabRockies/REopt_API](https://github.com/NatLabRockies/REopt_API) | BSD-3 + **marca REopt®** | 128 | 70 | 54 | 2026-11-17 | Dimensionado óptimo de DER en un emplazamiento (motor de reopt.nrel.gov) | North America |
| [NatLabRockies/BuildingsBench](https://github.com/NatLabRockies/BuildingsBench) | **BSD-3-Clause** | 123 | 24 | 0 | 2026-02-25 | Preentrenamiento y *benchmark* de previsión de carga a corto plazo | North America |
| [NatLabRockies/ParaEMT_public](https://github.com/NatLabRockies/ParaEMT_public) | **BSD-3-Clause** | 113 | 54 | 5 | 2026-01-15 | Simulación EMT paralelizada | North America |
| [NatLabRockies/bifacial_radiance](https://github.com/NatLabRockies/bifacial_radiance) | **BSD-3-Clause** | 111 | 56 | 85 | 2026-09-25 | Trazado de rayos para fotovoltaica bifacial | Global |
| [OpenSynth-energy/OpenSynth](https://github.com/OpenSynth-energy/OpenSynth) | **Apache-2.0** | 77 | 12 | 10 | 2026-10-12 | Modelos de **datos sintéticos** de consumo de contador | EMEA |
| [NatLabRockies/GEOPHIRES-X](https://github.com/NatLabRockies/GEOPHIRES-X) | **MIT** | 67 | 49 | 83 | 2026-11-19 | Simulador técnico-económico **geotérmico** | Global |
| [NatLabRockies/HOPP](https://github.com/NatLabRockies/HOPP) | **BSD-3-Clause** | 41 | **66** | 68 | 2026-04-10 | Plantas híbridas (renovable + almacenamiento + H₂). **Más forks que estrellas** | North America |

**`REopt_API` es, comercialmente, el repo más directo del pase.** Responde la pregunta con la que
empieza casi todo encargo de energía distribuida — *¿cuánta solar, cuánta batería y cuánto genset
conviene en este sitio, y a qué coste?* — y es el motor real detrás de la herramienta web de NREL,
con 70 forks y 54 issues abiertas. **No es BSD limpia**: ver la nota de licencia abajo.

**`OpenSynth` resuelve un obstáculo que la inteligencia de mercado de este pase identificó en EMEA.**
El informe de la Comisión Europea sobre IA en redes inteligentes señala el cumplimiento de GDPR y el
preprocesado como barreras para **entrenar** modelos. `OpenSynth` (Apache-2.0, cohorte LF Energy /
Centre for Net Zero) publica modelos generadores de perfiles de consumo sintéticos: datos de
contador que no son de nadie. Es la respuesta técnica a una objeción regulatoria, y encaja antes de
`openstef` o `BuildingsBench` en el pipeline.

### Trampa de licencia nueva, y es la peor que esta KB ha encontrado

Las licencias de los laboratorios nacionales **no son BSD estándar**, y la API de GitHub tiene razón
al decir `NOASSERTION`. Leídas en crudo:

| Repo | La API dice | Lo que dice el archivo | Consecuencia |
|------|-------------|------------------------|--------------|
| [NatLabRockies/resstock](https://github.com/NatLabRockies/resstock) (147 ★, 85 forks) | `NOASSERTION` | BSD-3 + **cláusula (3) de copyleft condicionado al tipo de redistribuidor** + marca ResStock™ | **Si el cliente es universidad, laboratorio nacional u ONG, todo el código fuente correspondiente de la redistribución —modificado o no— debe publicarse bajo esta misma licencia** |
| [NatLabRockies/REopt_API](https://github.com/NatLabRockies/REopt_API) (128 ★) | `NOASSERTION` | BSD-3 + cláusula (3) de **designación REopt®** + (4) no-endoso DOE/gobierno EE. UU. | Una versión modificada **no puede** llamarse REopt® y **debe** citar el original como REopt® |
| [NatLabRockies/OpenStudio](https://github.com/NatLabRockies/OpenStudio) (660 ★, 241 forks) | `NOASSERTION` | BSD-3 + marca OpenStudio® | Igual que `EnergyPlus`: prohibido el nombre en producto o promoción |
| [richard-weinhold/pomato](https://github.com/richard-weinhold/pomato) (101 ★) | `NOASSERTION` | **LGPL-3.0**, declarado en `LICENSE.md` | Copyleft de biblioteca; sin push desde 2025-08-12 |
| [NatLabRockies/electrolyzer](https://github.com/NatLabRockies/electrolyzer) (35 ★) | `NOASSERTION` | **Apache-2.0** limpia | Rescatada: usable sin reservas |

**La cláusula de `resstock` es un riesgo de tipo nuevo para esta KB.** Todas las trampas registradas
hasta ahora se activaban por *lo que hacías* con el código (SaaS → AGPL, modificar el motor → MPL).
Esta se activa por **quién es el cliente**. Un encargo de modelado de parque residencial con una
universidad o una fundación obliga a publicar el entregable. No se detecta leyendo la etiqueta de
licencia: hay que leer la cláusula.

### Hidrógeno y geotermia: medidos, y el resultado es "delgado pero permisivo"

**Geotermia — un solo repo usable.** `GEOPHIRES-X` (**MIT**, 67 ★, 49 forks, push 2026-11-19, 83
issues) es el único activo y permisivo. Su propio predecesor `GEOPHIRES-v2` es **GPL-3.0** y está
congelado desde 2023-10-31: *mismo simulador, licencia distinta según versión*. Lo demás es
`ICWallis/geothermal-cookbook` (Apache-2.0, 27 ★, sin push desde 2022) y
`SmartTensors/GeoThermalCloud.jl` (**GPL-3.0**, 36 ★). **Veredicto: hay base para un estudio
técnico-económico geotérmico; no hay ecosistema.**

**Hidrógeno — el término de búsqueda está inservible.** `hydrogen in:name stars:>50` devuelve, en
orden: `Shopify/hydrogen` (framework web, 2.183 ★), `nteract/hydrogen` (plugin de Jupyter, 4.018 ★),
`hydrogen-music/hydrogen` (caja de ritmos, 1.357 ★). **Ni un resultado energético en los primeros
quince.** Buscando por `electrolyzer` y por organización, lo que hay es:
`NatLabRockies/electrolyzer` (Apache-2.0, 35 ★, 28 forks), `NatLabRockies/HOPP` (BSD-3, 41 ★, 66
forks), `gassraphael/AlphaPEM` (**BSD-3-Clause**, 49 ★, 15 forks, push 2026-11-18, simulación de pila
PEMFC) y `e2nIEE/pandapipes` (ya en la KB). El resto son modelos académicos de 2-25 ★ sin licencia.

Añádase a la lista de términos inutilizables del cuarto pase: **`hydrogen` es un término de comercio
electrónico en GitHub, no de energía.**

### El gap de ejecución de mercado sigue abierto, ahora con la excepción nombrada

Consulta `day-ahead bidding electricity in:name,description`, 15 resultados. El mejor es
[`jo20ow/Obsyd`](https://github.com/jo20ow/Obsyd) (**AGPL-3.0**, 12 ★, creado 2026-03-04): 37 zonas
de oferta europeas con precios a 15 minutos — pero es **lectura de datos, no colocación de ofertas**,
y su AGPL muerde en un SaaS. Lo demás son 0-2 ★ y casi todo sin licencia:
`ThomasStatic/capstone-optimal-bidding` (sin licencia, agente RL de pujas),
`axelsjoberg1/elbud` (0 ★, SE1-SE4), `BRSTKL/powerbid` (0 ★, mercado turco).
La única pieza permisiva y real que *actúa* sobre precios es
[`romilandc/battery-storage-optimization-energy-ancillary`](https://github.com/romilandc/battery-storage-optimization-energy-ancillary)
(**Apache-2.0**, 11 ★): co-optimización de energía y servicios auxiliares que consume precios **vía
`gridstatus`**. Es un ejemplo de 11 ★, no una base de producción.

**Veredicto sin cambios respecto al tercer pase: no proponer un bot de pujas mayoristas.** Lo nuevo
es que ahora la frontera está dibujada: *leer* el mercado es MIT/BSD y maduro; *pujar* en él no tiene
base open source en ninguna de las cuatro regiones.

---

## 2026-11-20 — pase 4 (sincrofasores MIT, medición y verificación, y simulación de protocolo)

**Titular del pase: tres categorías enteras estaban ausentes, y la más valiosa comercialmente no es
técnica — es la que hace cobrable el ahorro.**

**1. PMU / sincrofasores, y es MIT.** La observabilidad de red de alta resolución se da por
propietaria (OSI PI, e-terra). No lo es:
[GridProtectionAlliance/openPDC](https://github.com/GridProtectionAlliance/openPDC) (**MIT**, 159 ★,
67 forks, push 2026-11-15) es un concentrador de datos de fasores de producción, con
[gsf](https://github.com/GridProtectionAlliance/gsf) (**MIT**, 179 ★, 76 forks) como base.

**2. Medición y verificación: el repo con más valor comercial directo del pase.**
[opendsm/opendsm](https://github.com/opendsm/opendsm) (**Apache-2.0**, 244 ★, 76 forks, creado 2016,
linaje OpenEEmeter/CalTRACK) implementa los métodos **estándar** de consumo normalizado (NMEC) y
ahorro medido. Sin esa capa, un piloto de optimización produce un número que nadie firma; con ella,
produce una factura. Su par operativo:
[FlexMeasures/flexmeasures](https://github.com/FlexMeasures/flexmeasures) (**Apache-2.0**, 217 ★,
248 issues abiertas, LF Energy) decide *cuándo* mover la carga.

**3. Simulación de protocolo sin hardware** — desbloquea el piloto cuando no hay subestación:
[suoten/ProtoForge](https://github.com/suoten/ProtoForge) (**MIT**, 325 ★, 100 forks, creado
2026-04-24, 28 protocolos), [Fraunhofer-FIT-DIEN/iec104-python](https://github.com/Fraunhofer-FIT-DIEN/iec104-python)
(GPL-3.0, 106 ★, IEC 60870-5-104), [Gurux/Gurux.DLMS.Python](https://github.com/Gurux/Gurux.DLMS.Python)
(GPL-2.0, 125 ★, **94 forks — relación 0.75, la más alta de la KB**),
[bemasher/rtlamr](https://github.com/bemasher/rtlamr) (AGPL-3.0, 2559 ★, lectura de medidor Itron por
radio). Defensa obligatoria: [mitre/caldera-ot](https://github.com/mitre/caldera-ot) (**Apache-2.0**,
265 ★, push hoy).

**4. Corrección de la tesis del pase 3 sobre O&G.** El pase 3 concluyó "100 % GPL-3.0". Era un
artefacto de la muestra: [sintefmath/JutulDarcy.jl](https://github.com/sintefmath/JutulDarcy.jl)
(**MIT**, 170 ★, simulación de yacimiento en Julia) y
[GeoBrain-Project/GeoBrain](https://github.com/GeoBrain-Project/GeoBrain) (**Apache-2.0**, 88 ★,
plataforma diferenciable de subsuelo) son permisivos y de primer nivel.

**5. El repo con más tracción del pase, y con dos trampas:**
[open-meteo/open-meteo](https://github.com/open-meteo/open-meteo) — 6704 ★, 485 forks, pero
**AGPL-3.0** y su servicio público es sólo para uso no comercial. Un piloto que pega a
`api.open-meteo.com` y pasa a producción cambia de régimen de licencia sin que nadie lo note.

**6. Repos sin licencia (categoría bloqueada, no ausente):** `douyimin/GEM` — *Geological Everything
Model 3D*, foundation model promptable de subsuelo zero-shot, **sin archivo de licencia en ninguna
rama**. El único foundation model de subsuelo encontrado, e inutilizable. Igual
`xingyuz-phd/Generic-EMT-Modeling-of-Data-Center-Load` (modelo EMT de carga de datacenter) y
`ames-market/AMES-V5.0`. `pnoker/iot-dc3` (1273 ★) usa una **licencia propia** *"IoT DC3 License
Notice v2026.5"*, ni OSI ni SPDX.

**Términos de búsqueda quemados en este pase** (para no repetirlos): `hydrogen` → Shopify Hydrogen;
`AMI` → Amiga/Amiibo; `utility billing` → utilidades de software; `reservoir` → reservoir computing.
Las consultas que **sí** rindieron: `IEC 61850`, `OpenADR`, `IEEE 2030.5`, `DLMS COSEM`, `DERMS`,
`"battery energy storage"`.

---

## 2026-11-20 — pase 3 (los activos físicos, la categoría que faltaba entera)

**Titular del pase: esta KB sabía modelar la RED y no sabía modelar los ACTIVOS. Doce repos
verificados, todos permisivos, cubren baterías, eólica, solar y nuclear — y el mayor de ellos
(`PyBaMM`, 1.737 ★) es más grande que cualquier repo que la KB tuviera registrado en su núcleo.**

Los dos pases anteriores barrieron agentes, mercados, O&M, planificación y gemelo digital. Todos son
capas de **sistema eléctrico**. Ninguno preguntó por la física del activo: qué pasa dentro de una
batería, de una turbina, de un reactor. Esa ausencia no estaba declarada como gap — es peor que un
gap declarado, porque no se veía.

### Baterías y almacenamiento — la ausencia más cara

| Nombre | Licencia | Descripción | Stars | Forks | Último push | Región origen |
|--------|----------|-------------|-------|-------|-------------|---------------|
| [pybamm-team/PyBaMM](https://github.com/pybamm-team/PyBaMM) | **BSD-3-Clause** | Modelos de batería **basados en física** (DFN, SPM, SPMe) en Python. El estándar de facto académico e industrial; respaldo de The Faraday Institution (Reino Unido) | 1737 | 845 | 2026-11-19 | EMEA |
| [pybamm-team/liionpack](https://github.com/pybamm-team/liionpack) | MIT | Simulación de **packs** (celdas en serie/paralelo) sobre PyBaMM: del modelo de celda al sistema | 120 | 39 | 2026-11-16 | EMEA |

Que una KB de energía con 81 repos registrados no tuviera `PyBaMM` es significativo: 845 forks es
más que casi todo lo demás en este archivo. Cualquier conversación de BESS, degradación, garantía de
capacidad o second-life empieza aquí.

### Eólica — del recurso a la turbina

| Nombre | Licencia | Descripción | Stars | Forks | Último push | Región origen |
|--------|----------|-------------|-------|-------|-------------|---------------|
| [OpenFAST/openfast](https://github.com/OpenFAST/openfast) | **Apache-2.0** | Simulación aeroelástica de turbina completa y de parque (FAST.Farm). Respaldo del laboratorio nacional de EE. UU. (NLR, ex-NREL) | 991 | 552 | 2026-11-20 | North America |
| [NatLabRockies/floris](https://github.com/NatLabRockies/floris) | BSD-3-Clause | Modelo de **estela** orientado a control: optimización de wake steering y layout de parque | 302 | 190 | 2026-11-18 | North America |
| [wind-python/windpowerlib](https://github.com/wind-python/windpowerlib) | MIT | Curva de potencia y salida de turbinas/parques. ⚠️ **Último push 2024-02-20**: usable, no mantenido | 397 | 113 | 2024-02-20 | EMEA |

### Solar, recurso y tecno-economía

| Nombre | Licencia | Descripción | Stars | Forks | Último push | Región origen |
|--------|----------|-------------|-------|-------|-------------|---------------|
| [NatLabRockies/SAM](https://github.com/NatLabRockies/SAM) | BSD-3-Clause | **System Advisor Model**: modelo tecno-económico de referencia para FV, CSP, eólica, geotermia y almacenamiento. Lo que se usa para decir si un proyecto cierra | 498 | 221 | 2026-11-19 | North America |
| [NatLabRockies/ssc](https://github.com/NatLabRockies/ssc) | BSD-3-Clause | Motor de cálculo de SAM, embebible como librería sin la GUI | 96 | 119 | 2026-11-19 | North America |
| [NatLabRockies/reV](https://github.com/NatLabRockies/reV) | BSD-3-Clause | Potencial técnico **geoespacial**: dónde cabe un parque y cuánto produciría, a escala de país | 144 | 63 | 2026-10-01 | North America |
| [NatLabRockies/sup3r](https://github.com/NatLabRockies/sup3r) | BSD-3-Clause | **GAN de super-resolución** para datos de recurso renovable: sube la resolución espacio-temporal de reanálisis climático. Es IA generativa aplicada al recurso, no al texto | 144 | 33 | 2026-11-18 | North America |

`sup3r` merece atención aparte: es de los pocos repos verificados en esta KB donde el modelo
generativo **es** el producto energético, y no una capa de conversación sobre otro motor.

### Nuclear — subsector nuevo, traído por la demanda de datacenter

| Nombre | Licencia | Descripción | Stars | Forks | Último push | Región origen |
|--------|----------|-------------|-------|-------|-------------|---------------|
| [openmc-dev/openmc](https://github.com/openmc-dev/openmc) | **MIT** (resuelta; la API dice `NOASSERTION`) | Transporte de neutrones Monte Carlo. Copyright MIT + UChicago Argonne. Base abierta para análisis de núcleo, incluidos SMR | 1147 | 704 | 2026-11-19 | North America |
| [idaholab/moose](https://github.com/idaholab/moose) | **LGPL-2.1** | Entorno multifísica de elementos finitos (Idaho National Laboratory). ⚠️ Copyleft débil: enlazable, pero no es permisivo | 2409 | 1282 | 2026-11-19 | North America |

### Respuesta de demanda: el estándar que faltaba

| Nombre | Licencia | Descripción | Stars | Forks | Último push | Región origen |
|--------|----------|-------------|-------|-------|-------------|---------------|
| [OpenLEADR/openleadr-python](https://github.com/OpenLEADR/openleadr-python) | **Apache-2.0** | Implementación de **OpenADR 2.0b**, el estándar de señalización de respuesta de demanda entre utility y recurso | 161 | 67 | 2026-11-16 | North America |

La KB tenía `CityLearn` (simular DR), `VOLTTRON` (ejecutar en el borde) y `evcc` (controlar carga),
pero **ninguna pieza que hablara el protocolo con la utility**. `openleadr-python` es ese eslabón.

### Planificación: tres añadidos y una trampa de licencia

| Nombre | Licencia | Descripción | Stars | Forks | Último push | Región origen |
|--------|----------|-------------|-------|-------|-------------|---------------|
| [PyPSA/pypsa-usa](https://github.com/PyPSA/pypsa-usa) | MIT | Modelo de sistema energético de EE. UU. sobre PyPSA, con datos abiertos | 153 | — | 2026-11-20 | North America |
| [OSeMOSYS/OSeMOSYS](https://github.com/OSeMOSYS/OSeMOSYS) | Apache-2.0 | Modelo de planificación de largo plazo usado por agencias y ministerios; base de muchos planes nacionales | 196 | 123 | 2025-10-22 | EMEA |
| [switch-model/switch](https://github.com/switch-model/switch) | **Apache-2.0** (resuelta; la API dice `NOASSERTION`) | Planificación de sistemas de alta penetración renovable | 158 | 95 | 2025-07-07 | North America |
| [GenXProject/GenX.jl](https://github.com/GenXProject/GenX.jl) | ⚠️ **GPL-2.0** | Expansión de capacidad configurable (Princeton). **Muy citado y NO permisivo**: no asumir MIT por venir de universidad | 370 | — | 2026-10-15 | North America |

### Huella ambiental de la propia IA

| Nombre | Licencia | Descripción | Stars | Forks | Último push | Región origen |
|--------|----------|-------------|-------|-------|-------------|---------------|
| [mlco2/ecologits](https://github.com/mlco2/ecologits) | MPL-2.0 | Mide consumo energético y huella de las llamadas a LLM por API. Cierra el círculo: la IA que optimiza la red también consume | 363 | 36 | 2026-11-19 | EMEA |

### Movimiento institucional de este trimestre (prensa, no verificado en GitHub)

- **OpenGrid (Linux Foundation, oct-2026)**: iniciativa de infraestructura abierta para planificación
  de red, con apoyo de Breakthrough Energy GRIDS y Google.org. **Buscado en GitHub y no localizado
  un repo con código**; es anuncio, no todavía base de código utilizable.
- **CommonGrid (Texture, 25-sep-2026)**: registro abierto y editable de la infraestructura eléctrica
  de EE. UU., bajo **Open Database License** (licencia de *datos*, no de software). Tampoco
  localizado como repo GitHub desde este entorno.
- **Grid Protectors (OpenAI, 4-nov-2026)**: programa de flexibilidad de carga de datacenter. **No es
  open source**; se registra como señal de mercado, no como activo técnico.

### Falsos amigos detectados y descartados en este pase

| Candidato | Por qué parecía relevante | Por qué se descarta |
|-----------|---------------------------|---------------------|
| `datamllab/OpenEBFM` | Aparece en listados de trending "energy" | **"Energy-based models"** es una técnica de ML, no el sector energético. Homonimia pura |
| `DatariusAI/AI-in-Energy` | Se presenta como hub diario de IA en energía | **0 ★, sin licencia**, contenido autogenerado. No citable |
| `DTUWindEnergy/PyWake` | Modelo de estela de DTU, nombre fuerte | Es un **espejo** de GitLab de DTU: licencia `null` y último push **2024-11-25**. El original no está aquí |
| `martymcenroe/best-of-pes-ai` | Lista curada IEEE PES | 3 ★, **CC-BY-SA-4.0** (licencia de contenido). Útil como pista, no como dependencia |

## 2026-11-20 — pase 2 (barrido de huecos declarados)

**Titular del pase: tres de los gaps que esta KB declaró vacíos hace una hora no estaban vacíos —
estaban mal consultados. Y apareció un subsector entero que la KB nunca había mirado: upstream de
petróleo y gas, con el perfil de licencia exactamente invertido.**

Todas las filas re-consultadas hoy con `gh api search/repositories` por `repo:owner/name` exacto.

### Re-verificación completa de enlaces de este archivo y del resto de la KB

Se extrajeron **las 80 URLs de GitHub distintas** presentes en los ocho archivos de esta KB y se
consultó cada una por `repo:owner/name` exacto:

- **78 de 80 resuelven.**
- **2 no resuelven**: `Hartblack356/mtd` y
  `Legalagecolouring820/Random-Forest-Model-EMS-system-data-machine-learning-early-warning`. Ambas
  están **sólo** en la sección histórica del **2026-07-02**, ya marcada como pipeline sin verificar.
  Se conservan por la regla append-only; no hay ninguna URL muerta en contenido curado.
- **Deriva de stars**: dos filas de secciones vivas quedaron a **±1 ★** del valor de la API en el
  mismo día (`PyPSA/atlite` 412→413, `OpenEMS/openems` 1631→1632). No se editan: ambos valores fueron
  ciertos a distinta hora, y reescribir una sección fechada rompería el append-only. La magnitud
  importa: **±1 ★ en horas** es ruido; los **−2,6×** que corrigió el pase anterior eran cifras
  arrastradas sin consultar.

---

### Gap 1 — "Mercados eléctricos y trading: cero repos" → **roto**

| Nombre | Licencia | Descripción | Stars | Forks | Último push | Región origen |
|--------|----------|-------------|-------|-------|-------------|---------------|
| [JaccoR/hass-entso-e](https://github.com/JaccoR/hass-entso-e) | Apache-2.0 | Precios day-ahead de ENTSO-E para Home Assistant: la vía más corta a precio horario europeo real | 280 | 65 | 2026-06-22 | EMEA |
| [assume-framework/assume](https://github.com/assume-framework/assume) | MIT | **ASSUME**: simulación basada en agentes de la evolución de mercados eléctricos (Fraunhofer IEE / INATECH / TU Dresden) | 128 | 53 | 2026-11-19 | EMEA |
| [alexanderkell/elecsim](https://github.com/alexanderkell/elecsim) | MIT | Modelo de agentes de mercado eléctrico a largo plazo: efecto de política pública sobre decisiones de inversión. **Último push 2025-12-03 — está quieto** | 61 | 13 | 2025-12-03 | EMEA |
| [acruzgarcia/OMIEData](https://github.com/acruzgarcia/OMIEData) | MIT | Importador de datos de OMIE (operador del mercado ibérico). **Quieto desde 2025-08** | 38 | 15 | 2025-08-10 | EMEA |

**Matiz que hay que decir en una propuesta**: esto **no** es "agentes de trading". Es simulación de
mercado y acceso a datos de mercado. Un bot que coloque ofertas en un mercado mayorista real sigue
sin tener equivalente open source — ese gap **sigue abierto**, y ahora está delimitado con precisión:
falta la capa de *ejecución*, no la de *modelado*.

### Gap 2 — "O&M de activos renovables: sólo un repo" → **roto**

| Nombre | Licencia | Descripción | Stars | Forks | Último push | Región origen |
|--------|----------|-------------|-------|-------|-------------|---------------|
| [sltzgs/OpenWindSCADA](https://github.com/sltzgs/OpenWindSCADA) | GPL-3.0 | Lista curada de datasets abiertos de SCADA de aerogeneradores + código | 259 | 48 | 2026-11-19 | EMEA |
| [NatLabRockies/OpenOA](https://github.com/NatLabRockies/OpenOA) | BSD-3-Clause | **Framework de evaluación de performance de parques eólicos** (metodologías de Operational Assessment). Es el motor que faltaba junto a los datasets | 259 | 113 | 2026-11-19 | North America |
| [NatLabRockies/rdtools](https://github.com/NatLabRockies/rdtools) | MIT | Análisis de degradación y suciedad en plantas fotovoltaicas: pérdida de performance medida en serie temporal real | 190 | 84 | 2026-10-20 | North America |
| [pvlib/pvanalytics](https://github.com/pvlib/pvanalytics) | MIT | Control de calidad, filtrado y etiquetado de features sobre datos de plantas PV | 145 | 44 | 2026-07-08 | North America |

**Por qué el pase anterior no los vio**: buscó `wind turbine SCADA machine learning` y
`mantenimiento predictivo`. El vocabulario real del dominio es **"operational assessment"**,
**"performance loss"** y **"degradation"** — nunca "mantenimiento predictivo", que es vocabulario de
vendor. La consulta que rinde es por **organización** (`NatLabRockies`, `pvlib`) y por **método**.

### Gap 3 — "Gemelo digital de distribución: sólo piezas" → **más piezas, y una trampa de licencia**

| Nombre | Licencia | Descripción | Stars | Forks | Último push | Región origen |
|--------|----------|-------------|-------|-------|-------------|---------------|
| [VOLTTRON/volttron](https://github.com/VOLTTRON/volttron) | **Apache-2.0** (resuelta; API dice `NOASSERTION`) | Plataforma de control distribuido de PNNL/Battelle: bus de mensajes + agentes en el borde | 504 | 284 | 2026-11-03 | North America |
| [gridlab-d/gridlab-d](https://github.com/gridlab-d/gridlab-d) | ⚠️ **licencia propia "GridLAB-D License v5.3"** (no OSI) | Simulador de distribución del DOE/PNNL: acopla red, edificios, mercados y DER | 221 | 136 | 2026-10-29 | North America |
| [dss-extensions/OpenDSSDirect.py](https://github.com/dss-extensions/OpenDSSDirect.py) | **BSD-3 + derechos del gobierno de EE. UU.** (API decía `NOASSERTION`) | Interfaz Python directa a OpenDSS (motor de distribución de EPRI) | 119 | 25 | 2026-02-26 | Global |
| [dss-extensions/DSS-Python](https://github.com/dss-extensions/DSS-Python) | BSD-3-Clause | Bindings nativos de Python para una implementación alternativa de OpenDSS | 80 | 8 | 2026-02-26 | Global |
| [dss-extensions/dss_capi](https://github.com/dss-extensions/dss_capi) | BSD-3-Clause | Librería C-API multiplataforma de OpenDSS | 42 | 20 | 2026-07-28 | Global |
| [e2nIEE/pandapipes](https://github.com/e2nIEE/pandapipes) | **BSD-3-Clause** (resuelta; API decía `NOASSERTION`) | Cálculo de flujo en tuberías: **gas, hidrógeno y calor**. Complementa `pandapower` para redes multi-energía | 247 | 91 | 2026-11-17 | EMEA |

**La trampa**: `GridLAB-D` **no es BSD**. Tiene una licencia escrita a medida por Battelle
("GridLAB-D License Version 5.3, October 2024"). El *permiso* es amplio —usar, copiar, modificar,
fusionar, publicar, distribuir, sublicenciar y vender— pero:

1. **Cláusula de nombre**: *"neither the name Battelle Memorial Institute or Battelle may be used in
   any form whatsoever without the express written consent of Battelle"*. Más estricta que la
   cláusula 3 de BSD: no se limita a promoción.
2. **Derechos del gobierno de EE. UU.** bajo contrato DE-AC05-76RL01830, con el término exacto
   "identificable mediante consulta a Battelle o al DOE" — es decir, **no está escrito en el
   archivo**.
3. **No está en la lista OSI ni en SPDX.** Un gate automático de compliance lo marcará como
   "licencia desconocida" aunque el permiso sea permisivo. Hay que resolverlo con legal **antes**,
   no en la auditoría.

### Subsector nuevo: upstream de petróleo y gas (la KB sólo había mirado electricidad)

"Energy" no es sólo red eléctrica. El upstream existe en open source, está activo, y su perfil de
licencia es **el inverso** del de la capa agéntica eléctrica:

| Nombre | Licencia | Descripción | Stars | Forks | Último push | Región origen |
|--------|----------|-------------|-------|-------|-------------|---------------|
| [OPM/opm-simulators](https://github.com/OPM/opm-simulators) | **GPL-3.0** | **OPM Flow**: simulador de yacimientos (reservoir) de referencia en open source | 182 | 163 | 2026-11-18 | EMEA |
| [equinor/ert](https://github.com/equinor/ert) | **GPL-3.0** | **ERT**: ensemble-based reservoir tool, para correr ensembles de modelos dinámicos y asimilación de datos (Equinor, Noruega) | 167 | 154 | 2026-11-19 | EMEA |
| [equinor/webviz-subsurface](https://github.com/equinor/webviz-subsurface) | **GPL-3.0** | Plugins de visualización de datos de subsuelo | 62 | 62 | 2026-11-19 | EMEA |

**Hallazgo de perfil de licencia** — y es el dato accionable de este bloque:

| Capa | Licencia típica | Implicación |
|------|-----------------|-------------|
| Agentes / MCP eléctricos (`Power-Agent/*`, `pypsa-mcp`) | **MIT** | Empotrable en producto de cliente |
| Modelado eléctrico (`PyPSA`, `pandapower`, `pvlib`) | **MIT / BSD-3** | Empotrable |
| Plataformas EMS/SCADA (`OpenEMS`, `openremote`, `json-scada`) | **AGPL / GPL** | Aislar detrás de API |
| **Upstream O&G (`OPM`, `equinor/*`)** | **GPL-3.0, sin excepción encontrada** | **Mismo tratamiento que SCADA: proceso aparte** |

No se encontró **ni un** repo upstream permisivo con tracción. Para un engagement de O&G, el límite
de proceso no es una buena práctica: es la condición para que exista el entregable.

### Hallazgo LATAM: el operador del sistema colombiano publica código MIT

El pase anterior declaró: *"no se encontró ningún repo energético de origen argentino, chileno,
colombiano o mexicano con tracción"*, y notó que el hallazgo brasileño (`json-scada`, `OSHMI`) es de
**un solo autor**. Ambas cosas acaban de cambiar en el lado colombiano:

| Nombre | Licencia | Descripción | Stars | Forks | Último push | Región origen |
|--------|----------|-------------|-------|-------|-------------|---------------|
| [EquipoAnaliticaXM/API_XM](https://github.com/EquipoAnaliticaXM/API_XM) | **MIT** — `Copyright (c) 2020 XM S.A. E.S.P.` | Cliente de consulta de la API de datos del **mercado eléctrico colombiano**: generación, demanda, precios, emisiones | 75 | 38 | 2026-11-10 | **LATAM** |
| [EquipoAnaliticaXM/datasets](https://github.com/EquipoAnaliticaXM/datasets) | sin licencia declarada | Archivos históricos de variables del sistema colombiano. Actualizado **2026-11-19** | 5 | 1 | 2026-11-19 | **LATAM** |

**Por qué importa más que los stars**: `XM S.A. E.S.P.` es el **operador del Sistema
Interconectado Nacional y administrador del mercado** de Colombia. No es un entusiasta: es la
institución, publicando bajo MIT, con el copyright corporativo en el `LICENSE`. El org tiene además
`Chatbot_XM` (MIT, 1 ★) y `documentacion_emisionesCO2` (MIT, 1 ★) — pequeños, pero muestran que la
publicación es **política del equipo de analítica**, no un accidente.

**Y hay ecosistema aguas abajo** (0–1 ★, no son hallazgos curados, son señal de demanda):
`Cdhernandezr/energyagent-colombia` (agente de IA sobre el mercado eléctrico colombiano, LangGraph +
FastAPI, **sin licencia**) y `CAINavy/tablero-xm` (tablero sobre datos de XM, push **2026-11-20**).
Es decir: ya hay gente construyendo agentes sobre esta API **hoy**, sin licencia ni soporte. Ese es
el hueco de mercado exacto.

**Precisión necesaria**: el gap LATAM se cierra para **Colombia y Brasil**. Para **Argentina
(CAMMESA), Chile (Coordinador Eléctrico Nacional) y México (CENACE)** se buscó por nombre de
institución y por término de dominio en español y portugués: **cero repos institucionales con
tracción**. Lo que aparece son dashboards personales de 0 ★. El gap sigue abierto ahí, ahora medido
por país y no por región.

### Planificación y expansión de capacidad: la categoría que la KB no tenía

| Nombre | Licencia | Descripción | Stars | Forks | Último push | Región origen |
|--------|----------|-------------|-------|-------|-------------|---------------|
| [oemof/oemof-solph](https://github.com/oemof/oemof-solph) | **MIT** (SPDX en `pyproject.toml`; API decía `null`) | Generador de modelos de sistemas energéticos LP/MILP; base de buena parte del modelado alemán | 430 | 158 | 2026-11-19 | EMEA |
| [pypsa-meets-earth/pypsa-earth](https://github.com/pypsa-meets-earth/pypsa-earth) | ⚠️ **AGPL-3.0-or-later** (SPDX en `README`; API decía `null`) | **PyPSA-Earth**: modelo de sistema energético para *cualquier* país — el único camino directo a LATAM/África/Asia | 384 | 383 | 2026-11-16 | Global |
| [calliope-project/calliope](https://github.com/calliope-project/calliope) | Apache-2.0 | Framework multi-escala de modelado de sistemas energéticos | 380 | 117 | 2026-10-20 | EMEA |
| [PowerGenome/PowerGenome](https://github.com/PowerGenome/PowerGenome) | MIT | Construcción de inputs para modelos de sistemas de potencia (foco EE. UU.) | 235 | 78 | 2026-11-19 | North America |
| [etsap-TIMES/TIMES_model](https://github.com/etsap-TIMES/TIMES_model) | GPL-3.0 | TIMES (MARKAL-EFOM): modelo bottom-up de energía-ambiente del ETSAP/IEA | 151 | 56 | 2026-11-05 | Global |
| [TemoaProject/temoa](https://github.com/TemoaProject/temoa) | MIT | Tools for Energy Model Optimization and Analysis | 116 | 77 | 2026-11-19 | North America |
| [rebase-energy/energydatamodel](https://github.com/rebase-energy/energydatamodel) | MIT | Representación de sistemas energéticos como data classes de Python: capa de modelo de dominio reutilizable | 99 | 10 | 2026-08-28 | EMEA |

**El dato que cambia una propuesta regional**: `PyPSA` (núcleo) es **MIT**, pero **`pypsa-eur` no
tiene licencia** y **`pypsa-earth` es AGPL-3.0-or-later**. O sea: el modelo europeo no se puede usar
y el modelo global —el único que cubre LATAM y APAC de fábrica— **obliga a liberar el servicio**
si se expone por red. Para un cliente que quiera un estudio de expansión como SaaS, la alternativa
permisiva es `calliope` (Apache-2.0), `oemof-solph` (MIT) o `temoa` (MIT), asumiendo el trabajo de
construir los datos del país. Ese trabajo de datos **es** el presupuesto.

---

## 2026-11-20 — pase 1 (renombres de org y correcciones de licencia)

**Titular del pase: dos renombres de organización rompieron URLs que esta KB daba por buenas, y se
confirmó el primer repo de origen LATAM con tracción real en toda la rotación.**

### Movimientos estructurales detectados

| Cambio | Antes | Ahora | Impacto |
|--------|-------|-------|---------|
| Renombre de org | `NREL/*` | **`NatLabRockies/*`** | Rompe URLs de `EnergyPlus` (1623 ★) y `PowerGridworld` (188 ★) |
| Renombre de org | `intelligent-environments-lab/CityLearn` | **`citylearn-project/CityLearn`** | 662 ★; URL previa no resuelve |
| Renombre de org | `openremote/openremote` | **`openremote/core`** | 2162 ★; URL previa no resuelve |
| Movimiento de org | `alliander/openstef` | **`OpenSTEF/openstef`** | 183 ★; ahora bajo LF Energy |

### Repos con tracción verificada esta semana

| Nombre | Licencia | Descripción | Stars | Forks | Último push |
|--------|----------|-------------|-------|-------|-------------|
| [evcc-io/evcc](https://github.com/evcc-io/evcc) | MIT | Carga inteligente de EV con excedente solar y tarifa dinámica; mayor tracción del ecosistema energético open source | 7638 | 1649 | 2026-11-19 |
| [PyPSA/PyPSA](https://github.com/PyPSA/PyPSA) | MIT | Python for Power System Analysis | 2248 | 743 | 2026-11-19 |
| [openremote/core](https://github.com/openremote/core) | AGPL-3.0 | Plataforma IoT/EMS (renombrada desde `openremote/openremote`) | 2162 | 526 | 2026-11-19 |
| [hubblo-org/scaphandre](https://github.com/hubblo-org/scaphandre) | Apache-2.0 | Agente de metrología de consumo energético de cómputo | 2019 | 133 | 2026-07-19 |
| [Akkudoktor-EOS/EOS](https://github.com/Akkudoktor-EOS/EOS) | Apache-2.0 | Energy Optimization System con PV, batería y tarifa dinámica | 1731 | 147 | 2026-11-17 |
| [pvlib/pvlib-python](https://github.com/pvlib/pvlib-python) | BSD-3-Clause | Modelado de performance fotovoltaica | 1730 | 1276 | 2026-11-19 |
| [OpenEMS/openems](https://github.com/OpenEMS/openems) | AGPL-3.0 | Energy Management System modular | 1631 | 706 | 2026-11-19 |
| [NatLabRockies/EnergyPlus](https://github.com/NatLabRockies/EnergyPlus) | BSD-3 + cláusula de marca | Simulación energética de edificio completo | 1623 | — | 2026-11-19 |
| [e2nIEE/pandapower](https://github.com/e2nIEE/pandapower) | BSD-3-Clause | Modelado y análisis de redes | 1331 | 639 | 2026-11-19 |
| [mz-automation/libiec61850](https://github.com/mz-automation/libiec61850) | GPL-3.0 | Librería de referencia de IEC 61850 | 1253 | 621 | 2026-10-21 |
| [steve-community/steve](https://github.com/steve-community/steve) | GPL-3.0 | Servidor OCPP de gestión de estaciones de carga | 1151 | 500 | 2026-11-14 |
| [MyEMS/myems](https://github.com/MyEMS/myems) | MIT | EMS para edificios, fábricas y campus (origen APAC) | 763 | 280 | 2026-11-16 |
| [riclolsen/json-scada](https://github.com/riclolsen/json-scada) | GPL-3.0 | **Origen LATAM (Brasil)** — SCADA/EMS/IIoT con IEC 61850, ICCP, 60870-5, DNP3, OPC-UA | 513 | 141 | 2026-11-17 |
| [Grid2op/grid2op](https://github.com/Grid2op/grid2op) | MPL-2.0 | Testbed de decisión secuencial en redes (RTE) | 494 | 155 | 2026-11-13 |
| [riclolsen/OSHMI](https://github.com/riclolsen/OSHMI) | GPL-3.0 | **Origen LATAM (Brasil)** — HMI SCADA para subestaciones | 467 | 171 | 2026-05-02 |
| [dos-group/vessim](https://github.com/dos-group/vessim) | MIT | Simulación de sistemas energéticos de datacenter | 103 | 16 | 2026-10-20 |

### Correcciones de licencia de este pase

Resueltas leyendo el `LICENSE` crudo, porque la API devolvía `NOASSERTION`:

| Repo | API decía | Realidad verificada | Veredicto |
|------|-----------|---------------------|-----------|
| `MyEMS/myems` | NOASSERTION | **MIT** | ✅ rescatado |
| `e2nIEE/pandapower` | NOASSERTION | **BSD-3-Clause** | ✅ rescatado |
| `Akkudoktor-EOS/EOS` | NOASSERTION | **Apache-2.0** | ✅ rescatado |
| `openremote/core` | NOASSERTION | **AGPL-3.0** (`LICENSE.txt`) | ⚠️ copyleft de red |
| `NatLabRockies/EnergyPlus` | NOASSERTION | **BSD-3 + cláusula (4) de marca** | ⚠️ restricción de nombre |
| `CURENT/andes` | NOASSERTION | **GPL-3.0** | ⚠️ copyleft |
| `u9n/dlms-cosem` | NOASSERTION | **Business Source License 1.1** | ❌ no permisiva |
| `Grid2op/grid2op` | MPL-2.0 | **MPL-2.0** (pases previos decían LGPL-2.1) | ✅ corregido |
| `PyPSA/pypsa-eur` | NONE | **sin licencia declarada** | ❌ sin permiso de uso |
| `GridMod/RTS-GMLC` | NONE | **sin licencia declarada** | ❌ sin permiso de uso |

**Lección de método reconfirmada**: `NOASSERTION` de la API no significa "sin licencia" — significa
"GitHub no la reconoció". Siete de diez casos revisados aquí tenían licencia real, y uno
(`dlms-cosem`) era una **BUSL** que habría pasado por open source.

**Lección de descubrimiento**: la consulta que encuentra estos repos es por **estándar o protocolo**
(`IEC 61850`, `IEC 61970`, `OpenADR`, `OCPP`, `IEEE 2030.5`, `SunSpec`) o por **`topic:`**
(`topic:power-systems`, `topic:smart-grid`), nunca por buzzword. `"top open source AI agents energy
2026"` devolvió casi exclusivamente proyectos de hackathon con 0–3 stars. Además, en la API de
GitHub **no se pueden combinar qualifiers con `OR`** (error 422) y un `OR` de términos libres se
aplica globalmente: `DER OR microgrid` trajo `derive_more` y `derailed_benchmarks`.

---

## Historial

### 2026-07-02 — pase automático (datos NO verificados)

⚠️ **Advertencia añadida 2026-11-20**: las filas de abajo provienen de un pipeline de keyword-match
sin verificación. Al menos una (`mtd`, conversor de Markdown a DOCX) **no pertenece al dominio
energético**, y varias tienen 0–2 stars. La entrada `openremote` apuntaba a una URL que **ya no
resuelve**. Se conservan por la regla append-only, **no** como hallazgos curados.
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
