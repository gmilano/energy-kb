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

## T9 — El perfil de licencia cambia por subsector, no por tecnología

Es el hallazgo más accionable del segundo pase del 2026-11-20. No existe "la licencia del sector
energético": hay cuatro regímenes, y cada uno impone una arquitectura distinta.

| Capa / subsector | Licencia dominante | Ejemplos verificados | Qué obliga |
|------------------|--------------------|----------------------|------------|
| Agentes y servidores MCP eléctricos | **MIT** | `Power-Agent/*`, `pypsa-mcp`, `idfkit-mcp` | Nada: empotrable en producto de cliente |
| Modelado y análisis eléctrico | **MIT / BSD-3 / Apache-2.0** | `PyPSA`, `pandapower`, `pandapipes`, `pvlib`, `calliope`, `oemof-solph`, `OpenOA`, `rdtools` | Atribución |
| Plataformas EMS / SCADA / IoT | **AGPL / GPL** | `OpenEMS`, `openremote`, `json-scada`, `SteVe` | Aislar detrás de API; cláusula de red en AGPL |
| **Upstream de petróleo y gas** | **GPL-3.0, sin excepción encontrada** | `OPM/opm-simulators`, `equinor/ert`, `equinor/webviz-subsurface` | **Mismo tratamiento que SCADA: proceso aparte** |

Y dos casos que no entran en ninguna casilla y por eso son los peligrosos:

- **`gridlab-d`** (221 ★): licencia **escrita a medida por Battelle** ("GridLAB-D License v5.3"),
  permisiva en el permiso pero con cláusula de nombre más amplia que BSD, derechos del gobierno de
  EE. UU. cuyo término "se identifica consultando a Battelle o al DOE", y **ausente de OSI y SPDX**.
  Un gate de compliance la marcará como desconocida.
- **`pypsa-earth`** (384 ★): **AGPL-3.0-or-later** declarada sólo en una línea SPDX del `README`.
  Es el único modelo energético con cobertura LATAM/APAC de fábrica, y es copyleft de red.

**Implicación para una propuesta**: la pregunta "¿qué licencia tiene el open source de energía?" no
tiene respuesta. La pregunta correcta es **"¿en qué capa vamos a tocar código?"**, y se responde
antes de estimar.

---

## T10 — Los gaps de esta KB eran, en parte, gaps de vocabulario

El pase anterior declaró vacías tres categorías. El segundo pase las encontró llenas **cambiando los
términos de búsqueda**, no esperando que apareciera software nuevo:

| Categoría | Consulta que fallaba | Consulta que funcionó | Resultado |
|-----------|----------------------|-----------------------|-----------|
| Mercados eléctricos | `energy trading agents` | `topic:electricity-market`, nombre del proyecto (`ASSUME`) | `assume` (MIT, 128 ★), `elecsim` (MIT, 61 ★), `hass-entso-e` (Apache-2.0, 280 ★) |
| O&M renovable | `wind turbine SCADA machine learning`, "mantenimiento predictivo" | **`operational assessment`**, `degradation`, y por organización (`NatLabRockies`, `pvlib`) | `OpenOA` (BSD-3, 259 ★), `rdtools` (MIT, 190 ★), `pvanalytics` (MIT, 145 ★) |
| Gemelo digital de distribución | `distribution digital twin` | `topic:opendss`, `GridLAB-D`, `VOLTTRON` por nombre | 5 repos reales, uno con licencia no OSI |

**La lección, y es de método, no de energía**: cuando una categoría aparece vacía, el primer sospechoso
es el vocabulario propio, no la ausencia del software. "Mantenimiento predictivo" es término de
*vendor*; el dominio lo llama *operational assessment*. Buscar con la palabra del folleto devuelve
cero y parece un hallazgo.

**Lo que sí sigue vacío, ahora delimitado con precisión**: no falta el *modelado* de mercados —falta
la **ejecución**. Ningún repo open source coloca ofertas en un mercado mayorista real. El límite está
entre simular y operar, no en el dominio entero.

---

## T11 — En LATAM apareció evidencia institucional, no sólo individual

Hasta este pase, la credencial LATAM de esta KB era `json-scada` + `OSHMI`: ~1.000 ★ combinadas,
**de un solo desarrollador** brasileño. Sigue siendo un hallazgo real, y sigue siendo un solo autor.

Lo nuevo es de otra naturaleza: **XM S.A. E.S.P.**, operador del Sistema Interconectado Nacional de
Colombia y administrador del mercado, publica
[`API_XM`](https://github.com/EquipoAnaliticaXM/API_XM) bajo **MIT**, con el copyright corporativo en
el `LICENSE` (75 ★, push 2026-11-10), y mantiene un org con histórico de datos actualizado al
**2026-11-19**.

**Por qué es una categoría distinta y no "un repo más"**: ante un comité de compras de una utility,
"el operador del sistema publica esto bajo MIT" es un argumento de procedencia que un repo de autor
individual no puede dar, por bueno que sea el código. Y hay demanda visible aguas abajo: ya existen
proyectos personales de agentes sobre esa API (`energyagent-colombia`, **sin licencia**;
`tablero-xm`, push 2026-11-20). Demanda sin oferta profesional es exactamente el hueco donde entra
un studio.

**Precisión que evita sobrevender**: el gap LATAM se cierra para **Brasil** y **Colombia**. Para
**Argentina, Chile y México** se buscó por institución (CAMMESA, Coordinador Eléctrico Nacional,
CENACE) y por término de dominio en español y portugués: **cero repos institucionales con tracción**.

---

## T12 — El techo de verificación ya no es la API: es la red

Tres pases consecutivos registraron "no se pudo verificar X". Este pase midió **por qué**, y el
resultado cambia lo que la KB debe prometer:

| Canal | Estado hoy | Consecuencia |
|-------|-----------|--------------|
| `gh api search/repositories` (`q=repo:owner/name`) | ✅ funciona | Única vía fiable a licencia/stars/forks/push |
| `raw.githubusercontent.com` | ✅ 200 | Licencias resolubles leyendo el archivo |
| `github.com` / `api.github.com` vía curl | ✅ **200** (el pase anterior registró 403) | La restricción anterior era de la sesión, no del sitio |
| `gh api repos/{owner}/{repo}` | ❌ 403 | La sesión sólo alcanza sus repos configurados |
| `huggingface.co`, `gitee.com`, `eur-lex.europa.eu`, `utilitydive.com` | ❌ **403 del proxy** | Política de red, **no** "no resuelve" |
| Fetch directo de páginas (`arxiv.org`, `oati.com`, `twobirds.com`) | ❌ fallo DNS/allowlist | Prensa y papers sólo llegan como *snippet* |

**Lo que esto obliga a decir en voz alta:**

1. **Las licencias de pesos de modelos no son verificables desde aquí.** Séptimo pase consecutivo.
   No es "todavía no se encontró": es **inalcanzable** por política de red. No afirmar nada sobre
   modelos descargables.
2. **La hipótesis "los repos energéticos chinos están en Gitee" no es testeable.** Dejar de
   repetirla como explicación del gap APAC: es una conjetura, no un hallazgo.
3. **Las fechas del AI Act no se pueden verificar contra el Diario Oficial.** El pase anterior pidió
   esa verificación; es imposible en este entorno. Lo honesto es "concordancia de nueve fuentes
   secundarias", y así queda registrado.
4. **Lo verificado de primera mano en esta KB es, sin excepción, lo que vive en GitHub.** Todo lo
   demás es secundario y está marcado como tal.

---

## Gaps declarados (estado al cierre del segundo pase, 2026-11-20)

Buscado y **no** encontrado. Un gap declarado es información; el silencio parece cobertura. Esta
tabla registra también **los gaps que se cerraron**, porque un gap que se arrastra cuando ya no
existe es tan dañino como uno que no se declara.

### Cerrados en el segundo pase

| Gap declarado por la mañana | Estado | Qué lo cerró |
|-----------------------------|--------|--------------|
| "Agentes de trading / mercados mayoristas: **cero** repos en 11 consultas" | 🟡 **parcialmente cerrado** | `assume` (MIT, 128 ★), `elecsim` (MIT, 61 ★), `hass-entso-e` (Apache-2.0, 280 ★), `OMIEData` (MIT, 38 ★). **Sigue faltando la ejecución**: nadie coloca ofertas reales |
| "O&M de activos renovables: sólo `OpenWindSCADA`" | ✅ **cerrado** | `OpenOA` (BSD-3, 259 ★), `rdtools` (MIT, 190 ★), `pvanalytics` (MIT, 145 ★) — el motor de análisis que faltaba junto a los datasets |
| "Gemelo digital de distribución: sólo piezas" | 🟡 **más piezas, aún sin plataforma** | `OpenDSS` vía `dss-extensions` (BSD-3), `gridlab-d` (licencia propia), `VOLTTRON` (Apache-2.0, 504 ★). Sigue siendo integración, no configuración |
| "Repos LATAM más allá de Brasil: ninguno" | ✅ **cerrado para Colombia** | `EquipoAnaliticaXM/API_XM` (**MIT**, 75 ★), publicado por el operador del sistema. Argentina, Chile y México siguen en cero |
| "Acoplamiento sectorial gas/hidrógeno: no registrado" | ✅ **cerrado** | `pandapipes` (BSD-3, 247 ★): flujo en tuberías de gas, hidrógeno y calor |
| "Planificación y expansión de capacidad: categoría ausente" | ✅ **cerrado** | `oemof-solph` (MIT, 430 ★), `calliope` (Apache-2.0, 380 ★), `temoa` (MIT, 116 ★), `PowerGenome` (MIT, 235 ★), `TIMES` (GPL-3.0, 151 ★) |

### Abiertos, con el límite medido

- **Ejecución de mercado (no simulación)**: ningún repo open source **coloca ofertas** en un mercado
  mayorista real. El modelado existe; la ejecución es enteramente propietaria. El límite está entre
  simular y operar.
- **Repos de origen APAC**: lo verificado sigue siendo `MyEMS` (MIT, 763 ★) y
  `ronaldowzy/price_forecast` (MIT, 25 ★, precio spot de mercados chinos). La hipótesis "están en
  Gitee" **no es testeable**: `gitee.com` devuelve 403 del proxy. Dejar de repetirla como
  explicación.
- **Repos institucionales en Argentina, Chile y México**: buscado por institución (CAMMESA,
  Coordinador Eléctrico Nacional, CENACE) y por término de dominio en español y portugués. **Cero
  con tracción**; sólo tableros personales de 0 ★.
- **Upstream de O&G permisivo**: **no existe** en lo encontrado. `OPM Flow`, `equinor/ert` y
  `webviz-subsurface` son **GPL-3.0** sin alternativa permisiva con tracción. No es una elección: es
  la restricción del subsector.
- **Verificación de licencias de pesos de modelos**: `huggingface.co` devuelve **403 del proxy**
  (séptimo pase consecutivo registrándolo, primero en medir que es política de red y no DNS).
  **Ninguna** licencia de pesos verificada. No afirmar nada sobre modelos energéticos descargables.
- **Verificación primaria de fechas regulatorias**: `eur-lex.europa.eu` devuelve **403 del proxy**.
  La fecha del AI Act (2-dic-2027, Reglamento (UE) 2026/1744) tiene **concordancia de nueve fuentes
  secundarias** y ninguna confirmación primaria desde este entorno. Suficiente para orientar
  estrategia; **insuficiente para firmar un plan de cumplimiento**.
- **Plataforma integrada de gemelo digital de distribución**: las piezas aumentaron a cinco, pero
  sigue **sin existir** una plataforma end-to-end open source. Proponerlo es presupuesto de
  integración.

---
*Investigado 2026-11-20 en dos pases. Lo verificado de primera mano es, sin excepción, lo que vive
en GitHub; todo lo regulatorio y de mercado es secundario y está marcado como tal.*
