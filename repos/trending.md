---
industry: energy
region: Global
updated: 2026-11-20
---

# 📈 Repos trending — energy

> **Archivo APPEND-ONLY.** Cada pase añade una sección fechada arriba y conserva el historial
> debajo. No reescribir: el valor de este archivo es la serie temporal.

## 2026-11-20

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
