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

**23 plataformas reales** (16 del primer pase + 7 añadidas en el segundo). Ninguna fila es plantilla.

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

## Cómo customizar con AI

1. Desplegar la plataforma base sin tocar su código (contenedor, su propia licencia, su propia API).
2. Añadir la capa agéntica como **servicio aparte**: `PowerMCP` / `EnergyPlus-MCP` / `pypsa-mcp`
   exponen las herramientas de ingeniería por MCP.
3. Envolver los flujos existentes con agentes que lean del histórico y escriban **solo** vía la API
   de la plataforma — nunca al actuador directamente.
4. UI conversacional sobre el sistema base, con los límites de seguridad en el servicio, no en el prompt.

---
*Ver `compose/patterns.md` para recetas concretas que combinan estas plataformas con los agentes.*
