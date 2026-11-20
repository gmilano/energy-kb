---
industry: energy
region: Global
updated: 2026-11-20
---

# 🏗️ Repos fundacionales — energy

> Bases sobre las cuales construir: licencia abierta, comunidad activa, mantenimiento verificado.
> Todas las filas verificadas contra la GitHub REST API el **2026-11-20**.

## Núcleo de modelado y análisis de redes

| Repo | Licencia | Descripción | Stars | Forks | Último push | Región origen |
|------|----------|-------------|-------|-------|-------------|---------------|
| [PyPSA/PyPSA](https://github.com/PyPSA/PyPSA) | MIT | Python for Power System Analysis: el estándar de facto para modelado y optimización de sistemas eléctricos | 2248 | 743 | 2026-11-19 | EMEA |
| [pvlib/pvlib-python](https://github.com/pvlib/pvlib-python) | BSD-3-Clause | Modelado de performance de sistemas fotovoltaicos; base de casi todo forecasting solar serio | 1730 | 1276 | 2026-11-19 | North America |
| [NatLabRockies/EnergyPlus](https://github.com/NatLabRockies/EnergyPlus) | BSD-3 + cláusula de marca (ver nota) | Simulación energética de edificio completo; motor de referencia del DOE | 1623 | — | 2026-11-19 | North America |
| [e2nIEE/pandapower](https://github.com/e2nIEE/pandapower) | BSD-3-Clause | Modelado y análisis de redes (AC/DC OPF) sobre PYPOWER + pandas | 1331 | 639 | 2026-11-19 | EMEA |
| [SanPen/VeraGrid](https://github.com/SanPen/VeraGrid) | MPL-2.0 | Software multiplataforma de sistemas de potencia con interfaz gráfica | 644 | 150 | 2026-11-16 | EMEA |
| [Sienna-Platform/PowerSystems.jl](https://github.com/Sienna-Platform/PowerSystems.jl) | BSD-3-Clause | Estructuras de datos en Julia para análisis de sistemas de potencia | 373 | 107 | 2026-11-18 | North America |
| [PowerGridModel/power-grid-model](https://github.com/PowerGridModel/power-grid-model) | MPL-2.0 | Librería Python/C++ de análisis de redes de distribución (Alliander, LF Energy) | 262 | 86 | 2026-11-19 | EMEA |
| [powsybl/powsybl-core](https://github.com/powsybl/powsybl-core) | MPL-2.0 | Framework para construir software de sistemas de potencia (RTE Francia, LF Energy) | 196 | 85 | 2026-11-19 | EMEA |
| [sogno-platform/dpsim](https://github.com/sogno-platform/dpsim) | MPL-2.0 | Simulador de red en tiempo real: powerflow, phasors dinámicos y EMT (RWTH Aachen) | 145 | 96 | 2026-11-19 | EMEA |

## Forecasting y recurso renovable

| Repo | Licencia | Descripción | Stars | Forks | Último push | Región origen |
|------|----------|-------------|-------|-------|-------------|---------------|
| [Nixtla/statsforecast](https://github.com/Nixtla/statsforecast) | Apache-2.0 | Forecasting estadístico y econométrico de alta velocidad; baseline obligatorio antes de meter deep learning en load forecasting | 4980 | 437 | 2026-11-19 | Global |
| [Green-Software-Foundation/carbon-aware-sdk](https://github.com/Green-Software-Foundation/carbon-aware-sdk) | MIT | SDK para desplazar cómputo según intensidad de carbono de la red | 600 | 112 | 2026-11-04 | Global |
| [PyPSA/atlite](https://github.com/PyPSA/atlite) | MIT | Cálculo de potenciales renovables y series temporales a partir de datos meteorológicos | 412 | 134 | 2026-11-19 | EMEA |
| [OpenSTEF/openstef](https://github.com/OpenSTEF/openstef) | **MPL-2.0** | Pipeline de forecasting energético de corto plazo en producción (LF Energy; origen Alliander + RTE) | 183 | 67 | 2026-11-19 | EMEA |

## Planificación y expansión de capacidad

Categoría ausente en pases anteriores de esta KB. Es la base de cualquier estudio de transición
energética, mix de generación o plan de expansión de red que un cliente encargue:

| Repo | Licencia | Descripción | Stars | Forks | Último push | Región origen |
|------|----------|-------------|-------|-------|-------------|---------------|
| [oemof/oemof-solph](https://github.com/oemof/oemof-solph) | **MIT** (SPDX en `pyproject.toml`) | Generador de modelos LP/MILP de sistemas energéticos; núcleo del ecosistema oemof | 430 | 158 | 2026-11-19 | EMEA |
| [pypsa-meets-earth/pypsa-earth](https://github.com/pypsa-meets-earth/pypsa-earth) | ⚠️ **AGPL-3.0-or-later** (SPDX en `README`) | **PyPSA-Earth**: modelo de sistema energético para cualquier país del mundo. El único con cobertura LATAM/APAC de fábrica | 384 | 383 | 2026-11-16 | Global |
| [calliope-project/calliope](https://github.com/calliope-project/calliope) | Apache-2.0 | Framework multi-escala de modelado de sistemas energéticos | 380 | 117 | 2026-10-20 | EMEA |
| [PowerGenome/PowerGenome](https://github.com/PowerGenome/PowerGenome) | MIT | Construye los inputs de modelos de sistemas de potencia (foco EE. UU.): la parte tediosa y reutilizable | 235 | 78 | 2026-11-19 | North America |
| [etsap-TIMES/TIMES_model](https://github.com/etsap-TIMES/TIMES_model) | GPL-3.0 | TIMES (MARKAL-EFOM) del ETSAP/IEA: modelo bottom-up energía-ambiente usado por ministerios | 151 | 56 | 2026-11-05 | Global |
| [TemoaProject/temoa](https://github.com/TemoaProject/temoa) | MIT | Tools for Energy Model Optimization and Analysis | 116 | 77 | 2026-11-19 | North America |
| [rebase-energy/energydatamodel](https://github.com/rebase-energy/energydatamodel) | MIT | Sistemas energéticos como data classes de Python: modelo de dominio reutilizable entre proyectos | 99 | 10 | 2026-08-28 | EMEA |

**Decisión de licencia de esta categoría**: `PyPSA` (núcleo) es MIT, pero sus dos modelos derivados
más citados **no son usables tal cual** — `pypsa-eur` **sin licencia declarada** y `pypsa-earth`
**AGPL-3.0-or-later**. Para un estudio entregado como servicio, la ruta permisiva es `calliope`
(Apache-2.0), `oemof-solph` (MIT) o `temoa` (MIT), **con el coste de construir los datos del país**.
Ese coste de datos es el presupuesto real del proyecto, no la licencia.

## Operación y mantenimiento de activos renovables

| Repo | Licencia | Descripción | Stars | Forks | Último push | Región origen |
|------|----------|-------------|-------|-------|-------------|---------------|
| [NatLabRockies/OpenOA](https://github.com/NatLabRockies/OpenOA) | BSD-3-Clause | Framework de **operational assessment** de parques eólicos: AEP, pérdidas, disponibilidad, incertidumbre | 259 | 113 | 2026-11-19 | North America |
| [sltzgs/OpenWindSCADA](https://github.com/sltzgs/OpenWindSCADA) | GPL-3.0 | Lista curada de **datasets abiertos** de SCADA de aerogeneradores + código asociado | 259 | 48 | 2026-11-19 | EMEA |
| [NatLabRockies/rdtools](https://github.com/NatLabRockies/rdtools) | MIT | Degradación y suciedad en plantas PV: tasa de pérdida de performance sobre serie temporal real | 190 | 84 | 2026-10-20 | North America |
| [pvlib/pvanalytics](https://github.com/pvlib/pvanalytics) | MIT | Control de calidad y etiquetado de datos de plantas PV: el paso previo a cualquier modelo | 145 | 44 | 2026-07-08 | North America |

**Lección de vocabulario** (vale para el próximo pase): este dominio **no** se llama "mantenimiento
predictivo" —ése es término de vendor— sino **operational assessment**, **performance loss** y
**degradation**. Buscar por el término de vendor devuelve cero; buscar por el término del dominio, o
por organización (`NatLabRockies`, `pvlib`), devuelve cuatro repos mantenidos.

## Redes de distribución y multi-energía

| Repo | Licencia | Descripción | Stars | Forks | Último push | Región origen |
|------|----------|-------------|-------|-------|-------------|---------------|
| [e2nIEE/pandapipes](https://github.com/e2nIEE/pandapipes) | **BSD-3-Clause** (Fraunhofer IEE) | Flujo en tuberías para **gas, hidrógeno y calor**: el complemento de `pandapower` para acoplamiento sectorial | 247 | 91 | 2026-11-17 | EMEA |
| [gridlab-d/gridlab-d](https://github.com/gridlab-d/gridlab-d) | ⚠️ **licencia propia Battelle v5.3** (no OSI) | Simulador de distribución del DOE/PNNL: acopla red, edificios, mercados y DER en un solo motor | 221 | 136 | 2026-10-29 | North America |
| [dss-extensions/OpenDSSDirect.py](https://github.com/dss-extensions/OpenDSSDirect.py) | **BSD-3 + derechos del gobierno de EE. UU.** | Interfaz Python directa al motor de distribución OpenDSS (EPRI) | 119 | 25 | 2026-02-26 | Global |
| [dss-extensions/DSS-Python](https://github.com/dss-extensions/DSS-Python) | BSD-3-Clause | Bindings nativos de Python de una implementación alternativa de OpenDSS | 80 | 8 | 2026-02-26 | Global |
| [dss-extensions/dss_capi](https://github.com/dss-extensions/dss_capi) | BSD-3-Clause | Librería C-API multiplataforma de OpenDSS: el nivel al que se integra desde otro lenguaje | 42 | 20 | 2026-07-28 | Global |

## Mercados eléctricos

| Repo | Licencia | Descripción | Stars | Forks | Último push | Región origen |
|------|----------|-------------|-------|-------|-------------|---------------|
| [assume-framework/assume](https://github.com/assume-framework/assume) | MIT | **ASSUME**: simulación basada en agentes de la evolución de mercados eléctricos (Fraunhofer IEE / INATECH / TU Dresden) | 128 | 53 | 2026-11-19 | EMEA |

## Upstream de petróleo y gas (subsector nuevo en esta KB)

"Energy" no es sólo red eléctrica, y el upstream tiene ecosistema propio, activo y **enteramente
GPL-3.0**:

| Repo | Licencia | Descripción | Stars | Forks | Último push | Región origen |
|------|----------|-------------|-------|-------|-------------|---------------|
| [OPM/opm-simulators](https://github.com/OPM/opm-simulators) | **GPL-3.0** | **OPM Flow**: el simulador de yacimientos de referencia en open source (Open Porous Media) | 182 | 163 | 2026-11-18 | EMEA |
| [equinor/ert](https://github.com/equinor/ert) | **GPL-3.0** | **ERT**: ensembles de modelos dinámicos de yacimiento y asimilación de datos (Equinor, Noruega) | 167 | 154 | 2026-11-19 | EMEA |
| [equinor/webviz-subsurface](https://github.com/equinor/webviz-subsurface) | **GPL-3.0** | Visualización de datos de subsuelo sobre `webviz-config` | 62 | 62 | 2026-11-19 | EMEA |

**No se encontró ningún repo upstream permisivo con tracción.** Para un engagement de O&G el límite
de proceso (ejecutar el simulador aparte y hablarle por API/archivos) no es buena práctica: es la
condición para que el entregable del cliente pueda ser propietario.

## Datos de mercado de origen institucional (LATAM)

| Repo | Licencia | Descripción | Stars | Forks | Último push | Región origen |
|------|----------|-------------|-------|-------|-------------|---------------|
| [EquipoAnaliticaXM/API_XM](https://github.com/EquipoAnaliticaXM/API_XM) | **MIT** — `Copyright (c) 2020 XM S.A. E.S.P.` | Cliente de la API de datos del mercado eléctrico colombiano (generación, demanda, precios, emisiones), publicado por el **operador del sistema** | 75 | 38 | 2026-11-10 | **LATAM** |

Equivalente funcional de lo que `hass-entso-e` (Apache-2.0, 280 ★) es para Europa, pero publicado
por la institución misma. Es el **sustrato de datos** sobre el que se puede construir un agente de
mercado para Colombia sin negociar acceso.

**34 repos fundacionales reales** (13 del primer pase + 21 añadidos en el segundo).

## Activos físicos: baterías, eólica, solar y nuclear (categoría añadida en el tercer pase del 2026-11-20)

Hasta este pase la KB modelaba **la red** y no **el activo**. Son dos preguntas distintas: una es
cómo fluye la potencia por el sistema, otra es qué ocurre dentro de la batería, la turbina o el
reactor. Todo lo de esta sección es permisivo salvo donde se indica.

### Baterías y almacenamiento

| Repo | Licencia | Para qué sirve | Stars | Forks | Último push | Región origen |
|------|----------|----------------|-------|-------|-------------|---------------|
| [pybamm-team/PyBaMM](https://github.com/pybamm-team/PyBaMM) | **BSD-3-Clause** | Modelos de batería basados en física (DFN, SPM, SPMe). Estándar de facto; respaldo de The Faraday Institution. **845 forks** — el repo con más derivación de toda esta KB | 1737 | 845 | 2026-11-19 | EMEA |
| [pybamm-team/liionpack](https://github.com/pybamm-team/liionpack) | MIT | Del modelo de celda al **pack** completo (serie/paralelo), sobre PyBaMM | 120 | 39 | 2026-11-16 | EMEA |

Punto de entrada obligado para degradación, garantía de capacidad, dimensionamiento de BESS y
second-life. Nada de eso se responde con un modelo de flujo de potencia.

### Eólica

| Repo | Licencia | Para qué sirve | Stars | Forks | Último push | Región origen |
|------|----------|----------------|-------|-------|-------------|---------------|
| [OpenFAST/openfast](https://github.com/OpenFAST/openfast) | **Apache-2.0** | Simulación aeroelástica de turbina completa y de parque (FAST.Farm). Laboratorio nacional de EE. UU. (NLR, ex-NREL) | 991 | 552 | 2026-11-20 | North America |
| [NatLabRockies/floris](https://github.com/NatLabRockies/floris) | BSD-3-Clause | Modelo de estela orientado a control: wake steering y optimización de layout | 302 | 190 | 2026-11-18 | North America |
| [wind-python/windpowerlib](https://github.com/wind-python/windpowerlib) | MIT | Curva de potencia y salida de turbinas/parques. ⚠️ sin mantenimiento desde **2024-02-20** | 397 | 113 | 2024-02-20 | EMEA |

⚠️ `DTUWindEnergy/PyWake` **no se recomienda desde aquí**: lo que hay en GitHub es un espejo del
GitLab de DTU, con licencia `null` y último push 2024-11-25. El proyecto vivo no está en GitHub.

### Solar, recurso renovable y tecno-economía

| Repo | Licencia | Para qué sirve | Stars | Forks | Último push | Región origen |
|------|----------|----------------|-------|-------|-------------|---------------|
| [NatLabRockies/SAM](https://github.com/NatLabRockies/SAM) | BSD-3-Clause | **System Advisor Model**: modelo tecno-económico de referencia (FV, CSP, eólica, geotermia, almacenamiento). Responde si un proyecto cierra financieramente | 498 | 221 | 2026-11-19 | North America |
| [NatLabRockies/ssc](https://github.com/NatLabRockies/ssc) | BSD-3-Clause | Motor de cálculo de SAM, embebible como librería sin GUI | 96 | 119 | 2026-11-19 | North America |
| [NatLabRockies/reV](https://github.com/NatLabRockies/reV) | BSD-3-Clause | Potencial técnico geoespacial a escala de país: dónde cabe y cuánto produce | 144 | 63 | 2026-10-01 | North America |
| [NatLabRockies/sup3r](https://github.com/NatLabRockies/sup3r) | BSD-3-Clause | **GAN de super-resolución** de datos de recurso: sube resolución espacio-temporal de reanálisis climático | 144 | 33 | 2026-11-18 | North America |

### Nuclear (subsector nuevo, traído por la demanda de datacenter)

| Repo | Licencia | Para qué sirve | Stars | Forks | Último push | Región origen |
|------|----------|----------------|-------|-------|-------------|---------------|
| [openmc-dev/openmc](https://github.com/openmc-dev/openmc) | **MIT** (resuelta en `LICENSE` crudo; la API dice `NOASSERTION`) | Transporte de neutrones Monte Carlo. Copyright MIT + UChicago Argonne. Base abierta para análisis de núcleo y SMR | 1147 | 704 | 2026-11-19 | North America |
| [idaholab/moose](https://github.com/idaholab/moose) | ⚠️ **LGPL-2.1** | Multifísica de elementos finitos (Idaho National Laboratory). Copyleft débil: enlazable, **no permisivo** | 2409 | 1282 | 2026-11-19 | North America |

## Respuesta de demanda: el protocolo que faltaba

| Repo | Licencia | Para qué sirve | Stars | Forks | Último push | Región origen |
|------|----------|----------------|-------|-------|-------------|---------------|
| [OpenLEADR/openleadr-python](https://github.com/OpenLEADR/openleadr-python) | **Apache-2.0** | Implementación de **OpenADR 2.0b**: la señalización estándar de respuesta de demanda entre la utility y el recurso flexible | 161 | 67 | 2026-11-16 | North America |

La KB ya tenía con qué **simular** DR (`CityLearn`), con qué **ejecutar** en el borde (`VOLTTRON`) y
con qué **controlar** carga de EV (`evcc`). Faltaba la pieza que **habla el protocolo con la
utility**. Sin ella, un piloto de flexibilidad no se integra con el programa del operador.

## Planificación: añadidos del tercer pase

| Repo | Licencia | Para qué sirve | Stars | Forks | Último push | Región origen |
|------|----------|----------------|-------|-------|-------------|---------------|
| [PyPSA/pypsa-usa](https://github.com/PyPSA/pypsa-usa) | MIT | Modelo del sistema eléctrico de EE. UU. sobre PyPSA, con datos abiertos | 153 | — | 2026-11-20 | North America |
| [OSeMOSYS/OSeMOSYS](https://github.com/OSeMOSYS/OSeMOSYS) | Apache-2.0 | Planificación de largo plazo usada por agencias y ministerios en planes nacionales | 196 | 123 | 2025-10-22 | EMEA |
| [switch-model/switch](https://github.com/switch-model/switch) | **Apache-2.0** (resuelta en `LICENSE` crudo) | Planificación de sistemas de alta penetración renovable | 158 | 95 | 2025-07-07 | North America |
| [GenXProject/GenX.jl](https://github.com/GenXProject/GenX.jl) | ⚠️ **GPL-2.0** | Expansión de capacidad (Princeton). Muy citado y **no permisivo** | 370 | — | 2026-10-15 | North America |

`OSeMOSYS` importa especialmente fuera de Europa: es el modelo con el que varios ministerios de
LATAM y África han construido planes nacionales, lo que lo vuelve una credencial de conversación
con reguladores, no sólo una herramienta.

## Notas de licencia que cambian decisiones

- **`NatLabRockies/EnergyPlus` no es BSD-3 plano.** El `LICENSE.txt` crudo añade una **cláusula (4)
  de marca**: si se distribuye el software sin cambios hay que llamarlo *"EnergyPlus version X"*, y
  está prohibido usar "EnergyPlus", "E+", "e+" o designaciones confundibles en nombre de empresa,
  de producto, publicidad o promoción **sin consentimiento escrito previo del U.S. DOE**. Pases
  anteriores lo registraron como "BSD3" sin más: para un entregable de marca blanca eso es
  justamente la cláusula que importa.
- **`NREL` se renombró a `NatLabRockies` en GitHub.** Afecta al menos a `EnergyPlus` y
  `PowerGridworld`. Toda URL `github.com/NREL/...` guardada en pases previos está rota.
- **`openSTEF` es MPL-2.0, no Apache-2.0**, y vive en la org `OpenSTEF` (no en `alliander`, que ya
  no resuelve).
- **`pandapower` es BSD-3-Clause** confirmado en el `LICENSE` crudo, aunque la API responde
  `NOASSERTION`. Es seguro usarlo.
- **`PyPSA/pypsa-eur` (640 ★) NO tiene licencia declarada** (`NONE` en la API). Es el modelo
  sectorial europeo más citado, pero sin licencia no hay permiso de uso: **no construir sobre él**
  para un cliente sin resolverlo antes. Igual caso: `GridMod/RTS-GMLC` (267 ★, `NONE`).
- **Evitar en entregables comerciales sin análisis legal**: `u9n/dlms-cosem` (124 ★) es
  **Business Source License 1.1** — source-available, no permisiva; la API solo dice `NOASSERTION`,
  así que es una trampa de licenciamiento fácil de pisar. `CURENT/andes` (389 ★) es **GPL-3.0**
  (también `NOASSERTION` en la API).

### Añadidos del tercer pase (2026-11-20)

| Repo | Trampa | Consecuencia |
|------|--------|--------------|
| `GenXProject/GenX.jl` | Viene de universidad y es muy citado → se asume MIT. Es **GPL-2.0** | Copyleft fuerte en un entregable de planificación: contamina el producto derivado |
| `openmc-dev/openmc` | La API dice `NOASSERTION` → parece sin licencia | Es **MIT** (texto verificado en `LICENSE` crudo). Descartarlo sería perder la única base nuclear abierta |
| `idaholab/moose` | Laboratorio nacional, 2.409 ★ → se asume permisivo | **LGPL-2.1**: enlazable, pero modificaciones al propio MOOSE deben liberarse |
| `open-meteo/open-meteo` (6.703 ★) | API de clima "gratis", muy usada en forecasting renovable | **AGPL-3.0** y su API pública es *non-commercial use*. Dos restricciones distintas y ambas muerden en un SaaS de cliente |
| `wind-python/windpowerlib` | MIT, 397 ★ | Sin mantenimiento desde **2024-02-20**: la licencia está bien, el riesgo es de soporte |

## Fuentes de descubrimiento (para el próximo pase)

Catálogos curados que rinden más que cualquier búsqueda por buzzword:

| Repo | Licencia | Qué aporta | Stars |
|------|----------|-----------|-------|
| [protontypes/open-sustainable-technology](https://github.com/protontypes/open-sustainable-technology) | CC-BY-4.0 | Directorio y análisis del ecosistema open source en clima/energía/sostenibilidad | 2586 |
| [ps-wiki/best-of-ps](https://github.com/ps-wiki/best-of-ps) | CC-BY-SA-4.0 | Ranking semanal de librerías de análisis de sistemas de potencia | 297 |
| [open-energy-transition/Awesome-Electricity-Demand](https://github.com/open-energy-transition/Awesome-Electricity-Demand) | MIT | Recursos de demanda eléctrica horaria y sub-horaria | 74 |
| [zhgqcn/awesome-NILM-with-code](https://github.com/zhgqcn/awesome-NILM-with-code) | CC-BY-4.0 | Non-Intrusive Load Monitoring con código | 149 |

---
*Ver también `verticals/solutions.md` para plataformas verticales completas.*
