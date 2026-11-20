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

**13 repos fundacionales reales.**

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
