---
industry: energy
region: Global
updated: 2026-11-20
---

# 🏭 Verticales de partida — Energy

> Plataformas verticales reales y funcionales, customizables con una capa agéntica arriba.
> Equivalentes energéticos de lo que Odoo es a ERP u OpenMRS a salud.
> Verificadas contra la GitHub REST API el **2026-11-20**.

## SCADA / EMS / ADMS — el núcleo operativo

| Plataforma | Licencia | URL | Stack | Caso de uso | Stars | Región origen |
|------------|----------|-----|-------|-------------|-------|---------------|
| **{json:scada}** | GPL-3.0 | [riclolsen/json-scada](https://github.com/riclolsen/json-scada) | Node.js 24, Go 1.26, .NET 8, MongoDB 8, PostgreSQL 18, TimescaleDB, Grafana 13 | SCADA/EMS/IIoT completo con IEC 61850, ICCP, IEC 60870-5-101/104, DNP3, OPC-UA, OPC-DA, Modbus, MQTT/Sparkplug B | 513 | **LATAM (Brasil)** |
| **OSHMI** | GPL-3.0 | [riclolsen/OSHMI](https://github.com/riclolsen/OSHMI) | HMI de subestación | HMI SCADA para subestaciones y automatización | 467 | **LATAM (Brasil)** |
| **OpenEMS** | AGPL-3.0 | [OpenEMS/openems](https://github.com/OpenEMS/openems) | Java/OSGi + Angular | Energy Management System modular; desplegado en utilities europeas | 1631 | EMEA (Alemania) |
| **OpenRemote** | AGPL-3.0 | [openremote/core](https://github.com/openremote/core) | Java + Angular, MQTT | Plataforma IoT/EMS: assets, reglas, dashboards, gestión de EV | 2162 | EMEA (Países Bajos) |
| **MyEMS** | MIT | [MyEMS/myems](https://github.com/MyEMS/myems) | Python + React | EMS para edificios, fábricas, malls, hospitales y campus: electricidad, agua, gas, frío, calor | 763 | APAC (China) |

## Optimización y operación de activos

| Plataforma | Licencia | URL | Stack | Caso de uso | Stars | Región origen |
|------------|----------|-----|-------|-------------|-------|---------------|
| **EOS (Akkudoktor)** | Apache-2.0 | [Akkudoktor-EOS/EOS](https://github.com/Akkudoktor-EOS/EOS) | Python, FastAPI | Energy Optimization System: optimiza distribución y despacho con PV, batería y tarifa dinámica | 1731 | EMEA (Alemania) |
| **Scaphandre** | Apache-2.0 | [hubblo-org/scaphandre](https://github.com/hubblo-org/scaphandre) | Rust | Agente de metrología de consumo energético de cómputo; exporta a Prometheus | 2019 | EMEA (Francia) |
| **vessim** | MIT | [dos-group/vessim](https://github.com/dos-group/vessim) | Python | Simulación de sistemas energéticos de **datacenter** (carbono, batería, PV on-site) | 103 | EMEA (Alemania) |

## Movilidad eléctrica y carga (el vertical con más tracción open source)

| Plataforma | Licencia | URL | Stack | Caso de uso | Stars | Región origen |
|------------|----------|-----|-------|-------------|-------|---------------|
| **evcc** | MIT | [evcc-io/evcc](https://github.com/evcc-io/evcc) | Go + Vue | Carga inteligente de EV con excedente solar y tarifa dinámica; **el repo energético open source con más tracción de esta KB** (7638 ★ / 1649 forks) | 7638 | EMEA (Alemania) |
| **SteVe** | GPL-3.0 | [steve-community/steve](https://github.com/steve-community/steve) | Java | Servidor OCPP y gestión de estaciones de carga en producción | 1151 | EMEA (Alemania) |
| **ocpp (Python)** | MIT | [mobilityhouse/ocpp](https://github.com/mobilityhouse/ocpp) | Python | Implementación del Open Charge Point Protocol | 1052 | EMEA |

## Conectividad de campo / protocolos (la capa que nadie quiere escribir dos veces)

| Plataforma | Licencia | URL | Stack | Caso de uso | Stars | Región origen |
|------------|----------|-----|-------|-------------|-------|---------------|
| **node-opcua** | MIT | [node-opcua/node-opcua](https://github.com/node-opcua/node-opcua) | TypeScript/Node | Stack OPC UA completo: puente a histórico industrial y PLC | 1671 | Global |
| **libiec61850** | GPL-3.0 | [mz-automation/libiec61850](https://github.com/mz-automation/libiec61850) | C | Librería de referencia de los protocolos IEC 61850 (MMS, GOOSE, SV) | 1253 | EMEA (Alemania) |
| **mbmd** | BSD-3-Clause | [volkszaehler/mbmd](https://github.com/volkszaehler/mbmd) | Go | Daemon de lectura de medidores e inversores Modbus | 281 | EMEA (Alemania) |

## Control distribuido y simulación operativa (añadido en el segundo pase del 2026-11-20)

| Plataforma | Licencia | URL | Stack | Caso de uso | Stars | Región origen |
|------------|----------|-----|-------|-------------|-------|---------------|
| **VOLTTRON** | **Apache-2.0** | [VOLTTRON/volttron](https://github.com/VOLTTRON/volttron) | Python, bus de mensajes, drivers BACnet/Modbus | Plataforma de **agentes en el borde**: corre lógica de control junto al equipo, con aislamiento entre agentes. PNNL/Battelle; desplegada en edificios y equipos de red | 504 | North America |
| **GridLAB-D** | ⚠️ **licencia propia Battelle v5.3** (no OSI) | [gridlab-d/gridlab-d](https://github.com/gridlab-d/gridlab-d) | C++ | Simulación de distribución que acopla red, edificios, mercados y DER en un solo motor; del DOE/PNNL | 221 | North America |
| **OpenDSS (vía dss-extensions)** | BSD-3 + derechos gov. EE. UU. | [dss-extensions/OpenDSSDirect.py](https://github.com/dss-extensions/OpenDSSDirect.py) | Python / C-API | Motor de análisis de distribución de EPRI, accesible desde Python: el estándar de facto para estudios de alimentadores | 119 | Global |

**Por qué `VOLTTRON` importa para la arquitectura de un engagement**: resuelve el problema que las
otras plataformas de esta página dejan abierto. `OpenEMS` y `openremote` son **AGPL** y
`json-scada` es **GPL**; poner lógica propietaria dentro de ellas contamina. `VOLTTRON` es
**Apache-2.0** y está diseñado precisamente para alojar agentes de terceros. Es el lugar donde la
capa agéntica MIT puede *ejecutarse* sin cruzar un límite de licencia.

**Nota de gobernanza**: el proyecto está migrando a la Eclipse Foundation
([eclipse-volttron/volttron](https://github.com/eclipse-volttron/volttron), Apache-2.0). Hoy esa org
tiene **0 ★ y último push 2026-07-21**: la fuente de verdad sigue siendo `VOLTTRON/volttron`. Vigilar
el cambio antes de fijar una dependencia en un contrato plurianual.

## Upstream de petróleo y gas

El subsector existe en open source, es activo y es **100 % GPL-3.0** en lo que se encontró:

| Plataforma | Licencia | URL | Stack | Caso de uso | Stars | Región origen |
|------------|----------|-----|-------|-------------|-------|---------------|
| **OPM Flow** | **GPL-3.0** | [OPM/opm-simulators](https://github.com/OPM/opm-simulators) | C++ | Simulación de yacimientos (black-oil, composicional, CO₂): referencia open source del sector | 182 | EMEA (Noruega/Alemania) |
| **ERT** | **GPL-3.0** | [equinor/ert](https://github.com/equinor/ert) | Python | Ensembles de modelos dinámicos y asimilación de datos; herramienta de producción de **Equinor** | 167 | EMEA (Noruega) |
| **webviz-subsurface** | **GPL-3.0** | [equinor/webviz-subsurface](https://github.com/equinor/webviz-subsurface) | Python / Dash | Dashboards de datos de subsuelo | 62 | EMEA (Noruega) |

**Consecuencia directa**: el patrón de "empotrar la librería en el producto del cliente" —válido con
`PyPSA`, `pvlib` o `pandapower`— **no aplica** aquí. En O&G hay que tratar el simulador como el
sistema de registro: contenedor aparte, intercambio por archivos o API, y la capa de IA del lado de
afuera. Presupuestar la integración, no la licencia.

## Plataformas de datos de mercado

| Plataforma | Licencia | URL | Stack | Caso de uso | Stars | Región origen |
|------------|----------|-----|-------|-------------|-------|---------------|
| **API_XM** | **MIT** (`XM S.A. E.S.P.`) | [EquipoAnaliticaXM/API_XM](https://github.com/EquipoAnaliticaXM/API_XM) | Python | Acceso a datos del mercado eléctrico colombiano —generación, demanda, precio de bolsa, emisiones— publicado por el **operador del Sistema Interconectado Nacional** | 75 | **LATAM (Colombia)** |
| **hass-entso-e** | Apache-2.0 | [JaccoR/hass-entso-e](https://github.com/JaccoR/hass-entso-e) | Python | Precios day-ahead de ENTSO-E: la vía más corta a precio horario europeo en un piloto | 280 | EMEA |

**23 plataformas reales** (16 del primer pase + 7 del segundo); **34 tras los pases tercero y
cuarto** (ver secciones fechadas). Ninguna fila es plantilla.

## Comercial de utility: facturación, medición y gestión de cliente (añadido en el tercer pase del 2026-11-20)

Esta KB tenía cubierto el lado **operativo** (SCADA, EMS, ADMS, protocolos) y nada del lado
**comercial**. En un encargo de utility el CIS/billing suele ser la mitad del alcance. No existe un
"Odoo de la energía" —un único sistema que cubra ERP + CRM + facturación + MDM—; lo que hay es un
conjunto de piezas que se componen, y conviene decirlo así en una propuesta.

| Plataforma | Licencia | Qué cubre | Stars | Forks | Último push | Región origen |
|------------|----------|-----------|-------|-------|-------------|---------------|
| [killbill/killbill](https://github.com/killbill/killbill) | **Apache-2.0** | Facturación y pagos por suscripción y por uso: catálogo de tarifas, medición de consumo, facturación, cobros. Maduro y desacoplado del sector | 5858 | 988 | 2026-11-19 | North America |
| [openmeterio/openmeter](https://github.com/openmeterio/openmeter) | **Apache-2.0** | Medición y agregación de eventos de uso a gran escala para facturar por consumo (hoy parte de Kong) | 2457 | 245 | 2026-11-19 | EMEA |
| [EnAccess/micropowermanager](https://github.com/EnAccess/micropowermanager) | **MIT** | Gestión completa de **utilities descentralizadas**: clientes, medidores, tarifas, prepago y cobro para mini-redes. Pensado para electrificación distribuida | 30 | 30 | 2026-11-19 | EMEA |
| [frappe/erpnext](https://github.com/frappe/erpnext) | ⚠️ **GPL-3.0** | ERP generalista de gran tracción, base sobre la que existen apps de utility billing | 41460 | 13572 | 2026-11-20 | APAC |
| [navariltd/utility-billing](https://github.com/navariltd/utility-billing) | ⚠️ **AGPL-3.0** | App de facturación de servicios y gestión de propiedades sobre ERPNext: lecturas de medidor, tarifas, inquilinos | 70 | 84 | 2026-11-18 | EMEA |

### Cómo elegir entre ellas (la decisión real)

- **Utility regulada de tamaño medio, entregable propietario** → `killbill` (Apache-2.0) como motor
  de facturación + `openmeter` (Apache-2.0) para la agregación de consumo. Ambos permisivos: el
  producto resultante se puede cerrar. Ninguno sabe de energía, así que la lógica tarifaria
  regulatoria es desarrollo propio — presupuestarla, no asumirla.
- **Mini-red, electrificación rural, prepago** → `micropowermanager` (MIT). Es el único que entiende
  el dominio de fábrica. 30 ★: funciona, pero no hay comunidad que sostenga un incidente; evaluar
  soporte propio.
- **ERPNext sólo si el cliente ya lo usa.** `erpnext` es GPL-3.0 y la app de utility billing es
  **AGPL-3.0**. Un SaaS construido sobre esa app activa la cláusula de red: hay que ofrecer el
  código del servicio. Para un entregable de marca blanca es, casi siempre, un no.

### Sala de control: la capa human-in-the-loop

| Plataforma | Licencia | Qué cubre | Stars | Forks | Último push | Región origen |
|------------|----------|-----------|-------|-------|-------------|---------------|
| [opfab/operatorfabric-core](https://github.com/opfab/operatorfabric-core) | **MPL-2.0** | Plataforma LF Energy de sala de control: agrega y encamina tarjetas de acción al operador, con trazabilidad y aceptación explícita | 42 | 29 | 2026-11-19 | EMEA |

Es el destino natural de cualquier recomendación agéntica en operación de red. Ningún TSO permite
ejecución automática de maniobras; sin una capa de aceptación humana trazable, un piloto agéntico
de red no pasa de demo.

## ERP/CRM generalista: la respuesta honesta a "¿cuál es el Odoo de la energía?" (cuarto pase, 2026-11-20)

El tercer pase estableció que no existe un sistema único que cubra ERP + CRM + facturación + MDM para
utilities. Este pase lo confirmó buscándolo explícitamente y conviene cerrar la pregunta con datos:

**No existe ningún ERP/CRM open source específico de energía con licencia MIT o Apache 2.0.** Lo que
hay son dos caminos:

| Plataforma | Licencia | Qué cubre | Stars | Forks | Último push | Región origen |
|------------|----------|-----------|-------|-------|-------------|---------------|
| [apache/ofbiz-framework](https://github.com/apache/ofbiz-framework) | **Apache-2.0** | Suite Java de ERP + CRM + e-commerce + SCM + MRP. Proyecto top-level de Apache desde 2006. **La opción permisiva más madura** para la capa empresarial | 1151 | 766 | 2026-11-19 | Global |
| [ishandutta2007/Awesome-Energy-Utilities-CRM](https://github.com/ishandutta2007/Awesome-Energy-Utilities-CRM) | **MIT** | Catálogo curado de CRM, facturación y medición para utilities. Creado 2026-10-12; **0 ★, sin tracción** — útil como punto de partida de búsqueda, no como referencia | 0 | 0 | 2026-10-12 | Global |

**La decisión, dicha sin rodeos**: `OFBiz` es Apache-2.0, maduro (766 forks) y **no sabe nada de
energía**. `ERPNext` tiene 41k ★ pero es GPL-3.0 y su app de utility billing es AGPL-3.0. Por tanto:

- **Entregable propietario / marca blanca** → `OFBiz` (Apache-2.0) para ERP/CRM + `killbill`
  (Apache-2.0) para facturación + `openmeter` (Apache-2.0) para agregación de consumo. Las tres
  permisivas. La lógica tarifaria regulada es **desarrollo propio**: presupuestarla explícitamente.
- **El cliente ya usa ERPNext** → extenderlo, aceptando el régimen GPL/AGPL y sus consecuencias
  para un SaaS multi-tenant.
- **Lo que no hay que hacer**: prometer un "vertical energético open source listo" en la capa
  comercial. No existe. Lo que existe es un conjunto de piezas permisivas y un trabajo de
  integración real y facturable.

## Flexibilidad y verificación de ahorro como plataforma (añadido en el cuarto pase)

| Plataforma | Licencia | Qué cubre | Stars | Forks | Último push | Región origen |
|------------|----------|-----------|-------|-------|-------------|---------------|
| [FlexMeasures/flexmeasures](https://github.com/FlexMeasures/flexmeasures) | **Apache-2.0** | Plataforma LF Energy de *scheduling* de flexibilidad: baterías, carga de EV, bombas de calor, con forecasting integrado. 248 issues abiertas = comunidad activa | 217 | 66 | 2026-11-19 | EMEA |
| [opendsm/opendsm](https://github.com/opendsm/opendsm) | **Apache-2.0** | Métodos estándar de consumo normalizado (NMEC) y ahorro medido. Linaje OpenEEmeter/CalTRACK, diez años de historia | 244 | 76 | 2026-11-14 | North America |
| [GridProtectionAlliance/openPDC](https://github.com/GridProtectionAlliance/openPDC) | **MIT** | Concentrador de datos de sincrofasores (IEEE C37.118) de producción: observabilidad de red de alta resolución sin plataforma propietaria | 159 | 67 | 2026-11-15 | North America |

**Esta fila cambia la forma de vender un proyecto de eficiencia.** El patrón habitual —"ponemos IA a
optimizar y el cliente ahorra"— se cae en la primera auditoría porque el ahorro no es demostrable con
un método aceptado. `FlexMeasures` (decide cuándo) + `opendsm` (certifica cuánto), ambas Apache-2.0 y
empotrables en un entregable cerrado, convierten el ahorro en una cifra firmable. Es, de todo lo
encontrado en los cuatro pases, la combinación con el camino más corto a facturación.

## Plataformas de datos de mercado: ampliación del quinto pase (2026-11-20)

La sección de arriba listaba las fuentes institucionales por país. Lo que faltaba son las **dos
librerías canónicas** que leen un mercado entero con una sola interfaz. No son plataformas verticales
en el sentido de "sistema a customizar", pero son la **dependencia de arranque** de todas las
recetas: sin esta capa, un piloto empieza escribiendo *scrapers*.

| Plataforma | Licencia | Cobertura | ★ | Rol en un encargo |
|------------|----------|-----------|---|-------------------|
| [fboerman/entsoe-py](https://github.com/fboerman/entsoe-py) | **MIT** | Toda Europa vía API de ENTSO-E: precios, generación, carga, flujos | 745 | Primer día de cualquier proyecto EMEA |
| [gridstatus/gridstatus](https://github.com/gridstatus/gridstatus) | **BSD-3-Clause** | CAISO, ERCOT, PJM, MISO, SPP, NYISO, ISO-NE | 456 | Primer día de cualquier proyecto North America |
| [singularity-energy/open-grid-emissions](https://github.com/singularity-energy/open-grid-emissions) | **MIT** | Generación y **emisiones horarias** de EE. UU. | 96 | Capa de carbono verificable (sólo EE. UU.) |
| [entsoe/application-profiles-library](https://github.com/entsoe/application-profiles-library) | **Apache-2.0** | Artefactos RDFS/SHACL oficiales de CGMES | 29 | Validación de intercambio de modelos de red en EMEA |
| [jo20ow/Obsyd](https://github.com/jo20ow/Obsyd) | ⚠️ **AGPL-3.0** | 37 zonas de oferta europeas, 15 min | 12 | Útil para análisis interno; **no en SaaS de cliente** |

**Decisión práctica:** en EMEA, `entsoe-py` (MIT) y no `Obsyd` (AGPL). En North America, `gridstatus`
más `open-grid-emissions`, ambos permisivos, encadenables con `carbon-aware-sdk` (MIT, ya en la KB).
**En LATAM y APAC no existe equivalente de cobertura regional**: hay que ir país por país (`API_XM`
en Colombia, `OMIEData` en España) y presupuestar la ingesta.

## Dimensionado de activo como servicio: la plataforma que faltaba antes de cualquier EMS

Antes de instalar un EMS hay que decidir **qué activo instalar**. Esa pregunta tenía su plataforma
abierta y esta KB no la tenía:

| Plataforma | Licencia | Qué resuelve | ★ |
|------------|----------|--------------|---|
| [NatLabRockies/REopt_API](https://github.com/NatLabRockies/REopt_API) | ⚠️ BSD-3 + **marca REopt®** | Mezcla óptima de solar + BESS + genset contra la tarifa real del emplazamiento. Es el motor de reopt.nrel.gov | 128 |
| [sylvan-energy/gridpath](https://github.com/sylvan-energy/gridpath) | **Apache-2.0** | Planificación **y** operación en un mismo modelo | 138 |
| [NatLabRockies/HOPP](https://github.com/NatLabRockies/HOPP) | **BSD-3-Clause** | Plantas híbridas: renovable + almacenamiento + H₂ | 41 |
| [NatLabRockies/GEOPHIRES-X](https://github.com/NatLabRockies/GEOPHIRES-X) | **MIT** | Tecno-economía geotérmica completa | 67 |
| [NatLabRockies/OpenStudio](https://github.com/NatLabRockies/OpenStudio) | ⚠️ BSD-3 + **marca OpenStudio®** | SDK de modelado energético de edificio sobre EnergyPlus | 660 |

**Secuencia correcta en un encargo de energía distribuida:** `REopt_API` decide el activo →
`OpenEMS`/`FlexMeasures` lo opera → `opendsm` certifica el ahorro. Las tres piezas existen, son
abiertas y **no estaban conectadas en esta KB** hasta este pase.

⚠️ **Las dos marcadas no son BSD limpias.** `REopt®` y `OpenStudio®` llevan cláusula de marca: el
nombre no puede aparecer en el producto ni en material promocional, y una versión modificada debe
citar el original. Es la misma restricción ya registrada para `EnergyPlus`. **No bloquea el uso;
bloquea el naming.**

## Datos sintéticos de consumo: la plataforma que desbloquea el entrenamiento en EMEA

| Plataforma | Licencia | Qué resuelve | ★ |
|------------|----------|--------------|---|
| [OpenSynth-energy/OpenSynth](https://github.com/OpenSynth-energy/OpenSynth) | **Apache-2.0** | Modelos generadores de perfiles **sintéticos** de consumo de contador (cohorte LF Energy) | 77 |
| [Enapter/marketplace](https://github.com/Enapter/marketplace) | **MIT** | *Blueprints* para integrar cualquier dispositivo en un EMS | 61 |

**Por qué `OpenSynth` es estratégico y no accesorio.** La inteligencia de mercado de este pase
registra que la Comisión Europea señala **GDPR, recolección y preprocesado** como barreras para
entrenar modelos de red. Un cliente europeo que no puede exportar datos de medición no puede entrenar
`openstef` ni `BuildingsBench` — pero **sí** puede entrenar sobre perfiles sintéticos y luego
afinar en sitio. `OpenSynth` convierte un bloqueo legal en una fase de proyecto.

**`Enapter/marketplace`** resuelve el problema aburrido y caro de todo EMS: cada inversor, contador y
cargador habla distinto. Es un catálogo MIT de integraciones de dispositivo, no una plataforma.

## El riesgo de licencia es el criterio de selección, no una nota al pie

Este vertical está dominado por **copyleft**, a diferencia de la capa de agentes (casi toda MIT):

- **AGPL-3.0** (`OpenEMS`, `openremote/core`): la cláusula de red obliga a ofrecer el código fuente
  a los usuarios del servicio. Para un SaaS multi-tenant de cliente esto **es** la decisión
  arquitectónica: o se acepta liberar, o se compra licencia comercial, o se aísla por API.
  OpenRemote ofrece licenciamiento comercial alternativo.
- **GPL-3.0** (`json-scada`, `OSHMI`, `SteVe`, `libiec61850`): copyleft fuerte. Ejecutar como
  proceso separado y hablarle por protocolo/API **no** deriva obra; enlazarlo en el binario del
  cliente **sí**. MZ Automation vende licencia comercial de `libiec61850` precisamente para eso.
- ⚠️ **Licencia propia no OSI** (`GridLAB-D`): el permiso es amplio (usar, modificar, distribuir,
  sublicenciar, vender) pero (1) prohíbe usar el nombre *Battelle* **en cualquier forma** sin
  consentimiento escrito, (2) arrastra derechos del gobierno de EE. UU. cuyo término exacto "se
  identifica consultando a Battelle o al DOE" —o sea, **no está en el archivo**— y (3) **no figura
  en la lista OSI ni en SPDX**, así que un gate automático de compliance la marcará como
  desconocida. Resolver con legal **antes** de la auditoría, no durante.
- ⚠️ **GPL-3.0 sin alternativa permisiva** (`OPM Flow`, `equinor/ert`): en upstream de O&G no se
  encontró ningún equivalente permisivo con tracción. No es una opción entre varias: es la
  restricción del subsector.
- **Permisivas y seguras para empotrar**: `MyEMS` (MIT), `evcc` (MIT), `ocpp` (MIT), `node-opcua`
  (MIT), `EOS` (Apache-2.0), `scaphandre` (Apache-2.0), `vessim` (MIT), `mbmd` (BSD-3).

**Implicación de arquitectura**: para un engagement comercial, poner la plataforma copyleft
(json-scada, OpenEMS) como **sistema de registro aislado detrás de su propia API**, y construir la
capa agéntica —que es MIT— como servicio separado. Ese límite de proceso es lo que mantiene limpio
el código propietario del cliente.

## Sexto pase (2026-11-20): se volvió a buscar el "Odoo de la energía" y la respuesta del cuarto pase se confirma

Este pase repitió la búsqueda a propósito, con la consulta más amplia posible —plataforma de utility
que cubra ERP + CRM + **gestión de datos de medición (MDM)**, con licencia MIT o Apache— para
comprobar si la conclusión del cuarto pase seguía en pie. **Sigue en pie, y conviene dejar constancia
de qué se encontró en su lugar, para que nadie vuelva a gastar el tiempo.**

**Lo que devuelve la búsqueda son productos comerciales, no open source.** Ninguno de estos declara
licencia abierta y todos aparecen en lo alto de los resultados de "plataforma energía utility ERP CRM
MDM":

| Candidato | Qué es en realidad | Veredicto |
|-----------|--------------------|-----------|
| **Neta Open Suite** (Eng) | Suite de utility con CRM, ERP, gestión de pagos y un módulo de MDM. El "Open" del nombre **no indica licencia abierta** | ❌ comercial |
| **energy.platform** (Cloudflight) | Conecta CRM/ERP/sistemas operativos existentes y ofrece **API REST abierta** a datos de medición | ❌ comercial, API abierta ≠ código abierto |
| **MECOMS** | Meter Data Management comercial | ❌ comercial |
| **Jmix** | Plataforma de **desarrollo** con casos de uso de monitorización energética, mantenimiento de activos y flujos de datos de medición | ⚠️ es un framework de desarrollo, no un vertical energético |

**El falso positivo que más confunde, y hay que nombrarlo**: un nombre con la palabra *"Open"* no es
una licencia. **Neta Open Suite** es el caso exacto. Mismo fenómeno que esta KB ya catalogó con los
términos de búsqueda inutilizables: la palabra está, el significado no.

**Lo que sí es open source y ya estaba catalogado** (sin cambios en el veredicto): `opentaps/opentaps_seas`
(**LGPL-3.0**, 88 ★, 47 forks, ⚠️ **sin push desde 2024-02-07** — el proyecto pasó de ERP a *smart
energy* en 2019 y su suite ERP/CRM original está archivada como `opentaps-1`, `NOASSERTION`, último
push 2019); `EnAccess/micropowermanager` (**MIT**, 30 ★, 30 forks, **136 issues abiertas**, push
2026-11-19 — vivo y la única opción permisiva real para utility descentralizada o mini-red, con CRM y
*ticketing* incluidos); y la vía compuesta del cuarto pase: `apache/ofbiz-framework` (Apache-2.0) +
`killbill` (Apache-2.0) + `openmeter` (Apache-2.0).

**La conclusión operativa no cambia y se refuerza con dos pases de evidencia**: **no existe un ERP/CRM
open source específico de energía con licencia permisiva.** Lo que existe es un conjunto de piezas
permisivas más integración, y la lógica tarifaria regulada es **siempre desarrollo propio**. Para
mini-red y acceso a la energía, `micropowermanager` es la excepción que sí cubre el vertical completo
con MIT — y su relación de 136 issues sobre 30 ★ con push de esta semana es, por la regla del quinto
pase, señal de equipo activo.

## Séptimo pase (2026-11-20): el vertical de carga de EV sí tiene su "Odoo", y se llama EVerest + CitrineOS

Los pases 4 y 6 concluyeron que **no existe un "Odoo de la energía"** — una plataforma vertical única,
customizable, que cubra el negocio entero de una utility. Esa conclusión se mantiene para la utility.
**Para el subsector de carga de vehículo eléctrico, en cambio, la respuesta es que sí existe**, y este
pase la nombra: dos plataformas permisivas, complementarias, con gobernanza de fundación una y
comunidad amplia la otra.

| Plataforma | Licencia | ★ / forks | Qué es | Papel en una propuesta |
|-----------|----------|-----------|--------|------------------------|
| [EVerest/EVerest](https://github.com/EVerest/EVerest) | Apache-2.0 | 298 / 215 | Stack de software de carga completo, **proyecto LF Energy** | La base cuando el cliente **fabrica o opera** la estación |
| [citrineos/citrineos-core](https://github.com/citrineos/citrineos-core) | Apache-2.0 | 309 / 175 | **CSMS** (Charging Station Management System) OCPP 2.0.1 | La base cuando el cliente **gestiona una red** de estaciones de terceros |

**Por qué esto es una plataforma vertical y no una librería.** Un CSMS es el equivalente funcional de
un ERP para un operador de carga: gestiona activos (estaciones), transacciones (sesiones de carga),
tarifas, autorización de usuarios, y se integra con roaming y facturación. `citrineos-core` es
Apache-2.0 y habla **OCPP 2.0.1**, la versión que las licitaciones europeas ya exigen. La alternativa
histórica que esta KB tenía catalogada, [`steve-community/steve`](https://github.com/steve-community/steve)
(1151 ★), es **GPL-3.0** y OCPP 1.6: excelente como referencia, bloqueante como base de producto
cerrado. Ese es exactamente el tipo de decisión que este archivo existe para informar.

### El stack de prueba, que es lo que hace el proyecto vendible

La razón por la que este vertical es proponible con bajo riesgo es que **se puede probar entero sin
una sola estación física** — el mismo argumento que el pase 4 estableció para protocolos de
subestación, ahora disponible para carga:

| Capa | Repo | Licencia | Para qué |
|------|------|----------|----------|
| Carga sintética a escala | [SAP/e-mobility-charging-stations-simulator](https://github.com/SAP/e-mobility-charging-stations-simulator) | Apache-2.0 | Miles de estaciones OCPP-J simuladas contra el CSMS |
| Emulador de escritorio | [monta-app/ocpp-emulator](https://github.com/monta-app/ocpp-emulator) | Apache-2.0 | Demo ejecutable en una laptop, para la reunión |
| Simulador para agentes | [shiv3/ocpp-cp-simulator](https://github.com/shiv3/ocpp-cp-simulator) | Apache-2.0 | Se declara explícitamente *for AI agent testing* |
| Protocolo, incl. **OCPP 2.1** | [tommymalmqvist/rust-ocpp](https://github.com/tommymalmqvist/rust-ocpp) | Apache-2.0 | La única librería del conjunto que ya cubre 2.1 |
| Firmware de estación | [ChargeLab/OpenOCPP](https://github.com/ChargeLab/OpenOCPP) | Apache-2.0 | Lado embarcado, si el cliente fabrica hardware |
| Piloto residencial | [lbbrhzn/ocpp](https://github.com/lbbrhzn/ocpp) | MIT | Prueba en casa vía Home Assistant, coste cero |
| Roaming entre operadores | [ocpi/ocpi](https://github.com/ocpi/ocpi) | ⚠️ **NOASSERTION** | Especificación OCPI — **leer licencia antes de incorporar** |

⚠️ La única pieza con riesgo de licencia del stack es `ocpi/ocpi` (602 ★, licencia no resuelta por la
API de GitHub). Hay alternativa permisiva para el roaming:
[`IZIVIA/ocpi-toolkit`](https://github.com/IZIVIA/ocpi-toolkit) (MIT, 39 ★), más pequeño pero con
licencia clara.

## Gemelo digital y conectividad de campo como plataforma (séptimo pase)

Ninguna de estas es energética por diseño; las tres se usan en el sector y las tres son customizables
con IA encima, que es el criterio de este archivo.

| Plataforma | Licencia | ★ / forks | Qué es | Dónde encaja en energía |
|-----------|----------|-----------|--------|--------------------------|
| [thingsboard/thingsboard-gateway](https://github.com/thingsboard/thingsboard-gateway) | Apache-2.0 | 2204 / 1008 | Gateway IoT multiprotocolo hacia la plataforma ThingsBoard | Ingesta de medidores, inversores y PLC sin escribir drivers |
| [eclipse-ditto/ditto](https://github.com/eclipse-ditto/ditto) | EPL-2.0 | 953 / 297 | Framework de gemelo digital de Eclipse IoT | Estado de activo consultable: la capa que un agente necesita para "saber" |
| [syzygyhack/open-foundry](https://github.com/syzygyhack/open-foundry) | Apache-2.0 | 137 / 40 | Plataforma de ontología para gemelos operativos | Modelo semántico de planta/subestación sobre el que razona el LLM |

**La decisión real entre ellas.** `thingsboard-gateway` resuelve *adquisición* (hablar 30+
protocolos); `ditto` resuelve *representación* (un gemelo consultable por API); `open-foundry` resuelve
*semántica* (qué significa cada señal). En un proyecto de agentes energéticos se necesitan las tres
capas, y el error frecuente es comprar una creyendo que cubre las otras dos. ⚠️ `ditto` es **EPL-2.0**:
copyleft débil, compatible con producto comercial pero con obligación de publicar modificaciones del
propio Ditto.

## Cómo customizar con AI

1. Desplegar la plataforma base sin tocar su código (contenedor, su propia licencia, su propia API).
2. Añadir la capa agéntica como **servicio aparte**: `PowerMCP` / `EnergyPlus-MCP` / `pypsa-mcp`
   exponen las herramientas de ingeniería por MCP.
3. Envolver los flujos existentes con agentes que lean del histórico y escriban **solo** vía la API
   de la plataforma — nunca al actuador directamente.
4. UI conversacional sobre el sistema base, con los límites de seguridad en el servicio, no en el prompt.

---
*Ver `compose/patterns.md` para recetas concretas que combinan estas plataformas con los agentes.*
