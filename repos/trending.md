---
industry: energy
region: Global
updated: 2026-11-20
---

# 📈 Repos trending — energy

> **Archivo APPEND-ONLY.** Cada pase añade una sección fechada arriba y conserva el historial
> debajo. No reescribir: el valor de este archivo es la serie temporal.

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
