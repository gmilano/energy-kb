---
industry: energy
region: Global
updated: 2026-11-20
---

# 📡 Tendencias — energy

> Estado del sector al **2026-11-20**.

## T1 — La red es el cuello de botella de la IA, no su beneficiaria

La inversión no viene de "digitalizar la energía" sino de que los datacenters de IA rompieron la
planificación eléctrica. Un datacenter tarda **1–2 años** en construirse; una ampliación de red
**5–10** (IBM). Gartner proyecta el consumo eléctrico de datacenters creciendo **~26-27 % en 2026**
hasta **132 GW**. BofA calcula que la demanda **excede en +100 GW** las adiciones planificadas hasta
2030. Consecuencia medible: la **confiabilidad desplazó al net zero** como principal preocupación
del sector (encuesta National Grid Partners), y la capacidad de gas planificada subió de **11,1 % a
18,1 %** del mix entre 2024 y 2026.

## T2 — Los operadores de red se volvieron proveedores de open source

El cambio estructural más útil para Globant: **RTE (Francia) y Alliander (Países Bajos) publican su
software de producción**. `Grid2Op` y `powsybl` (RTE), `power-grid-model` (Alliander), `openSTEF`
(LF Energy) son todos **MPL-2.0** — copyleft por archivo, enlazable sin contaminar el producto.
El núcleo técnico de red dejó de ser el activo diferencial de los vendors; el diferencial pasó a la
integración y a la capa agéntica.

## T3 — MCP se volvió el protocolo de integración de la ingeniería energética

En los últimos meses apareció una capa de servidores MCP que exponen herramientas de ingeniería
reales a los agentes, no demos:

- `Power-Agent/PowerMCP` (MIT, 238 ★) — software de sistemas de potencia (PowerWorld y otros).
- `LBNL-ETA/EnergyPlus-MCP` (BSD modificada, 130 ★) — **35 tools** sobre modelos EnergyPlus:
  cargar/validar IDF, inspeccionar zonas y schedules, modificar cargas, correr simulación, graficar.
- `open-energy-transition/pypsa-mcp` (MIT, 74 ★) — PyPSA para LLMs.

El patrón es consistente: **el agente no reimplementa el solver, lo conduce**. Es la misma lección
que esta KB registró en automotive (el `reason` del agente se loguea para el operador y nunca llega
al actuador).

## T4 — Existe un stack agéntico energético completo y es todo MIT

`Power-Agent` (Harvard SEAS) publicó en pocos meses cinco piezas coordinadas: **PowerMCP** (238 ★),
**PowerSkills** (81 ★), **PowerFM** (59 ★, foundation models), **PowerAgentBench** (50 ★) y
**PowerWF** (44 ★, workflows). Que exista un **benchmark** (`PowerAgentBench`) junto a las
herramientas es la señal de madurez: la categoría pasó de demo a evaluable. Precedente directo de la
categoría "assurance-as-code" que esta KB detectó en automotive.

## T5 — Regulación: tres regímenes divergentes, tres servicios distintos

- **EMEA**: hoja de ruta **COM(2026) 501** (junio 2026) con foundation models de red y ~**EUR 75 M**
  para 2026-2027; obligaciones de alto riesgo del AI Act desde el **2 de diciembre de 2027**
  (Reglamento (UE) 2026/1744); **BNetzA** supervisa IA en Alemania desde el **29 de julio de 2026**.
  Gestión de red y load forecasting se tratan como alto riesgo → **cumplimiento es el producto**.
- **North America**: FERC emitió el **18 de junio de 2026** *show-cause orders* a **PJM, MISO, SPP,
  CAISO, ISO-NE y NYISO** con **60 días** para reformar interconexión de cargas grandes. **Sin regla
  nacional única** → **seis marcos divergiendo** = consultoría por jurisdicción.
- **APAC**: **NDRC + NEA de China** emitieron en **diciembre de 2025** guía sobre IA en planificación,
  equipamiento, operación y seguridad de red — la política pública más explícita del mundo en el tema.
  El resto de APAC regula al *deployer*, con aplicación desigual.

## T6 — El datacenter como activo de red (y como objeto simulable)

La flexibilidad de carga pasó de concepto a línea de negocio: un estudio comisionado por Duke indica
que cargas flexibles de datacenter evitarían decenas de miles de millones en plantas nuevas. Ya hay
herramienta open source específica: **`dos-group/vessim`** (MIT, 103 ★) simula sistemas energéticos
de datacenter —carbono, batería, PV on-site— y **`hubblo-org/scaphandre`** (Apache-2.0, 2019 ★) mide
consumo de cómputo real. Combinados permiten cuantificar una oferta de flexibilidad con datos
propios en lugar de supuestos.

## T7 — Movilidad eléctrica es donde está la masa crítica real de la comunidad

`evcc` tiene **7638 ★ y 1649 forks** — más tracción que todo el resto del ecosistema energético
open source de esta KB junto. `SteVe` (1151 ★) y `mobilityhouse/ocpp` (1052 ★) lo acompañan. Si un
engagement necesita demostrar velocidad con comunidad detrás, el vertical de carga de EV es el que
tiene base probada.

## T8 — Advertencia de método: el dato de mercado de este sector no es confiable, el de adopción sí

Las estimaciones de "AI in energy" para 2026 van de **USD 7,86 B** a **USD 12,53 B** según
consultora (~1,6× de spread). En cambio son verificables: **78 %** de líderes de innovación de
utilities estadounidenses usando IA para gestionar demanda, **>200 M** de medidores aprobados en
India, **19,5 GW** subastados en Brasil, **6** operadores bajo orden de FERC. **Citar adopción, no
tamaño de mercado.**

## Gaps declarados (ausencia medida, no silencio)

Buscado y **no** encontrado. Un gap declarado es información; el silencio parece cobertura:

- **Repos de origen APAC**: salvo `MyEMS` (MIT, China, 763 ★) y plataformas IoT genéricas chinas
  (`iot-dc3`, `sagooiot`), **no se hallaron repos energéticos APAC de peso** pese a que China tiene
  la política pública más agresiva del mundo en IA para red. Probable publicación en Gitee, no GitHub.
- **Agentes de trading energético / mercados mayoristas**: **cero** repos open source relevantes en
  11 consultas. Dominio enteramente propietario.
- **O&M de activos renovables con IA**: sólo `sltzgs/OpenWindSCADA` (GPL-3.0, 259 ★, datasets de
  turbinas). No existe un equivalente open source maduro a los productos comerciales de
  mantenimiento predictivo de parques.
- **Gemelo digital de red de distribución end-to-end**: existen las piezas (`power-grid-model`,
  `pandapower`, `dpsim`) pero **ninguna plataforma integrada** open source.
- **Verificación de pesos de modelos**: `huggingface.co` **no resuelve** desde este entorno (sexto
  pase consecutivo en el que se registra). **Ninguna licencia de pesos** de modelo energético pudo
  verificarse: no afirmar nada sobre modelos de foundation energéticos descargables.
- **Repos de origen LATAM más allá de Brasil**: `json-scada` y `OSHMI` (Brasil) son hallazgo real,
  pero **no se encontró ningún repo energético de origen argentino, chileno, colombiano o
  mexicano** con tracción. El hallazgo brasileño es de **un solo autor**, no de un ecosistema.

---
*Investigado 2026-11-20 contra GitHub REST API y prensa sectorial.*
