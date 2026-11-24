---
industry: energy
region: Global
updated: 2026-11-24
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
| **OpenEMS** | ⚠️ **DOBLE, por componente**: **EPL-2.0** (Edge + Backend) / **AGPL-3.0** (UI) — ver nota abajo | [OpenEMS/openems](https://github.com/OpenEMS/openems) | Java/OSGi + Angular | Energy Management System modular; desplegado en utilities europeas | 1634 | EMEA (Alemania) |
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
otras plataformas de esta página dejan abierto. `openremote` es **AGPL** y `json-scada` es **GPL**;
poner lógica propietaria dentro de ellas contamina. (`OpenEMS` **ya no pertenece a ese grupo**: su
Edge y su Backend son **EPL-2.0** y sólo la UI es AGPL — ver la nota de licencia por componente.) `VOLTTRON` es
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

## Decimocuarto pase (2026-11-21): `OpenEMS` no es AGPL, y eso cambia la arquitectura de un EMS de cliente

**Es la corrección más valiosa de este pase y nace de una contradicción interna de esta propia KB.**
El catálogo decía `OpenEMS` = **AGPL-3.0** en seis lugares; la Receta 35 de `compose/patterns.md`
decía `OpenEMS` = **EPL-2.0**. No podían ser las dos. Resuelto por byte-read: **las dos estaban mal
tal y como estaban escritas, porque el repo tiene dos licencias a la vez.**

Lo que dice el `README` de `OpenEMS/openems`, en su sección *License*:

| Componente | Licencia | Archivo (rama `develop`) | Byte-read |
|------------|----------|--------------------------|-----------|
| **OpenEMS Edge** (el controlador) | **Eclipse Public License 2.0** | `LICENSE-EPL-2.0` | **14.474 B**, verbatim EPL-2.0 (`eclipse`×2, `affero`×0, `lesser`×0) |
| **OpenEMS Backend** (el servidor) | **Eclipse Public License 2.0** | `LICENSE-EPL-2.0` | ídem |
| **OpenEMS UI** (Angular) | **GNU AGPL v3** | `LICENSE-AGPL-3.0` | **35.184 B**, verbatim AGPL-3.0 (`affero`×15, `eclipse`×0) |

Copyright 2016-2026 OpenEMS Association e.V.; incluye software desarrollado en FENECON GmbH.

### La consecuencia comercial, que es el punto

**La cláusula de red del AGPL afecta sólo a la interfaz de usuario.** El controlador y el servidor
—que son **exactamente las piezas que un integrador empotra y extiende**— son **EPL-2.0, que no
tiene cláusula de red.** Por tanto:

> Se puede construir un **EMS comercial sobre `OpenEMS` Edge + Backend y mantener el código propio
> cerrado**, siempre que la UI Angular se sustituya por una propia o se trate por separado.

Eso **invierte** el consejo que esta KB venía dando para `OpenEMS` ("AGPL → aislar detrás de una
API" / "o se acepta liberar o se compra licencia"). Para `openremote` el consejo **sigue siendo
correcto** y se ha re-verificado (ver abajo); para `OpenEMS` era una restricción que no existía, y
que descartaba de facto la plataforma EMS **más desplegada de EMEA** (1.634 ★, utilities europeas).

### `openremote`: el positivo previo de la KB se confirma, y su archivo de licencia enseña otra cosa

`openremote` **sí es AGPL-3.0-or-later** — confirmado en el propio archivo: *"you can redistribute
it and/or modify it under the terms of the GNU Affero General Public License ... either version 3 ...
or any later version"*. **El registro previo de la KB era correcto y se mantiene** (T48).

Pero su `LICENSE.txt` mide **172.958 B / 2.697 líneas**, porque tras la concesión declara: *"This
software is a collective work, it combines the following independent works"*, y enumera **el
inventario de licencias de sus dependencias** (ANTLR BSD, aopalliance dominio público, logback
Eclipse Distribution License, cglib Apache-2.0, …).

⚠️ **Trampa de detección:** un `grep` de `LESSER` sobre ese archivo devuelve **35** coincidencias y
uno de `GNU GENERAL PUBLIC` devuelve **30** — un verificador automático etiquetaría `openremote`
como LGPL o GPL. **No lo es: es AGPL-3.0 y *envía* código de terceros bajo ~7 familias de licencia.**
Para un entregable de cliente, esa lista de materiales es justo lo que pide una revisión legal, y
está publicada: es un activo, no un problema, **si se lee como lo que es.**

- Los dos slugs están vivos y sirven el **mismo** `LICENSE.txt` (172.958 B):
  [`openremote/core`](https://github.com/openremote/core) (el que usa esta KB) y
  [`openremote/openremote`](https://github.com/openremote/openremote). Se mantiene `core`.

## ERP/CRM energético: por fin tiene nombre propio, es LGPL-3.0 y está parada

**Esto NO contradice la conclusión del cuarto y sexto pase: la confirma, y explica por qué.** Esos
pases cerraron la pregunta así: *"no existe ningún ERP/CRM open source específico de energía con
licencia **MIT o Apache 2.0**"*. Ese enunciado **sigue siendo cierto palabra por palabra**. Lo que
este pase añade es **el artefacto que ningún pase anterior había nombrado** —`opentaps` no aparecía
ni una sola vez en los ocho archivos— y la razón exacta de su ausencia: **es LGPL-3.0**, así que
**nunca podía aparecer en un barrido filtrado por MIT/Apache**. El filtro estaba bien y el hueco era
real; lo que faltaba era saber **qué** había justo al otro lado del filtro.

> **Lección de método, aplicable a todo hueco ya "cerrado" de cualquier KB:** un hueco medido con un
> filtro de licencia se cierra para *esa* licencia, no para el sector. Vale la pena re-ejecutar la
> consulta **sin** el filtro una vez, no para cambiar la conclusión sino para **poder nombrar lo que
> queda fuera**. Un cliente que pregunta *"¿y no hay nada?"* merece "sí hay uno, es LGPL-3.0 y está
> parado desde 2024" en lugar de "no hay nada permisivo".

Conviene registrarlo **con sus dos defectos**, porque es lo que va a aparecer en cualquier búsqueda
de cliente:

| Plataforma | Licencia | Repo | Estado | ★ |
|------------|----------|------|--------|---|
| **opentaps SEAS** | ⚠️ **LGPL-3.0** | [opentaps/opentaps_seas](https://github.com/opentaps/opentaps_seas) | *Smart Energy Applications Suite*. ⚠️ **sin push desde 2024-02-07** (~2,8 años) | 88 |
| **opentaps 1** (ERP+CRM Java original) | NOASSERTION | [opentaps/opentaps-1](https://github.com/opentaps/opentaps-1) | Histórico; sin push desde 2019 | 23 |

`opentaps` hizo en 2019 la transición *"de ERP a Smart Energy"* y su trabajo energético se apoya en
protocolos industriales estándar (**MODBUS**, **BACnet**). Es el único candidato real de "Odoo del
sector energético" encontrado — y **no es permisivo ni está vivo**. La lectura honesta para un
cliente: **no existe hoy un ERP/CRM energético open source permisivo y mantenido**; lo que hay es
`Apache OFBiz` (Apache-2.0) como **framework ERP genérico** sobre el que habría que construir el
vertical, que es un proyecto, no una adopción.

> ⚠️ **COLISIÓN DE NOMBRES, y cuesta un pase entero si se cae en ella:**
> [`opentap/opentap`](https://github.com/opentap/opentap) (**262 ★**, Keysight, automatización de
> **test de instrumentación**) **no tiene nada que ver** con `opentaps/*` (ERP → smart energy). Una
> sola letra de diferencia.
> Igual de peligroso: [`thliebig/openEMS`](https://github.com/thliebig/openEMS) (**798 ★**) es un
> **solver de campos electromagnéticos FDTD**, no un EMS; `OpenEMS/openems` (1.634 ★) es el Energy
> Management System. **Se diferencian sólo por la caja de las letras.** Al buscar `openems` en
> GitHub, los dos primeros resultados son proyectos de dominios distintos.

## El riesgo de licencia es el criterio de selección, no una nota al pie

Este vertical está dominado por **copyleft**, a diferencia de la capa de agentes (casi toda MIT):

- **AGPL-3.0** (`openremote/core`, y **sólo la UI** de `OpenEMS`): la cláusula de red obliga a ofrecer el código fuente
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

## Octavo pase (2026-11-20): el PPA como plataforma, y la confirmación externa de que no hay CIS de utility abierto

### Lo nuevo: contratación de energía (PPA) deja de ser una hoja de cálculo

Esta KB registraba el **dato de mercado** del PPA —LATAM firmando por debajo de 0,06 USD/kWh,
Equinix contratando eólica y solar con Auren en Brasil, Microsoft comprometiendo 2.700 M USD en São
Paulo— y **no tenía ninguna herramienta abierta para estructurarlo**. Es el artefacto que un cliente
corporativo pide primero: *¿a qué precio y con qué riesgo firmo?*

| Plataforma | Licencia | Qué cubre | Stars | Último push | Región origen |
|------------|----------|-----------|-------|-------------|---------------|
| [open-energy-transition/pypsa-ppa](https://github.com/open-energy-transition/pypsa-ppa) | **MIT** | Simulación y optimización de **Power Purchase Agreements** bajo distintos escenarios, sobre PyPSA | 8 | 2026-11-09 | EMEA |
| [open-energy-transition/earthpv](https://github.com/open-energy-transition/earthpv) | **MIT** | Mapeo de solar en tejado desde imagen satelital gratuita: inventario de DER que la distribuidora no tiene | 22 | 2026-11-20 | EMEA |
| [open-energy-transition/rooftopsenti](https://github.com/open-energy-transition/rooftopsenti) | **MIT**, ⚠️ **archivado** | Detección de solar en tejado con Sentinel-2 a escala país/estado/provincia | 7 | 2026-07-05 | EMEA |
| [catalyst-cooperative/pudl](https://github.com/catalyst-cooperative/pudl) | **MIT** | Formularios de FERC, EIA y EPA convertidos en datos listos para análisis (EE. UU.) | 621 | 2026-11-20 | North America |

⚠️ **`pypsa-ppa` tiene 8 ★.** Es MIT y resuelve el problema correcto, pero no hay comunidad detrás:
tratarlo como **punto de partida de un acelerador propio**, no como plataforma con soporte. La
dependencia sólida de esa pila es PyPSA (MIT, ya catalogado); `pypsa-ppa` es la capa de escenarios
sobre ella.

### Confirmación independiente: no existe CIS/MDM de utility open source permisivo

El tercer pase concluyó esto buscando en GitHub. El octavo lo volvió a medir **por un canal
distinto** (búsqueda web de plataformas de *utility billing / CIS / MDM* permisivas) y el resultado
es el mismo, lo que sube la confianza de la afirmación de "no encontrado" a "medido dos veces por
canales independientes":

- Lo que aparece como CIS/MDM de utility es **producto comercial** (Fluentgrid, SMART360): ninguno
  open source.
- Lo permisivo que existe es **facturación genérica, no energética**: `killbill` (Apache-2.0) y
  `openmeter` (Apache-2.0), ya catalogados arriba. Las alternativas de moda —Lago, Flexprice— son
  **AGPLv3**, lo que las descarta para un entregable cerrado.
- **La lógica tarifaria regulada sigue siendo desarrollo propio en los cuatro regiones.** Esa frase
  es un argumento de venta, no una disculpa: es alcance facturable y defendible.

⚠️ **Trampa de término, para no volver a gastar un pase en ella:** en GitHub y en la web de producto,
**`MDM` significa casi siempre *mobile device management***, no *meter data management*. Headwind MDM
(Apache-2.0), Fleet (MIT), MicroMDM y NanoMDM (MIT) son gestión de dispositivos Android y Apple y no
tienen nada que ver con medición eléctrica. Los términos que sí funcionan para medición siguen siendo
`"smart meter"`, `DLMS`, `COSEM`, `rtlamr` y `"meter reading"`.


## Añadidos del noveno pase (2026-11-20)

### Operación de carga de EV: la plataforma vertical que esta KB tenía a medias

El octavo pase catalogó el lado del **CSMS** (`steve` GPL-3.0, `EVerest` Apache-2.0, `evcc` MIT,
`mobilityhouse/ocpp` MIT). Falta registrar como vertical la capa de **protocolo con el vehículo**,
que es la que decide si el producto puede hacer Plug & Charge:

| Plataforma | Licencia | URL | Stack | Caso de uso | ★ | Región origen |
|------------|----------|-----|-------|-------------|---|---------------|
| **Josev (comunidad)** | **Apache-2.0** | [ecog-io/josev](https://github.com/ecog-io/josev) | Python | "Sistema operativo" de estación de carga V2G: orquesta ISO 15118 + OCPP en el poste | 164 | EMEA |
| **iso15118** | **Apache-2.0** | [ecog-io/iso15118](https://github.com/ecog-io/iso15118) | Python | Pila ISO 15118 **-2, -20, -8**: Plug & Charge, autenticación por certificado, V2G | 250 | EMEA |

**Decisión de arquitectura que esto habilita:** con `josev` + `iso15118` (ambos Apache-2.0) el
operador de carga puede ofrecer Plug & Charge **sin licenciar una pila propietaria y sin tocar
GPL**. Si además necesita back-office, `EVerest` (Apache-2.0) encaja permisivo y `steve` (GPL-3.0)
exige el límite de proceso de la regla de arquitectura.

### Flexibilidad doméstica como vertical en EMEA (EEBus + S2)

| Plataforma | Licencia | URL | Stack | Caso de uso | ★ | Región origen |
|------------|----------|-----|-------|-------------|---|---------------|
| **eebus-go** | **MIT** | [enbility/eebus-go](https://github.com/enbility/eebus-go) | Go | Stack EEBUS para hablar con bombas de calor, wallboxes y baterías domésticas | 123 | EMEA |
| **openeebus** | **Apache-2.0** | [NIBEGroup/openeebus](https://github.com/NIBEGroup/openeebus) | C (SHIP + SPINE) | Igual, publicado por el **fabricante** NIBE: referencia de conformidad del lado del equipo | 68 | EMEA (Suecia) |
| **FlexMeasures + S2** | **Apache-2.0** | [FlexMeasures/flexmeasures-s2](https://github.com/FlexMeasures/flexmeasures-s2) | Python | Mensajería **S2 (EN 50491-12-2)** sobre el motor FlexMeasures ya catalogado | 2 | EMEA |

Que un **fabricante de bombas de calor** publique el stack de protocolo extiende T2 más allá de los
operadores de red: en EMEA el integrador ya no necesita una pila EEBus propietaria para controlar un
activo térmico doméstico. El contrapunto honesto: **el tooling del estándar S2 tiene 2 estrellas** —
la norma está, la comunidad no.

### Ingeniería de subestación como producto customizable

| Plataforma | Licencia | URL | Stack | Caso de uso | ★ | Región origen |
|------------|----------|-----|-------|-------------|---|---------------|
| **Open-SCD** | **Apache-2.0** | [openscd/open-scd](https://github.com/openscd/open-scd) | Web components / TypeScript | Editor de **SCL (IEC 61850-6 Ed2)**: configuración de subestación digital | 145 | EMEA |

⚠️ **Estado real antes de proponerlo:** push **2026-01-12 (10 meses)** y **229 issues abiertas**. Es
el único editor SCL abierto y es Apache-2.0, lo que lo hace la base correcta para una herramienta de
ingeniería con capa agéntica encima; pero el mantenimiento hay que asumirlo en el presupuesto, no
darlo por hecho.

### Atlas del sistema eléctrico nacional (LATAM, México)

| Plataforma | Licencia | URL | Stack | Caso de uso | ★ | Región origen |
|------------|----------|-----|-------|-------------|---|---------------|
| **atlas-sen** | **MIT** (API dice `NOASSERTION`; rescatada en `LICENSE` crudo: *"Copyright (c) 2026 Batu Energy"*) | [batuenergy/atlas-sen](https://github.com/batuenergy/atlas-sen) | Web interactiva | Atlas abierto del **Sistema Eléctrico Nacional de México**: generación y transmisión | 10 | **LATAM (México)** |

Creado 2026-06-21, **push 2026-11-20 (hoy)**, respaldado por una empresa (Batu Energy). Es el
**segundo repo institucional de origen LATAM** que esta KB registra en energía, después de
`json-scada` / `OSHMI` (Brasil) — y el primero de México. Dato de contraste en la misma consulta:
`AngelCarballoCremades/CENACE-Scraper-Dashboard` (scraper de CENACE, **sin licencia**, 7 ★) está
**muerto desde 2021**. La vía viva para México es `atlas-sen`, no el scraper.

## Décimo pase (2026-11-20): la plataforma de datos operativos que faltaba, y es MIT

**La pregunta que un cliente de utility hace siempre y esta KB no sabía responder: "¿con qué
reemplazo o complemento mi historiador?"** Nueve pases catalogaron SCADA/EMS (`OpenEMS`,
`openremote`, `json-scada`), modelado (`pandapower`, `PyPSA`) y datos de mercado (`gridstatus`,
`entsoe-py`). El **histórico operativo** —la pieza donde vive la serie temporal de la red, hoy
ocupada por el PI System de AVEVA/OSIsoft— estaba ausente.

Es [`GridProtectionAlliance`](https://github.com/GridProtectionAlliance), y es una plataforma, no
piezas:

| Capa | Repo | Licencia | ★ | Push |
|------|------|----------|---|------|
| **Histórico de series temporales** | [openHistorian](https://github.com/GridProtectionAlliance/openHistorian) | **MIT** | 207 | 2026-11-15 |
| **Ingesta fasorial** | [openPDC](https://github.com/GridProtectionAlliance/openPDC) + [gsf](https://github.com/GridProtectionAlliance/gsf) | **MIT** | 159 / 179 | 2026-11-15 |
| **Sincronización de tiempo** | [PTPSync](https://github.com/GridProtectionAlliance/PTPSync) | **MIT** | 97 | 2026-11-15 |
| **Analítica de perturbaciones** | [openXDA](https://github.com/GridProtectionAlliance/openXDA) | **MIT** | 20 | 2026-11-19 |
| **Calidad de onda (front)** | [PQDashboard](https://github.com/GridProtectionAlliance/PQDashboard) | **BSD-3-Clause** | 23 | 2026-08-10 |
| **Recolección de medidores** | [openMIC](https://github.com/GridProtectionAlliance/openMIC) | **MIT** | 18 | 2026-11-15 |
| **Analítica en el lazo** | [openECA](https://github.com/GridProtectionAlliance/openECA) | **MIT** | 16 | 2026-11-15 |
| **Intercambio entre control rooms** | [SIEGate](https://github.com/GridProtectionAlliance/SIEGate) | **MIT** | 9 | 2026-11-15 |
| **Visualización** | [openHistorian-grafana](https://github.com/GridProtectionAlliance/openHistorian-grafana) | **MIT** | 9 | 2026-02-22 |

**La pieza comercialmente más astuta del conjunto no es el historiador: es
[`osisoftpi-grafana`](https://github.com/GridProtectionAlliance/osisoftpi-grafana) (Apache-2.0,
65 ★, 36 forks, push 2026-11-16).** Un plugin de Grafana para el PI System permite entrar en un
cliente **sin pedirle que migre su histórico** — se lee lo que ya tiene y se construye la capa de
analítica e IA encima. Es el patrón de adopción de menor fricción que ha encontrado esta KB para una
utility con instalación propietaria, y aplica igual en las cuatro regiones.

**Riesgos que hay que decir en la propuesta:**

- Es un stack **.NET/Windows** en su origen (GPA nace del mundo NERC/DOE norteamericano). Verificar
  el plan de despliegue antes de prometer contenedores Linux.
- `openECA` tiene **20 issues abiertas**, `PQDashboard` **21** y `openHistorian` **14**. Es software
  de verdad, con deuda de verdad.
- Las estrellas son bajas (9-207) para lo que son. Es software de **nicho operativo**, no de
  comunidad de desarrolladores: el indicador útil aquí es el push de noviembre de 2026 en diez
  repos, no el ranking.

### Medición: la frontera se movió un escalón, y conviene reescribir el presupuesto

El octavo pase concluyó —y el noveno cuantificó— que **no hay plataforma MDM abierta**. **Eso sigue
siendo verdad.** Lo que este pase cambia es la capa de abajo. La KB tenía registrado que
`u9n/dlms-cosem` es **Business Source License**, de donde se seguía que hablar el protocolo de
medidor obligaba a licencia comercial. Es falso:

| Capa de un meter-to-cash | Estado tras este pase | Pieza |
|--------------------------|----------------------|-------|
| **Protocolo de medidor (EMEA)** | ✅ **Permisivo** | [epri-dev/DLMS-COSEM](https://github.com/epri-dev/DLMS-COSEM) **BSD-3**, [dlms-access-point](https://github.com/epri-dev/dlms-access-point) **BSD-3** |
| **Protocolo de medidor (NA)** | 🟡 Existe, bloqueado | [epri-dev/c12test](https://github.com/epri-dev/c12test) (**ANSI C12**, `NOASSERTION`, 12 ★) |
| **Traducción a modelo de red** | ✅ **Permisivo** | [epri-dev/dlms-cim](https://github.com/epri-dev/dlms-cim) **BSD-3** (DLMS → CIM) |
| **Recolección** | ✅ **Permisivo y vivo** | [openMIC](https://github.com/GridProtectionAlliance/openMIC) **MIT**, push 2026-11-15 |
| **Gestión de datos de medición (MDM)** | ❌ **Sigue ausente** | Lo mejor del mercado abierto: 7 ★ y dos años sin push (medido en el pase 9) |
| **Tarifa regulada y facturación** | ❌ **Desarrollo propio** | Sustrato: `killbill` Apache-2.0, `openmeter` Apache-2.0 — **no conocen una tarifa eléctrica** |

**Consecuencia de presupuesto:** un SoW de metering ya **no** tiene que incluir escribir el
protocolo ni la recolección. Sigue teniendo que incluir el MDM y toda la lógica tarifaria. La
conclusión del cuarto pase ("no existe un Odoo de la energía") se mantiene intacta; lo que se reduce
es el tamaño del desarrollo a medida.

### Valoración de almacenamiento como plataforma de laboratorio

El noveno pase midió la oferta de optimización de BESS en **un** repo. Buscando por institución son
cinco, todos permisivos — y dos de ellos son plataformas con interfaz, no librerías:

| Plataforma | Licencia | Qué hace | ★ | Push |
|-----------|----------|----------|---|------|
| [sandialabs/snl-quest](https://github.com/sandialabs/snl-quest) | **BSD-3** *(rescatada)* | **QuESt**: aplicación de análisis de almacenamiento de Sandia, modular. ⚠️ 44 issues | 162 | 2026-11-09 |
| [epri-dev/StorageVET-deprecated](https://github.com/epri-dev/StorageVET-deprecated) | **BSD-3** | Valoración de almacenamiento de EPRI. ⚠️ El nombre dice `deprecated` | 64 | 2026-10-24 |
| [epri-dev/DER-VET](https://github.com/epri-dev/DER-VET) | **BSD-3** | Valoración de DER, con [GUI](https://github.com/epri-dev/DER-VET-GUI) ⚠️ **sin licencia** | 6 | 2026-10-21 |

⚠️ **Antes de comprometer `StorageVET-deprecated` en un alcance hay que resolver qué lo reemplaza**:
el repo se llama *deprecated* y tiene push de hace cuatro semanas, que es una combinación que no se
interpreta sola.

## Calor de distrito como vertical (décimo pase, 2026-11-20)

Vertical ausente en nueve pases, y es el **dominante en el norte y este de EMEA**: Escandinavia,
Alemania, Polonia y los bálticos calefaccionan por red, no por caldera individual.

| Repo | Licencia | Qué cubre | ★ | Push |
|------|----------|-----------|---|------|
| [oemof/DHNx](https://github.com/oemof/DHNx) | **MIT** | Optimización y simulación de la red de calor. ⚠️ 35 issues | 47 | 2026-11-14 |
| [jylambert/topotherm](https://github.com/jylambert/topotherm) | **MIT** | Optimización de **topología** (TU München) | 37 | 2026-10-06 |
| [oemof/tespy](https://github.com/oemof/tespy) | **MIT** | Ciclo térmico del lado de generación: bomba de calor, CHP, planta | 440 | 2026-11-19 |
| [oemof/oemof-demand](https://github.com/oemof/oemof-demand) | **MIT** | Perfiles de demanda de calor desde valores anuales | 76 | 2026-10-22 |

**Veredicto honesto, en los términos de esta KB:** `DHNx` + `topotherm` + `tespy` + `oemof-demand`
es un **estudio de red de calor** completo y todo MIT — dimensionado, topología, generación y
demanda. **No es una plataforma de operación**: no hay SCADA de calor, ni facturación de calor, ni
gestión de subestación térmica en open source. Vender estudio y diseño; no vender operación.


---
*Ver `compose/patterns.md` para recetas concretas que combinan estas plataformas con los agentes.*

## Undécimo pase (2026-11-20): la plataforma nuclear, la monitorización de consumo, y la cuarta confirmación externa de que no hay ERP de utility

### El patrón "plataforma + modelos" en nuclear: MOOSE como sistema customizable

La categoría que esta KB trata como vertical —un sistema real que se customiza, tipo Odoo u
OpenMRS— tiene un equivalente nuclear que el pase 10 declaró inexistente por error de consulta:

| Plataforma | Licencia | ★ | Qué es | Cómo se customiza |
|-----------|----------|---|--------|-------------------|
| [idaholab/moose](https://github.com/idaholab/moose) | LGPL-2.1 | 2409 | Entorno multifísica de elementos finitos del INL. **Es la plataforma**: los físicos escriben *kernels*, no resuelven ecuaciones | Módulos y *apps* derivadas. ⚠️ **LGPL-2.1: enlazable, no incrustable** sin análisis |
| [idaholab/raven](https://github.com/idaholab/raven) | **Apache-2.0** | 274 | **RAVEN**: la capa de riesgo probabilístico e incertidumbre **sobre** MOOSE | Plugins y modelos externos. Es la pieza permisiva del par |
| [idaholab/virtual_test_bed](https://github.com/idaholab/virtual_test_bed) | ⚠️ **CC-BY-4.0** | 81 (**103 forks**) | Modelos listos de reactores avanzados (microrreactor, SFR, HTGR, MSR) | Se bifurca y se adapta: 103 forks frente a 81 ★ dicen que es **material de partida**, no producto |
| [idaholab/DeepLynx](https://github.com/idaholab/DeepLynx) | **MIT** *(rescatada en crudo)* | 102 | Almacén de datos de **gemelo digital** orientado a grafo para integración de datos de ingeniería | La capa de integración del vertical |

**La lectura de vertical:** `MOOSE` + `RAVEN` + `virtual_test_bed` es exactamente el patrón "el
sistema existe y se customiza" —plataforma, capa analítica y modelos de referencia— para nuclear
avanzado. Y `DeepLynx` es la pieza de integración de datos de ingeniería, **MIT**, que sirve fuera de
nuclear. ⚠️ Pero el perfil de licencia obliga a una arquitectura concreta: lo propio del cliente se
construye **sobre** `RAVEN` (Apache-2.0) y `DeepLynx` (MIT), con `MOOSE` enlazado y respetando
LGPL-2.1, y los modelos de `virtual_test_bed` tratados como **datos CC-BY** (atribución obligatoria,
sin herencia de permiso de software).

### Monitorización de consumo en hardware abierto: útil como referencia, no como dependencia

`org:openenergymonitor` (92 repos) es la referencia del sector en medición de consumo con hardware
abierto, y es un caso de libro de por qué hay que leer licencias antes de prometer:

| Repo | Licencia | ★ | Push | Nota |
|------|----------|---|------|------|
| [EmonLib](https://github.com/openenergymonitor/EmonLib) | **AGPL-3.0** | 628 | 2023-05-08 | Librería de medida eléctrica. **AGPL: incompatible con producto cerrado** |
| [emonpi](https://github.com/openenergymonitor/emonpi) | ⚠️ sin licencia | 280 | 2026-10-11 | Monitor energético sobre Raspberry Pi: hardware + firmware. **Vivo** |
| [emonhub](https://github.com/openenergymonitor/emonhub) | ⚠️ sin licencia | 107 | 2026-11-11 | Servicio Python que entrega a MQTT/Emoncms. **Vivo** |
| [EmonESP](https://github.com/openenergymonitor/EmonESP) | ⚠️ sin licencia | 169 | 2023-09-22 | Puente serie-WiFi ESP8266 |

**Veredicto:** sirve como **arquitectura de referencia y banco de pruebas** para un piloto de
submedición (el patrón "arrancar sin subestación" que esta KB ya documenta). **No como dependencia de
producto**: la pieza con licencia es AGPL y el resto no tiene archivo de licencia. Para producto, la
ruta sigue siendo la capa de protocolo permisiva del pase 10 (`epri-dev/DLMS-COSEM` BSD-3,
`GridProtectionAlliance/openMIC` MIT).

### ERP/CRM/facturación de utility: cuarta medición, mismo resultado

La consulta mandada —`open source platform energy utility ERP CRM billing MIT Apache 2026`— devuelve
**cero plataformas específicas de utility**. Lo que hay es genérico, y conviene tenerlo nombrado con
su licencia porque es la respuesta honesta cuando el cliente pregunta:

| Pieza | Licencia | Qué cubre | Lo que **no** cubre |
|-------|----------|-----------|---------------------|
| [Apache OFBiz](https://ofbiz.apache.org/) | **Apache-2.0** | ERP/CRM sobre framework Java; proyecto *top-level* de Apache desde 2006 | Nada de dominio eléctrico |
| [Kill Bill](https://killbill.io/) | **Apache-2.0** (la edición enterprise *Aviate* es aparte) | Motor de facturación y suscripción | Lógica tarifaria eléctrica |
| [OpenMeter](https://openmeter.io/) | **Apache-2.0** (de Kong) | Medición de uso y facturación por consumo | Ciclo meter-to-cash regulado |
| ERPNext / iDempiere / Dolibarr / Axelor | GPLv3 / GPLv2 / GPLv3+ / AGPLv3 | ERP generalista | Copyleft, y sin dominio eléctrico |

**Lo que sigue sin existir, por cuarta medición consecutiva y ahora también vía buscador web:**
plataforma abierta con **gestión de datos de medida (MDM), motor tarifario y reporting regulatorio**.
La frontera que el pase 10 movió un escalón hacia abajo —el protocolo ya no se escribe— se mantiene
donde estaba: **la lógica tarifaria y el ciclo meter-to-cash son desarrollo propio**. Es la
conclusión más repetidamente verificada de esta KB, y por eso es la más segura de poner en una
propuesta.

⚠️ Licencias de `BillRun` y `OpenBRM` **no verificadas** en este pase; aparecieron en resultados sin
licencia declarada. No proponerlas sin comprobarlas.

## Duodécimo pase (2026-11-20): el vertical de analítica de mercado del NEM, y el "banco de ensayo de cumplimiento" como categoría de producto

### Analítica de mercado eléctrico australiano: hay stack vertical completo, con una costura de licencia en medio

Esta KB ya tenía un vertical de "plataformas de datos de mercado" construido sobre `gridstatus`
(North America), `entsoe-py` (EMEA) y `api_xm` (LATAM). **APAC estaba vacío y ya no lo está.** Lo que
hay en Australia no es un repo: es una pila que cubre de la ingesta al despacho.

| Capa del vertical | Pieza | Licencia | Se puede embeber en entregable propietario |
|---|---|---|---|
| Ingesta de datos históricos | [`NEMOSIS`](https://github.com/UNSW-CEEM/NEMOSIS) (113 ★) | GPL-3.0-or-later | ⛔ **no** — aislar tras servicio |
| Ingesta de pronósticos (pre-dispatch, PASA) | [`NEMSEER`](https://github.com/UNSW-CEEM/NEMSEER) | GPL-3.0 | ⛔ **no** — aislar tras servicio |
| Normalización de supuestos regulatorios (IASR en Excel) | [`isp-workbook-parser`](https://github.com/Open-ISP/isp-workbook-parser) | GPL-3.0 | ⛔ **no** |
| Series temporales de demanda/solar/viento | [`isp-trace-parser`](https://github.com/Open-ISP/isp-trace-parser) | GPL-3.0 | ⛔ **no** |
| Expansión de capacidad (metodología AEMO ISP) | [`ISPyPSA`](https://github.com/Open-ISP/ISPyPSA) | GPL-3.0 | ⛔ **no** |
| **Simulación del despacho real del mercado** | [`nempy`](https://github.com/UNSW-CEEM/nempy) (71 ★) | **BSD-3** | ✅ **sí** |
| **Emisiones del NEM** | [`NEMED`](https://github.com/UNSW-CEEM/NEMED) | **BSD-3** | ✅ **sí** |
| **Respuesta de DER a perturbaciones** | [`DER_disturbance_analysis`](https://github.com/UNSW-CEEM/DER_disturbance_analysis) | **MIT** | ✅ **sí** |
| Visualización de pujas / resultados | [`nem-bidding-dashboard`](https://github.com/UNSW-CEEM/nem-bidding-dashboard), [`market-control-room`](https://github.com/UNSW-CEEM/market-control-room) | BSD-3 / MIT | ✅ sí, pero inactivos (2023, 2022) |
| Diseño y análisis de tarifas | [`TDA_Python`](https://github.com/UNSW-CEEM/TDA_Python) | ⛔ sin licencia | ⛔ **bloqueado** (T20) |

**La decisión de producto que sale de esta tabla**, y es la razón de ponerla así: lo *embebible* es
la **capa de modelo** (despacho, emisiones, DER) y lo *copyleft* es la **capa de datos**. Eso define
el producto vendible en Australia sin ambigüedad: **servicio de datos del NEM aislado (GPL,
contenedor propio, interfaz estable) + motor analítico propietario encima que usa `nempy` y `NEMED`
embebidos.** No es una restricción incómoda: es la arquitectura que de todas formas conviene, porque
la capa de ingesta es la que cambia cuando AEMO cambia sus formatos. Ver Receta 31.

### El banco de ensayo de cumplimiento de red: una categoría de producto que esta KB no tenía

Antes de conectar un parque o una batería a la red, el promotor debe **prequalificar su modelo de
simulación** contra los requisitos del operador. Es trabajo de ingeniería caro, repetitivo y con un
entregable formal — es decir, un producto.

| Pieza | Licencia | ★ | Simulador que necesita | Usable |
|---|---|---|---|---|
| [`Energinet-SimTools/MTB`](https://github.com/Energinet-SimTools/MTB) | ⛔ **no-OSI, revocable** | 83 | **PSCAD / PowerFactory** (comerciales) | Sólo como **especificación** de requisitos |
| [`Energinet-SimTools/IMTB`](https://github.com/Energinet-SimTools/IMTB) | **MPL-2.0** ✅ | 41 | PSCAD / PowerFactory | ✅ Sí (copyleft por archivo) |

Dos advertencias que cambian la propuesta, y las dos hay que decirlas antes de prometer nada:

1. **El `MTB` es el repo más estrellado del TSO danés y no es open source.** Su licencia concede
   derecho de uso, modificación y distribución **y permite a Energinet retirarlo**
   (*"Energinet may withdraw or modify the right to use, modify and distribute"*), reteniendo toda la
   propiedad intelectual. No sostiene un entregable de cliente. Ver agents/top.md §3 y T33.
2. **El simulador subyacente es comercial.** El banco es abierto; PSCAD y PowerFactory no lo son. El
   proyecto cliente **ya tiene** esas licencias (son el estándar de facto del estudio de red) — pero
   eso sale del alcance de la oferta y hay que decirlo explícitamente, no descubrirlo en ejecución.

**Dónde está el negocio de todas formas:** la automatización del **expediente** —ejecutar la batería
de casos, recoger resultados, redactar el informe de cumplimiento contra el requisito del operador y
mantener la trazabilidad— es trabajo de orquestación y de documento, exactamente lo que la capa
agéntica hace bien, y es independiente de quién posea el banco. El `MTB` dice *qué* hay que
comprobar; el proyecto construye el *cómo* se demuestra. Combina con la Receta 30 (`pypowsybl-mcp`
para la parte de red) y con la Receta 2 (expediente de cumplimiento).

### Acceso unificado a datos de mercado europeos como capa de plataforma

[`ClariGrid`](https://github.com/AlexanderHoogsteyn/ClariGrid) (**Apache-2.0**, 3 ★, push 2026-11-19)
da una **interfaz Python única** sobre varias fuentes de mercado europeas, devolviendo siempre
`DataFrame` con husos horarios, nombres de columna y unidades normalizados (incluye conector Fingrid
con clave gratuita). Resuelve el trabajo aburrido que todo proyecto EMEA repite: cada TSO publica en
su formato, su huso y sus unidades.

Es de **autor individual y 3 ★**: **patrón a copiar, no dependencia a asumir.** La licencia
(Apache-2.0) permite justamente eso — tomar el diseño de normalización y mantenerlo en el proyecto.

## Lectura local de medidor como plataforma de arranque (decimotercer pase, 2026-11-20)

El patrón de esta sección —tomar un sistema real y personalizable y poner IA encima— tiene en la capa
de medición una variante barata que esta KB no había registrado: **no hay que construir el
*head-end*, hay que leer el medidor localmente**.

[`marq24/ha-tibber-pulse-local`](https://github.com/marq24/ha-tibber-pulse-local) (**Apache-2.0**,
297 ★, 20 forks, **0 issues abiertas**, push 2026-11-08) lee el Tibber Pulse **por LAN, sin pasar por
la nube del fabricante**. Combinado con
[`volkszaehler/mbmd`](https://github.com/volkszaehler/mbmd) (**BSD-3-Clause**, 281 ★) como demonio de
adquisición Modbus y
[`Apollon77/smartmeter-obis`](https://github.com/Apollon77/smartmeter-obis) (**MIT**) como
normalizador OBIS multi-fabricante, se obtiene una **plataforma de telemetría doméstica/edificio
completa y permisiva** sin licencia de producto y sin dependencia de nube.

**Por qué es una solución vertical y no sólo una librería:**

1. **Es el argumento de privacidad convertido en arquitectura.** "El dato del medidor no sale de la
   instalación" es una propiedad verificable del despliegue, no una promesa contractual. En EMEA, con
   el acceso local a datos del hogar como política, es el punto de partida correcto.
2. **Convierte un mandato regulatorio en base instalada direccionable.** Donde hay mandato de medidor
   inteligente —EMEA, y Brasil si la consulta del MME se convierte en norma— hay parque de medidores
   que alguien tiene que leer.
3. **El modelo de datos ya existe y es normativo**:
   [`sunspec/models`](https://github.com/sunspec/models) (Apache-2.0) para inversores y DER,
   [`NeverBlink-OSS/saref-linkml`](https://github.com/NeverBlink-OSS/saref-linkml) (BSD-3-Clause) para
   la semántica SAREF. No hay que inventar el esquema, que es donde estos proyectos se atascan.

**Y la trampa de esta vertical, que hay que conocer antes de dibujar el diagrama:** es la capa de la
KB con **más densidad de licencias no-OSI**, y las piezas bloqueadas tienen **más estrellas** que las
limpias. `UtilitechAS/amsreader-firmware` (471 ★) parece la elección obvia para el lado firmware y es
**Fair Source License 0.9 con tope de 5 usuarios**; `binsentsu/home-assistant-solaredge-modbus`
(420 ★) no tiene licencia. **Elegir por estrellas aquí rompe el entregable.** Sustitutos limpios:
`lvzon/dsmr-p1-parser` (Apache-2.0) para firmware/edge y
`WillCodeForCats/solaredge-modbus-multi` (Apache-2.0) para SolarEdge.

---

## Pase 15 (2026-11-21) — tres verticales abiertas nuevas: intercambio de modelo de red, subestación y recarga de VE

### 1. Intercambio de modelos de red — CIM / CGMES (IEC 61970)

Es la vertical **estructuralmente más importante** que se añade: el formato en el que los TSO y DSO
europeos **se intercambian el modelo del sistema**. Quien sabe leer y escribir CGMES puede entrar en
el flujo de trabajo del operador sin pedirle que cambie de herramienta.

| Plataforma | Licencia | Qué es | Personalizable con IA encima |
|------------|----------|--------|------------------------------|
| [`sogno-platform/cimpy`](https://github.com/sogno-platform/cimpy) | Apache-2.0 | Importa/exporta CGMES / CIM IEC-61970 en XML/RDF (Python, RWTH Aachen) | Sí — es la puerta de entrada del modelo al agente |
| [`sogno-platform/cim4j`](https://github.com/sogno-platform/cim4j) | Apache-2.0 | Clases Java para CIM / CGMES; activo | Sí |
| [`RWTH-IAEW/cimpyorm`](https://github.com/RWTH-IAEW/cimpyorm) | BSD-3-Clause | ORM de Python sobre datasets CIM/CGMES | Sí — da esquema consultable |
| [`SOPTIM/OpenCGMES`](https://github.com/SOPTIM/OpenCGMES) | Apache-2.0 | Suite CGMES/CIM con RDFS, SHACL y CIMXML (ya en la KB) | Sí — **SHACL es validación declarativa**: el agente propone, SHACL decide si el modelo es válido |

> **El patrón que habilita esta vertical:** con CGMES + SHACL la salida de un agente **se valida
> contra el esquema del propio sector antes de tocar nada**. Es la forma más limpia de cumplir la
> restricción de arquitectura (apoyo a la decisión, no control) sin renunciar a automatizar: el
> agente escribe un modelo candidato, **SHACL lo rechaza o lo acepta**, y el humano firma.

### 2. Subestación — IEC 61850

| Plataforma | Licencia | Qué es | Nota |
|------------|----------|--------|------|
| [`robidev/iec61850_open_server`](https://github.com/robidev/iec61850_open_server) | Apache-2.0 | **IED** IEC 61850 abierto sobre lib61850 | Activo (2026-03) |
| [`beanit/iec61850bean`](https://github.com/beanit/iec61850bean) | Apache-2.0 | Pila **MMS** IEC 61850 en Java, cliente y servidor | ⚠️ Sin push desde jul-2023: referencia, no base de producto |

A diferencia de la capa prosumer —densa en licencias no-OSI— **la de subestación tiene ancla
permisiva real y en Apache-2.0**. Permite construir laboratorio y simulación de IED sin comprometer
la propiedad del entregable.

### 3. Recarga de vehículo eléctrico — OCPP

| Plataforma | Licencia | Qué es | Consecuencia |
|------------|----------|--------|--------------|
| [`ChargeTimeEU/Java-OCA-OCPP`](https://github.com/ChargeTimeEU/Java-OCA-OCPP) | MIT | Cliente y servidor OCPP en Java | **Empotrable** |
| [`lorenzodonini/ocpp-go`](https://github.com/lorenzodonini/ocpp-go) | MIT | OCPP 1.6 y 2.0.1 en Go | **Empotrable** |
| `steve-community/steve` | **GPL-3.0** | SteVe: servidor OCPP de gestión de puntos de carga, el más usado | ⚠️ Copyleft fuerte: **no empotrable** en producto propietario |
| `dallmann-consulting/OCPP.Core` | **GPL-3.0** | Servidor OCPP + UI de gestión en .NET | ⚠️ Mismo límite |

> **La regla de esta vertical, y es un input directo de cotización:** en OCPP **el protocolo es
> permisivo y el producto de gestión es copyleft fuerte**. Un encargo de "plataforma de recarga"
> tiene por tanto dos presupuestos muy distintos según si el cliente quiere **producto propietario**
> (hay que construir la gestión sobre las librerías MIT) o acepta **GPL-3.0** (se parte de SteVe y se
> ahorra el núcleo, a cambio de liberar las modificaciones).

### Nota de licencia para las tres verticales nuevas

Aparece **EUPL-1.2** en la capa europea financiada con fondos de la UE
([`HVDC-WISE/HVDC-Wise_lib`](https://github.com/HVDC-WISE/HVDC-Wise_lib)). Es **copyleft débil con
compatibilidad explícita, no permisiva**, y **engaña a los detectores por palabra clave** porque su
texto nombra GPL, LGPL, AGPL y MPL (T59). En EMEA hay que esperarla y clasificarla leyendo **la
primera línea** del archivo.

## Pase 16 (2026-11-24) — el portal de datos abiertos como plataforma, y la quinta confirmación de que no hay ERP de utility abierto

### Nueva categoría de plataforma: el portal de datos del operador con capa semántica y MCP

Hasta ahora este archivo trataba los portales de datos como **fuente**, no como **plataforma**. El
ONS brasileño convierte el suyo en plataforma, y publica las dos mitades permisivamente:

| Plataforma | Licencia | Qué es | Personalizable con IA |
|------------|----------|--------|------------------------|
| **Portal de Dados Abertos del ONS** + [TIAGO-Dados-Abertos](https://github.com/ONSBR/TIAGO-Dados-Abertos) | **Apache-2.0** (servidor) | `dados.ons.org.br`: **85 datasets** del sistema eléctrico brasileño, con un **servidor MCP oficial** y una capa semántica **ODCS v3.1.0** que declara schema, unidades y aditividad por columna. Motor DuckDB | **Es ya la capa de IA.** Lo personalizable es el conjunto de contratos: añadir datasets propios del cliente al mismo patrón de validación |
| [bitol-io/open-data-contract-standard](https://github.com/bitol-io/open-data-contract-standard) (ODCS) | **Apache-2.0** | El estándar de contrato de datos que hace posible lo anterior | Es el formato de la compuerta: la personalización **es** escribir contratos |

**Por qué esto es una vertical y no un repo.** El patrón es replicable sobre **cualquier portal de
datos de regulador u operador** —ANEEL, CAMMESA, CEN de Chile, EIA, ENTSO-E— y el trabajo facturable
es exactamente el que el ONS ya hizo y publicó: **escribir los contratos ODCS del dominio del
cliente**. El servidor es Apache-2.0 y reutilizable; el valor está en el modelado semántico, que es
consultoría de dominio. Detalle de ingeniería que lo hace vendible: **ningún LLM corre en el
servidor**, así que el despliegue no arrastra una decisión de soberanía de modelo. Receta 53.

### Previsión de carga y de afluencia como producto, con el modelo del operador dentro

| Plataforma | Licencia | Qué permite montar |
|------------|----------|--------------------|
| [ONSBR/prevcarga](https://github.com/ONSBR/prevcarga) / [PrevCargaDESSEM](https://github.com/ONSBR/PrevCargaDESSEM) | **Apache-2.0** / **MIT** | Previsión de carga para despacho de corto plazo (DESSEM), con copyright **CEPEL + ONS**: es el modelo del operador, no una aproximación académica |
| [ONSBR/smapOnsR](https://github.com/ONSBR/smapOnsR) | **MIT** | **SMAP/ONS** en R: afluencias. En un sistema hidrotérmico como el brasileño, la previsión de agua es la variable de la que cuelga el resto |

Para un *engagement* en Brasil esto cambia el punto de partida: no se propone construir un modelo de
previsión, se propone **operacionalizar, validar y poner interfaz al modelo que el operador ya
publica** — y eso es defendible ante el regulador precisamente porque es el modelo del operador.

### ⚠️ Quinta confirmación externa: sigue sin haber ERP ni CIS de utility open source

El barrido obligatorio de verticales (`open source platform energy ERP CRM MIT Apache`) devolvió,
una vez más, **suites generalistas y ningún sistema de utility**: Apache OFBiz (Apache-2.0), Krayin
(MIT), EPESI (MIT), ERPNext (**GPL-3.0**), Odoo (edición comunitaria + enterprise). El único hilo
energético es **opentaps**, que abandonó el ERP y se reorientó a construir aplicaciones de negocio
sobre datos de energía:

| Repo | Licencia | Nota |
|------|----------|------|
| [opentaps/opentaps_seas](https://github.com/opentaps/opentaps_seas) | ⚠️ **LGPL-3.0** | *Smart Energy Applications Suite*: el pivote de un ERP open source hacia datos de energía, sobre **VOLTTRON**. 88 ★, **último push 2024-02-07** |

Dos advertencias para no venderlo mal: **LGPL-3.0** es copyleft (enlazable, no forkeable en
silencio), y **lleva 21 meses sin push**. Vale como **precedente de arquitectura** —que el camino
ERP→energía se recorrió— no como base de producto. La conclusión de los pases 8, 9, 11 y 12 se
mantiene intacta: **el hueco de ERP/CIS de utility es real y es la oportunidad de producto más
grande y más vacía de este archivo.**

### VOLTTRON como plataforma de edificios y DER: usar la versión de Eclipse

[`eclipse-volttron/volttron-core`](https://github.com/eclipse-volttron/volttron-core) es
**Apache-2.0**; el canónico [`VOLTTRON/volttron`](https://github.com/VOLTTRON/volttron) (504 ★, PNNL)
es `NOASSERTION`. Para proponer VOLTTRON como plataforma de automatización de edificios/DER hay que
citar **la de Eclipse**. Complemento ya inventariado:
[`eclipse-volttron/volttron-openadr-ven`](https://github.com/eclipse-volttron/volttron-openadr-ven)
(Apache-2.0), el nodo **OpenADR** sobre esa plataforma.
