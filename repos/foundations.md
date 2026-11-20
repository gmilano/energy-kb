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

## Open Energy Transition: la organización que sostiene la capa de datos de red abierta (octavo pase, 2026-11-20)

Esta KB tenía catalogado un repo de esta organización (`pypsa-mcp`) y la organización tiene alrededor
de treinta. Es la mayor adición de oferta de cualquier pase. Importa para una fundación —y no sólo
como *trending*— porque cubre la capa que estaba más vacía: **de dónde salen los datos de red**.
Todas las filas verificadas con `search/repositories` el 2026-11-20.

| Repo | Licencia | Descripción | ★ | Push | Región origen |
|------|----------|-------------|---|------|---------------|
| [open-energy-transition/grid2poster](https://github.com/open-energy-transition/grid2poster) | MIT | Renderiza la topología de la red eléctrica de un país a partir de datos abiertos | 272 | 2026-10-23 | EMEA |
| [open-energy-transition/Awesome-Electrical-Grid-Mapping](https://github.com/open-energy-transition/Awesome-Electrical-Grid-Mapping) | CC0-1.0 | Dataset curado de mapas y datasets de red eléctrica globales; dominio público | 171 | 2026-11-17 | EMEA |
| [open-energy-transition/MapYourGrid](https://github.com/open-energy-transition/MapYourGrid) | CC-BY-4.0 | Iniciativa y tooling para mapear la red eléctrica por país sobre OpenStreetMap | 103 | 2026-10-01 | EMEA |
| [open-energy-transition/earthpv](https://github.com/open-energy-transition/earthpv) | MIT | Mapeo de solar en tejado desde imagen satelital gratuita | 22 | 2026-11-20 | EMEA |
| [open-energy-transition/PyPSA-Explorer](https://github.com/open-energy-transition/PyPSA-Explorer) | MIT | Explorador interactivo de redes PyPSA | 18 | 2026-09-03 | EMEA |
| [open-energy-transition/osm-powerplants](https://github.com/open-energy-transition/osm-powerplants) | MIT | Extrae y procesa datos de centrales eléctricas desde OpenStreetMap | 11 | 2026-07-01 | EMEA |
| [open-energy-transition/pypsa-ppa](https://github.com/open-energy-transition/pypsa-ppa) | MIT | Toolkit PyPSA para simular y optimizar **PPAs** bajo distintos escenarios | 8 | 2026-11-09 | EMEA |
| [open-energy-transition/rooftopsenti](https://github.com/open-energy-transition/rooftopsenti) | MIT, ⚠️ **archivado** | Detecta solar en tejado con Sentinel-2 a escala país/estado/provincia | 7 | 2026-07-05 | EMEA |
| [open-energy-transition/openmod-features](https://github.com/open-energy-transition/openmod-features) | MIT | Inventario comparado de capacidades de las herramientas de modelado energético abierto | 6 | 2026-11-01 | EMEA |

⚠️ **Dentro de esta misma organización hay cuatro repos AGPL-3.0 y al menos tres sin licencia.** Son
`solver-benchmark` (78 ★), `demandcast` (47 ★), `geothermal-modelling` (6 ★) y
`efuels-supply-potentials` (4 ★) en AGPL-3.0; `Awesome-Grid-Model-Data` (80 ★), `pypsa-moon` (8 ★) y
`pypsa-training-sessions` (7 ★) sin archivo de licencia. **Una organización confiable no es una
licencia.** El caso que más muerde es `demandcast`: es exactamente la pieza que uno querría para un
producto de forecasting de demanda, y su AGPL-3.0 obliga a liberar el servicio derivado.

### Datos de utilities de EE. UU.: la capa que precede a toda la analítica

| Repo | Licencia | Descripción | ★ | Push | Región origen |
|------|----------|-------------|---|------|---------------|
| [catalyst-cooperative/pudl](https://github.com/catalyst-cooperative/pudl) | MIT | **Public Utility Data Liberation**: formularios de FERC, EIA y EPA limpiados y entregados como datos listos para análisis | 621 | 2026-11-20 | North America |
| [TextureHQ/commongrid](https://github.com/TextureHQ/commongrid) | ⚠️ **ODbL-1.0** | Registro abierto de la red eléctrica de EE. UU. (iniciativa de Texture) | 14 | 2026-11-19 | North America |

`pudl` (MIT, 621 ★, push del mismo día) es el repo de mayor tracción que esta KB no tenía. Es el
atajo que convierte los formularios regulatorios de EE. UU. en tablas analizables: **el trabajo sucio
que precede a cualquier analítica de cola de interconexión**.

⚠️ `commongrid` corrige una afirmación de pases anteriores —que no tenía repo de código localizable—
y confirma la advertencia de licencia desde el `LICENSE` crudo: *Open Data Commons Open Database
License (ODbL) v1.0, Copyright (c) 2025-2026 Texture, Inc.* Es licencia de **base de datos** con
obligación de compartir derivados de la base: **fuente sí, dataset empotrado en un entregable
cerrado no.**

## Ecosistema de los frameworks de planificación: OSeMOSYS, Temoa y Calliope (octavo pase, 2026-11-20)

La KB ya tenía los motores (`OSeMOSYS` Apache-2.0, `temoa` MIT, `calliope` Apache-2.0). Faltaba lo
que los hace usables: conversión de datos, interfaces y las instancias nacionales.

| Repo | Licencia | Descripción | ★ | Push | Región origen |
|------|----------|-------------|---|------|---------------|
| [OSeMOSYS/otoole](https://github.com/OSeMOSYS/otoole) | MIT | Conversión de datos de entrada/salida de OSeMOSYS. ⚠️ Sin push desde 2024-11-18 | 33 | 2024-11-18 | EMEA |
| [EAPD-DRB/MUIOGO](https://github.com/EAPD-DRB/MUIOGO) | Apache-2.0 | Interfaz de modelado para OG-Core y OSeMOSYS | 26 | 2026-10-31 | North America |
| [OSeMOSYS/MUIO](https://github.com/OSeMOSYS/MUIO) | Apache-2.0 | Interfaz de usuario de modelado de OSeMOSYS | 22 | 2026-10-01 | EMEA |
| [MAHTEP/TEMOA-Italy](https://github.com/MAHTEP/TEMOA-Italy) | **MIT** (código) + **CC-BY-4.0** (datos) | Modelo del sistema energético italiano 2006-2050. Politecnico di Torino, grupo MAHTEP | 13 | 2026-11-16 | EMEA |
| [MAHTEP/TEMOA-Europe](https://github.com/MAHTEP/TEMOA-Europe) | **MIT** (código) + **CC-BY-4.0** (datos) | Modelo europeo de región única con base de datos abierta hasta 2050 | 4 | 2026-10-25 | EMEA |
| [CANOE-main/canoe-electricity](https://github.com/CANOE-main/canoe-electricity) | MIT | Sector eléctrico canadiense para el modelo CANOE (datasets compatibles Temoa) | 3 | 2026-09-10 | North America |
| [CANOE-main/canoe-transportation](https://github.com/CANOE-main/canoe-transportation) | MIT | Sector transporte canadiense del modelo CANOE | 3 | 2026-11-18 | North America |
| [CANOE-main/canoe-industry](https://github.com/CANOE-main/canoe-industry) | MIT | Sector industrial canadiense del modelo CANOE | 2 | 2026-09-04 | North America |
| [calliope-project/ec_modules](https://github.com/calliope-project/ec_modules) | MIT, ⚠️ **archivado** | Módulos reutilizables de workflow para modelos Calliope | 4 | 2026-04-02 | EMEA |

⚠️ **Variantes del mismo ecosistema que NO son permisivas**, y conviene saberlo antes de elegir:
`transition-zero/tz-osemosys` (46 ★) y `OSeMOSYS/osemosys_global` (46 ★) son **AGPL-3.0**;
`NetZeroAtlantic/ACES-Temoa` es **GPL-2.0**. La ruta permisiva al modelado de expansión sigue siendo
`temoa` (MIT) / `calliope` (Apache-2.0) / `oemof-solph` (MIT), **con el coste de construir los datos
del país** — salvo en Italia, Europa y Canadá, donde MAHTEP y CANOE ya los publicaron bajo MIT.

### El quinto sitio donde buscar una licencia: un `LICENSE` que se parte por tipo de contenido

La regla de esta KB tenía cuatro lugares (`LICENSE*`, `COPYING`, el SPDX de `pyproject.toml`, un
`legal.html` dentro del árbol del paquete). `MAHTEP/TEMOA-Italy` añade el quinto: la API de GitHub
reporta `NOASSERTION` y el texto crudo dice *"TEMOA-Italy is released under two licenses, according
to the type of content"* — **CC-BY-4.0** para bases de datos (`*.sql`, `*.zip`), documentación y
figuras, y **MIT** para todo el código (`*.py`). Un gate automático de licencias lo habría
descartado, y es un modelo nacional europeo completo de una universidad politécnica.

**Regla operativa:** `NOASSERTION` en un **modelo energético nacional** casi siempre significa
licencia dual (datos vs. código), no ausencia de licencia. Leer el `LICENSE` crudo entero, no sus
primeras líneas: en TEMOA-Italy la parte MIT aparece **después** de la parte CC.

### Alemania: el único rescate institucional del barrido de normas de conexión

| Repo | Licencia | Descripción | ★ | Push | Región origen |
|------|----------|-------------|---|------|---------------|
| [KIT-IAI/PIDE](https://github.com/KIT-IAI/PIDE) | **MIT** (verificada en `LICENSE` crudo) | Simulación de integración de generación distribuida y control autónomo de potencia reactiva en redes de distribución (VDE-AR-N) | 5 | 2026-08-05 | EMEA |

Del Institute for Automation and Applied Informatics del Karlsruhe Institute of Technology. 5 ★ no es
tracción: vale como **referencia de método citable** en una propuesta alemana, no como dependencia.

## Fuentes de descubrimiento (para el próximo pase)

Catálogos curados que rinden más que cualquier búsqueda por buzzword:

| Repo | Licencia | Qué aporta | Stars |
|------|----------|-----------|-------|
| [protontypes/open-sustainable-technology](https://github.com/protontypes/open-sustainable-technology) | CC-BY-4.0 | Directorio y análisis del ecosistema open source en clima/energía/sostenibilidad | 2586 |
| [ps-wiki/best-of-ps](https://github.com/ps-wiki/best-of-ps) | CC-BY-SA-4.0 | Ranking semanal de librerías de análisis de sistemas de potencia | 297 |
| [open-energy-transition/Awesome-Electricity-Demand](https://github.com/open-energy-transition/Awesome-Electricity-Demand) | MIT | Recursos de demanda eléctrica horaria y sub-horaria | 74 |
| [zhgqcn/awesome-NILM-with-code](https://github.com/zhgqcn/awesome-NILM-with-code) | CC-BY-4.0 | Non-Intrusive Load Monitoring con código | 149 |
| [martymcenroe/best-of-pes-ai](https://github.com/martymcenroe/best-of-pes-ai) | CC-BY-SA-4.0 | Ranking de proyectos open source de IA/ML para los dominios de la IEEE Power & Energy Society; complementa `best-of-ps` con el eje de IA (añadido en el octavo pase) | 3 |
| [open-energy-transition/Awesome-Grid-Model-Data](https://github.com/open-energy-transition/Awesome-Grid-Model-Data) | ⚠️ **sin licencia** | Catálogo de datasets de red para probar interoperabilidad y reproducibilidad. Útil para orientarse; sin licencia no se redistribuye (octavo pase) | 80 |
| [DatariusAI/AI-in-Energy](https://github.com/DatariusAI/AI-in-Energy) | ⚠️ **sin licencia** | Hub de investigación y código de IA para energía refrescado a diario. Vale como *feed*, no como dependencia (octavo pase) | 0 |


## Añadidos del noveno pase (2026-11-20)

Todas las filas verificadas contra `search/repositories` el 2026-11-20; licencias `NOASSERTION`
resueltas leyendo `LICENSE` crudo en `raw.githubusercontent.com` probando `main`, `master` y
`develop` en ese orden.

### Protocolo vehículo↔cargador (ISO 15118): la mitad de la categoría está permisiva y viva, la otra mitad parada

| Repo | Licencia | Descripción | ★ | Forks | Push | Región origen |
|------|----------|-------------|---|-------|------|---------------|
| [ecog-io/iso15118](https://github.com/ecog-io/iso15118) | **Apache-2.0** | ISO 15118 **-2, -20, -8**: Plug & Charge y comunicación V2G | 250 | 142 | 2026-11-17 | EMEA |
| [ecog-io/josev](https://github.com/ecog-io/josev) | **Apache-2.0** | "Sistema operativo" comunitario para estaciones de carga V2G | 164 | 23 | 2026-11-16 | EMEA |
| [SwitchEV/RISE-V2G](https://github.com/SwitchEV/RISE-V2G) | **MIT** | Implementación de referencia histórica de la interfaz V2G | 261 | 95 | ⚠️ 2025-12-19 | EMEA |
| [matth-x/MicroOcpp](https://github.com/matth-x/MicroOcpp) | **MIT** | Cliente OCPP 1.6 / 2.0.1 **para microcontroladores** | 547 | 220 | ⚠️ 2025-12-04 | EMEA |

### Flexibilidad doméstica EMEA (EEBus / SPINE / S2)

| Repo | Licencia | Descripción | ★ | Forks | Push | Región origen |
|------|----------|-------------|---|-------|------|---------------|
| [enbility/eebus-go](https://github.com/enbility/eebus-go) | **MIT** | Stack EEBUS en Go | 123 | 53 | 2026-11-06 | EMEA |
| [NIBEGroup/openeebus](https://github.com/NIBEGroup/openeebus) | **Apache-2.0** | EEBUS (SHIP + SPINE) en C, de un fabricante de bombas de calor | 68 | 18 | 2026-11-12 | EMEA (Suecia) |
| [volschin/eebus-ha-bridge](https://github.com/volschin/eebus-ha-bridge) | **MIT** | Puente EEBUS → Home Assistant con API gRPC | 41 | 9 | 2026-11-19 | EMEA |
| [FlexMeasures/flexmeasures-s2](https://github.com/FlexMeasures/flexmeasures-s2) | **Apache-2.0** | Tooling de mensajes **S2 (EN 50491-12-2)** dentro de FlexMeasures | 2 | 0 | 2026-09-21 | EMEA |

### Ingeniería de subestación IEC 61850 (la configuración, no el runtime)

| Repo | Licencia | Descripción | ★ | Forks | Push | Región origen |
|------|----------|-------------|---|-------|------|---------------|
| [openscd/open-scd](https://github.com/openscd/open-scd) | **Apache-2.0** | Editor de **SCL (IEC 61850-6 Ed2)**: descripción de configuración de subestación | 145 | 53 | ⚠️ 2026-01-12 (229 issues) | EMEA |

**La licencia del stack 61850 se parte por capa:** runtime `libiec61850` **GPL-3.0**, ingeniería
`open-scd` **Apache-2.0**. Para un producto, la pieza enlazable es la de ingeniería.

### Forecasting de precio y foundation models de forecasting

| Repo | Licencia | Descripción | ★ | Forks | Push | Región origen |
|------|----------|-------------|---|-------|------|---------------|
| [jeslago/epftoolbox](https://github.com/jeslago/epftoolbox) | **Apache-2.0** | Benchmark abierto de **electricity price forecasting**: baseline obligatorio antes de prometer un modelo propio | 417 | 115 | 2026-05-18 | EMEA (España) |
| [alliander-opensource/s4casting](https://github.com/alliander-opensource/s4casting) | **MPL-2.0** | Time series foundation models para forecasting energético (**Alliander**) | 12 | 2 | **2026-11-20** | EMEA |
| [runyao-yu/PriceFM](https://github.com/runyao-yu/PriceFM) | ⚠️ **sin licencia** | Foundation model probabilístico de precio: 158 ★ y legalmente inusable | 158 | 13 | 2026-10-25 | — |

### Eólica: recurso, activo de referencia y análisis

| Repo | Licencia | Descripción | ★ | Forks | Push | Región origen |
|------|----------|-------------|---|-------|------|---------------|
| [IEAWindSystems/IEA-15-240-RWT](https://github.com/IEAWindSystems/IEA-15-240-RWT) | **Apache-2.0** | Turbina de referencia de **15 MW** de IEA Wind: activo canónico para dimensionar | 314 | 161 | 2026-10-21 | Global |
| [ebranlard/welib](https://github.com/ebranlard/welib) | **MIT** | Librería de análisis de turbinas y energía eólica (Python/Matlab) | 120 | 43 | 2026-11-10 | North America |

### Geotermia: corrección de inventario sobre T26 (eran tres repos usables, no uno)

| Repo | Licencia | Descripción | ★ | Forks | Push | Región origen |
|------|----------|-------------|---|-------|------|---------------|
| [MassimoCimmino/pygfunction](https://github.com/MassimoCimmino/pygfunction) | **BSD-3-Clause** | Factores de respuesta térmica (g-functions) de intercambiadores geotérmicos de pozo | 75 | 26 | 2026-09-12 | North America (Canadá) |
| [waiwera/waiwera](https://github.com/waiwera/waiwera) | LGPL-3.0 | Simulador paralelo de flujo geotérmico | 62 | 16 | **2026-11-20** | APAC (Nueva Zelanda) |

`pygfunction` es **más permisivo y más estrellado que `GEOPHIRES-X`** y T26 no lo tenía. La tesis de
T26 no cambia (base para estudio técnico-económico, no ecosistema de plataforma); cambia el
inventario.

### Carbono, semántica y seguridad de medición

| Repo | Licencia | Descripción | ★ | Forks | Push | Región origen |
|------|----------|-------------|---|-------|------|---------------|
| [thegreenwebfoundation/grid-intensity-go](https://github.com/thegreenwebfoundation/grid-intensity-go) | **Apache-2.0** | Intensidad de carbono como factor de decisión de dónde/cuándo correr cómputo (Go) | 84 | 10 | 2026-05-11 | EMEA |
| [JamesTwallin/GridSeis](https://github.com/JamesTwallin/GridSeis) | **MIT** | Predice intensidad de carbono desde **frecuencia de red** (FFT + gradient boosting) | 31 | 1 | 2026-11-04 | EMEA (UK) |
| [DataTreehouse/maplib](https://github.com/DataTreehouse/maplib) | **Apache-2.0** | Mapeo a grafos RDF: la pieza entre CIM/CGMES y una capa semántica consultable | 192 | 14 | **2026-11-20** | EMEA (Noruega) |
| [rsmusllp/termineter](https://github.com/rsmusllp/termineter) | **BSD-3-Clause** | Framework de pruebas de **seguridad de medidores inteligentes** | 281 | 106 | 2026-03-17 | North America |
| [WillCodeForCats/solaredge-modbus-multi](https://github.com/WillCodeForCats/solaredge-modbus-multi) | **Apache-2.0** | Integración Modbus/TCP completa de inversores SolarEdge | 343 | 29 | 2026-11-19 | North America |
| [argonne-citadel/grid-stix](https://github.com/argonne-citadel/grid-stix) | GPL-3.0 | Inteligencia de amenazas en formato **STIX** para dominio de red (**Argonne National Laboratory**). 2 ★: señal de dirección | 2 | 1 | 2026-08-19 | North America |

### Petrofísica / O&G: la capa de datos que faltaba

| Repo | Licencia | Descripción | ★ | Forks | Push | Región origen |
|------|----------|-------------|---|-------|------|---------------|
| [kinverarity1/lasio](https://github.com/kinverarity1/lasio) | **MIT** | Lectura/escritura de registros de pozo en formato **LAS** (Log ASCII Standard) | 411 | 175 | 2026-11-18 | APAC (Australia) |
| [agilescientific/welly](https://github.com/agilescientific/welly) | **Apache-2.0** | Carga de pozos, registros wireline, calidad de log y ciencia de datos de subsuelo | 381 | 141 | ⚠️ 2025-07-16 | North America |

Complementa T21 (el subsector O&G no es "todo GPL"): la **capa de datos** de subsuelo es MIT y
Apache, y es lo que un agente necesita leer antes de razonar.

### Anomalías ★/fork registradas (no citar como validados por comunidad)

- [`Ali-Marandi/grid-resilience`](https://github.com/Ali-Marandi/grid-resilience) — MIT, análisis de resiliencia N-1 basado en grafos, **108 ★ y 0 forks**.
- `KEV0143/Comparative-analysis-of-hourly-load-forecasting-using-PatchTST-TFT-NHiTS-and-CatBoost` — Apache-2.0, **1.764 ★ y 0 forks**.

Consistente con T19. Un repo con 1.764 estrellas y cero forks no lo usó nadie.

## La capa institucional norteamericana: EPRI, Grid Protection Alliance y Sandia (décimo pase, 2026-11-20)

> **Por qué estaba ausente.** Nueve pases buscaron por categoría y por norma. Estas tres
> organizaciones nombran sus herramientas por el **acrónimo interno del método** (`StorageVET`,
> `QuESt`, `openXDA`, `openMIC`, `ProGRESS`), así que ninguna consulta de categoría las devuelve.
> La consulta que funciona es `org:<nombre>`. Ver **T47**.
> Totales: `epri-dev` **59 repos**, `GridProtectionAlliance` **66**, portafolio energético de
> `sandialabs` **30**. Esta KB tenía **tres** (`gsf`, `openPDC`, `quest_planning`).

### EPRI — Electric Power Research Institute (`epri-dev`)

Perfil de licencia dominante: **BSD-3-Clause**. El archivo se llama `LICENSE.txt`, no `LICENSE`.

| Repo | Licencia | Para qué | ★ | Forks | Push | Región |
|------|----------|----------|---|-------|------|--------|
| [IEEE-2030.5-Client](https://github.com/epri-dev/IEEE-2030.5-Client) | **BSD-3-Clause** | Cliente **IEEE 2030.5**: el estándar de comunicación con DER de Norteamérica | 96 | 56 | ⚠️ 2023-02-27 | North America |
| [OpenDER](https://github.com/epri-dev/OpenDER) | **BSD-3-Clause** *(rescatada del `NOASSERTION`)* | Modelo de DER conforme a **IEEE 1547-2018** | 76 | 32 | 2025-06-23 | North America |
| [StorageVET-deprecated](https://github.com/epri-dev/StorageVET-deprecated) | **BSD-3-Clause** | Valoración de almacenamiento (StorageVET 2.0) | 64 | 24 | 2026-10-24 | North America |
| [OpenADR-Virtual-End-Node](https://github.com/epri-dev/OpenADR-Virtual-End-Node) | **BSD-3-Clause** | **VEN** OpenADR de referencia (lado del nodo) | 43 | 20 | ⚠️ 2023-04-20 | North America |
| [DLMS-COSEM](https://github.com/epri-dev/DLMS-COSEM) | **BSD-3-Clause** | Protocolo de datos de medidor **DLMS/COSEM**, permisivo | 40 | 18 | ⚠️ 2024-11-13 | Global |
| [US-REGEN](https://github.com/epri-dev/US-REGEN) | **BSD-3-Clause** | Modelo regional de economía, GEI y energía de EE. UU. | 24 | 4 | 2025-05-27 | North America |
| [Risk-Screening-Tool](https://github.com/epri-dev/Risk-Screening-Tool) | **BSD-3-Clause** | Cribado de riesgo | 14 | 3 | 2026-10-31 | North America |
| [dlms-cim](https://github.com/epri-dev/dlms-cim) | **BSD-3-Clause** | Traducción **DLMS/COSEM → CIM**: el puente de un MDM | 8 | 3 | ⚠️ 2021-01-24 | Global |
| [ES-CIM](https://github.com/epri-dev/ES-CIM) | **Apache-2.0** | Energy Supply Common Information Model | 7 | 4 | ⚠️ 2022-12-19 | Global |
| [DER-VET](https://github.com/epri-dev/DER-VET) | **BSD-3-Clause** | Valoración de DER | 6 | 4 | 2026-10-21 | North America |
| [dlms-access-point](https://github.com/epri-dev/dlms-access-point) | **BSD-3-Clause** | *Access point* DLMS/COSEM de referencia. Fork:★ = **2,0** | 5 | 10 | 2025-05-27 | Global |
| [plexos2duckdb](https://github.com/epri-dev/plexos2duckdb) | **BSD-3-Clause** | Soluciones **PLEXOS** → DuckDB: salida de la herramienta propietaria de planificación | 5 | 2 | 2026-11-04 | North America |
| [SPI-Tool](https://github.com/epri-dev/SPI-Tool) | **BSD-3-Clause** | Stochastic Planning Inputs Tool | 1 | 0 | 2026-11-14 | North America |
| [Universal-Semantic-Standard-Test-Harness](https://github.com/epri-dev/Universal-Semantic-Standard-Test-Harness) | **BSD-3-Clause** | Banco de pruebas de interoperabilidad semántica | 0 | 1 | 2026-08-18 | Global |

⚠️ **Bloqueados por licencia en la misma organización** (no usar): `DER-VET-GUI` (5 ★, sin
licencia), `c12test` (12 ★, `NOASSERTION`, conformidad **ANSI C12**), `PV-BESS-Hybrid` (23 ★, sin
licencia), `OpenDSS-C` (7 ★, sin licencia).

### Grid Protection Alliance (`GridProtectionAlliance`) — el stack de datos operativos, MIT y vivo

Los diez repos de abajo tuvieron push entre junio y **noviembre de 2026**.

| Repo | Licencia | Para qué | ★ | Forks | Push | Región |
|------|----------|----------|---|-------|------|--------|
| [openHistorian](https://github.com/GridProtectionAlliance/openHistorian) | **MIT** | **Historiador de series temporales** de red: el sustituto abierto de un PI System | 207 | 60 | 2026-11-15 | North America |
| [gsf](https://github.com/GridProtectionAlliance/gsf) *(ya catalogado)* | **MIT** | Grid Solutions Framework | 179 | 76 | 2026-11-13 | North America |
| [openPDC](https://github.com/GridProtectionAlliance/openPDC) *(ya catalogado)* | **MIT** | Concentrador de datos fasoriales | 159 | 67 | 2026-11-15 | North America |
| [PTPSync](https://github.com/GridProtectionAlliance/PTPSync) | **MIT** | Sincronización **PTP**: base de toda medida fasorial | 97 | 26 | 2026-11-15 | North America |
| [osisoftpi-grafana](https://github.com/GridProtectionAlliance/osisoftpi-grafana) | **Apache-2.0** | Plugin Grafana para **OSIsoft PI**: puente desde el histórico propietario instalado | 65 | 36 | 2026-11-16 | North America |
| [PMUConnectionTester](https://github.com/GridProtectionAlliance/PMUConnectionTester) | **MIT** | Verificación de flujos de sincrofasores | 29 | 14 | 2026-06-04 | North America |
| [PQDashboard](https://github.com/GridProtectionAlliance/PQDashboard) | **BSD-3-Clause** | Calidad de onda a escala de sistema. ⚠️ 21 issues | 23 | 12 | 2026-08-10 | North America |
| [openXDA](https://github.com/GridProtectionAlliance/openXDA) | **MIT** | **Analítica de perturbaciones** extensible | 20 | 17 | 2026-11-19 | North America |
| [openMIC](https://github.com/GridProtectionAlliance/openMIC) | **MIT** | **Meter Information Collection**: recolección de datos de medidor | 18 | 15 | 2026-11-15 | North America |
| [openECA](https://github.com/GridProtectionAlliance/openECA) | **MIT** | Control y analítica extensible. ⚠️ **20 issues** | 16 | 8 | 2026-11-15 | North America |
| [SIEGate](https://github.com/GridProtectionAlliance/SIEGate) | **MIT** | Gateway seguro de intercambio entre control rooms | 9 | 6 | 2026-11-15 | North America |

### Sandia National Laboratories (`sandialabs`) — cuatro licencias rescatadas, una bloqueada

La API reporta `NOASSERTION` en todo el portafolio porque el `LICENSE` abre con el preámbulo de
contrato **DE-NA0003525 (NTESS)** antes del otorgamiento. El otorgamiento es estándar. Ver **T46**.

| Repo | Licencia real (leída en crudo) | Para qué | ★ | Forks | Push | Región |
|------|-------------------------------|----------|---|-------|------|--------|
| [snl-quest](https://github.com/sandialabs/snl-quest) | **BSD-3-Clause** | **QuESt**: plataforma de análisis de almacenamiento. ⚠️ **44 issues** | 162 | 53 | 2026-11-09 | North America |
| [snl-pstess](https://github.com/sandialabs/snl-pstess) | **MIT** | Power and Energy Storage Systems Toolbox | 40 | 7 | 2026-01-20 | North America |
| [snl-progress](https://github.com/sandialabs/snl-progress) | **BSD-3-Clause** | **ProGRESS**: fiabilidad probabilística de red con almacenamiento | 24 | 10 | 2026-09-25 | North America |
| [pvOps](https://github.com/sandialabs/pvOps) | **BSD-3-Clause** | O&M de fotovoltaica: investigación de operaciones sobre datos de planta | 22 | 12 | ⚠️ 2025-09-12 | North America |
| [quest_planning](https://github.com/sandialabs/quest_planning) *(ya catalogado)* | **NOASSERTION** | Expansión de capacidad a largo plazo | 21 | 3 | 2026-11-19 | North America |

⚠️ [`sandialabs/OpenCSP`](https://github.com/sandialabs/OpenCSP) (13 ★, **20 forks**, 91 issues,
push 2026-09-17) — solar de concentración, **sin archivo de licencia en `main`**. Es la única base
abierta de CSP que ha encontrado esta KB y está bloqueada por permiso, no por calidad.

## La familia `oemof`: 18 repos, 15 MIT (décimo pase, 2026-11-20)

Mismo patrón que `open-energy-transition` en el pase 8, ahora en EMEA. La KB tenía `oemof-solph`.

| Repo | Licencia | Para qué | ★ | Forks | Push | Región |
|------|----------|----------|---|-------|------|--------|
| [tespy](https://github.com/oemof/tespy) | **MIT** | **Thermal Engineering Systems in Python**: ciclos térmicos, bombas de calor, plantas. Más estrellado que `oemof-solph` | 440 | 150 | 2026-11-19 | EMEA |
| [oemof-demand](https://github.com/oemof/oemof-demand) | **MIT** | Perfiles horarios de demanda de calor y electricidad desde valores anuales | 76 | 46 | 2026-10-22 | EMEA |
| [DHNx](https://github.com/oemof/DHNx) | **MIT** | Optimización y simulación de **redes de calor de distrito**. ⚠️ 35 issues | 47 | 16 | 2026-11-14 | EMEA |
| [cydets](https://github.com/oemof/cydets) | **MIT** | Detección de ciclos en series temporales (ciclado de batería) | 41 | 6 | ⚠️ 2022-12-01 | EMEA |
| [oemof-thermal](https://github.com/oemof/oemof-thermal) | **MIT** | Componentes térmicos para oemof | 36 | 15 | ⚠️ 2025-05-26 | EMEA |
| [exerpy](https://github.com/oemof/exerpy) | **MIT** | Análisis **exergético** desde entrada tabular | 22 | 9 | 2026-11-19 | EMEA |

⚠️ **Archivados, y ninguna consulta lo advierte**: [`feedinlib`](https://github.com/oemof/feedinlib)
(MIT, **117 ★, 43 forks**, modelos PV) y [`marketlib`](https://github.com/oemof/marketlib) (MIT,
16 ★). Para generación PV la pieza viva sigue siendo `pvlib-python`.

## Calor de distrito: la categoría ausente que domina el norte de EMEA (décimo pase, 2026-11-20)

| Repo | Licencia | Para qué | ★ | Forks | Push | Región |
|------|----------|----------|---|-------|------|--------|
| [oemof/DHNx](https://github.com/oemof/DHNx) | **MIT** | Optimización y simulación de red de calor | 47 | 16 | 2026-11-14 | EMEA |
| [jylambert/topotherm](https://github.com/jylambert/topotherm) | **MIT** | Optimización de **topología** de red de calor (TU München) | 37 | 11 | 2026-10-06 | EMEA |
| [raomin/ESPAltherma](https://github.com/raomin/ESPAltherma) | **MIT** | Lectura de bomba de calor **Daikin Altherma** por ESP32. Fork:★ = 0,35 | 540 | 188 | 2026-11-18 | EMEA |

⚠️ [`idiap/pydhn`](https://github.com/idiap/pydhn) (23 ★, Idiap Research Institute) — **sin
licencia**. Bloqueado por permiso.

**Veredicto honesto:** dos repos MIT de optimización de red de calor (47 ★ y 37 ★) son base para un
**estudio**, no para una plataforma. Pero la KB no tenía ninguno, y el calor de distrito es el vector
de descarbonización dominante en Escandinavia, Alemania, Polonia y los bálticos.

## Transporte de datos ENTSO-E: EDX y OPDM, MIT, una sola persona (décimo pase, 2026-11-20)

El pase 7 catalogó la **tubería** CGMES. Esto es el **transporte**: cómo se mueven de verdad los
modelos entre TSOs europeos.

| Repo | Licencia | Para qué | ★ | Forks | Push | Región |
|------|----------|----------|---|-------|------|--------|
| [Haigutus/USVDM](https://github.com/Haigutus/USVDM) | **MIT** | Uso e intercambio de CIM. Fork:★ = **0,9** | 10 | 9 | 2026-08-08 | EMEA |
| [Haigutus/cim-bench](https://github.com/Haigutus/cim-bench) | **MIT** | **Benchmarking de herramientas CIM** | 10 | 5 | 2026-07-16 | EMEA |
| [Haigutus/EDX](https://github.com/Haigutus/EDX) | **MIT** | API SOAP de **EDX (ENTSO-E Data Exchange)** | 7 | 2 | 2025-12-07 | EMEA |
| [Digital4Grids/Bridge_energy_schemas](https://github.com/Digital4Grids/Bridge_energy_schemas) | **MIT** | Esquemas CIM de referencia del Bridge Data Working Group | 5 | 2 | 2026-11-19 | EMEA |
| [Haigutus/triplets](https://github.com/Haigutus/triplets) | **MIT** | XML/RDF → pandas/polars/**DuckDB**. ⚠️ 32 issues | 3 | 1 | 2026-11-18 | EMEA |
| [Haigutus/OPDM](https://github.com/Haigutus/OPDM) | **MIT** | API del **Operational Planning Data Management** de ENTSO-E | 2 | 2 | 2025-05-21 | EMEA |

⚠️ **Riesgo de bus único, declarado:** cinco de los seis son de **una cuenta individual** y tienen
2-10 estrellas. Es la pieza que hace operable el CGMES europeo y el punto de fallo más concentrado de
esta KB. Usar como **acelerador internalizado**, no como dependencia de producción sin plan propio.

## Sistema eléctrico de Ecuador: primera aparición de LATAM-Andina (décimo pase, 2026-11-20)

| Repo | Licencia | Para qué | ★ | Forks | Push | Región |
|------|----------|----------|---|-------|------|--------|
| [wilianguamancuenca/EC-PowerSystems](https://github.com/wilianguamancuenca/EC-PowerSystems) | **MIT** | Información y material del sistema eléctrico ecuatoriano. Fork:★ = **1,86**, el ratio más alto medido en este pase | 21 | 39 | ⚠️ 2024-05-02 | LATAM |

Añade **Ecuador** a la credencial LATAM verificable (Brasil, Colombia, Chile, México). **Argentina
sigue en cero por sexta medición consecutiva.**


---
*Ver también `verticals/solutions.md` para plataformas verticales completas.*

## Co-simulación, nuclear, eólica y DLR: el barrido por institución, ronda 2 (undécimo pase, 2026-11-20)

El pase 10 barrió las instituciones norteamericanas de red (`epri-dev`, `GridProtectionAlliance`,
`sandialabs`). Este pase barrió la capa que quedaba: **laboratorio nacional de propósito general** y
**TSO europeo que publica código**. Son seis organizaciones (`GMLC-TDC`, `idaholab`, `statnett`,
`DTUWindEnergy`, `pnnl`, `openenergymonitor`), y la pieza más importante llevaba once pases ausente.

### El bus de co-simulación que faltaba bajo toda esta KB

| Repo | Licencia | ★ / Forks | Push | Qué aporta | Región |
|------|----------|-----------|------|------------|--------|
| [GMLC-TDC/HELICS](https://github.com/GMLC-TDC/HELICS) | **BSD-3-Clause** | 178 / 54 | 2026-11-20 | *Hierarchical Engine for Large-scale Infrastructure Co-Simulation*: acopla transmisión, distribución, comunicaciones y mercado en un mismo experimento. Motor del **Grid Modernization Lab Consortium** del DOE. ⚠️ 96 issues | North America |

Esta KB tenía `gridlab-d`, `pandapower`, `powsybl` y una sección de co-simulación — **y no tenía el
bus que los conecta**. Se escapó porque su nombre no contiene ninguna palabra del dominio y su
organización se llama por el acrónimo del consorcio. Es la dependencia natural de cualquier receta que
combine un simulador de distribución con uno de transmisión.

### Nuclear: la fila que el pase 10 cerró en falso

| Repo | Licencia | ★ / Forks | Push | Qué aporta | Región |
|------|----------|-----------|------|------------|--------|
| [idaholab/raven](https://github.com/idaholab/raven) | **Apache-2.0** | 274 / 151 | 2026-11-19 | **RAVEN**: riesgo probabilístico y cuantificación de incertidumbre; envoltorio estadístico sobre MOOSE. ⚠️ 197 issues | North America |
| [idaholab/DeepLynx](https://github.com/idaholab/DeepLynx) | **MIT** *(rescatada en crudo)* | 102 / 36 | 2026-10-30 | Almacén de datos de **gemelo digital** orientado a grafo para integración de datos de ingeniería | North America |
| [idaholab/MontePy](https://github.com/idaholab/MontePy) | **MIT** | 68 / 32 | 2026-11-19 | Lectura/escritura de *inputs* MCNP en Python | North America |
| [idaholab/STIG](https://github.com/idaholab/STIG) | **BSD-3-Clause** | 102 / 32 | 2026-09-30 | *Structured Threat Intelligence Graph* (STIX): inteligencia de amenazas en grafo | North America |
| [idaholab/moose](https://github.com/idaholab/moose) | LGPL-2.1 | 2409 / 1282 | 2026-11-20 | Entorno multifísica. **Enlazable, no incrustable** sin análisis de copyleft | North America |
| [idaholab/virtual_test_bed](https://github.com/idaholab/virtual_test_bed) | ⚠️ **CC-BY-4.0** | 81 / **103** | 2026-11-19 | Modelos de reactores avanzados (microrreactor, SFR, HTGR, MSR) para MOOSE. Licencia de **datos/documentación**, no de software | North America |

**Cómo proponer esta fila sin exagerarla:** `raven` + `MontePy` + `DeepLynx` son permisivos y
proponibles. `moose` y `mastodon` son LGPL-2.1. `virtual_test_bed` es CC-BY-4.0: son *modelos*, y de
una licencia CC **no se hereda permiso de software**. El gap nuclear deja de ser de oferta y pasa a
ser de licencia.

### Dynamic line rating: la norma implementada, por un TSO, en MIT

| Repo | Licencia | ★ / Forks | Push | Qué aporta | Región |
|------|----------|-----------|------|------------|--------|
| [statnett/linerate](https://github.com/statnett/linerate) | **MIT** | 8 / 3 | **2026-11-20** | Ampacidad de líneas aéreas: una función pura por cada ecuación de **CIGRE TB 601**, más CIGRE TB 207 e **IEEE 738**; solver de bisección vectorizado; tipos de conductor, vano y meteorología. Reproduce el *Example B* (pp. 79-81) de CIGRE TB 601. ⚠️ 7 issues | EMEA |
| [statnett/cimsparql](https://github.com/statnett/cimsparql) | **MIT** | 10 / 7 | 2026-11-16 | Consulta de modelos **CIM** por SPARQL desde Python. Mitad ejecutable del patrón NL→CIM. ⚠️ 9 issues | EMEA |

⚠️ [`statnett/Nordic44`](https://github.com/statnett/Nordic44) (modelo sintético de la red nórdica,
6 ★, 29 issues) es **CC-BY-NC-SA-4.0** — la API dice `NOASSERTION`. **NonCommercial: no usable en
encargo de cliente.**

### Eólica: diseño de parque y control de planta

| Repo | Licencia | ★ / Forks | Push | Qué aporta | Región |
|------|----------|-----------|------|------------|--------|
| [DTUWindEnergy/WindGym](https://github.com/DTUWindEnergy/WindGym) | **MIT** | 59 / 5 | 2026-11-19 | Entorno de **RL para control de parque eólico**. El único del clúster con tracción y actividad | EMEA |
| [DTUWindEnergy/TopFarm2](https://github.com/DTUWindEnergy/TopFarm2) | **MIT** | 18 / 14 | 2026-07-16 | Optimización de **layout** de parque | EMEA |
| [DTUWindEnergy/OptiWindNet](https://github.com/DTUWindEnergy/OptiWindNet) | **MIT** | 14 / 2 | 2026-10-19 | Optimización de la **red de colección** interna | EMEA |
| [DTUWindEnergy/PyWake](https://github.com/DTUWindEnergy/PyWake) | ⚠️ **sin archivo de licencia** en `main`, `master` ni `develop` | 85 / 28 | 2024-11-25 | Modelo de **estela**. El más citado del clúster y **no proponible** | EMEA |

⚠️ **Advertencia estructural, no anecdótica:** `TopFarm2`, `OptiWindNet`, `WindEnergyToolbox` y
`WindGym` **declaran en su propia descripción de API ser "Mirror of
https://gitlab.windenergy.dtu.dk/..."**. El repositorio canónico de la ingeniería eólica europea está
en un GitLab autoalojado; GitHub indexa espejos, **y a veces el espejo pierde la licencia** — que es
precisamente lo que le ocurre a `PyWake`. Antes de descartar una pieza europea por "sin licencia",
hay que ir al GitLab de origen.

### PNNL: aprendizaje con restricciones físicas y ACOPF en GPU

| Repo | Licencia | ★ / Forks | Push | Qué aporta | Región |
|------|----------|-----------|------|------------|--------|
| [pnnl/neuromancer](https://github.com/pnnl/neuromancer) | **Battelle — permisiva tipo BSD-3, no SPDX** | 1399 / 190 | 2026-10-22 | Programación diferenciable: control predictivo y aprendizaje **con restricciones físicas**. El de más estrellas del pase | North America |
| [pnnl/ExaGO](https://github.com/pnnl/ExaGO) | **Battelle — misma licencia** | 93 / 16 | 2026-03-23 | **ACOPF en GPU/HPC**, multiperiodo y estocástico | North America |

⚠️ **Acotación que matiza T46 y que importa en un SoW:** la API dice `NOASSERTION`; el texto en crudo
es la licencia propia de **Battelle Memorial Institute**, que concede uso, copia, modificación,
sublicencia y venta con retención de aviso y cláusula de no-uso-del-nombre. Es **permisiva en
sustancia, equivalente a BSD-3 — pero no es un identificador SPDX**, no pasará un escáner automático
de licencias y requiere visto bueno legal explícito. "Rescatada como permisiva no estándar" no es lo
mismo que "rescatada como BSD-3".

## El stack del mercado eléctrico australiano: la región que esta KB tenía con dos repos y tiene treinta (duodécimo pase, 2026-11-20)

Hasta este pase, APAC en esta KB eran esencialmente `unsw-ceem/nemseer`, `bje-/nemo` y
`pypsa/pypsa-china`. El barrido por institución —el método de los pases 10 y 11, aplicado esta vez al
**operador de mercado australiano (AEMO) y a su entorno académico**— abre dos organizaciones enteras
que ninguna consulta genérica había devuelto.

Y abre con una condición de licencia que **decide la arquitectura de cualquier proyecto APAC**: ver
la frontera al final de la sección y **T32**.

### `Open-ISP`: el Integrated System Plan de AEMO, reimplementado en abierto

AEMO **no publica** su modelo. `Open-ISP` reimplementa su metodología y sus datasets. Los tres repos
con contenido están **todos bajo GPL-3.0**:

| Repo | Licencia | ★ / forks | Push | Qué es |
|---|---|---|---|---|
| [Open-ISP/ISPyPSA](https://github.com/Open-ISP/ISPyPSA) | **GPL-3.0** | 31 / 8 | **2026-11-20** | Modelo de expansión de capacidad sobre **PyPSA** siguiendo la metodología y las asunciones del **Integrated System Plan** de AEMO |
| [Open-ISP/isp-trace-parser](https://github.com/Open-ISP/isp-trace-parser) | **GPL-3.0** | 19 / 4 | 2026-11-16 | Reformatea y sirve las series temporales de demanda, solar y viento que usa AEMO |
| [Open-ISP/isp-workbook-parser](https://github.com/Open-ISP/isp-workbook-parser) | **GPL-3.0** | 12 / 6 | 2026-11-16 | Lee los datos del **IASR** (Inputs, Assumptions and Scenarios Report) desde los Excel de AEMO |

Los otros cinco repos de la organización son infraestructura de proyecto (`project-planning`,
`dev-practices`, `template-repository`, `open-isp-docs`, `.github`) y no aportan código reutilizable.

**Por qué importa que exista `isp-workbook-parser`:** es el repo menos vistoso de los tres y el que
más tiempo ahorra. El IASR de AEMO se publica como libro de Excel; convertir eso en datos utilizables
es exactamente el trabajo sucio que un engagement paga dos veces si no sabe que ya está hecho. Mismo
patrón que `pudl` en North America.

**Nota de actividad:** `ISPyPSA` tenía push **el mismo día de este pase**. La organización está viva,
no es un archivo.

### `UNSW-CEEM`: la capa de datos y de despacho del NEM (29 repos, barridos)

El Collaboration on Energy and Environmental Markets de la UNSW es, de hecho, el proveedor de datos
abiertos del NEM. Lo relevante, con licencia **resuelta fichero a fichero** (ver agents/top.md §2 del
duodécimo pase):

| Repo | Licencia | ★ / forks | Push | Qué es |
|---|---|---|---|---|
| [UNSW-CEEM/NEMOSIS](https://github.com/UNSW-CEEM/NEMOSIS) | **GPL-3.0-or-later** ⚠️ la API dice `NOASSERTION` | **113** / 39 | 2026-10-05 | **La capa estándar de acceso** a datos históricos publicados por AEMO. El repo más estrellado del stack |
| [UNSW-CEEM/nempy](https://github.com/UNSW-CEEM/nempy) | **BSD-3-Clause** | 71 / 36 | 2025-10-22 | Modela el **procedimiento de despacho** del NEM. Permisivo |
| [UNSW-CEEM/NEMSEER](https://github.com/UNSW-CEEM/NEMSEER) | **GPL-3.0** | 39 / 9 | 2026-11-16 | Descarga y maneja los **pronósticos** de AEMO (pre-dispatch, PASA) |
| [UNSW-CEEM/NEMED](https://github.com/UNSW-CEEM/NEMED) | **BSD-3-Clause** | 15 / 7 | 2024-05-20 | Datos de **emisiones** del NEM. Permisivo |
| [UNSW-CEEM/nem-bidding-dashboard](https://github.com/UNSW-CEEM/nem-bidding-dashboard) | **BSD-3-Clause** | 11 / 5 | 2023-08-01 | Visualización de datos de **puja**. Permisivo, pero parado desde 2023 |
| [UNSW-CEEM/DER_disturbance_analysis](https://github.com/UNSW-CEEM/DER_disturbance_analysis) | **MIT** | 6 / 1 | 2024-04-29 | Respuesta de PV y DER ante **perturbaciones del sistema**. Permisivo |
| [UNSW-CEEM/TDA_Python](https://github.com/UNSW-CEEM/TDA_Python) | sin licencia ⚠️ | 8 / 2 | 2023-03-03 | Diseño y análisis de **tarifas**. **Bloqueado** (T20) |
| [UNSW-CEEM/market-control-room](https://github.com/UNSW-CEEM/market-control-room) | **MIT** | 2 / 2 | 2022-12-08 | Explorador web de resultados de simulación de mercado. Permisivo, inactivo |

`UNSW-CEEM/tm_solarshift` (simulación térmica de calentadores eléctricos domésticos) y
`Pacific_Islands_Energy_Balance` (datos energéticos de países insulares del Pacífico — único repo de
esta KB que cubre esa subregión) existen **sin licencia declarada**: interesantes, bloqueados.

### ⚠️ La frontera de licencia del NEM, que es una decisión de arquitectura y no una nota al pie

**Lo que un proyecto australiano puede embeber en un entregable propietario:** `nempy` (despacho),
`NEMED` (emisiones), `nem-bidding-dashboard`, `DER_disturbance_analysis`, `market-control-room` —
BSD-3 y MIT.

**Lo que no puede embeber:** `NEMOSIS` (acceso a datos), `NEMSEER` (pronósticos), y los tres de
`Open-ISP` (expansión de capacidad) — **GPL-3.0**.

El reparto es cruel, porque **el GPL cae justo sobre la capa de entrada de datos**: no se puede
construir un producto cerrado del NEM sin tocar `NEMOSIS`. La salida arquitectónica —y es la única
limpia— es **aislar GPL detrás de un proceso o servicio separado** (contenedor propio, interfaz de
datos, sin enlazado), y mantener la lógica propietaria del cliente al otro lado de esa frontera. Es
exactamente la "regla de arquitectura que atraviesa todas las recetas" de compose/patterns.md,
aplicada a una región entera. Ver **Receta 31** y **T32**.

## Herramientas de simulación publicadas por TSOs nórdicos (duodécimo pase)

El barrido de TSOs europeos del pase 11 cubrió Statnett (Noruega). Este pase cubre **Energinet
(Dinamarca)**, y la organización `Energinet-SimTools` tiene exactamente dos repos con contenido — con
**licencias opuestas**, que es el hallazgo:

| Repo | Licencia | ★ / forks | Push | Qué es |
|---|---|---|---|---|
| [Energinet-SimTools/IMTB](https://github.com/Energinet-SimTools/IMTB) | **MPL-2.0** ✅ (la API dice `NOASSERTION`; la MPL está escrita en Markdown) | 41 / 10 | 2026-08-18 | **Immittance Measurement ToolBox**: medida de inmitancia para estudios de estabilidad |
| [Energinet-SimTools/MTB](https://github.com/Energinet-SimTools/MTB) | ⛔ **NO es OSI — permiso revocable** | **83** / 24 | 2026-11-19 | **Model Test Bench**: automatiza estudios de cumplimiento de red en **PSCAD** y **PowerFactory** |

**`IMTB` es usable** (MPL-2.0, copyleft por archivo, enlazable desde código propietario).

**`MTB` no lo es, y es el más estrellado de los dos.** Su `LICENSE.md` no nombra licencia alguna:
concede *"a worldwide, non-exclusive, non-payable right to use, modify and distribute"* y acto
seguido declara que **"Energinet may withdraw or modify the right to use, modify and distribute"**,
reteniendo toda la propiedad intelectual. Un permiso revocable no es open source y no sostiene un
entregable de cliente. **Úsese como especificación de los requisitos de prequalificación de
Energinet** —que es su función real— sin incorporar el código. Ver agents/top.md §3 y **T33**.

Advertencia adicional sobre los dos: ambos orquestan **PSCAD** y **PowerFactory**, que son
**comerciales**. El repo es abierto; el simulador que necesita, no. Mismo patrón que
`PowerAgentBench-Dyn` sobre PowerFactory.

## Acceso unificado a datos de mercado europeos: la pieza permisiva que faltaba (duodécimo pase)

| Repo | Licencia | ★ / forks | Push | Qué es |
|---|---|---|---|---|
| [AlexanderHoogsteyn/ClariGrid](https://github.com/AlexanderHoogsteyn/ClariGrid) | **Apache-2.0** ✅ (la API dice `NOASSERTION`) | 3 / 0 | 2026-11-19 | Interfaz Python **única y estable** sobre datos de mercado de varias fuentes europeas; devuelve siempre `pandas.DataFrame` con husos horarios, nombres de columna y unidades normalizados |

Complementa, no sustituye, a `entsoe-py` y a la capa CGMES del séptimo pase: lo que aporta es
**normalización entre fuentes heterogéneas** (incluye conector de Fingrid, que requiere clave de API
gratuita). Es de autor individual y 3 ★ — **patrón a copiar antes que dependencia a asumir**, con el
mismo criterio que la cola larga de MCP.

## ⚠️ Corrección de inventario: `Open-Power-System-Data` está congelado desde 2020

Aparece en toda bibliografía europea de datos abiertos y conviene fijar su estado real, porque un
engagement que lo tome como fuente viva se lleva un dato de hace seis años:

| Repo | Licencia | ★ | Último push |
|---|---|---|---|
| [Open-Power-System-Data/time_series](https://github.com/Open-Power-System-Data/time_series) | MIT | 152 | **2020-10-06** |
| [Open-Power-System-Data/conventional_power_plants](https://github.com/Open-Power-System-Data/conventional_power_plants) | MIT | 54 | **2020-10-01** |
| [Open-Power-System-Data/national_generation_capacity](https://github.com/Open-Power-System-Data/national_generation_capacity) | MIT | 18 | **2020-10-01** |
| [Open-Power-System-Data/renewable_power_plants](https://github.com/Open-Power-System-Data/renewable_power_plants) | MIT | 70 | **2020-08-26** |
| [Open-Power-System-Data/weather_data](https://github.com/Open-Power-System-Data/weather_data) | MIT | 66 | **2019-04-09** |

Licencia impecable (MIT, los cinco), **datos muertos**. Ninguno está marcado como archivado, así que
no hay señal automática: el único indicador es la fecha. Para series vivas, usar `entsoe-py`,
`ClariGrid`, `gridstatus` o `rebase-energy/energydatamodel`. Para **datos históricos reproducibles
hasta 2020 con licencia limpia**, siguen siendo la mejor fuente que existe — ese es su uso legítimo.

## Capa de medición y modelo de datos de DER (añadida en el decimotercer pase, 2026-11-20)

Esta KB tenía el **motor** de red, los **entornos RL**, los **protocolos de carga** y la **capa
agéntica**. Faltaba el cimiento de abajo: **cómo se lee el medidor y el inversor, y con qué modelo de
datos**. Sin esta capa, un piloto de agente se queda en simulación; con ella, toca hardware real del
cliente. Se abrió con tres términos de **protocolo** (`SunSpec`, `IEC 62056`, `SAREF`), aplicando la
regla del pase 8 — *buscar el protocolo máquina-a-máquina, no la norma documental de cumplimiento*.

Todas las filas verificadas por consulta `repo:` exacta contra `search/repositories` el 2026-11-20.
Ninguna archivada.

### Modelo de datos normativo de DER e inversores

| Repo | Licencia | ★ | Forks | Último push | Por qué es cimiento |
|---|---|---|---|---|---|
| [sunspec/models](https://github.com/sunspec/models) | **Apache-2.0** | 135 | 67 | 2026-08-20 | **Definiciones de modelos de la propia alianza SunSpec.** Es el diccionario de datos normativo de inversores y DER: convierte "registro Modbus 40072" en un campo con semántica. Pieza de referencia, no implementación de un tercero |
| [sunspec/pysunspec2](https://github.com/sunspec/pysunspec2) | **Apache-2.0** | 76 | 32 | 2026-10-21 | Librería Python **oficial** de la alianza para hablar con dispositivos SunSpec por Modbus TCP/RTU |
| [volkszaehler/mbmd](https://github.com/volkszaehler/mbmd) | **BSD-3-Clause** | 281 | 95 | 2026-11-09 | *ModBus Measurement Daemon* en Go: un demonio, no una librería — se despliega como servicio y publica lecturas. El camino más corto a telemetría continua |
| [WillCodeForCats/solaredge-modbus-multi](https://github.com/WillCodeForCats/solaredge-modbus-multi) | **Apache-2.0** | 343 | 29 | 2026-11-19 | Integración SolarEdge multi-inversor por Modbus/TCP. **Sustituto limpio** de `binsentsu/home-assistant-solaredge-modbus` (420 ★, **sin licencia**) |
| [CJNE/ha-sunspec](https://github.com/CJNE/ha-sunspec) | **MIT** | 90 | 27 | 2026-11-19 | SunSpec sobre Home Assistant: banco de pruebas con inversor real en horas, no semanas |

### Lectura de medidor (IEC 62056 / DLMS-COSEM / OBIS / P1)

| Repo | Licencia | ★ | Forks | Último push | Por qué es cimiento |
|---|---|---|---|---|---|
| [marq24/ha-tibber-pulse-local](https://github.com/marq24/ha-tibber-pulse-local) | **Apache-2.0** | 297 | 20 | 2026-11-08 | Lectura **local, sin nube**, por LAN. **0 issues abiertas** — el repo más limpio de esta capa. Demuestra el patrón "el dato del medidor no sale de casa", que es el argumento de privacidad en EMEA |
| [pwitab/iec62056-21](https://github.com/pwitab/iec62056-21) | **BSD-3-Clause** | 89 | 25 | 2026-04-13 | Implementación Python de **IEC 62056-21** (antes IEC 1107). Implementa **el estándar**, no un fabricante: es lo que la hace cimiento y no integración |
| [lvzon/dsmr-p1-parser](https://github.com/lvzon/dsmr-p1-parser) | **Apache-2.0** | 60 | 14 | 2026-02-27 | Parser en C generado con Ragel del puerto **P1** DSMR y telegramas IEC 62056-21. Para firmware y *edge*, donde Python no entra. **Sustituto limpio** de `arduino-dsmr` (145 ★, sin licencia, parado en 2023) |
| [Apollon77/smartmeter-obis](https://github.com/Apollon77/smartmeter-obis) | **MIT** | 57 | 20 | 2026-06-04 | Normaliza varios protocolos de medidor que siguen la lógica de números **OBIS**. Es la capa de traducción que evita escribir un adaptador por fabricante |

### Ontología y grafo semántico de energía

| Repo | Licencia | ★ | Forks | Último push | Por qué es cimiento |
|---|---|---|---|---|---|
| [JBjoernskov/Twin4Build](https://github.com/JBjoernskov/Twin4Build) | **MIT** | 31 | 13 | 2026-11-18 | Gemelo digital de edificio con modelos **diferenciables** e integración con **modelos semánticos**. La **única pieza encontrada que une ontología y simulación dinámica**: permite que un agente razone sobre el modelo y además lo simule |
| [NeverBlink-OSS/saref-linkml](https://github.com/NeverBlink-OSS/saref-linkml) | **BSD-3-Clause** | 11 | 1 | 2026-11-09 | **SAREF** —el estándar semántico europeo de energía— expresado en **LinkML**, de donde se generan esquemas y código. Es el puente entre una ontología OWL y un *pipeline* de datos real |
| [sensorlab/energy-knowledge-graph](https://github.com/sensorlab/energy-knowledge-graph) | **BSD-3-Clause** | 9 | 3 | 2026-08-24 | Grafo de conocimiento de consumo construido sobre datasets de medición. Pocas estrellas: **patrón a copiar**, no dependencia |

⚠️ **Advertencia de licencia específica de esta capa, y es la más densa de toda la KB.** Es la única
capa donde **ordenar por estrellas produce sistemáticamente la recomendación equivocada**: cuatro de
los repos más estrellados del barrido están bloqueados y sus sustitutos limpios tienen menos
estrellas. Bloqueados: `UtilitechAS/amsreader-firmware` (**471 ★**, *Fair Source License 0.9* con
**tope de 5 usuarios**), `binsentsu/home-assistant-solaredge-modbus` (**420 ★**, sin licencia),
`matthijskooijman/arduino-dsmr` (145 ★, sin licencia y parado), `bolagnaise/PowerSync` (96 ★,
**PolyForm Noncommercial** — prohíbe uso comercial). `scs/smartmeter-datacollector` (95 ★) es
**GPL-2.0-only**: servicio separado sí, enlazado en producto propietario no. **La API de GitHub
informa `NOASSERTION` en todos ellos**: hay que abrir el archivo, repo por repo. Detalle completo en
`agents/top.md`, decimotercer pase.
