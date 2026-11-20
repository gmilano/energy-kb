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

**11 agentes/entornos reales.** Ninguna fila es ejemplo ni plantilla.

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

---
*Verificado contra GitHub REST API el 2026-11-20. Re-verificar antes de citar en una propuesta.*
