---
industry: energy
region: Global
updated: 2026-11-20
---

# 🎯 Agentes AI — energy

> Agentes y tooling agéntico open source para el sector energético. Foco: MIT / Apache 2.0 / BSD.
> Toda fila verificada contra la GitHub REST API (`search/repositories`, campos `license.spdx_id`,
> `stargazers_count`, `forks_count`, `pushed_at`) el **2026-11-20**. Licencias `NOASSERTION`
> resueltas leyendo el `LICENSE` crudo en `raw.githubusercontent.com`.

## Hallazgo principal de este pase: `Power-Agent` es un stack agéntico completo, todo MIT

No es un repo aislado sino **cinco repos MIT coordinados** (Harvard SEAS Power & AI Initiative) que
cubren el ciclo entero: servidores MCP → skills → workflows → foundation models → benchmark.
Es el punto de partida más fuerte que existe hoy para agentes de sistemas de potencia.

| Nombre | Licencia | Descripción | Stars | Forks | Último push | Región origen |
|--------|----------|-------------|-------|-------|-------------|---------------|
| [Power-Agent/PowerMCP](https://github.com/Power-Agent/PowerMCP) | MIT | Colección de servidores MCP para software de sistemas de potencia (PowerWorld y otros): expone las herramientas de ingeniería al agente | 238 | 67 | 2026-11-17 | North America |
| [LBNL-ETA/EnergyPlus-MCP](https://github.com/LBNL-ETA/EnergyPlus-MCP) | BSD modificada (ver nota) | Servidor MCP con **35 tools** para cargar, validar, modificar, simular y analizar modelos EnergyPlus (IDF). Lawrence Berkeley National Lab | 130 | — | 2026-11-20 | North America |
| [Power-Agent/PowerSkills](https://github.com/Power-Agent/PowerSkills) | MIT | Agent Skills para análisis de sistemas de potencia | 81 | — | 2026-10-24 | North America |
| [open-energy-transition/pypsa-mcp](https://github.com/open-energy-transition/pypsa-mcp) | MIT | Servidor MCP que expone PyPSA a LLMs: modelado energético conversacional | 74 | 10 | 2026-03-20 | EMEA |
| [Power-Agent/PowerFM](https://github.com/Power-Agent/PowerFM) | MIT | Foundation models para el dominio de potencia y energía | 59 | — | 2026-10-24 | North America |
| [Power-Agent/PowerAgentBench](https://github.com/Power-Agent/PowerAgentBench) | MIT | Benchmark para evaluar agentes de sistemas de potencia | 50 | — | 2026-11-02 | North America |
| [Power-Agent/PowerWF](https://github.com/Power-Agent/PowerWF) | MIT | Workflows agénticos para sistemas de potencia | 44 | — | 2026-11-12 | North America |

## Entornos RL / simulación para entrenar y evaluar agentes

| Nombre | Licencia | Descripción | Stars | Forks | Último push | Región origen |
|--------|----------|-------------|-------|-------|-------------|---------------|
| [citylearn-project/CityLearn](https://github.com/citylearn-project/CityLearn) | MIT | Entorno RL oficial para demand response y load shaping en distritos urbanos | 662 | — | 2026-11-19 | North America |
| [Grid2op/grid2op](https://github.com/Grid2op/grid2op) | **MPL-2.0** | Testbed de decisión secuencial en redes eléctricas (RTE Francia); base de la competencia L2RPN | 494 | 155 | 2026-11-13 | EMEA |
| [ugr-sail/sinergym](https://github.com/ugr-sail/sinergym) | MIT | Entorno Gym para simulación y control de edificios sobre EnergyPlus (Univ. de Granada) | 242 | 57 | 2026-11-17 | EMEA |
| [NatLabRockies/PowerGridworld](https://github.com/NatLabRockies/PowerGridworld) | BSD-3-Clause | Framework liviano y modular para RL multi-agente en redes (Alliance for Sustainable Energy / NREL) | 188 | 49 | 2026-11-15 | North America |

## Plataformas de agentes en el borde (hallazgo del segundo pase del 2026-11-20)

La capa agéntica no empieza con los LLM. Existe infraestructura de agentes **ya desplegada en campo**,
con licencia permisiva, que resuelve el problema de "dónde corre el agente cuando está al lado del
equipo y no en la nube":

| Nombre | Licencia | Descripción | Stars | Forks | Último push | Región origen |
|--------|----------|-------------|-------|-------|-------------|---------------|
| [VOLTTRON/volttron](https://github.com/VOLTTRON/volttron) | **Apache-2.0** | Plataforma de control distribuido de PNNL/Battelle: bus de mensajes, aislamiento de agentes y drivers de campo. Despliegue probado en edificios y equipos de red | 504 | 284 | 2026-11-03 | North America |
| [eclipse-volttron/volttron](https://github.com/eclipse-volttron/volttron) | Apache-2.0 | Nuevo hogar del proyecto en la Eclipse Foundation. **Migración en curso, no terminada**: 0 ★ y último push 2026-07-21 | 0 | 1 | 2026-07-21 | North America |
| [idfkit/idfkit-mcp](https://github.com/idfkit/idfkit-mcp) | **MIT** | Servidor MCP para EnergyPlus con **licencia limpia**: la alternativa al de LBNL cuando la revisión legal tiene que ser corta. Joven (14 ★) | 14 | 2 | 2026-11-16 | North America |

**Cómo encaja con `Power-Agent`**: `PowerMCP` y `PowerSkills` dan el *razonamiento* sobre
herramientas de ingeniería; `VOLTTRON` da el *lugar de ejecución* en el borde, con Apache-2.0 y sin
cláusula de red. Es el puente entre la plataforma copyleft de registro y la capa agéntica MIT.

## Simulación de mercados basada en agentes

Categoría que pases anteriores declararon vacía. No lo está — pero es **modelado**, no ejecución:

| Nombre | Licencia | Descripción | Stars | Forks | Último push | Región origen |
|--------|----------|-------------|-------|-------|-------------|---------------|
| [assume-framework/assume](https://github.com/assume-framework/assume) | MIT | **ASSUME**: agentes que representan actores de mercado eléctrico para estudiar su evolución (Fraunhofer IEE / INATECH / TU Dresden). Activo: push 2026-11-19 | 128 | 53 | 2026-11-19 | EMEA |
| [alexanderkell/elecsim](https://github.com/alexanderkell/elecsim) | MIT | Modelo de agentes de mercado a largo plazo: efecto de la política pública sobre decisiones de inversión. ⚠️ **sin actividad desde 2025-12-03** | 61 | 13 | 2025-12-03 | EMEA |

⚠️ **Límite que hay que declarar**: ninguno de los dos coloca ofertas en un mercado real. Son
simuladores. Un agente de *ejecución* de trading mayorista sigue sin equivalente open source.

**16 agentes/entornos reales.** Ninguna fila es ejemplo ni plantilla.

## Notas de licencia que cambian decisiones

- **`LBNL-ETA/EnergyPlus-MCP`**: la API devuelve `NOASSERTION` y **no hay archivo `LICENSE`**; el
  README declara *"This software is distributed under a modified BSD license"* con el texto en
  `License.txt` (L mayúscula, por eso un fetch de `LICENSE` da 404). Titular: Regents of the
  University of California / LBNL, *"subject to receipt of any required approvals from the U.S.
  Dept. of Energy"*. Versión declarada **0.1.0**. Para uso en cliente: pedir revisión legal del
  `License.txt` y considerar el aviso de U.S. Government Rights. Contacto de IP: IPO@lbl.gov.
- **`Grid2op` es MPL-2.0**, no LGPL-2.1. Pases anteriores de esta KB registraron LGPL-2.1: era
  incorrecto. MPL-2.0 es copyleft por archivo — enlazable sin contaminar el resto del producto.
- **`PowerGridworld` cambió de organización**: `NREL/PowerGridworld` ya **no resuelve**. El repo
  vive en `NatLabRockies/PowerGridworld` (BSD-3-Clause confirmado en `LICENSE` crudo, copyright
  "Alliance for Sustainable Energy, LLC"). Toda URL `NREL/...` registrada antes está rota.
- **`CityLearn` cambió de organización**: `intelligent-environments-lab/CityLearn` ya no resuelve;
  ahora es `citylearn-project/CityLearn`.

## Correcciones de datos sobre pases anteriores

Los pases de energy de ciclos previos (2026-08-01) sobreestimaron stars de forma sistemática.
Medido de nuevo contra la API el 2026-11-20:

| Repo | Registrado antes | Real hoy | Delta |
|------|------------------|----------|-------|
| CityLearn | ~1.7k ★ | **662 ★** | −2.6× (y org distinta) |
| Grid2Op | ~1.2k ★, LGPL-2.1 | **494 ★, MPL-2.0** | −2.4× + licencia errónea |
| Carbon Aware SDK | ~2.2k ★ | **600 ★** | −3.7× |
| openSTEF | ~500 ★, Apache-2.0 | **183 ★, MPL-2.0** | −2.7× + licencia errónea |
| PowerGridworld | ~430 ★, org NREL | **188 ★, org NatLabRockies** | −2.3× + org rota |
| sinergym | ~310 ★ | **242 ★** | −1.3× |

Causa probable: cifras arrastradas entre pases sin re-consultar la API. Esta tabla existe para que
el próximo pase no las vuelva a propagar.

## Resoluciones de licencia del segundo pase (2026-11-20)

La regla del pase anterior —*"`NOASSERTION` no significa sin licencia: leer el `LICENSE` crudo"*— es
correcta pero incompleta. Hay repos **sin archivo `LICENSE` en ninguna rama** que sí declaran
licencia, mediante un identificador **SPDX** en `pyproject.toml` o en el `README` (estándar REUSE).

**Orden de verificación que esta KB adopta desde hoy:**

1. `LICENSE` / `LICENSE.txt` / `License.txt` / `COPYING` crudo en `raw.githubusercontent.com`.
2. `SPDX-License-Identifier:` en `pyproject.toml`, `setup.py`, `README`.
3. Sólo entonces: declararlo **irresuelto** (y no construir sobre él).

Resueltas así en este pase:

| Repo | API decía | Realidad verificada | Dónde estaba | Veredicto |
|------|-----------|---------------------|--------------|-----------|
| `VOLTTRON/volttron` | NOASSERTION | **Apache-2.0** (Battelle Memorial Institute) | `LICENSE` | ✅ rescatado, 504 ★ |
| `oemof/oemof-solph` | `null` | **MIT** | SPDX en `pyproject.toml` | ✅ rescatado, 430 ★ |
| `pypsa-meets-earth/pypsa-earth` | `null` | **AGPL-3.0-or-later** | SPDX en `README` | ⚠️ **copyleft de red** |
| `e2nIEE/pandapipes` | NOASSERTION | **BSD-3-Clause** (Fraunhofer IEE) | `LICENSE` | ✅ rescatado, 247 ★ |
| `dss-extensions/OpenDSSDirect.py` | NOASSERTION | **BSD-3 + derechos del gobierno de EE. UU.** | `LICENSE` | ⚠️ revisar cláusula gov |
| `gridlab-d/gridlab-d` | NOASSERTION | **licencia propia de Battelle v5.3 (no OSI, no SPDX)** | `LICENSE` | ⚠️ gate de compliance la marcará |
| `idfkit/idfkit-mcp` | MIT | **MIT** confirmada | `LICENSE` | ✅ |
| `u9n/dlms-cosem` | NOASSERTION | **Business Source License 1.1** (re-confirmada) | `LICENSE` | ❌ no permisiva |

**El caso que más caro habría salido**: `pypsa-earth`. Es el único modelo de sistema energético que
cubre LATAM y APAC de fábrica, la API no declara licencia, y la respuesta —AGPL-3.0-or-later— está
en una línea del `README`. Tratarlo como permisivo en un SaaS de cliente habría significado
obligación de liberar el servicio.

---
*Verificado contra GitHub REST API el 2026-11-20. Re-verificar antes de citar en una propuesta.*
