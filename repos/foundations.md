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

**34 repos fundacionales reales** (13 del primer pase + 21 añadidos en el segundo);
**63 tras los pases tercero y cuarto** (ver secciones fechadas más abajo).

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

## Sincrofasores y calidad de medida: la categoría MIT que faltaba (cuarto pase, 2026-11-20)

Esta KB tenía modelado de red (PyPSA, pandapower, power-grid-model) y protocolos de campo
(libiec61850), pero nada de la capa que en una utility real alimenta la detección de eventos:
**PMU / sincrofasores**. Es además, y esto es inusual en el sector eléctrico, **MIT**.

| Repo | Licencia | Descripción | Stars | Forks | Último push | Región origen |
|------|----------|-------------|-------|-------|-------------|---------------|
| [GridProtectionAlliance/gsf](https://github.com/GridProtectionAlliance/gsf) | **MIT** | *Grid Solutions Framework*: biblioteca base de la Grid Protection Alliance para aplicaciones de red (series temporales, adaptadores, transporte) | 179 | 76 | 2026-11-13 | North America |
| [GridProtectionAlliance/openPDC](https://github.com/GridProtectionAlliance/openPDC) | **MIT** | *Phasor Data Concentrator* open source: ingesta, concentra y encamina flujos de sincrofasores en tiempo real (IEEE C37.118) | 159 | 67 | 2026-11-15 | North America |

**Por qué cambia una propuesta**: el argumento habitual es que la observabilidad de red de alta
resolución obliga a producto propietario (OSI PI, e-terra). `openPDC` es un PDC de producción con
licencia MIT y 67 forks. Permite ofrecer analítica de eventos sobre datos de PMU **sin** licencia de
plataforma y sin contaminar el código del cliente. Es el complemento aguas arriba de todo lo demás
en esta página: los modelos predicen, el PDC mide.

## Medición y verificación de ahorros: el repo que hace facturable la eficiencia

| Repo | Licencia | Descripción | Stars | Forks | Último push | Región origen |
|------|----------|-------------|-------|-------|-------------|---------------|
| [opendsm/opendsm](https://github.com/opendsm/opendsm) | **Apache-2.0** | Métodos **estándar** de cálculo de consumo energético normalizado (NMEC) y ahorro medido. Linaje OpenEEmeter/CalTRACK; creado 2016 | 244 | 76 | 2026-11-14 | North America |
| [FlexMeasures/flexmeasures](https://github.com/FlexMeasures/flexmeasures) | **Apache-2.0** | Motor de optimización energética listo para empresa: *scheduling* y forecasting de flexibilidad (baterías, carga de EV, bombas de calor). Proyecto LF Energy; creado 2020, 248 issues abiertas = comunidad viva | 217 | 66 | 2026-11-19 | EMEA |

**`opendsm` es la pieza con más valor comercial directo de este pase.** Un proyecto de eficiencia o
de respuesta de demanda sólo se cobra si el ahorro se puede **demostrar** con un método que el
regulador o el cliente acepten. `opendsm` implementa precisamente esos métodos, con Apache-2.0 y
diez años de historia. Sin esa capa, un piloto de optimización con IA produce un número que nadie
firma. Con ella, produce una factura.

**`FlexMeasures`** es el par operativo: decide *cuándo* mover la carga; `opendsm` certifica *cuánto*
se ahorró. Ambas Apache-2.0, ambas empotrables en un entregable cerrado.

## Simulación de protocolo sin hardware: cómo arrancar un piloto sin subestación

El bloqueo más frecuente de un piloto energético no es el modelo: es que no hay acceso al equipo. La
KB tenía librerías *cliente* de protocolo; faltaban los **simuladores de la contraparte**.

| Repo | Licencia | Descripción | Stars | Forks | Último push | Región origen |
|------|----------|-------------|-------|-------|-------------|---------------|
| [suoten/ProtoForge](https://github.com/suoten/ProtoForge) | **MIT** | Simulador **sin hardware** de 28 protocolos industriales (Modbus TCP, S7, OPC UA, BACnet, MQTT…). Permite probar SCADA/HMI contra equipo virtual. Creado 2026-04-24 | 325 | 100 | 2026-11-19 | Global |
| [Fraunhofer-FIT-DIEN/iec104-python](https://github.com/Fraunhofer-FIT-DIEN/iec104-python) | ⚠️ GPL-3.0 | Simula comunicación **SCADA y RTU** sobre IEC 60870-5-104 para investigar comportamiento TIC en red. Fraunhofer FIT | 106 | 30 | 2026-11-10 | EMEA |
| [Gurux/Gurux.DLMS.Python](https://github.com/Gurux/Gurux.DLMS.Python) | ⚠️ GPL-2.0 | Pila **DLMS/COSEM**: el estándar de lectura de medidor inteligente en Europa y buena parte de LATAM | 125 | 94 | 2026-11-19 | EMEA |
| [bemasher/rtlamr](https://github.com/bemasher/rtlamr) | ⚠️ AGPL-3.0 | Receptor rtl-sdr para medidores Itron ERT en banda ISM 900 MHz: lectura de medidor **por radio**, sin integración con la utility. 2559 ★ | 2559 | 283 | 2026-11-18 | North America |
| [mitre/caldera-ot](https://github.com/mitre/caldera-ot) | **Apache-2.0** | Plugins OT para MITRE Caldera: emulación de adversario sobre protocolos industriales. La contraparte defensiva obligatoria de todo lo anterior | 265 | 34 | 2026-11-20 | North America |

⚠️ **Aviso de licencia que decide el uso**: sólo `ProtoForge` (MIT) y `caldera-ot` (Apache-2.0) son
empotrables. `Gurux` es **GPL-2.0** y `rtlamr` **AGPL-3.0** — útiles como herramienta de laboratorio
o proceso aislado, nunca enlazados en el producto del cliente. `Gurux` tiene 94 forks sobre 125 ★
(relación 0.75, la más alta de esta KB): señal de que se usa como base de integraciones, no de que
se lea.

**`caldera-ot` no está aquí por completismo.** Cualquier propuesta que ponga un agente a leer o
escribir en protocolo industrial recibirá la pregunta de seguridad en la primera revisión. Tener
nombrada la herramienta de emulación de adversario del MITRE, Apache-2.0, convierte esa pregunta en
una línea del plan de pruebas.

## Dinámica, EMT y co-simulación (añadidos del cuarto pase)

| Repo | Licencia | Descripción | Stars | Forks | Último push | Región origen |
|------|----------|-------------|-------|-------|-------------|---------------|
| [JuliaEnergy/PowerDynamics.jl](https://github.com/JuliaEnergy/PowerDynamics.jl) | **MIT** (leída del `LICENSE`) | Modelado **dinámico** de redes en Julia: estabilidad, transitorios electromecánicos | 141 | 40 | 2026-11-18 | EMEA |
| [Future-Power-Networks/Simplus-Grid-Tool](https://github.com/Future-Power-Networks/Simplus-Grid-Tool) | **BSD-3-Clause** | Análisis de estabilidad de redes con alta penetración de electrónica de potencia (impedancia, modos) | 148 | 64 | 2026-11-10 | EMEA |
| [lbl-srg/modelica-buildings](https://github.com/lbl-srg/modelica-buildings) | **BSD-3-Clause** (vía `Buildings/legal.html`) | Librería Modelica de edificios de LBNL: HVAC, envolvente, plantas térmicas, districts | 363 | 193 | 2026-11-20 | North America |
| [PowerGridModel/power-grid-model-ds](https://github.com/PowerGridModel/power-grid-model-ds) | MPL-2.0 | Toolkit de data science sobre `power-grid-model` (Alliander): el puente de la ingeniería a pandas | 34 | 20 | 2026-11-19 | EMEA |
| [rtc-tools/rtc-tools](https://github.com/rtc-tools/rtc-tools) | ⚠️ LGPL-3.0 | Framework de modelado, simulación y **optimización de sistemas dinámicos** (origen en gestión hídrica, aplicable a hidro y térmica) | 31 | 25 | 2026-11-19 | EMEA |
| [sandialabs/quest_planning](https://github.com/sandialabs/quest_planning) | **BSD** (Sandia) | Expansión de capacidad a largo plazo: mezcla de recursos coste-óptima. Sandia National Laboratories | 21 | 3 | 2026-11-19 | North America |
| [DrafProject/draf](https://github.com/DrafProject/draf) | **MIT** | *Demand Response Analysis Framework*: evalúa el valor de la flexibilidad industrial | 29 | 6 | 2026-06-10 | EMEA |

## Upstream de O&G: ampliación del cuarto pase

El tercer pase concluyó que el subsector es "100 % GPL-3.0". **Eso era un artefacto de la muestra.**
Hay piezas MIT y BSD de primer nivel:

| Repo | Licencia | Descripción | Stars | Forks | Último push | Región origen |
|------|----------|-------------|-------|-------|-------------|---------------|
| [sintefmath/JutulDarcy.jl](https://github.com/sintefmath/JutulDarcy.jl) | **MIT** | Simulación de yacimientos en Julia: flujo de Darcy multifásico y multicomponente. **La alternativa permisiva a OPM Flow** | 170 | 46 | 2026-11-19 | EMEA (Noruega) |
| [OPM/ResInsight](https://github.com/OPM/ResInsight) | ⚠️ GPL-3.0 | Visor 3D y post-proceso de modelos de yacimiento. 808 issues abiertas = producto real en uso | 222 | 106 | 2026-11-19 | EMEA |
| [SINTEF-AppliedCompSci/MRST](https://github.com/SINTEF-AppliedCompSci/MRST) | ⚠️ GPL-3.0 | *MATLAB Reservoir Simulation Toolbox*: la referencia académica del sector | 147 | 54 | 2026-11-03 | EMEA (Noruega) |
| [equinor/ecalc](https://github.com/equinor/ecalc) | ⚠️ GPL (leída del `LICENSE`) | Cálculo de **demanda energética y emisiones de GEI** de producción de petróleo y gas. Herramienta de Equinor | 54 | 10 | 2026-11-19 | EMEA (Noruega) |
| [equinor/xtgeo](https://github.com/equinor/xtgeo) | ⚠️ LGPL-3.0 | Librería Python de superficies, cubos, pozos y grids de subsuelo | 123 | 71 | 2026-11-19 | EMEA (Noruega) |
| [equinor/resdata](https://github.com/equinor/resdata) | ⚠️ GPL-3.0 | Lectura/escritura de resultados del simulador Eclipse | 129 | 104 | 2026-11-19 | EMEA (Noruega) |
| [GeoBrain-Project/GeoBrain](https://github.com/GeoBrain-Project/GeoBrain) | **Apache-2.0** | Plataforma **diferenciable de extremo a extremo** para modelado integrado de subsuelo: permite meter ML dentro del lazo físico | 88 | 10 | 2026-08-20 | APAC |
| [douyimin/CIG-bench](https://github.com/douyimin/CIG-bench) | **MIT** | Survey y benchmark de interpretación de imagen de subsuelo con IA | 66 | 11 | 2026-06-18 | APAC |

**Corrección de la tesis del tercer pase**: `JutulDarcy.jl` (MIT) y `GeoBrain` (Apache-2.0) rompen la
conclusión de que en O&G hay que aceptar GPL. Para un encargo nuevo de simulación de yacimiento con
capa de IA, `JutulDarcy.jl` es el punto de partida que **sí** se puede empotrar. `GeoBrain` además es
diferenciable, que es la propiedad que permite acoplar un modelo aprendido al simulador físico en vez
de ponerlo al lado.

## Recurso meteorológico: la dependencia que todo forecasting arrastra

| Repo | Licencia | Descripción | Stars | Forks | Último push | Región origen |
|------|----------|-------------|-------|-------|-------------|---------------|
| [open-meteo/open-meteo](https://github.com/open-meteo/open-meteo) | ⚠️ **AGPL-3.0** | API de pronóstico meteorológico abierta, auto-hospedable. 6704 ★: el repo con más tracción de este pase | 6704 | 485 | 2026-11-19 | EMEA |

⚠️ **Dos trampas en una fila.** (1) Es **AGPL-3.0**: auto-hospedarla dentro de un SaaS de cliente
activa la cláusula de red. (2) El servicio público es *"free for non-commercial use"* — un piloto que
pega a `api.open-meteo.com` y luego pasa a producción comercial cambia de régimen de licencia sin que
nadie lo note. Decidir desde el día uno: plan comercial de Open-Meteo, o proveedor meteorológico del
cliente, o aceptar AGPL. Es la clase de detalle que aparece en la auditoría, no en el piloto.

## Acceso a datos de mercado y de red: la capa que faltaba (quinto pase, 2026-11-20)

Cuatro pases construyeron capacidad de **simular** mercados y **ninguna** de leerlos. Estas son las
librerías canónicas del sector para bajar precio, carga, generación y flujos reales del operador.
Son el primer día de cualquier encargo.

| Repo | Licencia | Descripción | Stars | Forks | Último push | Región origen |
|------|----------|-------------|-------|-------|-------------|---------------|
| [fboerman/entsoe-py](https://github.com/fboerman/entsoe-py) | **MIT** | Cliente Python de la API de ENTSO-E: precios, generación, carga y flujos transfronterizos de toda Europa. Creado 2017, 11 issues abiertas | 745 | 270 | 2026-11-17 | EMEA |
| [gridstatus/gridstatus](https://github.com/gridstatus/gridstatus) | **BSD-3-Clause** | Extrae datos de los siete ISO/RTO estadounidenses (CAISO, ERCOT, PJM, MISO, SPP, NYISO, ISO-NE) con una sola interfaz | 456 | 89 | 2026-11-18 | North America |
| [PyPSA/powerplantmatching](https://github.com/PyPSA/powerplantmatching) | **MIT** (SPDX en README) | Reconcilia varias bases de datos de centrales eléctricas en un registro único y deduplicado | 235 | 77 | 2026-11-19 | EMEA |
| [singularity-energy/open-grid-emissions](https://github.com/singularity-energy/open-grid-emissions) | **MIT** | Generación y emisiones **horarias** de la red de EE. UU.; 97 issues abiertas sobre 96 ★ = proyecto trabajado | 96 | 7 | 2026-11-19 | North America |
| [gridstatus/gridstatusio](https://github.com/gridstatus/gridstatusio) | **BSD-3-Clause** | Cliente de la API alojada de GridStatus.io (misma familia, servicio gestionado) | 58 | 5 | 2026-11-16 | North America |
| [entsoe/application-profiles-library](https://github.com/entsoe/application-profiles-library) | **Apache-2.0** | Artefactos RDFS/SHACL **oficiales** de CGMES y perfiles CIM. Cuenta institucional `entsoe` | 29 | 9 | 2026-10-28 | EMEA |
| [entsoe/ReliCapGrid](https://github.com/entsoe/ReliCapGrid) | NOASSERTION | Modelos de prueba CGMES y perfiles CIM de códigos de red; útil para validar integraciones | 21 | 6 | 2026-11-18 | EMEA |
| [jo20ow/Obsyd](https://github.com/jo20ow/Obsyd) | **AGPL-3.0** | "GridStatus para Europa": 37 zonas de oferta, precios *day-ahead* a 15 minutos. Nuevo (creado 2026-03-04) | 12 | 1 | 2026-11-11 | EMEA |

**Cómo encaja con lo que ya había.** `gridstatus` → `open-grid-emissions` → `carbon-aware-sdk` (ya en
la KB) cierra la cadena *dato de red → emisión horaria → decisión de carga* enteramente en MIT/BSD
para North America. En EMEA el equivalente es `entsoe-py` → `openstef`, y la pieza de emisiones
horarias **no tiene equivalente abierto**: es un gap medido, no una omisión.

**Advertencia sobre `Obsyd`:** es lo más parecido a un "GridStatus europeo" y es **AGPL-3.0**. En un
SaaS de cliente obliga a liberar el servicio. Para EMEA, la ruta permisiva es `entsoe-py` (MIT).

## Plataformas de planificación y tecno-economía de laboratorio nacional (quinto pase)

La KB tenía los modelos académicos de expansión de capacidad; faltaban las plataformas que la
industria y los laboratorios usan de verdad.

| Repo | Licencia | Descripción | Stars | Forks | Último push | Región origen |
|------|----------|-------------|-------|-------|-------------|---------------|
| [NatLabRockies/ROSCO](https://github.com/NatLabRockies/ROSCO) | **Apache-2.0** | Controlador de referencia de aerogenerador; la capa de control que faltaba sobre `openfast` y `floris`. 125 forks sobre 182 ★ | 182 | 125 | 2026-09-29 | Global |
| [NatLabRockies/ReEDS-2.0](https://github.com/NatLabRockies/ReEDS-2.0) | **BSD-3-Clause** | Modelo de expansión de capacidad del sistema eléctrico de EE. UU. a escala nacional | 176 | 79 | 2026-04-22 | North America |
| [grid-parity-exchange/Egret](https://github.com/grid-parity-exchange/Egret) | **BSD-3-Clause** (leída en crudo; la API dice `NOASSERTION`) | Bloques de construcción para problemas de optimización de sistemas de potencia (unit commitment, OPF) | 173 | 72 | 2026-11-08 | North America |
| [NatLabRockies/pysam](https://github.com/NatLabRockies/pysam) | **BSD-3-Clause** | Envoltorio Python del System Advisor Model: modelo técnico **y** financiero de proyecto | 157 | 87 | 2026-09-27 | Global |
| [sylvan-energy/gridpath](https://github.com/sylvan-energy/gridpath) | **Apache-2.0** | Plataforma que resuelve planificación **y** operación en un mismo modelo; 58 issues abiertas | 138 | 71 | 2026-11-19 | Global |
| [NatLabRockies/REopt_API](https://github.com/NatLabRockies/REopt_API) | BSD-3 + **cláusula de marca REopt®** | Dimensionado óptimo de DER en un emplazamiento (solar + BESS + genset + tarifa). Motor de reopt.nrel.gov | 128 | 70 | 2026-11-17 | North America |
| [NatLabRockies/BuildingsBench](https://github.com/NatLabRockies/BuildingsBench) | **BSD-3-Clause** | Preentrenamiento a gran escala y *benchmark* de previsión de carga a corto plazo | 123 | 24 | 2026-02-25 | North America |
| [NatLabRockies/ParaEMT_public](https://github.com/NatLabRockies/ParaEMT_public) | **BSD-3-Clause** | Simulación de transitorios electromagnéticos paralelizada; complementa `dpsim` | 113 | 54 | 2026-01-15 | North America |
| [NatLabRockies/bifacial_radiance](https://github.com/NatLabRockies/bifacial_radiance) | **BSD-3-Clause** | Trazado de rayos para fotovoltaica bifacial; 85 issues abiertas | 111 | 56 | 2026-09-25 | Global |
| [OpenSynth-energy/OpenSynth](https://github.com/OpenSynth-energy/OpenSynth) | **Apache-2.0** | Modelos generadores de **datos sintéticos** de consumo de contador (cohorte LF Energy) | 77 | 12 | 2026-10-12 | EMEA |
| [NatLabRockies/GEOPHIRES-X](https://github.com/NatLabRockies/GEOPHIRES-X) | **MIT** | Simulador técnico-económico **geotérmico**: reservorio, pozo y planta de superficie | 67 | 49 | 2026-11-19 | Global |
| [NatLabRockies/HOPP](https://github.com/NatLabRockies/HOPP) | **BSD-3-Clause** | Plantas híbridas: renovable + almacenamiento + hidrógeno. **66 forks sobre 41 ★** | 41 | 66 | 2026-04-10 | North America |

**`OpenSynth` merece atención aparte.** La inteligencia de mercado de este pase registra que el
informe de la Comisión Europea sobre IA en redes inteligentes señala **GDPR y preprocesado** como
barreras para entrenar modelos. `OpenSynth` publica generadores de perfiles de consumo sintéticos:
datos de contador que no pertenecen a ningún consumidor. Va **antes** de `openstef` o
`BuildingsBench` en el pipeline de un cliente europeo que no puede exportar datos de medición.

## Edificios: el SDK que faltaba bajo EnergyPlus (quinto pase)

| Repo | Licencia | Descripción | Stars | Forks | Último push | Región origen |
|------|----------|-------------|-------|-------|-------------|---------------|
| [NatLabRockies/OpenStudio](https://github.com/NatLabRockies/OpenStudio) | BSD-3 + **marca OpenStudio®** | SDK y colección de herramientas para modelado energético de edificio completo sobre EnergyPlus; 281 issues | 660 | 241 | 2026-11-17 | Global |
| [NatLabRockies/resstock](https://github.com/NatLabRockies/resstock) | **Licencia propia: BSD-3 + copyleft condicionado al tipo de redistribuidor + marca ResStock™** | Modelado granular del **parque residencial** a escala nacional, regional y local, sobre OpenStudio | 147 | 85 | 2026-11-19 | North America |

⚠️ **`resstock` tiene la cláusula más peligrosa catalogada en esta KB.** Ver `compose/patterns.md`.

## Hidrógeno y pila de combustible: delgado, pero permisivo (quinto pase)

Categoría buscada explícitamente y medida. El término `hydrogen` **no sirve en GitHub** (lo copan
`Shopify/hydrogen`, `nteract/hydrogen` y una caja de ritmos). Buscando por `electrolyzer` y por
organización, lo utilizable es:

| Repo | Licencia | Descripción | Stars | Forks | Último push | Región origen |
|------|----------|-------------|-------|-------|-------------|---------------|
| [gassraphael/AlphaPEM](https://github.com/gassraphael/AlphaPEM) | **BSD-3-Clause** | Simulación de sistemas de pila de combustible PEMFC | 49 | 15 | 2026-11-18 | EMEA |
| [NatLabRockies/electrolyzer](https://github.com/NatLabRockies/electrolyzer) | **Apache-2.0** (rescatada del crudo; la API dice `NOASSERTION`) | Modelo de electrolizador; 31 issues abiertas | 35 | 28 | 2026-08-12 | North America |

Más `NatLabRockies/HOPP` (BSD-3, arriba) para el dimensionado del conjunto y `e2nIEE/pandapipes` (ya
en la KB) para la red de gas/H₂. **Todo lo demás encontrado son modelos académicos de 2 a 25 ★ sin
archivo de licencia.** Hay base para un estudio; no hay ecosistema.

## Geotermia: un solo repo usable (quinto pase)

`GEOPHIRES-X` (**MIT**, 67 ★, tabla de arriba) es el único activo y permisivo. Registrado para que no
se vuelva a buscar:

- `NatLabRockies/GEOPHIRES-v2` — **GPL-3.0**, 48 ★, sin push desde 2023-10-31. *Mismo simulador,
  licencia distinta según la versión*: usar siempre la X.
- `ICWallis/geothermal-cookbook` — Apache-2.0, 27 ★, sin push desde 2022-10-25.
- `SmartTensors/GeoThermalCloud.jl` — **GPL-3.0**, 36 ★.

## Modelos de sistema eléctrico de origen LATAM: el gap que el quinto pase mandó cerrar, cerrado (sexto pase, 2026-11-20)

El quinto pase terminó `intel/market.md` con una instrucción concreta: *"buscar `PyPSA-CL`, `PyPSA-MX`
y `PyPSA-BR` por nombre"*. **Se hizo, y existen.** Hay cuatro modelos nacionales de sistema eléctrico
latinoamericano construidos sobre PyPSA, y **tres son MIT**.

Esto cambia el enunciado que cinco pases arrastraron. La afirmación correcta a partir de hoy no es
"LATAM no produce repos energéticos", ni la versión matizada "sólo Brasil, y de un solo
desarrollador". Es: **existen modelos de despacho y planificación de Chile y México, con licencia
permisiva, construidos sobre datos públicos de los operadores nacionales.**

| Repo | Licencia | Descripción | ★ | Forks | Último push | Región |
|------|----------|-------------|---|-------|-------------|--------|
| [paredes-vergara/PyPSA-CL](https://github.com/paredes-vergara/PyPSA-CL) | **MIT** | Planificación de inversión a largo plazo, *unit commitment* y despacho económico del **Sistema Eléctrico Nacional de Chile**. Datos públicos del Coordinador Eléctrico Nacional, la CNE y el Ministerio de Energía | 15 | 2 | 2026-07-27 | LATAM |
| [sanjaygrr/pypsa-chile](https://github.com/sanjaygrr/pypsa-chile) | **MIT** | Modelo abierto de despacho del **SEN chileno** con datos públicos. Recién activo: push 2026-11-16 | 0 | 1 | 2026-11-16 | LATAM |
| [BrandolRuizOlmeda/pypsa-mexico_base](https://github.com/BrandolRuizOlmeda/pypsa-mexico_base) | **MIT** | PyPSA aplicado al **Mercado Eléctrico Mayorista** de México. ⚠️ la licencia está en la rama `master`, no en `main` | 0 | 0 | 2026-04-07 | LATAM |
| [leonardovbonatto/pypsa-meets-brazil](https://github.com/leonardovbonatto/pypsa-meets-brazil) | ❌ **sin licencia** | Modelo nodal abierto del **SIN brasileño** con física de hidráulica y valores de agua estocásticos. Técnicamente el más interesante de los cuatro, y **no se puede usar** | 0 | 0 | 2026-11-06 | LATAM |

**Cómo hay que presentarlo, sin inflarlo.** Entre 0 y 15 ★. No son productos ni comunidades: son
**modelos de red nacional ya parametrizados con datos del operador**, que es exactamente el trabajo
caro de las primeras semanas de un encargo de planificación. El valor no es el código: es que la
topología, las centrales y las series del Coordinador chileno o del MEM mexicano ya están mapeadas a
un formato que `linopy` resuelve y que esta KB ya sabe conectar a una capa agéntica.

**El caso brasileño repite el patrón más caro de esta KB.** `pypsa-meets-brazil` modela el SIN con
física de hidráulica —el problema difícil y específico de Brasil, donde el agua embalsada es la
batería del sistema— y **no tiene archivo de licencia en `main` ni en `master`**. Sin concesión
expresa es copyright exclusivo del autor: no empotrable en un entregable. Es el mismo final que
`douyimin/GEM` en el cuarto pase. Acción barata y concreta: abrir issue pidiendo licencia explícita.

**Consecuencia de método, y es la lección general del pase.** Los cinco pases anteriores buscaron
LATAM por **dominio** (`eléctrico`, `CENACE`, `coordinador electrico`, `XM`, `energia`) y por
**institución**, y midieron cero. La consulta que funcionó fue el **nombre del framework** —`pypsa` —
con el sufijo de país. El gap no era de oferta: era del vocabulario de búsqueda, otra vez. Para el
próximo pase, la generalización vale la pena probarla en el resto: `calliope-`, `temoa-`, `osemosys-`
y `pypsa-` + país, en las cuatro regiones.

## Interoperabilidad CIM / CGMES: la tubería que la red europea ya habla (séptimo pase, 2026-11-20)

Esta KB tenía el motor (`powsybl-core`) y los perfiles (`entsoe/application-profiles-library`), y no
tenía las piezas que convierten el modelo de red europeo en algo programable. Importa **ahora** porque
la hoja de ruta de la Comisión Europea (COM/2026/501, 3 de junio de 2026) financia foundation models
de gestión y planificación de red con **30 M€ en 2026 y 20 M€ en 2027**, y el formato de entrada de
esos modelos es CGMES. Quien controla la tubería de datos entra en el proyecto.

| Repo | Licencia | ★ / forks | Último push | Rol |
|------|----------|-----------|-------------|-----|
| [powsybl/powsybl-diagram](https://github.com/powsybl/powsybl-diagram) | MPL-2.0 | 136 / 32 | 2026-11-19 | Unifilares de subestación y grafos de red en SVG |
| [powsybl/pypowsybl](https://github.com/powsybl/pypowsybl) | MPL-2.0 | 106 / 35 | 2026-11-19 | Enlace Python↔PowSyBl vía imagen nativa GraalVM |
| [eliagroup/ToOp](https://github.com/eliagroup/ToOp) | MPL-2.0 | 76 / 24 | 2026-11-19 | Motor de optimización de **topología** del Elia Group: DC load flow en GPU, optimización DC, validación AC |
| [eigenergy/powerio](https://github.com/eigenergy/powerio) | Apache-2.0 | 39 / 8 | 2026-11-20 | *"Power system compiler infrastructure"*: capa de E/S entre formatos |
| [PNNL-CIM-Tools/CIM-Graph](https://github.com/PNNL-CIM-Tools/CIM-Graph) | BSD-3-Clause | 31 / 17 | 2026-11-17 | CIM como grafo de propiedades etiquetado en memoria (PNNL) |
| [SOPTIM/RDFArchitect](https://github.com/SOPTIM/RDFArchitect) | Apache-2.0 | 30 / 6 | 2026-11-20 | Editor web de esquemas RDFS con extensiones CIM |
| [sogno-platform/libcimpp](https://github.com/sogno-platform/libcimpp) | Apache-2.0 | 27 / 19 | 2026-10-30 | Import/export CGMES / CIM IEC-61970 en XML/RDF, C++ |
| [sogno-platform/cimgen](https://github.com/sogno-platform/cimgen) | Apache-2.0 | 25 / 11 | 2026-11-16 | Generación de código desde el modelo CIM a varios lenguajes |
| [alliander-opensource/pycgmes](https://github.com/alliander-opensource/pycgmes) | Apache-2.0 | 19 / 4 | 2026-11-19 | Dataclasses CGMES 3 + descripción RDFS + ficheros SHACL (DSO Alliander) |
| [Welthulk/Sparlectra.jl](https://github.com/Welthulk/Sparlectra.jl) | Apache-2.0 | 17 / 5 | 2026-11-12 | Flujo AC, cortocircuito IEC 60909, contingencia N-1 y N-2, estimación de estado WLS |
| [SOPTIM/OpenCGMES](https://github.com/SOPTIM/OpenCGMES) | Apache-2.0 | 9 / 6 | 2026-11-20 | Suite de herramientas CGMES / CIM: RDFS, SHACL, CIMXML |

**Lectura de licencia de este bloque: es el más limpio de toda la KB.** Nueve de once son Apache-2.0,
BSD-3 o MPL-2.0 — ninguno copyleft fuerte. Es la capa donde Globant puede construir producto sin
condiciones. Nótese el patrón de autoría: **Elia Group (TSO belga), Alliander (DSO neerlandés),
Statnett (TSO noruego), PNNL y SOPTIM** — el trend T2 de esta KB ("los operadores de red se volvieron
proveedores de open source") se confirma por séptimo pase con cinco autores institucionales nuevos.

## Carga de vehículo eléctrico: el stack completo, y la categoría más grande que la KB tenía a medias (séptimo pase)

El trend T7 afirma desde el pase 2 que la movilidad eléctrica concentra la masa crítica real de la
comunidad. La KB sostenía esa afirmación con cuatro repos. Buscando por **protocolo** (`OCPP`, `OCPI`)
aparecen once más, y juntos forman un stack probable de punta a punta: CSMS, firmware de estación,
emulador, simulador de carga y roaming entre operadores.

| Repo | Licencia | ★ / forks | Último push | Capa |
|------|----------|-----------|-------------|------|
| [ocpi/ocpi](https://github.com/ocpi/ocpi) | ⚠️ NOASSERTION | 602 / 230 | 2026-09-07 | Especificación de **roaming** entre operadores de carga (OCPI) |
| [lbbrhzn/ocpp](https://github.com/lbbrhzn/ocpp) | MIT | 415 / 177 | 2026-11-18 | Integración Home Assistant para cargadores OCPP |
| [citrineos/citrineos-core](https://github.com/citrineos/citrineos-core) | Apache-2.0 | 309 / 175 | 2026-11-18 | **CSMS OCPP 2.0.1** permisivo |
| [dallmann-consulting/OCPP.Core](https://github.com/dallmann-consulting/OCPP.Core) | ⚠️ GPL-3.0 | 304 / 126 | 2026-11-15 | Servidor OCPP + UI de gestión en .NET Core |
| [EVerest/EVerest](https://github.com/EVerest/EVerest) | Apache-2.0 | 298 / 215 | 2026-11-20 | Stack de software de carga completo — proyecto **LF Energy** |
| [SAP/e-mobility-charging-stations-simulator](https://github.com/SAP/e-mobility-charging-stations-simulator) | Apache-2.0 | 231 / 102 | 2026-11-19 | Simulador de estaciones OCPP-J a escala (autoría SAP) |
| [monta-app/ocpp-emulator](https://github.com/monta-app/ocpp-emulator) | Apache-2.0 | 182 / 29 | 2026-11-20 | Emulador de punto de carga, Kotlin Multiplatform + Compose |
| [juherr/awesome-ev-charging](https://github.com/juherr/awesome-ev-charging) | CC0-1.0 | 185 / 29 | 2026-11-19 | Índice curado de la categoría |
| [tommymalmqvist/rust-ocpp](https://github.com/tommymalmqvist/rust-ocpp) | Apache-2.0 | 106 / 35 | 2026-11-03 | Librerías OCPP 1.6 / 2.0.1 / **2.1** — la única con 2.1 |
| [ChargeLab/OpenOCPP](https://github.com/ChargeLab/OpenOCPP) | Apache-2.0 | 92 / 47 | 2026-11-06 | Firmware embarcado OCPP 1.6/2.0.1 para estaciones |
| [shiv3/ocpp-cp-simulator](https://github.com/shiv3/ocpp-cp-simulator) | Apache-2.0 | 48 / 22 | 2026-11-18 | Simulador de punto de carga **declarado para pruebas de agentes AI** |

⚠️ **Dos trampas en esta tabla.** `ocpi/ocpi` tiene 602 ★ y licencia **no resuelta** por la API: es la
especificación de roaming de referencia, pero no se puede asumir permisiva — leer el repositorio antes
de incorporarla. `OCPP.Core` es **GPL-3.0**: útil como referencia y como herramienta interna, no
integrable en un producto cerrado. El camino permisivo completo existe sin ninguno de los dos:
`citrineos-core` (CSMS) + `EVerest` (stack) + `rust-ocpp` (protocolo) + `SAP/...simulator` (carga).

## Forecasting con foundation models de series temporales (séptimo pase)

| Repo | Licencia | ★ / forks | Último push | Rol |
|------|----------|-----------|-------------|-----|
| [amazon-science/chronos-forecasting](https://github.com/amazon-science/chronos-forecasting) | Apache-2.0 | 6328 / 774 | 2026-10-05 | Modelos fundacionales pre-entrenados de series temporales; sustrato zero-shot |
| [openclimatefix/open-source-quartz-solar-forecast](https://github.com/openclimatefix/open-source-quartz-solar-forecast) | MIT | 162 / 117 | 2026-09-06 | Pronóstico solar a nivel de **sitio** (Open Climate Fix) |
| [williamhobbs/hefty](https://github.com/williamhobbs/hefty) | BSD-3-Clause | 85 / 13 | 2026-11-13 | Forecasting de corto plazo solar, viento y carga: la línea base |
| [arnaud-vs/open-predico](https://github.com/arnaud-vs/open-predico) | Apache-2.0 | 54 / 4 | 2026-11-15 | Forecasting energético sobre TSFM |
| [carbonfirst/CarbonCast](https://github.com/carbonfirst/CarbonCast) | Apache-2.0 | 49 / 22 | 2026-10-09 | Predicción de **intensidad de carbono horaria** por red, con ML |
| [bluehands/Carbon-Aware-Computing](https://github.com/bluehands/Carbon-Aware-Computing) | MIT | 47 / 7 | 2026-11-02 | Ejecuta tareas en el momento de mínima intensidad de carbono |

`CarbonCast` cierra un hueco concreto: la KB tenía `carbon-aware-sdk` (consumo de señal) y
`open-grid-emissions` (histórico), y no tenía **predicción** de intensidad horaria — la pieza que
vuelve verificable un compromiso de PPA 24/7.

## Modelos de sistema energético multi-sector y electroquímica (séptimo pase)

| Repo | Licencia | ★ / forks | Último push | Nota |
|------|----------|-----------|-------------|------|
| [PyPSA/pypsa-eur](https://github.com/PyPSA/pypsa-eur) | ⚠️ sin licencia única (ver nota del pase 6) | 640 / 494 | 2026-11-20 | Modelo sectorialmente acoplado del sistema energético europeo. **494 forks**: el más reutilizado del bloque |
| [FZJ-IEK3-VSA/FINE](https://github.com/FZJ-IEK3-VSA/FINE) | ⚠️ NOASSERTION | 102 / 46 | 2026-11-19 | ETHOS.FINE: modelado, optimización y evaluación de sistemas energéticos (Jülich) |
| [openFuelCell2/openFuelCell2](https://github.com/openFuelCell2/openFuelCell2) | ⚠️ GPL-3.0 | 64 / 30 | 2026-10-20 | CFD de pilas de combustible y dispositivos electroquímicos |
| [BattMoTeam/BattMo](https://github.com/BattMoTeam/BattMo) | ⚠️ GPL-3.0 | 62 / 22 | 2026-11-19 | Modelado continuo de dispositivos electroquímicos |
| [macroenergy/MacroEnergy.jl](https://github.com/macroenergy/MacroEnergy.jl) | **MIT** | 57 / 46 | 2026-11-10 | Optimización de diseño y operación de sistemas energéticos **multi-sector** |
| [IIT-EnergySystemModels/openTEPES](https://github.com/IIT-EnergySystemModels/openTEPES) | ⚠️ AGPL-3.0 | 57 / 29 | 2026-11-19 | Planificación de operación y expansión de generación, almacenamiento y transmisión |
| [FZJ-IEK3-VSA/HiSim](https://github.com/FZJ-IEK3-VSA/HiSim) | MIT | 46 / — | 2026-11-19 | Simulador de infraestructura de vivienda |

**`MacroEnergy.jl` es el hallazgo accionable de este bloque:** multi-sector **y MIT**. Frente a
`GenX.jl` (GPL-2.0) y `openTEPES` (AGPL-3.0), es el único de su clase sobre el que se puede construir
producto. 46 forks sobre 57 ★ es una proporción alta: se está usando, no sólo mirando.

## Campo, gemelo digital y protocolo de subestación: añadidos del séptimo pase

| Repo | Licencia | ★ / forks | Último push | Rol |
|------|----------|-----------|-------------|-----|
| [thingsboard/thingsboard-gateway](https://github.com/thingsboard/thingsboard-gateway) | Apache-2.0 | 2204 / 1008 | 2026-11-19 | Gateway IoT multiprotocolo. **El repo con más tracción de todo este pase** |
| [eclipse-ditto/ditto](https://github.com/eclipse-ditto/ditto) | EPL-2.0 | 953 / 297 | 2026-11-19 | Framework de **gemelo digital** de Eclipse IoT |
| [Orange-Cyberdefense/awesome-industrial-protocols](https://github.com/Orange-Cyberdefense/awesome-industrial-protocols) | CC0-1.0 | 783 / 122 | 2026-10-20 | Índice de protocolos industriales orientado a seguridad |
| [wendy512/iec61850](https://github.com/wendy512/iec61850) | ⚠️ GPL-3.0 | 182 / 54 | 2026-09-25 | Librería **IEC 61850** en Go |
| [syzygyhack/open-foundry](https://github.com/syzygyhack/open-foundry) | Apache-2.0 | 137 / 40 | 2026-11-15 | Plataforma de **ontología** para gemelos digitales operativos |
| [VILLASframework/node](https://github.com/VILLASframework/node) | Apache-2.0 | 22 / 23 | 2026-11-02 | Gateway multiprotocolo en tiempo real para co-simulación |
| [mzaniolo/iec61850](https://github.com/mzaniolo/iec61850) | **MIT** | 15 / 2 | 2026-09-01 | IEC 61850 en Rust. Diminuto, pero la **única MIT** de la familia 61850 en siete pases |
| [open-energy-transition/Awesome-Electrical-Grid-Mapping](https://github.com/open-energy-transition/Awesome-Electrical-Grid-Mapping) | CC0-1.0 | 171 / 22 | 2026-11-17 | Mapas y datasets de redes eléctricas del mundo |

## Repos de origen APAC: el bloque que faltaba (séptimo pase)

El término que abre APAC no es "APAC": es el nombre de su norma de conexión (**CSIP-AUS**,
**IEEE 2030.5**) y de su mercado (**NEM**).

| Repo | Licencia | ★ / forks | Último push | Rol |
|------|----------|-----------|-------------|-----|
| [longzheng/open-dynamic-export](https://github.com/longzheng/open-dynamic-export) | **MIT** | 57 / 16 | 2026-11-17 | Control dinámico de exportación y curtailment de inversores bajo **CSIP-AUS / SEP2 / IEEE 2030.5** |
| [bje-/NEMO](https://github.com/bje-/NEMO) | ⚠️ GPL-3.0 | 55 / 19 | 2026-10-02 | Optimizador del National Electricity Market australiano |
| [UNSW-CEEM/NEMSEER](https://github.com/UNSW-CEEM/NEMSEER) | ⚠️ GPL-3.0 | 39 / 9 | 2026-11-16 | Descarga y manejo de pronósticos del **AEMO** para el NEM (UNSW) |
| [ethanndickson/sep2_client](https://github.com/ethanndickson/sep2_client) | Apache-2.0 | 24 / 12 | 2026-09-21 | Cliente **IEEE 2030.5** en Rust (con `sep2_common`, Apache-2.0, 14 ★) |

`open-dynamic-export` es el accionable: **MIT** y atado al régimen de conexión obligatorio en
Australia. Los dos GPL-3.0 sirven como referencia de mercado y validación, no como base de producto.

## Marco de justificación de open source ante una utility regulada (séptimo pase)

| Repo | Licencia | Creado | Rol |
|------|----------|--------|-----|
| [lf-energy/lfe-oss-benefit-cost-framework](https://github.com/lf-energy/lfe-oss-benefit-cost-framework) | Apache-2.0 | 2026-09-08 | **Marco de coste-beneficio de open source para operadores de red**, de LF Energy |
| [lf-energy/lfenergy-landscape](https://github.com/lf-energy/lfenergy-landscape) | Apache-2.0 | — (45 ★) | Mapa vivo del ecosistema LF Energy |

Es nuevo y pequeño, y resuelve lo que ninguna de las 24 recetas anteriores resolvía: **cómo justificar
ante una utility regulada, con su regulador mirando, la adopción de open source en lugar de un
producto licenciado.** En una propuesta vale como anexo, no como dependencia técnica.

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
