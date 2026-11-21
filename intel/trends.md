---
industry: energy
region: Global
updated: 2026-11-21
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
| Plataformas EMS / SCADA / IoT | **AGPL / GPL** | `openremote`, `json-scada`, `SteVe` | Aislar detrás de API; cláusula de red en AGPL |
| **EMS con licencia partida** | **EPL-2.0 (Edge/Backend) + AGPL-3.0 (UI)** | `OpenEMS` — ver pase 14 | **Lo que se empotra es EPL-2.0: sin cláusula de red.** Sustituir o aislar sólo la UI |
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

## T13 — La capa agéntica energética tiene dos geografías y dos licencias

El hallazgo estructural del tercer pase. No hay *un* stack agéntico energético open source: hay dos,
y la diferencia no es técnica sino de origen y de licencia.

| | North America | EMEA |
|---|---|---|
| **Quién lo construye** | Universidad (Harvard SEAS, Power & AI Initiative) | Operadores de red (RTE, Alliander) bajo LF Energy |
| **Licencia** | **MIT**, sin excepción | **MPL-2.0**, sin excepción |
| **Piezas** | `PowerMCP`, `PowerSkills`, `PowerWF`, `PowerFM`, `PowerAgentBench` | `Grid2Op`, `ExpertOp4Grid`, `power-grid-model-ai`, `operatorfabric-core`, `PowSyBl`, `openSTEF` |
| **Tracción** | 44–238 ★ | 1–494 ★ |
| **Qué asume** | El agente razona sobre herramientas de ingeniería | El agente **propone a un operador humano** que acepta |

La segunda fila es la que cambia un presupuesto. MPL-2.0 es copyleft **por archivo**: se enlaza
desde código propietario sin contaminar el producto, pero las modificaciones a los archivos MPL que
se distribuyan hay que publicarlas. Entregable de integración, sin problema; entregable de marca
blanca con el motor modificado y cerrado, no.

La cuarta fila es la que cambia una arquitectura. El stack europeo trae `operatorfabric-core`: una
sala de control donde la recomendación del agente espera aceptación humana trazable. El americano no
tiene equivalente. Para un TSO —que nunca permite ejecución automática de maniobras— esa pieza no es
opcional, y su ausencia es la razón por la que muchas demos agénticas de red no llegan a piloto.

## T14 — La KB sabía modelar la red y no sabía modelar el activo

Durante dos pases esta KB barrió agentes, mercados, O&M, planificación y gemelo digital. Todas son
capas de **sistema eléctrico**. Ninguna preguntaba qué ocurre dentro de una batería, una turbina o
un reactor. No era un gap declarado: era un gap invisible, que es peor, porque el silencio parece
cobertura.

Doce repos permisivos lo cubren (ver `repos/foundations.md`), y el mayor —**`PyBaMM`, BSD-3,
1.737 ★ y 845 forks**— tiene más derivación que cualquier repo que la KB tuviera en su núcleo.

Por qué importa comercialmente: las preguntas que hoy traen los clientes —dimensionar un BESS,
garantizar capacidad a 10 años, evaluar second-life, optimizar wake steering de un parque, decir si
un proyecto cierra— **no se responden con un modelo de flujo de potencia**. Se responden con
`PyBaMM`, `OpenFAST`, `floris` y `SAM`. Tener sólo la capa de red significaba poder conversar sobre
la red y no sobre el activo que el cliente compró.

Corolario regulatorio con efecto inmediato en APAC: si Singapur, Malasia y Corea exigen plan de
baterías y vertido para aprobar un datacenter, el dimensionamiento de BESS deja de ser ingeniería de
detalle y pasa a ser **requisito de permiso**. Esa es una puerta de entrada, no un entregable menor.

## T15 — El open source energético se está institucionalizando, y todavía no es código

Tres movimientos en un trimestre, todos de instituciones y ninguno con base de código utilizable
hoy desde este entorno:

- **OpenGrid** (Linux Foundation, oct-2026): infraestructura abierta para planificación de red, con
  Breakthrough Energy GRIDS y Google.org. Buscado en GitHub: **no localizado un repo con código**.
- **CommonGrid** (Texture, 25-sep-2026): registro abierto y editable de la infraestructura eléctrica
  de EE. UU., bajo **Open Database License** — licencia de **datos**, no de software. La distinción
  importa: ODbL impone obligaciones de *share-alike sobre la base de datos derivada*, que es un
  análisis legal distinto al de una licencia de código.
- **AINETUS** (LF Energy / AI4REALNET, ~jun-2026): éste **sí** tiene código, y este pase lo localizó
  en la organización `ainetus` (MPL-2.0, activa esta semana). El pase anterior lo conocía sólo por
  prensa.

Lectura para una propuesta: anunciar que "existe OpenGrid" no es lo mismo que poder construir sobre
él. De los tres, sólo AINETUS es hoy una dependencia real. Conviene seguir los otros dos sin
comprometerlos en alcance.

## T16 — Lo que la IA consume ya es parte del alcance de un proyecto de IA energética

`mlco2/ecologits` (MPL-2.0, 363 ★) mide el consumo y la huella de las llamadas a LLM por API. Se
registra porque cierra un círculo incómodo y cada vez más auditado: un agente que optimiza una red
tiene a su vez un coste energético, y en un encargo de sostenibilidad el cliente va a preguntar por
él. Tenerlo instrumentado desde el inicio es más barato que justificarlo al final.

## T17 — Apareció la capa de modelo: foundation models de red, permisivos y corporativos

Los pases 1–3 describieron una arquitectura agéntica con un hueco en el medio: servidores MCP para
razonar sobre herramientas, entornos RL para entrenar, sala de control para aceptar — pero ningún
**modelo preentrenado del dominio**. En este pase aparece, con tres señales que no se habían dado
antes juntas:

1. **Respaldo corporativo**: `microsoft/GridSFM` (MIT, 177 ★) — *Small Foundation Models for the
   Power Grid*, publicado por Microsoft en abril de 2026.
2. **Herramientas de entrenamiento, no sólo pesos**: `gridfm/gridfm-datakit` (Apache-2.0, 170 ★)
   genera los datos de flujo de potencia y `gridfm/gridfm-graphkit` (Apache-2.0, 113 ★) entrena y
   hace fine-tuning del GNN fundacional. Son un par, diseñado para usarse en secuencia.
3. **Una vara de medir**: `emarche/RL2Grid` (MIT, 58 ★), benchmark estandarizado de agentes RL en
   entornos de red realistas.

**Por qué es un cambio de fase y no un repo más**: hasta ahora, proponer IA de red significaba
entrenar desde cero con datos del cliente — meses, y riesgo de que no converja. Con esta capa, el
punto de partida es *fine-tuning*. Cambia la forma de la propuesta: fase de evaluación corta sobre un
modelo existente, en lugar de un proyecto de investigación.

⚠️ **Y el límite, dicho con la misma claridad**: 58–177 ★. `GridSFM` no tiene push desde julio de
2026. Es una categoría **naciente**: vía de evaluación técnica, no base de producción. La relación
fork/star de `gridfm-graphkit` (0,36, la más alta de la capa agéntica de esta KB) indica que se está
usando de verdad, pero por decenas de equipos, no por cientos.

## T18 — La verificación del ahorro es la pieza comercial, y estaba ausente de esta KB

De todo lo encontrado en cuatro pases, la combinación con el camino más corto a factura **no es
agéntica**:

- `opendsm/opendsm` (**Apache-2.0**, 244 ★, 76 forks, creado en 2016, linaje OpenEEmeter/CalTRACK)
  implementa los **métodos estándar** de consumo normalizado (NMEC) y ahorro medido.
- `FlexMeasures/flexmeasures` (**Apache-2.0**, 217 ★, LF Energy) decide **cuándo** mover la carga.

El patrón habitual —"ponemos IA a optimizar y el cliente ahorra"— se cae en la primera auditoría,
porque el ahorro no es demostrable con un método que el regulador o el CFO acepten. `FlexMeasures`
decide, `opendsm` certifica. Ambas permisivas y empotrables en entregable cerrado.

**La lección de método**: esta KB pasó tres pases buscando *agentes* y se le escapó la capa que hace
cobrable lo que los agentes optimizan. Un gap de vocabulario otra vez (T10), pero de vocabulario
**comercial**: `NMEC`, `measurement and verification`, `CalTRACK` — no `AI` ni `agent`.

## T19 — Las estrellas de GitHub ya se compran en este sector

Hallazgo nuevo y directamente accionable. Dos repos de forecasting de carga eléctrica, misma cuenta:

| Repo | ★ | Forks | Issues |
|------|---|-------|--------|
| `KEV0143/Comparative-analysis-of-hourly-load-forecasting-...` | 1764 | **0** | 0 |
| `KEV0143/Adaptive-forecasting-of-electricity-consumption-...` | 1627 | **0** | 0 |

Habrían encabezado la tabla de forecasting de esta KB por un factor de 7 sobre el siguiente. La
relación fork/star del resto de la KB va de **0,10 a 0,75**; una de **0,00** con cuatro cifras de
estrellas no describe adopción.

**Regla operativa**: ante >1000 ★, comprobar `forks_count` y `open_issues_count` **antes** de escribir
la fila. `stars` es el único campo de la API que se puede comprar — `forks` e `issues` exigen que
alguien use el código. Este es el primer pase de esta KB que documenta el problema en el sector
energético, y conviene asumir que no son los dos únicos.

## T20 — "Sin licencia" es una categoría bloqueada, distinta de una categoría ausente

El tercer pase estableció que `NOASSERTION` se resuelve leyendo el `LICENSE` crudo. Este pase
encuentra el caso peor: repos **sin archivo de licencia en ninguna rama**. Sin concesión expresa, el
código está bajo copyright exclusivo del autor y **no es utilizable**, por público que sea el repo.

El caso que más cuesta: **`douyimin/GEM`** — *Geological Everything Model 3D*, foundation model
promptable de subsuelo, zero-shot. Es el único foundation model de subsuelo encontrado en cuatro
pases, resuelve exactamente lo que pediría un cliente de O&G, y es intocable. Igual
`xingyuz-phd/Generic-EMT-Modeling-of-Data-Center-Load` (modelo EMT de carga de datacenter, el objeto
central de T1/T6) y `ames-market/AMES-V5.0` (test bed de mercado mayorista RTO/ISO).

**Acción barata y concreta para el próximo pase**: abrir issue pidiendo licencia explícita en los
tres. Son repos académicos de decenas de estrellas; sus autores suelen responder. Es la diferencia
entre tres categorías bloqueadas y tres disponibles, por el coste de tres issues.

Caso aparte: **`pnoker/iot-dc3`** (1273 ★, runtime IIoT con 36 protocolos) usa una **licencia propia**,
*"IoT DC3 License Notice, Version 2026.5"* — ni OSI ni SPDX. Un gate automático de compliance la
marcará como desconocida, igual que `GridLAB-D` (T9).

## T21 — El subsector de O&G no es "todo GPL": era un artefacto de la muestra

El tercer pase concluyó que el upstream de petróleo y gas open source es **100 % GPL-3.0** y que por
tanto hay que tratar el simulador como sistema de registro aislado. **La conclusión de licencia era
falsa**, aunque el consejo arquitectónico siga siendo prudente:

- `sintefmath/JutulDarcy.jl` — **MIT**, 170 ★, 46 forks: simulación de yacimiento (Darcy multifásico,
  multicomponente) en Julia, de SINTEF. **La alternativa permisiva a OPM Flow.**
- `GeoBrain-Project/GeoBrain` — **Apache-2.0**, 88 ★: plataforma **diferenciable de extremo a extremo**
  para modelado integrado de subsuelo. Diferenciable significa que el modelo aprendido se acopla
  *dentro* del lazo físico, no al lado.
- `douyimin/CIG-bench` — **MIT**, 66 ★: benchmark de interpretación de imagen de subsuelo con IA.

**La lección de método, que es la misma de T19 y T10**: una conclusión de *categoría* ("este
subsector es copyleft") sacada de 3–4 repos es una conclusión sobre la muestra, no sobre el mundo. Si
un pase declara una propiedad de un subsector entero, el siguiente debe intentar refutarla
explícitamente. Este pase lo hizo y la refutó.

## T22 — La KB sabía simular los mercados y no sabía leerlos

Cuatro pases catalogaron 147 repos: modelado de red, optimización, expansión de capacidad,
simulación de mercados, entornos RL, servidores MCP, *foundation models*. Faltaba la capa que un
encargo necesita el **primer día**: bajar precio, carga y generación reales del operador.

Lo que faltaba no era marginal ni oscuro:

- [`fboerman/entsoe-py`](https://github.com/fboerman/entsoe-py) — **MIT**, **745 ★**, 270 forks,
  creado en 2017, 11 issues abiertas. **El repo con más estrellas que esta KB ha añadido en cinco
  pases.**
- [`gridstatus/gridstatus`](https://github.com/gridstatus/gridstatus) — **BSD-3-Clause**, 456 ★,
  los siete ISO/RTO de EE. UU. con una sola interfaz.

**Diagnóstico:** los pases anteriores buscaron por **función** (`forecasting`, `optimization`,
`DERMS`, `agent`) y nunca por **fuente de datos**. Es la confirmación más cara de T10 ("los gaps eran
gaps de vocabulario"), porque el hueco estaba en la categoría más elemental de todas y llevaba nueve
años tapado a la vista.

**Regla operativa para el próximo pase:** antes de buscar por capacidad, buscar por **el nombre del
operador y del dato** — `ENTSO-E`, `ISO`, `RTO`, `SCADA`, `AMI`, `CGMES`, `settlement`, `tariff`.

## T23 — MPL-2.0 nombra la AGPL dentro de su propio texto, y eso rompe la verificación por `grep`

Hallazgo de método, con consecuencia directa sobre el valor de esta KB.

Un detector de licencias por lectura del archivo crudo marcó `energnn/energnn` como **AGPL-3.0**. La
API de GitHub decía **MPL-2.0**, y la API tenía razón: la cláusula **1.12** de la MPL-2.0 define
"Secondary Licenses" **nombrando** GPL-2.0, LGPL-2.1 y **AGPL-3.0**. Cualquier `grep` de *"GNU
Affero"* sobre un archivo MPL devuelve un falso positivo.

**Por qué es grave en esta KB en particular:** T9 y la nota del tercer pase establecieron que
**MPL-2.0 es la licencia por defecto del sector eléctrico europeo** — `Grid2Op`, `PowSyBl`,
`operatorfabric-core`, `ExpertOp4Grid`, `power-grid-model`, `power-grid-model-ai`, `openstef`,
`VeraGrid`, `dpsim` y ahora toda la familia `energnn`. Un pase que "rescate licencias leyendo el
crudo" sin esta precaución **reclasificaría a AGPL buena parte de la KB** e inventaría una obligación
de liberar el servicio del cliente que no existe.

**Jerarquía de verificación, corregida:**

1. Si la API da un SPDX concreto → **ese es el dato**.
2. Si la API da `null` o `NOASSERTION` → leer el archivo crudo.
3. Al leer el crudo, identificar la licencia por su **título** (primera línea), nunca por la mención
   de otras licencias en el cuerpo.
4. Ante conflicto entre API y texto en la familia MPL → **gana la API**.

## T24 — `NOASSERTION` en un laboratorio nacional no es un defecto de la API: es el dato correcto

El cuarto pase trató `NOASSERTION` como ruido a corregir. En los repos de laboratorio nacional es
**exacto**: esas licencias **no son OSI**. Leídas en crudo, tres patrones distintos:

| Patrón | Repo | Qué añade sobre BSD-3 |
|--------|------|------------------------|
| **Copyleft condicionado al tipo de redistribuidor** | `NatLabRockies/resstock` (147 ★) | Si redistribuye una **universidad, laboratorio nacional u ONG**, todo el código correspondiente debe publicarse bajo la misma licencia |
| **Cláusula de designación de marca** | `NatLabRockies/REopt_API` (128 ★), `OpenStudio` (660 ★), `EnergyPlus` (ya registrado) | La versión modificada no puede usar el nombre, y debe citar el original con su marca |
| **No-endoso gubernamental** | `REopt_API`, `resstock` | Prohibido invocar DOE o el gobierno de EE. UU. para promocionar el derivado |

**El caso `resstock` es de un tipo nuevo para esta KB.** Todas las trampas catalogadas hasta ahora se
activaban por **lo que haces** con el código: servirlo en SaaS (AGPL), modificar el motor (MPL),
enlazarlo (LGPL). Esta se activa por **quién es tu cliente**. Un encargo de modelado de parque
residencial con una universidad o una fundación —perfiles de cliente habituales en proyectos de
eficiencia financiados— **obliga a publicar el entregable**. No se detecta leyendo la etiqueta: hay
que leer la cláusula.

**Implicación de proceso:** el *gate* de compliance no puede basarse en el campo `license` de la API.
Para cualquier repo de `NatLabRockies` o de laboratorio equivalente, **leer el archivo completo**.

## T25 — Leer el mercado es maduro y permisivo; pujar en él no tiene base en ninguna región

El tercer pase declaró el gap de *trading* y el cuarto lo mantuvo. Este pase lo **delimita por
completo**, y la frontera resulta ser nítida:

| Capa | Estado | Evidencia |
|------|--------|-----------|
| **Leer** precio/carga/generación | ✅ **Maduro y permisivo** | `entsoe-py` MIT 745 ★ · `gridstatus` BSD-3 456 ★ · `API_XM` (Colombia) · `Obsyd` AGPL 12 ★ (EU, 37 zonas) |
| **Simular** el mercado | 🟡 **Hay base** | `assume` MIT 128 ★ · `elecsim` MIT 61 ★ · `pomato` **LGPL-3.0** 101 ★ (sin push desde 2025-08) · `gridpath` Apache-2.0 138 ★ |
| **Optimizar** una cartera contra precios | 🟡 **Ejemplos, no bases** | `battery-storage-optimization-energy-ancillary` Apache-2.0 **11 ★** (co-optimiza energía + servicios auxiliares leyendo `gridstatus`) |
| **Pujar** de verdad | ❌ **Cero** | 15 resultados de `day-ahead bidding`: ninguno pasa de 12 ★, casi todos **sin licencia** (`capstone-optimal-bidding`, `elbud`, `powerbid`) |

**Conclusión estable a cinco pases: no proponer un bot de pujas mayoristas.** Lo nuevo es que ya no
es una ausencia difusa, sino una frontera medida: el salto de *simular* a *ejecutar* no lo ha dado
nadie en open source, en ninguna de las cuatro regiones. Un cliente que lo pida está pidiendo
desarrollo desde cero más integración con el operador de mercado, y conviene presupuestarlo así.

## T26 — Dos categorías enteras resultaron delgadas pero permisivas: hidrógeno y geotermia

Buscadas explícitamente en este pase, con resultado medido en lugar de silencio:

- **Geotermia: un solo repo usable.** `GEOPHIRES-X` (**MIT**, 67 ★, 49 forks, push 2026-11-19, 83
  issues). Su predecesor `GEOPHIRES-v2` es **GPL-3.0** y está congelado desde 2023 — *mismo
  simulador, licencia distinta según versión*, patrón que conviene comprobar siempre. El resto:
  `geothermal-cookbook` (Apache-2.0, 27 ★, muerto desde 2022) y `GeoThermalCloud.jl` (GPL-3.0, 36 ★).
- **Hidrógeno: existe, y el término de búsqueda no sirve.** `hydrogen in:name stars:>50` devuelve un
  framework de comercio electrónico (`Shopify/hydrogen`, 2.183 ★), un plugin de Jupyter (4.018 ★) y
  una caja de ritmos (1.357 ★): **ni un resultado energético en quince**. Buscando por
  `electrolyzer`, `PEMFC` y por organización aparece lo real y es permisivo:
  `NatLabRockies/electrolyzer` (**Apache-2.0**, 35 ★), `HOPP` (BSD-3, 41 ★, **66 forks**),
  `AlphaPEM` (**BSD-3**, 49 ★), más `pandapipes` para la red de gas/H₂.

**Veredicto para ambas:** hay base para un **estudio técnico-económico**, no hay ecosistema para una
plataforma. Presupuestar como ingeniería de modelo, no como integración de producto.

**Añadido a la lista de términos inutilizables en GitHub** (que ya incluía los genéricos del cuarto
pase): **`hydrogen`** y **`eléctrico`/`electrico`**. El segundo es el que ha estado ocultando
LATAM: buscar `CENACE` o `coordinador electrico` devuelve contenedores de Electron, patinetes y
cargadores. Lo que funcionó para encontrar Argentina fue buscar por **nombre de modelo**
(`pypsa`), no por institución.

## T27 — Los gaps regionales de esta KB eran gaps de vocabulario, y ahora hay una receta que los cierra

Es la generalización del hallazgo más importante del sexto pase, y vale para cualquier industria de
esta rotación, no sólo para energy.

Cinco pases midieron **cero repos de origen LATAM** en energía buscando por **dominio**
(`eléctrico`, `energia`), por **institución** (`CENACE`, `coordinador electrico`, `XM`) y por
**país**. Todas esas consultas devuelven ruido: `electrico` resuelve a un contenedor de apps Electron
de 809 ★, a patinetes y a cargadores. El pase 5 sospechó el patrón y dejó escrita la consulta
correcta. El pase 6 la ejecutó y encontró **cuatro modelos nacionales, tres MIT**.

**La receta, en una línea: buscar el nombre del *framework* más el sufijo de país.** No el dominio, no
la institución, no el idioma. `pypsa-cl`, `pypsa-chile`, `pypsa-mexico`, `pypsa-brazil`.

Por qué funciona: quien publica un modelo de red nacional no nombra el repo con el dominio ni con el
regulador — lo nombra con **la herramienta que usó**, porque su público son los demás usuarios de esa
herramienta. El vocabulario del autor es el del framework, no el del sector.

**Consecuencia inmediata y comprobable**: el gap APAC sigue abierto y el próximo pase tiene la
consulta exacta que hay que probar — `pypsa-india`, `pypsa-vietnam`, `pypsa-indonesia`,
`pypsa-korea`, y lo mismo con `calliope-` y `osemosys-`. Si T27 es correcto, ese gap se cierra igual.
Si no se cierra con esa consulta, entonces **sí** es un gap de oferta y puede afirmarse como tal.

Esto acota T10 ("los gaps eran gaps de vocabulario") con algo accionable: ya no es sólo "buscar el
estándar o el protocolo, nunca el sustantivo del dominio" — para repos **de origen regional**, la
clave es el **nombre del framework**.

## T28 — Las tres regiones convergieron en la misma frase: la IA asiste, no decide

Durante cinco pases esta KB sostuvo que `operatorfabric-core` —la capa de aceptación humana— era la
pieza sin la cual una demo agéntica de red no es desplegable. Era un argumento de ingeniería. En este
pase pasó a tener respaldo normativo **en las tres regiones a la vez y por tres vías distintas**:

| Región | De dónde viene la obligación | Qué dice |
|--------|------------------------------|----------|
| North America | **Guía de la NERC** | La IA debe **apoyar la decisión**, no actuar de forma autónoma |
| EMEA | **Guías de la Comisión sobre el artículo 6 del AI Act** (redactadas) | Clasificación de alto riesgo; si un copiloto de red entra, la supervisión humana es exigible |
| APAC | **IEA**, recogido por el ADB | La adopción sigue **limitada en la operación de red crítica para el sistema** |
| LATAM | **Stimson Center / CAF con Microsoft** | Exige **gobernanza transparente** y planificación a largo plazo |

**Lo que esto cambia en la práctica comercial**: la capa *human-in-the-loop* deja de ser una decisión
de arquitectura que un cliente puede recortar del alcance para ahorrar, y pasa a ser la parte del
alcance que **justifica** el resto. Un copiloto de operación sin trazabilidad de aceptación no es una
versión más barata del producto: es un producto que no se puede poner en una sala de control.

Corolario de posicionamiento: esto favorece a un integrador frente a un proveedor de modelo. El valor
no está en el agente, está en el **circuito de aceptación auditable** alrededor del agente — que es
trabajo de integración, es facturable, y tiene ahora cuatro fuentes regulatorias que lo exigen.

## T29 — El techo de verificación ya no es la red: es que el comando de verificación devuelve éxito

T12 estableció que el límite de esta KB había pasado de la API a la red. Este pase lo corrige hacia
algo peor y más específico: **la comprobación prescrita para validar URLs pasa siempre, incluso sobre
archivos que no existen.**

`curl -sI` a través del proxy de este entorno imprime `HTTP/1.1 200 Connection Established` —la
respuesta del `CONNECT`, no la del recurso— para cualquier URL. Comprobado contra un path inventado:
`curl -sI` dice 200; el código real es **404**. Y `github.com` responde **403** a todo desde aquí,
para repos que existen.

**Un fallo silencioso que devuelve éxito es peor que un bloqueo.** Un 403 limpio (como el de
`eur-lex.europa.eu`) se registra como gap y se dice al cliente. Un 200 falso **se escribe como dato
verificado**. La diferencia entre T12 y T29 es la diferencia entre saber que no se sabe y creer que se
sabe.

**Las tres recetas que sí verifican, y hay que usar la correcta según el host:**

1. **Archivos** (`raw.githubusercontent.com`): `curl -s -o /dev/null -w "%{http_code}"`.
2. **Repos y metadatos** (`github.com` bloqueado): `gh api -X GET search/repositories -f q="repo:owner/name"`
   — es la API REST, y `license.spdx_id`, `stargazers_count`, `forks_count` y `pushed_at` son de
   primera mano.
3. **Antes de declarar "sin licencia"**: probar `main` **y** `master`.
   `BrandolRuizOlmeda/pypsa-mexico_base` da 404 en `main` y MIT en `master`; un verificador de una
   sola rama lo habría descartado por error.

Y el corolario sobre repos multi-licencia: si hay un directorio `LICENSES/` o un `REUSE.toml`, el
proyecto es multi-licencia **por tipo de archivo** y ningún `grep` de un solo archivo acierta. En
`pypsa-eur`, el SPDX del `README` dice `CC-BY-4.0` —que es la licencia *del README*— mientras el
código es **MIT**. Dos pases distintos de esta KB han escrito ya tres lecturas diferentes de la
licencia de ese repo; la correcta está en `doc/licenses.md`.

## T30 — La IEA le puso número al hueco agéntico, y coincide con lo que esta KB medía contando repos

Durante cuatro pases esta KB sostuvo, contando repositorios, que **no existe un agente de operación de
red open source proponible**, mientras sí existe una capa madura de forecasting, mantenimiento y
planificación. Ese era un argumento de inventario, y un cliente podía descartarlo como sesgo de
muestra. Ya no: una **encuesta de la IEA a operadores de red de 13 países** (China y Japón incluidos)
encuentra que **23 % usa IA para operación en tiempo real** y **~70 % para mantenimiento de activos y
planificación de la operación**.

Dos métodos independientes —conteo de repos permisivos y encuesta a operadores— miden el mismo hueco
en el mismo lugar. Eso deja de ser una observación y pasa a ser **una tesis de posicionamiento**: el
trabajo vendible hoy vive en el 70 %. Cuando un cliente pide autonomía en el lazo de control, la
respuesta no es "no se puede", es **"la industria entera está en el otro lado, y aquí está el número"**.

## T31 — La categoría más grande del open source energético es la carga de vehículo eléctrico, y es permisiva

El trend T7 afirmaba desde el pase 2 que la movilidad eléctrica concentra la masa crítica real de la
comunidad. El séptimo pase cuantifica cuánto se subestimaba: la KB tenía **cuatro** repos de la
categoría, y buscando por protocolo (`OCPP`, `OCPI`) aparecen **once más**, de 48 a 602 ★, **nueve de
ellos permisivos** y todos con push de noviembre de 2026.

Lo relevante no es el conteo sino la **completitud**: CSMS (`citrineos-core`, Apache-2.0), stack
integral (`EVerest`, Apache-2.0, LF Energy), protocolo incluyendo **OCPP 2.1** (`rust-ocpp`,
Apache-2.0), firmware embarcado (`ChargeLab/OpenOCPP`), simulación a escala (`SAP/...simulator`),
emulación de escritorio (`monta-app/ocpp-emulator`) y un simulador que se declara **para pruebas de
agentes** (`shiv3/ocpp-cp-simulator`). Es el **único subsector energético donde existe de verdad algo
equivalente a "el Odoo de", y existe dos veces**.

Consecuencia práctica: es el vertical donde una demo se construye sin hardware, en días, con licencia
limpia. Es el camino de menor resistencia para entrar en una cuenta de utility o de operador de
movilidad.

## T32 — El término que abre una región es el nombre de su norma de conexión, no el nombre de la región

El pase 6 cerró el gap de LATAM buscando modelos nacionales por país. El séptimo lo generaliza y lo
convierte en método: **APAC no carecía de repos, esta KB carecía del vocabulario regulatorio local.**
Buscar `CSIP-AUS`, `IEEE 2030.5` y `NEM` devuelve cuatro repos australianos verificados
(`open-dynamic-export` MIT, `sep2_client` Apache-2.0, `NEMSEER` y `NEMO` GPL-3.0) donde buscar "APAC"
devolvía nada.

Es la misma lección que el automotive-KB aprendió en otro dominio: **buscar el estándar, no el
buzzword** — aquí especializada a geografía. Candidatos sin explorar para el próximo pase, uno por
mercado: **CEI 0-21** (Italia), **VDE-AR-N 4105** (Alemania), **G99** (Reino Unido), **PRODIST**
(Brasil), **NOM-001-SEDE** (México), **GB/T 19964** (China).

El corolario incómodo: cada vez que esta KB declaró un "gap regional" en siete pases, al menos dos
veces era un gap de vocabulario. Un gap regional no debe declararse sin haber buscado primero el
nombre de la norma de conexión del mercado.

## T33 — La UE financia foundation models de red, y su formato de entrada es CGMES

La hoja de ruta **COM/2026/501** (3 de junio de 2026) asigna **30 M€ en 2026 y 20 M€ en 2027**
específicamente a **foundation models para gestión y planificación de red**, dentro de ~75 M€ para
aplicaciones de IA en energía y ~100 M€ para red inteligente, con prueba de concepto en **Q1 2027** y
primeros modelos operativos a **fin de 2027**.

El eslabón que esto ilumina es de ingeniería, no de política: esos modelos consumirán **CGMES**, el
modelo de datos de la red europea. El séptimo pase añadió once repos de esa tubería —`pypowsybl`,
`powsybl-diagram`, `ToOp`, `libcimpp`, `cimgen`, `pycgmes`, `CIM-Graph`, `OpenCGMES`, `RDFArchitect`,
`powerio`, `Sparlectra.jl`— y **nueve son Apache-2.0, BSD-3 o MPL-2.0**.

La tesis: **en EMEA el activo diferencial no es el modelo, es la tubería de datos que lo alimenta.**
Hay muchos equipos capaces de entrenar un GNN de red; hay pocos que sepan ingerir, validar con SHACL y
versionar CGMES de un TSO. Ese es el cuello por el que se entra a los 50 M€.

Nótese además la autoría del bloque: **Elia Group, Alliander, Statnett, PNNL, SOPTIM**. El trend T2
("los operadores de red se volvieron proveedores de open source") suma cinco autores institucionales
nuevos y queda confirmado por séptimo pase consecutivo.

## T34 — El proyecto energético de IA ya no muere en el piloto: muere después de aprobar el piloto

El dato más accionable de la encuesta sectorial de **Grant Thornton 2026**: **38 %** está en piloto o
prueba de valor, y **32 % se estanca después de haber sido declarado listo para escalar**. Ese segundo
número es distinto del primero y más importante. Un piloto que fracasa es un problema de modelo; un
piloto aprobado que no escala es un problema de **operacionalización, integración y gobernanza** — y
eso es exactamente el servicio de un integrador, no de un proveedor de modelos.

En la misma encuesta, **54 %** señala la **incertidumbre regulatoria y de cumplimiento** como su
principal preocupación al desplegar IA agéntica. Súmese la guía **CISA/NSA de mayo de 2026** (zero
trust, defensa en profundidad, **mínimo privilegio** para infraestructura crítica) y la posición
escrita de la NERC de que la IA debe **asistir** la decisión, no actuar de forma autónoma.

Las tres cosas apuntan al mismo entregable: la capa de **aceptación humana trazable**
([`opfab/operatorfabric-core`](https://github.com/opfab/operatorfabric-core), MPL-2.0) no es un extra
de arquitectura, es el requisito que desbloquea el 32 %. Vender gobernanza no es vender menos: es
vender lo que está bloqueando el gasto.

## T35 — Un cero de la API de GitHub no es un gap del sector hasta haber reescrito la consulta

Hallazgo de método del séptimo pase, con consecuencia retroactiva. La consulta
`(electrolyzer OR hydrogen OR geothermal OR "small modular reactor") in:name,description` devolvió
**cero filas, sin mensaje de error**. La misma búsqueda sin paréntesis devolvió **dieciséis**
resultados, entre ellos `openFuelCell2`, `BattMo`, `MacroEnergy.jl`, `openTEPES` y `FINE`.

Los paréntesis agrupando `OR` dentro de un calificador `in:` hacen que la búsqueda **falle en
silencio**, lo que es peor que fallar con error: produce un cero que parece un dato.

Consecuencia retroactiva: los gaps de **hidrógeno, geotermia y nuclear** registrados en pases
anteriores deben considerarse **sospechosos de ser artefactos de sintaxis** hasta reconsultarlos sin
paréntesis. El séptimo pase ya recuperó hidrógeno y electroquímica por esta vía. Esto se suma a T29
("el techo de verificación es que el comando de verificación devuelve éxito"): aquí el comando devolvió
éxito **y cero filas**, que es la variante más engañosa.

Canal de verificación que sí funciona en este entorno, para que el próximo pase no lo re-descubra:
`gh api -X GET search/repositories -f q='repo:owner/name'` (✅, es la REST API y sus campos son de
primera mano) — mientras `gh api repos/{owner}/{repo}` devuelve **403** por alcance de sesión y
`curl github.com` / `api.github.com` devuelven **403** por política del host. **51 de 51** repos nuevos
de este pase resolvieron por el primer canal.

## T36 — Refinamiento de T32: lo que abre una región es el **protocolo**, no la norma

T32 (séptimo pase) afirmó que el término que abre una región es el nombre de su norma de conexión.
El octavo pase lo puso a prueba con los cinco candidatos que T32 dejó listados y **la afirmación hay
que corregirla**: de `VDE-AR-N 4105` (Alemania), `CEI 0-21` (Italia), `G99` (Reino Unido),
`NOM-001-SEDE` (México) y `PRODIST` (Brasil), **ninguno devolvió un repo institucional con tracción**.

La versión corregida distingue dos clases de instrumento:

| Clase de instrumento | Ejemplos | Qué produce en GitHub |
|---------------------|----------|----------------------|
| **Protocolo máquina-a-máquina con implementación obligatoria** | `IEEE 2030.5`, `CSIP-AUS`, `OpenADR`, `IEC 61850`, `DLMS/COSEM`, CIM/CGMES | Librerías, clientes, servidores, suites de conformidad |
| **Norma documental de cumplimiento** | `VDE-AR-N 4105`, `CEI 0-21`, `G99`, `NOM-001-SEDE`, `PRODIST` | Hojas de cálculo y calculadoras de 0 ★, de autor individual |

**La diferencia no es la madurez eléctrica del país.** Alemania e Italia no están detrás de
Australia; lo que ocurre es que Australia **obliga a que dos máquinas se hablen** y Alemania obliga a
entregar un expediente. Donde la norma impone interoperabilidad, el open source aparece; donde impone
documentación, aparece el PDF.

**Consecuencia para el método de esta KB:** antes de declarar que una región tiene o no tiene oferta,
preguntar **qué clase de instrumento rige**. Si es documental, el gap de repos es esperable y **no
mide la madurez del mercado** — mide la naturaleza de la norma. Y esa asimetría es, en sí, una
oportunidad: el expediente de cumplimiento documental es trabajo que nadie ha automatizado.

## T37 — Las cuatro regiones convergieron en el mismo instrumento regulatorio: acceso condicional

T28 registró que las regiones convergieron en la frase *"la IA asiste, no decide"*. El octavo pase
registra una segunda convergencia, y es más accionable porque crea entregables:

| Región | Instrumento de 2026 | Qué condiciona el acceso a la red |
|--------|--------------------|-----------------------------------|
| **North America** | Órdenes de la FERC del 18-jun-2026 a los seis operadores + tarifas estatales de carga grande | Reforma de la tarifa de conexión; los datacenters pagarían las mejoras que causan |
| **EMEA** | Esquema de calificación de datacenters ≥500 kW TI (propuesto 21-sep-2026) | Califica eficiencia energética e hídrica, calor residual **e interacción con la red** |
| **APAC** | Marcos de *acceso condicional, diversificación geográfica, soporte a la red y controles de capacidad* | La conexión se concede contra compromisos de fiabilidad y flexibilidad |
| **LATAM** | REDATA (Lei 15.504, 15-sep-2026) y acceso directo a AT autorizado por ANEEL | Habilita el acceso y lo ordena; 38 GW de solicitudes contra ~12 GW disponibles |

**La tendencia, dicha en una frase:** en las cuatro regiones el permiso de conectarse dejó de ser un
trámite de capacidad y pasó a ser **un expediente que hay que argumentar**. Eso traslada el gasto
desde el equipamiento hacia el **análisis**, que es exactamente lo que esta KB puede equipar.

⚠️ **Y el contrapeso que hay que decir antes de que lo diga el cliente**: según IDC (Gaia Gallotti),
la barrera para escalar IA agéntica en operaciones centrales de energía **no es la tecnología sino el
entorno de datos**, más escasez de perfiles y una cultura cautelosa. Converge con T34 (el proyecto
muere después del piloto) y reordena la propuesta: **fase uno es ingeniería de datos.**

## T38 — Una organización confiable no es una licencia

El octavo pase catalogó alrededor de treinta repos de **Open Energy Transition**, la autora de
`pypsa-mcp`. MIT domina, **y dentro de la misma organización hay cuatro repos AGPL-3.0**
(`solver-benchmark`, `demandcast`, `geothermal-modelling`, `efuels-supply-potentials`) y al menos
tres **sin archivo de licencia**, uno de ellos con 80 ★ (`Awesome-Grid-Model-Data`).

El caso que más muerde es `demandcast`: es precisamente la pieza que uno querría para un producto de
forecasting de demanda, y su **AGPL-3.0 obliga a liberar el servicio derivado**. Un equipo que
apruebe "la organización" en lugar del repo se lleva esa cláusula sin verla.

**Regla:** la aprobación de licencia es **por repo**, siempre, incluso dentro de una organización ya
usada en producción. Y la heurística inversa también falla: `pudl` (MIT, 621 ★) viene de una
cooperativa pequeña y es más permisivo que repos de laboratorios nacionales.

## T39 — En modelos energéticos nacionales, `NOASSERTION` suele significar licencia dual, no ausencia

Esta KB ya tenía cuatro sitios donde buscar una licencia que la API de GitHub reporta como
`NOASSERTION` (`LICENSE*`, `COPYING`, el SPDX de `pyproject.toml`, un `legal.html` dentro del árbol).
`MAHTEP/TEMOA-Italy` añade un quinto caso, y es de una clase nueva: **un único `LICENSE` que se parte
por tipo de contenido**. El texto crudo dice *"released under two licenses, according to the type of
content"* — **CC-BY-4.0** para bases de datos (`*.sql`, `*.zip`), documentación y figuras, y **MIT**
para todo el código (`*.py`).

Tiene sentido estructural: un modelo energético nacional **es** dos cosas —un dataset del país y el
código que lo resuelve— y sus autores les ponen licencias distintas a propósito. Un gate automático
de licencias habría descartado un modelo nacional europeo completo del Politecnico di Torino.

**Regla:** ante `NOASSERTION` en un modelo energético nacional, leer el `LICENSE` crudo **entero**, no
sus primeras líneas: en TEMOA-Italy la parte MIT aparece *después* de la parte Creative Commons.

## T40 — La capa de autorización humana dejó de ser una frase de README y es código ejecutable

T28 registró que las tres regiones convergieron en la misma frase: *la IA asiste, no decide*. Este
pase encontró la **primera implementación** de esa frase en energía:
[`Ninemilo/OpenVigil`](https://github.com/Ninemilo/OpenVigil) (**Apache-2.0**, 180 ★, 37 forks)
separa **22 agentes en tres capas — decisión, revisión y ejecución** — y hace que la persona
autorice las acciones de alto riesgo, con orden de trabajo, evidencia de campo y traza auditable.

Lo que lo hace citable no es su precisión —no publica ninguna— sino que **marca UNVERIFIED** la
exactitud de campo, la calibración, la operación en sombra y la calificación de release, y admite
que la salida de su demo viene de **fixtures deterministas, no de modelos en vivo**.

**Tercera confirmación del patrón en esta rotación**: automotive encontró `LionDriver` publicando
**42 defeaters abiertos** y `wtfault-scanner` con su *"never makes anything up"*; energy encuentra
`OpenVigil`. **Publicar el propio límite se consolidó como movimiento de credibilidad en industrias
reguladas** — y es replicable: un entregable de Globant que publique su propia matriz de lo no
verificado compite mejor, no peor.

## T41 — El plazo regulatorio de EMEA se movió, y la noticia útil es que la prórroga no es firme

El *Digital Omnibus* (acuerdo político del **7 de mayo de 2026**) corre las obligaciones de **alto
riesgo del Anexo III** —donde cae la mayor parte de la IA operativa de energía— del **2 de agosto de
2026** al **2 de diciembre de 2027**. Pero **hasta la adopción y publicación formales rigen las
fechas originales**.

Las dos mitades de esa frase tienen que viajar juntas, y de ahí sale el servicio:

- **Mal asesoramiento**: "hay prórroga, tienen hasta diciembre de 2027".
- **Asesoramiento correcto**: preparar el expediente contra la **fecha original** y tratar la
  prórroga como **margen de ejecución**, no como plan.

Esto además **desactiva una confusión entre regiones**: varias fuentes latinoamericanas siguen
advirtiendo del alcance extraterritorial del AI Act con la fecha del 2 de agosto de 2026. No están
equivocadas sobre la vigencia; están incompletas sobre el Anexo III. Un exportador LATAM que sirve
usuarios en la UE necesita **las dos fechas y el estado de la prórroga**, no una.

## T42 — Tres gaps de esta KB ahora tienen número, y dos de ellos están debajo de recetas ya escritas

La diferencia entre "no encontramos nada" y "la oferta abierta es un repo" es presupuestable. Este
pase midió:

| Gap | Consulta | Resultado | Receta afectada |
|-----|----------|-----------|-----------------|
| **Optimización de BESS** | `"battery energy storage" in:name,description stars:>25` | **total = 1** (`DBESS-Arbitrage`, Apache-2.0, 26 ★). El término `BESS` lo ocupan un switch de Berkeley, un overclocker de GPU y funciones de Bessel | **Receta 13** se apoya en una base de un repo → presupuestar como **ingeniería de modelo**, no integración |
| **Cumplimiento NERC CIP** | `"NERC CIP" in:name,description,readme` | **573 resultados, ninguno del sector**. Único adyacente: `argonne-citadel/grid-stix` (GPL-3.0, **2 ★**, Argonne) | **Receta 29** corre contra el plazo de **diciembre de 2026** con oferta abierta **cero** → el expediente es el entregable |
| **MDM / meter-to-cash** | `"meter data management"` | 155 resultados; el mejor tiene **7 ★** y dos años sin push | Confirma (no reemplaza) la conclusión del octavo pase en `verticals/solutions.md` |

El único optimizador sectorial de baterías con tracción, `FlexPwr/bess-optimizer` (118 ★), tiene
además **licencia copyleft de familia GPL** (leída en `LICENSE` crudo; la API dice `NOASSERTION`) y
**trece meses sin push**. El gap no es de visibilidad: es de oferta.

## T43 — Refinamiento operativo de T36: una consulta con `OR` entre frases entrecomilladas no mide nada

T36 estableció que lo que abre una región es el **protocolo**, no la norma. Este pase encontró
**cómo se rompe la consulta** al aplicarlo, y es un error silencioso porque devuelve miles de
resultados en lugar de cero:

| Consulta | Resultados | Primeros hits |
|----------|-----------|---------------|
| `EEBus OR "EN 50491" OR "S2 protocol" flexibility` | **1.890.158** | `sindresorhus/awesome`, `tensorflow/tensorflow` |
| `"Green Button" OR "NERC CIP"` | **355.887** | `30-Days-Of-Python`, un toolkit de macOS |
| `EEBus` (término único) | **229** | `evcc`, `eebus-go`, `openeebus` — **la categoría real** |
| `"NERC CIP"` (término único) | **573** | listas de cumplimiento genéricas |

**Regla operativa, válida para cualquier industria de esta rotación: un término por consulta.** El
`OR` entre frases entrecomilladas diluye el filtro hasta volverlo ruido, y el resultado *parece*
exitoso porque hay miles de filas.

**Corolario distinto y también medido:** `"Green Button"` **a solas** sigue devolviendo 355.315
resultados, porque sus dos palabras son demasiado comunes. T35 decía que un cero de la API no es un
gap del sector hasta reescribir la consulta; T43 añade el caso contrario: **hay nombres de protocolo
real que GitHub no puede buscar de ninguna forma**. Para esos, la vía es la organización o el
proveedor, no el término.

## T44 — La frontera del canal de verificación está en el endpoint, no en el host

Precisión sobre lo que el pase de automotive dejó escrito ("`gh api search/repositories` ES la API
REST"). Verificado por error y corregido en este pase:

- **`gh api search/repositories` NO está limitado al alcance de la sesión**: resuelve cualquier repo
  público con el calificador `repo:owner/name`, y `license.spdx_id`, `stargazers_count`,
  `forks_count`, `pushed_at`, `created_at` y `open_issues_count` son campos de primera mano.
- **`gh api repos/{owner}/{repo}` SÍ está limitado**: devuelve un error JSON pidiendo `add_repo`.
- **Consecuencia práctica no obvia:** como no se puede leer `default_branch`, la verificación de un
  `LICENSE` crudo debe **probar `main`, luego `master`, luego `develop`**. `MyEMS/myems` se rescató
  como **MIT** sólo por el *fallback* a `master` — en `main` el archivo devuelve 404. Un pase que
  sólo pruebe `main` concluirá "sin licencia" sobre repos que sí la tienen.

## T45 — ~~"Sin licencia" ya bloquea la única implementación de un protocolo entero~~ **DEROGADA EN EL PASE 13**

> ❌ **T45 era falsa y se deroga.** Se conserva aquí porque su modo de fallo es la lección, y porque
> el dato equivocado se había propagado a `agents/top.md`, `compose/patterns.md` y este archivo.
> La sustituye **T46**.

**Lo que T45 afirmaba:** que [`OpenLEADR/openleadr-rs`](https://github.com/OpenLEADR/openleadr-rs)
—la implementación de OpenADR 3.0 (VTN + VEN en Rust, 107 ★, 30 forks)— **no tenía archivo de
licencia** en `main`, `master` ni `develop`, y que por tanto **"OpenADR 3.0 no tiene implementación
abierta licenciada"**.

**Lo que el pase 13 verificó, en tres canales independientes:**

| Canal | Resultado |
|-------|-----------|
| `Cargo.toml` (manifiesto del paquete) | `license = "Apache-2.0 OR MIT"` |
| `raw.githubusercontent.com/.../main/LICENSE-MIT` | **200** (texto MIT, "Copyright (c) 2024 Stichting ElaadNL and Contributors") |
| `raw.githubusercontent.com/.../main/LICENSE-APACHE` | **200** (texto Apache-2.0 canónico) |

Ambos archivos devuelven **200 también en `master`**. **`openleadr-rs` es doble Apache-2.0 / MIT y
es perfectamente usable en un entregable de cliente.**

**Por qué falló la medición, que es lo único que hay que recordar:** la lista de sondas de esta KB
era `LICENSE`, `LICENSE.md`, `LICENSE.txt`, `COPYING`, `LICENCE`. **Ninguna de ellas existe en este
repo** — `LICENSE` da 404 en las tres ramas, que es exactamente lo que el pase anterior midió y
reportó con honestidad. Lo que faltaba era saber que **el ecosistema Rust parte la licencia en dos
archivos** (`LICENSE-MIT` + `LICENSE-APACHE`), convención del propio Cargo para el dual-licensing
que casi todo el ecosistema usa. La sonda no estaba mal ejecutada: estaba **incompleta para el
lenguaje**.

**El coste de no haberlo visto, dicho sin rodeos:** la KB recomendaba durante dos pases entregar
sobre **OpenADR 2.0b**, o negociar licencia durante semanas, o **reimplementar 3.0 desde la
especificación como "trabajo facturable"**. Las tres eran innecesarias. Es el error más caro que
esta KB ha cometido y registrado: no un repo mal clasificado, sino **una decisión de arquitectura
regional tomada sobre un hecho falso**.

## T46 — La licencia la declara el gestor de paquetes, y hay que leerla ahí primero

Sustituye a T45 y generaliza T39 (`NOASSERTION` es una pregunta, no un dato) y T44 (probar varias
ramas).

**La regla:** antes de concluir cualquier cosa sobre la licencia de un repo, leer el **manifiesto
del gestor de paquetes**, porque contiene la licencia como **expresión SPDX declarada por el autor**
en una sola línea legible por máquina:

| Ecosistema | Archivo | Campo |
|-----------|---------|-------|
| Rust / Cargo | `Cargo.toml` | `license = "..."` (y la convención `LICENSE-MIT` + `LICENSE-APACHE`) |
| Python | `pyproject.toml`, `setup.py`, `setup.cfg` | `license`, `classifiers` |
| JS / Node | `package.json` | `"license"` |
| Java / Maven | `pom.xml` | `<licenses>` |
| Go | sin campo — hay que caer a los archivos | — |
| .NET | `*.csproj` | `<PackageLicenseExpression>` |

**Lista de sondas corregida y completa**, en este orden:
`Cargo.toml`/`pyproject.toml`/`package.json`/`pom.xml` → `LICENSE` → `LICENSE.md` → `LICENSE.txt`
→ `LICENSE-MIT` → `LICENSE-APACHE` → `COPYING` → `LICENCE`, cada uno contra las ramas
`main`, `master`, `develop`.

**Y la consecuencia transversal, que vale para todas las industrias de esta rotación, no sólo
energy:** cualquier KB de esta familia que haya clasificado un repo de **Rust** como "sin licencia"
leyendo sólo `LICENSE` tiene **un falso negativo con la misma firma** y debe re-verificarse. El
patrón diagnóstico es exacto y se puede buscar: **`LICENSE` da 404 en todas las ramas y el repo
sigue vivo y con tracción** ⇒ no es un repo sin licencia, es un repo cuyo archivo de licencia tiene
otro nombre.

Otras piezas que entran en la misma categoría bloqueada este pase: `runyao-yu/PriceFM` (158 ★,
foundation model de precio), `california-energy-commission/MIDAS` (dato tarifario **oficial** de un
organismo público de California, 9 ★) y `pnoker/iot-dc3`, que no está sin licencia sino con una
**propia** — `LICENSE.txt` abre con *"IoT DC3 License Notice, Version: 2026.5"*, lo que exige
revisión legal y no es asimilable a una licencia estándar.

## Gaps declarados (estado al cierre del tercer pase, 2026-11-20)

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

### Cerrados o acotados en el tercer pase

| Gap | Estado | Qué lo cambió |
|-----|--------|---------------|
| "AINETUS: anunciado en prensa, **código no localizado**" | ✅ **cerrado** | Organización `ainetus` en GitHub: `ExpertOp4Grid` (MPL-2.0, 12 ★), `Expert_op4grid_recommender`, `soft_label_gnn`, `Grid2Op_MORL`. Activa 2026-11-18 |
| Modelado de **activos físicos** (no declarado antes: gap invisible) | ✅ **cerrado** | `PyBaMM` (BSD-3, 1737 ★), `liionpack` (MIT), `OpenFAST` (Apache-2.0, 991 ★), `floris` (BSD-3), `SAM`/`ssc`/`reV`/`sup3r` (BSD-3), `openmc` (MIT, 1147 ★) |
| **Respuesta de demanda**: faltaba el protocolo con la utility | ✅ **cerrado** | `OpenLEADR/openleadr-python` (Apache-2.0, 161 ★), implementación de OpenADR 2.0b |
| **Capa human-in-the-loop** para agentes de red (gap invisible) | ✅ **cerrado** | `opfab/operatorfabric-core` (MPL-2.0, 42 ★): sala de control con aceptación trazable |
| **Comercial de utility** (facturación, CIS, medición): categoría ausente | 🟡 **hay piezas, no hay plataforma** | `killbill` (Apache-2.0, 5858 ★), `openmeter` (Apache-2.0, 2457 ★), `micropowermanager` (MIT, 30 ★). **No existe un "Odoo de la energía"**: la lógica tarifaria regulatoria es desarrollo propio |
| **Nuclear / SMR**: subsector ausente | ✅ **cerrado como base abierta** | `openmc` (MIT verificada, 1147 ★), `moose` (LGPL-2.1, 2409 ★) |

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


### Añadidos y precisiones del tercer pase sobre los gaps abiertos

- **Verificación primaria europea: no es un problema de EUR-Lex, es de dominio.** Pases anteriores
  registraban `eur-lex.europa.eu` → 403. Este pase midió **seis hosts distintos**:
  `eur-lex.europa.eu`, `ec.europa.eu`, `op.europa.eu`, `data.europa.eu`,
  `data.consilium.europa.eu` y `oeil.secure.europarl.europa.eu`. **Todos fallan en el CONNECT del
  proxy.** La conclusión correcta no es "EUR-Lex está caído" sino que **ninguna fuente primaria de
  la UE es alcanzable desde este entorno**. Dejar de intentarlo host por host; cualquier fecha
  regulatoria europea de esta KB es, y seguirá siendo, secundaria mientras no cambie la política de
  red. COM(2026) 501 y ST-10101-2026 entran con esa misma marca.
- **Huggingface: octavo pase, y ahora con el mecanismo identificado.** `huggingface.co` falla con
  `CONNECT tunnel failed, response 403`, tanto en la raíz como en `/api/models/...`. Es **rechazo
  del proxy**, no DNS ni bloqueo de la aplicación. Probar otra ruta de la misma API no va a
  funcionar. **Ninguna licencia de pesos verificada**; no afirmar nada sobre modelos descargables.
- **Límite de método nuevo, importante para el próximo pase**: `gh api repos/{owner}/{repo}`
  devuelve **403** para cualquier repo no adjuntado a la sesión. El **único** canal de verificación
  que funciona es `gh api -X GET search/repositories -f q='repo:owner/name'`, que sí es la REST API
  de GitHub y devuelve `license.spdx_id`, `stargazers_count`, `forks_count` y `pushed_at` de primera
  mano. `raw.githubusercontent.com` responde 200 y sigue siendo la vía para resolver `NOASSERTION`.
- **`OpenGrid` y `CommonGrid` no son todavía dependencias.** Buscados en GitHub por nombre y
  descripción: sin repo de código localizable. Son anuncios institucionales (ver T15).
- **Repos de origen APAC: sin cambio.** El tercer pase no añadió ninguno. Lo verificado sigue siendo
  `MyEMS` (MIT, 763 ★) y `price_forecast` (MIT, 25 ★). Nota: `frappe/erpnext` (GPL-3.0, 41.460 ★) es
  de origen APAC y de tracción enorme, pero es ERP generalista, no energía — no cuenta como
  credencial sectorial.
- **Argentina, Chile y México: sin cambio.** Cero repos institucionales con tracción. La credencial
  LATAM verificable sigue siendo Brasil y Colombia.

### Estado al cierre del cuarto pase (2026-11-20)

**Cerrados en este pase:**

- **Foundation models de red** (estaba implícito como hueco en T4): `GridSFM`, `gridfm-datakit`,
  `gridfm-graphkit`, `RL2Grid`. Naciente pero real.
- **Sincrofasores / PMU**: ausente por completo hasta hoy. `openPDC` + `gsf`, ambos **MIT**.
- **Medición y verificación de ahorro (NMEC)**: `opendsm` (Apache-2.0). Era el hueco comercial más
  caro de la KB.
- **Scheduling de flexibilidad como plataforma**: `FlexMeasures` (Apache-2.0, LF Energy).
- **Simulación de protocolo sin hardware**: `ProtoForge` (MIT, 28 protocolos), `iec104-python`,
  `Gurux` DLMS. Desbloquea pilotos sin acceso a subestación.
- **Seguridad OT de la capa agéntica**: `mitre/caldera-ot` (Apache-2.0).
- **O&G permisivo**: `JutulDarcy.jl` (MIT), `GeoBrain` (Apache-2.0) — refuta la tesis del pase 3.
- **ERP/CRM de utility**: cerrado **como respuesta negativa verificada**. No existe ERP/CRM open
  source específico de energía con licencia MIT/Apache. La ruta es `OFBiz` (Apache-2.0) + `killbill`
  + `openmeter`, con la lógica tarifaria como desarrollo propio.

**Abiertos, con el límite medido:**

- **Agente de ejecución de trading mayorista**: cuarto pase consecutivo sin encontrarlo. `assume` y
  `elecsim` son simuladores. Parece ser un hueco estructural, no de búsqueda.
- **Foundation model de subsuelo utilizable**: existe (`GEM`) y está **bloqueado por ausencia de
  licencia**, no ausente.
- **Oferta de origen LATAM**: sin crecimiento. Sigue siendo `json-scada` + `OSHMI` (Brasil, GPL-3.0)
  y `API_XM` (Colombia, MIT). Tres repos, dos autores.
- **Oferta de origen APAC**: escasa y medida — `MyEMS`, `hass-state-grid`, `GeoBrain`, `CIG-bench`.
  Hueco de **oferta**, no de demanda: APAC lidera adopción según fuentes secundarias.
- **DERMS open source**: no se encontró ninguna plataforma DERMS completa. Hay piezas
  (`FlexMeasures`, `OpenLEADR`, `power-grid-model`), no el sistema.
- **Pesos de modelo con licencia verificada**: `huggingface.co` sigue sin resolver desde este entorno
  (sexto pase consecutivo). Ninguna afirmación sobre licencia de pesos es verificable aquí.


### Estado al cierre del quinto pase (2026-11-20)

**Cerrados en este pase:**

- **Acceso a datos de mercado y de red** → `entsoe-py` (MIT, 745 ★) para EMEA, `gridstatus` (BSD-3,
  456 ★) para North America, `open-grid-emissions` (MIT, 96 ★) para emisiones horarias de EE. UU.
  Era el gap más básico y el que llevaba más tiempo sin verse.
- **Tecno-economía de generación y de activo** → `REopt_API`, `gridpath`, `ReEDS-2.0`, `Egret`,
  `pysam`, `ROSCO`, `HOPP`, `bifacial_radiance`, `GEOPHIRES-X`.
- **SDK de edificios bajo EnergyPlus** → `OpenStudio` (660 ★) y `resstock` (147 ★, con la cláusula
  que hay que leer).
- **Datos de entrenamiento sin problema de GDPR** → `OpenSynth` (Apache-2.0, 77 ★). Responde a la
  barrera que la propia Comisión Europea declara.
- **Geotermia** → acotado: un repo usable (`GEOPHIRES-X`, MIT).
- **Hidrógeno** → acotado: tres repos permisivos, ningún ecosistema.

**Abiertos, con el límite medido (actualizado):**

- **Ejecución de mercado (pujas reales)**: cero en las cuatro regiones. Ver T25. **Es la frontera
  mejor medida de esta KB.**
- **Emisiones horarias de red fuera de EE. UU.**: `open-grid-emissions` sólo cubre EE. UU. **Gap
  nuevo, declarado explícitamente en este pase.**
- **DERMS open source completo**: sin cambios. Piezas, no sistema.
- **Oferta de origen LATAM**: cambia de naturaleza. `PyPSA-AR` (Argentina) **existe** con 10 ★ y
  **sin archivo de licencia**: ya no es gap de oferta, es **gap de permiso**. Chile y México siguen en
  **cero** verificado, y ahora se sabe que el término `eléctrico` es la causa de que las búsquedas
  por institución no encuentren nada.
- **Oferta de origen APAC**: se mueve poco pero verificado. `PyPSA-China` tiene **MIT confirmada** por
  README y `LICENSES/MIT.txt`. Precisión obligada: vive bajo la organización `PyPSA`, de liderazgo
  europeo — es un modelo **de** China, no un repo **de origen** chino. `gitee.com` → 403, **octavo
  pase consecutivo**.
- **Pesos de modelo con licencia verificada**: `huggingface.co` sigue sin resolver, **séptimo pase
  consecutivo**.
- **Confirmación primaria regulatoria**: sin cambios y ahora con más superficie expuesta. Lo añadido
  en este pase (órdenes de la FERC de junio de 2026, alerta NERC de nivel 3, hoja de ruta de la CE,
  los 75 M€ de Horizon Europe, la autorización de ANEEL a Scala, el criterio del SEA chileno) es
  **todo secundario**. `eur-lex.europa.eu` sigue devolviendo 403. Sirve para planear; **no para
  firmar**.

### Estado al cierre del noveno pase (2026-11-20)

**Cerrados o acotados en este pase**

- **Protocolo vehículo↔cargador**: cerrado. `ecog-io/iso15118` (Apache-2.0, 250 ★, 142 forks) e
  `ecog-io/josev` (Apache-2.0, 164 ★) cubren ISO 15118 -2/-20/-8. Con la advertencia de que
  `RISE-V2G` y `MicroOcpp`, las piezas más citadas, llevan ~11 meses sin push.
- **Flexibilidad doméstica EMEA**: cerrado con `enbility/eebus-go` (MIT) y `NIBEGroup/openeebus`
  (Apache-2.0). Queda **acotado** el estándar **S2**: existe tooling (`flexmeasures-s2`,
  Apache-2.0) y tiene **2 estrellas**.
- **Ingeniería IEC 61850 (configuración SCL)**: cerrado con `openscd/open-scd` (Apache-2.0, 145 ★),
  acotado por mantenimiento: 10 meses sin push, 229 issues.
- **Benchmark de forecasting de precio**: cerrado con `jeslago/epftoolbox` (Apache-2.0, 417 ★).
- **Geotermia**: inventario corregido — tres repos usables, no uno (`pygfunction` BSD-3 75 ★,
  `waiwera` LGPL-3.0 62 ★, `GEOPHIRES-X` MIT 67 ★). La tesis de T26 no cambia.
- **Capa de datos de subsuelo (O&G)**: cerrado con `lasio` (MIT, 411 ★) y `welly` (Apache-2.0,
  381 ★, sin push desde 2025-07).
- **LATAM**: ya son **dos** repos institucionales, no uno. `batuenergy/atlas-sen` (**MIT**
  rescatada, México, push de hoy) se suma a `json-scada`/`OSHMI` (Brasil).

**Abiertos, ahora con el límite medido**

- **Optimización de BESS**: **un** repo abierto con >25 ★ en toda la categoría. Gap de oferta, no de
  búsqueda.
- **Cumplimiento NERC CIP**: **cero** herramientas del sector frente al plazo de diciembre de 2026.
- **MDM / meter-to-cash**: el mejor repo tiene **7 ★** y dos años sin push.
- ~~**OpenADR 3.0**: sin implementación abierta licenciada (T45)~~ → **GAP CERRADO, NUNCA EXISTIÓ**
  (pase 13). `openleadr-rs` es **Apache-2.0 OR MIT** por `Cargo.toml`; `ElaadNL/openadr3-client` es
  Apache-2.0. Ver T45 derogada y T46.
- **Foundation models de red descargables**: `gridfm-graphkit` (Apache-2.0) **no publica
  checkpoint preentrenado**. Hay framework de entrenamiento, no modelo listo.
- **Relación DOE "GridFM 2.0" ↔ organización GitHub `gridfm/*`**: **no verificada**. Adyacente por
  nombre y tema; no afirmarla en material de cliente.
- **`Mcp-Brasil/mcp-brasil` (MIT, 1.867 ★) ¿incluye APIs energéticas?**: no verificado. Tarea
  barata y de alto retorno para el próximo pase.
- **Protocolos que GitHub no puede buscar**: "Green Button" devuelve 355.315 resultados a solas.
  Para esos, la vía es la organización o el proveedor (T43).


## T46 — `NOASSERTION` en un laboratorio nacional depende **del laboratorio**: acotación de T24

T24 estableció que en los repos de `NatLabRockies` (ex-NREL) el `NOASSERTION` es **exacto**: esas
licencias no son OSI porque añaden cláusulas reales (copyleft según el tipo de redistribuidor en
`resstock`, designación de marca en `REopt_API` y `OpenStudio`, no-endoso gubernamental). Eso sigue
siendo verdad y el proceso que T24 impuso —leer el archivo completo— sigue siendo obligatorio.

**Lo que este pase descubre es que la conclusión no se traslada a otros laboratorios.** En
`sandialabs`, la API reporta `NOASSERTION` en **todo** el portafolio energético y es un **falso
negativo** en cuatro de cinco casos:

| Repo | API | `LICENSE` leído en crudo | Cláusula añadida |
|------|-----|--------------------------|------------------|
| `snl-quest` (162 ★) | NOASSERTION | **BSD-3-Clause** | ninguna |
| `snl-pstess` (40 ★) | NOASSERTION | **texto MIT íntegro** | ninguna |
| `snl-progress` (24 ★) | NOASSERTION | **BSD-3-Clause** | ninguna |
| `pvOps` (22 ★) | NOASSERTION | **BSD-3-Clause** | ninguna |
| `OpenCSP` (13 ★) | NOASSERTION | **no existe el archivo** | — (bloqueado de verdad) |

**La causa es mecánica y generalizable:** el archivo abre con *"Copyright … National Technology &
Engineering Solutions of Sandia, LLC (NTESS). Under the terms of Contract DE-NA0003525 with NTESS,
the U.S. Government retains certain rights in this software"* **antes** del otorgamiento. Ese
preámbulo de contrato DOE rompe el clasificador de GitHub; el otorgamiento que sigue es estándar.

**Las dos mitades juntas dan la regla utilizable:** en un repo de laboratorio nacional,
`NOASSERTION` significa *"el clasificador no pudo decidir"*, y hay **dos razones posibles con
consecuencias opuestas** — cláusula añadida real (NREL: bloquea o condiciona) o preámbulo de
contrato (Sandia: no cambia nada). **Nunca se puede inferir cuál sin leer el archivo**, y leer sólo
la etiqueta falla en las dos direcciones: descarta BSD-3 usable en Sandia y acepta como permisivo lo
que en NREL no lo es.

**Corolario de método que costó dos intentos en este pase:** EPRI y Sandia nombran el archivo
`LICENSE.txt`, no `LICENSE`. Pedir sólo `LICENSE` devuelve 404 y haría declarar "sin licencia" a
`StorageVET`, `DER-VET` y `OpenDER`, tres repos **BSD-3 perfectamente usables**. Antes de declarar
ausencia de licencia hay que pedir `LICENSE`, `LICENSE.txt` y `LICENSE.md`.

## T47 — Cuando la oferta esperable es de investigación aplicada, buscar **la institución**, no la cosa

Esta es la corrección de método más rentable de la rotación, medida en repos: **~125 encontrados en
un pase**, en organizaciones que nueve pases anteriores no vieron.

La cadena de lecciones de esta KB venía siendo:

| Pase | Lección | Alcance real |
|------|---------|--------------|
| 7 | Buscar **el nombre de la norma local** (`CSIP-AUS`), no la región | Abrió APAC |
| 8 | Esa regla **no generaliza**: la norma sin comunidad no devuelve nada | Acotó la anterior |
| 9 | Buscar **la norma**, no el buzzword (`ISO 15118`, `ISO 26262`) | Abrió la capa de protocolo |
| **10** | **Buscar la institución, no la categoría** | **~125 repos de EPRI, GPA y Sandia** |

**El mecanismo por el que la búsqueda por categoría falla es que las instituciones nombran sus
herramientas con el acrónimo interno del método, y ese acrónimo no contiene ningún término de
dominio:**

| Herramienta | Qué es | Término de categoría que **no** aparece en su nombre |
|-------------|--------|----------------------------------------------------|
| `StorageVET`, `DER-VET` | Valoración de almacenamiento y DER | *battery energy storage* |
| `QuESt` (`snl-quest`) | Análisis de almacenamiento | *storage*, *BESS* |
| `ProGRESS` (`snl-progress`) | Fiabilidad probabilística con almacenamiento | *reliability*, *storage* |
| `openMIC` | Recolección de datos de medidor | *meter data management* |
| `openXDA` | Analítica de perturbaciones | *power quality*, *disturbance analytics* |
| `SPI-Tool` | Entradas estocásticas de planificación | *planning* |

El pase 9 midió `"battery energy storage" in:name,description stars:>25` → **total = 1**. La
medición era correcta y la conclusión ("la oferta abierta es un repo") era **falsa**: hay cinco
herramientas permisivas de valoración de almacenamiento, y ninguna se llama así.

**Regla operativa para los próximos pases.** Antes de declarar un gap en una categoría donde cabe
esperar investigación aplicada —fiabilidad, protección, valoración regulada, conformidad de norma—
barrer por `org:` los institutos y laboratorios que ya aparecen en la KB: `epri-dev`,
`GridProtectionAlliance`, `sandialabs`, `pnnl`, `argonne-citadel`, `lbl-srg`, `NatLabRockies`,
`entsoe`, `statnett`, `alliander-opensource`, `equinor`. Un gap declarado sin ese barrido no está
medido.

## T48 — El lado del **activo de campo** está vacío, y es exactamente donde está el presupuesto

Nueve pases midieron huecos en mercados, medición, cumplimiento y modelado de red — el lado del
**sistema**. Ninguno buscó el lado del **activo**: lo que una utility compra primero. Este pase lo
midió con ocho consultas y encontró cuatro categorías vacías:

| Categoría | Mejor oferta abierta real | Veredicto |
|-----------|--------------------------|-----------|
| Riesgo de incendio / PSPS | **nada del sector** en tres ángulos de consulta distintos | ❌ cero |
| Salud de transformador (DGA) | `engineers-tools/xDGA` **MIT, 18 ★, push 2022-06-28** | ❌ sin base viva |
| Capacidad de alojamiento de DER | `PauloRadatz/HostingCapacity_OpenDSS` **MIT, 7 ★, 2022-11-30** | ❌ sin base viva |
| Inspección de línea por visión | YOLO académicos **MIT de 34-37 ★** (2024-2025); el de **145 ★ sin licencia** | ❌ sin base viva |
| Fuga de metano | `STARCOP` **GPL-3.0** 74 ★; `MethaneMapper` **sin licencia** 85 ★ | 🟡 existe, no permisivo |
| Inversor grid-forming | `GridFormingConverters` **sin licencia** 140 ★ (2020); modelos WECC de `pnnl` **sin licencia** | 🟡 existe, no permisivo |

**La asimetría es la tesis.** El open source energético es fuerte donde el publicador es un
**operador de red o un instituto** —que modela el sistema— y vacío donde el dueño del problema es
**el propietario del activo**, que no publica porque el modelo *es* su ventaja operativa. Eso explica
la forma del mapa mejor que cualquier argumento de madurez: no es que la categoría sea joven, es que
**nadie tiene incentivo para publicarla**.

**Consecuencia comercial directa, y es buena noticia:** estas categorías tienen presupuesto aprobado
y **no** tienen acelerador que un competidor pueda forkear. Son desarrollo a medida sobre bases
genéricas (`OpenDSS`/`pandapower` para red, visión por computador estándar para inspección) y hay que
presupuestarlas como desarrollo. Lo que **no** se puede hacer es prometer un acelerador reutilizable,
ni estimarlas como integración.

**Y una advertencia de medición que se repitió en serie:** **cuatro de las cinco consultas chocan
con herramientas de desarrollador que ocupan el término.** `wildfire` es un plugin de Vim de 605 ★ y
uno de Neovim de 270 ★; `hosting capacity` es un script de Oracle Cloud de 1.309 ★; `grid forming`
es un framework JavaScript de 492 ★; `SMR`/`nuclear` es un reproductor de música de 18.970 ★ y tres
mods de Minecraft; `PSPS` devuelve 32.500 resultados de listas genéricas. Es T35 en su forma más
peligrosa: **no devuelven cero, devuelven miles de resultados equivocados** — que es lo que hace que
el error pase inadvertido.

## T49 — El techo de verificación ya no es sólo técnico: los registros regulatorios primarios no resuelven

T12 estableció que el techo de verificación es la red, y T44 lo afinó al endpoint. Este pase lo
extiende al **dominio regulatorio**, que es el que más importa cuando el entregable es un expediente:

| Dominio | Resultado desde este entorno | Qué queda sin verificar |
|---------|------------------------------|-------------------------|
| `eur-lex.europa.eu` | **no resuelve** (séptimo pase consecutivo con fallo) | `COM(2026) 501`, fechas del AI Act, Reglamento (UE) 2026/1744 |
| `energy.ec.europa.eu` | **no resuelve** | Hoja de ruta de digitalización e IA en energía, acuerdo tripartito |
| `apec.org` | **no resuelve** | Declaración ministerial de energía de APEC 2026 |
| `huggingface.co` | no resuelve (sexto pase consecutivo) | Licencias de pesos de modelos |
| `raw.githubusercontent.com` | **200** | Licencias de repo: ✅ canal confirmado por décima vez |
| `search/repositories` (vía `gh api`) | **200** | Metadatos de repo: ✅ 56/56 resueltos este pase |

**La consecuencia práctica es una regla de redacción, no una queja de infraestructura:** esta KB
puede afirmar con primera mano **cualquier cosa sobre un repo** y **ninguna cosa sobre una norma**.
Toda fecha regulatoria de este documento es concordancia de fuentes secundarias. En un entregable de
cliente, las fechas de código se citan; las fechas de norma **se verifican en el registro oficial
antes de firmar**. La distinción tiene que viajar escrita, porque las dos parecen igual de duras en
una tabla.

## T50 — EMEA convirtió la regulación en un **contrato tripartito**, y ahí está el expediente facturable

T37 observó que las cuatro regiones convergieron en el mismo instrumento: **acceso condicional** a la
red. Este pase encuentra la forma contractual que EMEA le está dando, y es más específica y más
vendible que una obligación de cumplimiento.

La hoja de ruta europea prevé publicar en el **segundo semestre de 2026** un **acuerdo tripartito
modelo** entre **operador de datacenter + parte energética + autoridad pública** (fuente secundaria;
ver T49). Un contrato modelo con tres firmantes obliga a que **cada parte traiga un expediente
técnico**:

| Firmante | Lo que tiene que poder demostrar | Con qué se construye en esta KB |
|----------|----------------------------------|--------------------------------|
| Operador de datacenter | Perfil de carga, **flexibilidad comprometida y verificable**, plan de eficiencia | `vessim`, `dcgym`/`dchub`, `carbon-aware-sdk`, `FlexMeasures` |
| Parte energética (TSO/DSO/generador) | Estudio de conexión, impacto en red, escenarios | `pandapower`, `PyPSA`, `power-grid-model`, `plexos2duckdb` |
| Autoridad pública | Trazabilidad y auditoría de ambos expedientes | `openHistorian` + `openXDA` como registro, `opendsm` para M&V |

**Por qué esto es mejor negocio que "cumplimiento del AI Act":** el cumplimiento es un gasto que el
cliente intenta minimizar; un contrato de conexión es la **condición para que su datacenter exista**.
Y la flexibilidad que firme ahí tiene que ser **medida y verificada de forma continua**, no declarada
una vez — lo que convierte un proyecto de documentación en una plataforma operativa con mantenimiento
recurrente. Es la misma conversión que T18 identificó para la verificación del ahorro, aplicada al
mayor consumidor marginal de la década.

## T51 — El perfil de licencia también cambia con la **geografía de la institución que publica**, y favorece a Norteamérica

T9 estableció que el perfil de licencia cambia por **subsector**. Este pase añade un segundo eje, y
tiene consecuencia directa sobre qué se puede prometer en cada región:

| Origen | Quién publica | Licencia dominante | Qué permite en un entregable |
|--------|---------------|-------------------|------------------------------|
| **EMEA** | Operadores de red y TSOs (RTE, Alliander, Elia, Statnett) y la familia **LF Energy** | **MPL-2.0** de forma consistente | Integración sí; **marca blanca con motor modificado no** (copyleft por archivo) |
| **EMEA** | Consorcios académicos (`oemof`, `pypsa`, TU München) | **MIT** | Libre |
| **North America** | **EPRI** (59 repos), **Sandia** (30) | **BSD-3-Clause** | Libre, incluida marca blanca |
| **North America** | **Grid Protection Alliance** (66 repos) | **MIT** | Libre, incluida marca blanca |
| **North America** | **NatLabRockies** (ex-NREL) | BSD-3 **con cláusulas añadidas** | Condicionado: marca, no-endoso, y en `resstock` según **quién es el cliente** (T24) |
| **LATAM** | Instituciones de mercado (XM, Batu Energy) y académicos | **MIT** cuando hay licencia; **ausente** con frecuencia | Caso por caso (T20) |

**La lectura comercial, que invierte un supuesto de nueve pases de esta KB:** el stack abierto de la
energía *no* es predominantemente europeo y copyleft. Lo era en la muestra que esta KB había
construido. Con EPRI, GPA y Sandia catalogados, **la base institucional norteamericana es más
permisiva que la europea** — BSD-3 y MIT frente a MPL-2.0.

Para un cliente que quiere **producto propio** con motor modificado y sin obligación de publicar:
partir de `openHistorian`/`openXDA` (MIT), `StorageVET`/`DER-VET`/`snl-quest` (BSD-3) y
`DLMS-COSEM` (BSD-3) da mejores términos que la ruta LF Energy. La ruta europea sigue siendo la
correcta cuando lo que se necesita es **el modelo de red europeo** y su interoperabilidad
(CGMES, `pypowsybl`, `power-grid-model`), donde no hay equivalente norteamericano. **La elección de
base ya no es técnica ni regional por defecto: es una decisión de licencia, y hay que tomarla
explícitamente en la fase de propuesta.**

---
*Investigado 2026-11-20 en diez pases. Lo verificado de primera mano es, sin excepción, lo que vive
en GitHub; todo lo regulatorio y de mercado es secundario y está marcado como tal (ver T49).*

## T52 — Un 404 en `README.md` no es un repo vacío: AsciiDoc es el formato de la ingeniería industrial europea

El canal de verificación de esta KB sondea `raw.githubusercontent.com/{repo}/{branch}/README.md`. Es
barato y funciona —salvo en la familia de repos donde más importa. `statnett/Talk2PowerSystem`
devuelve **404 en cinco variantes** (`main/README.md`, `master/README.md`, `main/readme.md`,
`main/README.rst`, `main/docs/index.md`) y tiene documentación extensa: su README se llama
**`ReadMe.adoc`**.

**AsciiDoc es el formato habitual de documentación en ingeniería industrial europea** — Eclipse,
consorcios IEC, TSOs. Y es justamente la población de repos que esta KB más valora (origen EMEA,
autoría institucional, norma IEC). El sesgo es por tanto **sistemático y dirigido contra el material
de mayor valor**, no aleatorio.

**Regla operativa:** antes de concluir que un repo institucional europeo está indocumentado, probar
`ReadMe.adoc`, `README.adoc`, `README.asciidoc`. Y un 404 de README **nunca** justifica por sí solo
una conclusión sobre el contenido del repo: en este caso costó dos pases clasificar como "precedente"
lo que era una arquitectura de referencia con ontología y conector incluidos.

## T53 — La oferta europea de investigación vive en GitLab autoalojado, y GitHub indexa espejos que pierden la licencia

Hallazgo de primera mano, leído en el campo `description` de la propia API, no inferido:
`DTUWindEnergy/TopFarm2`, `OptiWindNet`, `WindEnergyToolbox` y `WindGym` **se describen como
"Mirror of https://gitlab.windenergy.dtu.dk/..."**. El repositorio canónico de la ingeniería eólica
europea está en un GitLab institucional; lo que GitHub indexa son réplicas.

Dos consecuencias, y la segunda es la que cuesta dinero:

1. **Toda medición de oferta que esta KB haya hecho con consultas de GitHub subestima a las
   instituciones europeas.** Varios de los "ceros" históricos de este KB pueden ser ceros de índice,
   no de oferta — el mismo error de categoría que T47 y el pase 10 ya corrigieron dos veces, ahora en
   su versión geográfica. No se sabe cuántos; se sabe que el sesgo existe y en qué dirección va.
2. **El espejo puede perder el archivo de licencia.** `PyWake` —85 ★, el modelo de estela más citado
   del clúster— **no tiene `LICENSE` en `main`, `master` ni `develop`** en GitHub. Antes de descartar
   una pieza europea como "no proponible por licencia", hay que ir al GitLab de origen: la licencia
   puede estar allí y el problema ser del espejo.

**Regla operativa:** para oferta de origen EMEA, GitHub es un índice incompleto. `gitlab.com`, los
GitLab institucionales (`gitlab.windenergy.dtu.dk`, `git.rwth-aachen.de`, los de Fraunhofer) y el
Eclipse Marketplace son fuentes de primer orden, no complementos.

## T54 — La licencia permisiva no estándar: un tercer estado entre "permisiva" y "sin licencia"

T46 estableció que `NOASSERTION` en un laboratorio nacional depende del laboratorio. Este pase añade
el caso que no es ni rescate ni descarte. `pnnl/neuromancer` (1399 ★) y `pnnl/ExaGO` reportan
`NOASSERTION`, y en crudo tienen la **licencia propia de Battelle Memorial Institute**: concede uso,
copia, modificación, fusión, publicación, distribución, sublicencia y venta, con retención de aviso y
cláusula de no-uso-del-nombre. Sustancialmente **es BSD-3**.

Pero **no es un identificador SPDX**. Y eso tiene tres efectos operativos concretos:

- **No pasa un escáner automático de licencias** (FOSSA, Black Duck, Snyk License): aparecerá como
  desconocida y bloqueará un *pipeline* de cumplimiento del cliente.
- **Requiere visto bueno legal explícito**, una vez, por texto — no por etiqueta.
- **No se debe anotar como "BSD-3" en un inventario.** Decir "BSD-3" es cómodo y es falso; lo correcto
  es "permisiva no estándar (Battelle), equivalente funcional a BSD-3, revisada en crudo el
  2026-11-20".

El mismo patrón aplica a `virtual_test_bed` por el otro extremo: **CC-BY-4.0 no es una licencia de
software**. De una licencia Creative Commons no se hereda permiso de software, aunque el contenido
sea técnicamente utilizable. Son modelos de reactor, no código, y conviene decirlo antes de meterlos
en un pipeline.

**Taxonomía de licencia que esta KB debería usar desde aquí:** (1) SPDX permisiva, (2) **permisiva no
estándar** (texto propio institucional — proponible con revisión legal), (3) copyleft, (4) licencia de
datos/documentación (CC), (5) no comercial (bloqueante), (6) sin archivo de licencia (no proponible).
Los pases anteriores colapsaban (1) y (2), y mezclaban (4) y (5) dentro de "rescatada".

## T31 — `NOASSERTION` no es un dato: es una pregunta sin responder, y la respuesta depende de la institución

El quinto pase estableció **T24**: "`NOASSERTION` en un laboratorio nacional no es un defecto de la
API: es el dato correcto". Era cierto en su muestra y **se ha estado generalizando mal**. Este pase
resolvió a mano cuatro repos `NOASSERTION` fuera de ese perfil (un TSO europeo, una universidad
australiana, un autor individual) y **tres de los cuatro tenían licencia OSI estándar**:

| Repo | API | Realidad | Causa del falso negativo |
|---|---|---|---|
| `Energinet-SimTools/IMTB` | `NOASSERTION` | **MPL-2.0** | MPL **reescrita en Markdown** (`# Mozilla Public License`, `### 1.1.`) |
| `UNSW-CEEM/NEMOSIS` | `NOASSERTION` | **GPL-3.0-or-later** | Cabecera GPL **indentada**, precedida del nombre del programa |
| `AlexanderHoogsteyn/ClariGrid` | `NOASSERTION` | **Apache-2.0** | Texto canónico íntegro; falso negativo sin causa aparente |
| `Energinet-SimTools/MTB` | `NOASSERTION` | **no-OSI, revocable** | Aquí sí era correcto (ver T33) |

**La regla correcta: `NOASSERTION` significa "el *matcher* de GitHub no reconoció el fichero", no
"no hay licencia".** En laboratorio nacional norteamericano suele resolverse en licencia propia (T24).
En TSO europeo y universidad, suele resolverse en **licencia OSI mal formateada**.

Lo que hace esto grave y no anecdótico es que **el coste del error es asimétrico en las dos
direcciones**:

- Descartar `NEMOSIS` (113 ★, la capa de acceso a datos del NEM) por "sin licencia" = **perder el
  acceso a una región entera** por un problema de indentación.
- Dar por permisivo el `MTB` de Energinet (83 ★) = **riesgo contractual** en el entregable.

Procedimiento obligatorio antes de concluir cualquier cosa sobre licencia: sondear `LICENSE`,
`LICENSE.md`, `LICENSE.txt`, `COPYING`, `LICENCE` contra las ramas `main` y `master`, y **leer las
primeras líneas**. Se añade a la lista de trampas de verificación de esta KB, junto con el `.adoc`
del pase 11, la rama por defecto del sexto y las cuatro licencias de `pypsa-eur`.

## T32 — El stack eléctrico australiano es copyleft en la capa de datos, y eso decide la arquitectura antes de escribir código

APAC pasó en este pase de ~2 a más de 30 repos, y el reparto de licencias **no es aleatorio: sigue la
capa**.

- **Copyleft (GPL-3.0): toda la capa de entrada de datos y de supuestos.** `NEMOSIS` (histórico),
  `NEMSEER` (pronósticos), `isp-workbook-parser` (IASR), `isp-trace-parser` (series), `ISPyPSA`
  (expansión de capacidad).
- **Permisivo (BSD-3 / MIT): toda la capa de modelo.** `nempy` (despacho), `NEMED` (emisiones),
  `DER_disturbance_analysis`, `nem-bidding-dashboard`, `market-control-room`.

El GPL cae justo donde **no se puede esquivar**: no existe producto analítico del NEM que no pase por
`NEMOSIS`. La consecuencia práctica no es que Australia esté cerrada, es que **la frontera de
licencia hay que dibujarla en el diagrama de arquitectura antes de la primera línea de código**:
servicio de datos GPL aislado (proceso o contenedor propio, interfaz de datos, sin enlazado) y lógica
propietaria del cliente al otro lado, embebiendo `nempy` y `NEMED` que sí lo permiten.

**Esto generaliza y es el valor del hallazgo:** T9 decía que "el perfil de licencia cambia por
subsector, no por tecnología". Australia añade un eje: **el perfil de licencia cambia por *capa de la
pila*.** La capa de ingesta tiende a copyleft (la escriben académicos y consorcios que quieren que
las mejoras vuelvan); la capa de modelo tiende a permisiva (la escriben para que se adopte). Vale la
pena comprobar si el patrón se repite en las otras tres regiones — sería una regla de selección
reutilizable, no una curiosidad australiana.

## T33 — En este sector existe la licencia **revocable**, y ningún verificador automático la detecta

[`Energinet-SimTools/MTB`](https://github.com/Energinet-SimTools/MTB) (83 ★, 24 forks, push
2026-11-19), el repo más estrellado del TSO danés, lleva un `LICENSE.md` que **no nombra ninguna
licencia**. Concede *"a worldwide, non-exclusive, non-payable right to use, modify and distribute the
MTB"* y a continuación:

> **"Energinet may withdraw or modify the right to use, modify and distribute."**
> **"All intellectual property rights, including copyright to the MTB remains at Energinet."**

Un permiso **revocable unilateralmente** no es open source bajo ninguna definición: no hay licencia
OSI que permita retirar el derecho ya concedido. Y la diferencia con "sin licencia" importa, porque
el riesgo es de otra naturaleza: no es que falte el permiso, es que **el permiso puede desaparecer
después de que el entregable esté en producción en el cliente**.

**Por qué ningún automatismo lo ve:** no hay cadena SPDX que *grepear*. No aparece `MIT`, ni
`Apache`, ni `GPL`, ni `MPL`. Un verificador de identificadores de licencia **no encuentra nada** y
clasifica el repo como "sin licencia" — que resulta ser la clasificación operativa correcta (T20,
"bloqueada, distinta de ausente") **por el motivo equivocado**, y por pura suerte. Si el mismo texto
hubiera incluido la palabra "MIT" en cualquier parte, el verificador lo habría aprobado.

La defensa es de procedimiento y no es automatizable: **cualquier repo institucional con muchas
estrellas y `NOASSERTION` se lee a mano antes de proponerlo.** Es poco trabajo (son pocos repos) y
cubre el caso de mayor impacto.

Uso legítimo del `MTB`, que lo tiene: como **especificación de los requisitos de prequalificación de
Energinet**. Un proyecto de cumplimiento de red en Dinamarca necesita saber qué comprueba el banco;
eso se lee sin incorporar el código. Lo que no se puede es empaquetarlo y vendérselo a un cliente.

## T34 — La capa agéntica de red no estaba ausente: estaba publicada en el vocabulario del motor, no del sector

Entre los pases 4 y 11, esta KB registró **siete u ocho veces** "cero agentes de operación de red", y
lo atribuyó a inmadurez del sector. Este pase encontró
[`powsybl/pypowsybl-mcp`](https://github.com/powsybl/pypowsybl-mcp) (MPL-2.0, `Copyright (c) 2026,
RTE`, arXiv 2607.14158), que expone load flow, seguridad N-1 y análisis de sensibilidad como
herramientas MCP.

**No era inmadurez: era vocabulario** — y es la cuarta confirmación consecutiva del mismo fallo
(pase 10: `StorageVET`; pase 11: `HELICS`; este pase: `Open-ISP` y `pypowsybl-mcp`). La capa agéntica
de red **no se publica como "grid agent"**: se publica *dentro de la organización del motor de red*,
por el equipo del operador, y se anuncia en un paper de posición en vez de en un README promocional.
Buscar "AI agent grid" nunca iba a encontrarla.

**La receta de búsqueda que esto deja, y que debería aplicarse a las demás industrias de esta
rotación:** no buscar la función (*"agente de X"*), buscar **el motor que la función necesita** y
mirar si su organización ha publicado una capa MCP o de herramientas encima. `powsybl` → `pypowsybl-mcp`.
`EnergyPlus` → `energyplus-mcp`. `OpenDSS` → `opendss-mcp-server`. `PyPSA` → `pypsa-mcp`. El patrón
es tan regular que **predice**: donde haya un motor de simulación con comunidad, buscar su servidor
MCP antes de declarar el gap.

Corolario sobre madurez, para no sobrevender: `pypowsybl-mcp` tiene **7 ★ y 2 forks**, transporte
HTTP (no stdio, el servidor debe estar ya corriendo) y **sesiones en memoria que se pierden al
reiniciar**. Es un cimiento institucional joven. Proponerlo honestamente significa decir que el
proyecto va a contribuir a él.

## T35 — En MCP energético la procedencia institucional pesa más que las estrellas

Medición completa de este pase, ocho servidores MCP energéticos de la cola larga, todos verificados
por API: **rango 0–4 ★, y sólo uno con forks > 0**. Licencias buenas (casi todo MIT/Apache-2.0),
actividad decente (cinco con push en 2026), **comunidad inexistente**.

Al lado: `pypowsybl-mcp` con 7 ★ es proponible, y `Power-Agent/PowerMCP` (MIT, **238 ★**, 67 forks)
es el centro real de la categoría. La variable que separa a los dos grupos no es la licencia ni la
actividad ni el número de estrellas en términos absolutos: es **si hay una institución detrás que
responda del código**.

Esto invierte, para esta categoría, la heurística habitual. Un repo de 7 ★ con un TSO detrás es mejor
apuesta que uno de 4 ★ sin nadie, aunque la diferencia de estrellas sea estrecha. Y liga con **T19**
("las estrellas de GitHub ya se compran en este sector"): cuando la métrica es manipulable y los
números son pequeños, **la procedencia es la señal de calidad más fiable que queda**.

Regla operativa: en MCP energético, **la cola larga es material de referencia y de copia de patrón,
nunca dependencia**. Para dependencia, exigir institución.

## T36 — El gap de LATAM dejó de ser de existencia y pasó a ser de licenciamiento

Durante varios pases, y en varias industrias de esta rotación, el hallazgo LATAM fue "cero repos de
origen regional". Este pase barrió los operadores de la región (CAMMESA, CENACE México, CENACE
Ecuador, Coordinador Eléctrico de Chile) y **encontró repos activos**: `cammesa-dashboard` (push
2026-11-20), `CENACE-CHALLENGE` (2026-11-17), `cenace-monitor` (2026-11-20), `cammesa-api` (MIT, pero
parado desde 2017).

**Tres de los cuatro no tienen licencia.** El muro se movió: **ya no es "no hay repos", es "los repos
están sin licencia"** (T20: bloqueada, distinta de ausente).

La diferencia es importante por dos razones:

1. **Es un diagnóstico distinto.** Un gap de existencia significa que el ecosistema no está; un gap
   de licenciamiento significa que **está y no se puede usar**. Lo segundo es un problema de práctica
   de la comunidad, no de capacidad técnica de la región.
2. **Es accionable a coste cero, y lo primero no lo era.** Son repos de autor individual. Un *issue*
   pidiendo que añadan una licencia es una contribución que cuesta minutos y que, si prospera,
   desbloquea la pieza. Es la primera vez en esta KB que un gap regional tiene una acción concreta
   asociada en vez de "seguir buscando".

El dato institucional LATAM sigue siendo escaso y vale recordarlo: el único usable de origen
institucional sigue siendo `equipoanaliticaxm/api_xm` (XM, Colombia). Y **Brasil sigue en cero**: el
mayor mercado de datacenter de la región no tiene presencia de código abierto de su operador (ONS)
tras doce pases — el gap de mayor valor potencial que queda en LATAM.

## T47 — La capa de medición es donde se concentran las licencias no-OSI, y la tracción engaña

Añadida en el decimotercer pase (2026-11-20). Generaliza T20 ("sin licencia" = bloqueada, distinta de
ausente) y T33 (existe la licencia revocable, indetectable por SPDX).

El pase 12 encontró **una** licencia revocable (Energinet `MTB`) y la registró como caso. El pase 13
barrió la capa de medición (`SunSpec`, `IEC 62056`, `SAREF`) y encontró que **no era un caso aislado
sino una familia con cuatro clases distintas**, todas informadas como `NOASSERTION` por la API:

| Clase | Ejemplo | ★ | Efecto en un entregable |
|-------|---------|---|------------------------|
| Permisiva **con tope de usuarios** | `UtilitechAS/amsreader-firmware` — *Fair Source License 0.9*, `Use Limitation: 5 users` | **471** | **Bloqueo duro.** Un tope de 5 usuarios no se resuelve con atribución |
| **No comercial** | `bolagnaise/PowerSync` — *PolyForm Noncommercial 1.0.0* | 96 | **Bloqueo total.** Un encargo es uso comercial por definición |
| **Revocable** (T33) | `Energinet-SimTools/MTB` | 83 | **Bloqueo de continuidad**, no de atribución |
| **Permisiva en sustancia, no OSI** | `universaldevices/oadr30` — *"Universal Devices Free/MIT License"* de redacción propia | 10 | **No bloquea**: requiere lectura legal, no descarte |

**La regla práctica, que es la parte nueva:** en esta capa **la tracción y la usabilidad legal están
descorreladas**, y es la única capa de esta KB donde eso ocurre de forma sistemática. Los sustitutos
limpios tienen **menos** estrellas que las piezas bloqueadas:

| Bloqueada | ★ | Sustituto limpio | ★ |
|-----------|---|------------------|---|
| `binsentsu/home-assistant-solaredge-modbus` (sin licencia) | 420 | `WillCodeForCats/solaredge-modbus-multi` (Apache-2.0) | 343 |
| `matthijskooijman/arduino-dsmr` (sin licencia, parado 2023) | 145 | `lvzon/dsmr-p1-parser` (Apache-2.0) | 60 |
| `UtilitechAS/amsreader-firmware` (Fair Source, 5 usuarios) | 471 | `pwitab/iec62056-21` (BSD-3) / `volkszaehler/mbmd` (BSD-3) | 89 / 281 |

**Consecuencia para el método de esta KB: en la capa de consumidor/*prosumer*, el filtro de licencia
va ANTES del filtro de popularidad.** En las capas de motor de red, entornos RL y laboratorio
nacional, ordenar por estrellas da una primera aproximación razonable. Aquí da sistemáticamente la
respuesta equivocada, porque el repo popular de esta capa nació como proyecto de aficionado con
licencia elegida para proteger al autor, no para habilitar reutilización comercial.

**Y la asimetría del coste, que explica por qué merece una entrada propia:** descartar una pieza
limpia por pereza cuesta una alternativa; meter `amsreader-firmware` en un diagrama de arquitectura y
descubrir el tope de 5 usuarios en la revisión legal del cliente cuesta **el rediseño de la capa de
adquisición a mitad de proyecto**.

## T48 — Un negativo nuevo no gana a un positivo verificado sólo por ser más reciente

Añadida en el decimotercer pase. Es una regla de **gobierno de la propia KB**, no una observación del
sector, y nace del error más caro que esta KB ha cometido y registrado (ver T45 derogada y T46).

**Lo que pasó:** un pase resolvió correctamente la licencia de `openleadr-rs` como doble MIT /
Apache-2.0 y lo escribió en una tabla titulada *"Licencias rescatadas leyendo el archivo crudo"*. Un
pase posterior volvió a medirla con una lista de sondas más corta, obtuvo 404 —correctamente, porque
`LICENSE` no existe con ese nombre en ese repo— y **escribió la conclusión contraria sin consultar el
registro propio**. El dato falso se propagó a tres archivos y sostuvo una receta entera que
recomendaba trabajo innecesario.

**La regla:**

> Antes de escribir un hallazgo **negativo** —"sin licencia", "cero repos", "no existe", "no hay
> implementación"— **buscar la entidad en la propia KB**. Si existe un registro positivo previo, el
> negativo nuevo **debe explicar la discrepancia**, no sobrescribirla.

**Por qué el sesgo correcto es asimétrico y no neutral.** Un positivo verificado es la salida de una
medición que **encontró algo**: alguien leyó un archivo y lo citó. Un negativo es la salida de una
medición que **no encontró nada**, y eso tiene dos causas posibles —no existe, o no se buscó bien— que
son indistinguibles desde dentro del resultado. Esta KB tiene **el registro acumulado de la segunda
causa**: `PRODIST`, `hydrogen` con paréntesis, `IEEE 1547`, `AMI`, `reservoir`, *forks* no indexados,
`NOASSERTION`, `master` frente a `main`, y ahora `LICENSE-MIT`. Nueve maneras documentadas de medir
cero sin que el cero sea real.

**Coste asimétrico, que es el argumento final:** un falso positivo mete un repo malo en una tabla y
se corrige en la siguiente revisión. Un falso negativo **borra una capacidad del catálogo y nadie la
vuelve a buscar, porque ya está "medida"** — el gap falso de OpenADR 3.0 sobrevivió dos pases por eso
exactamente, y lo que lo rompió no fue una búsqueda nueva sino **leer el registro propio**.

**Aplicación concreta para el próximo pase, en orden de coste creciente:**

1. `grep` de la entidad en los 8 archivos antes de escribir cualquier negativo. Coste: segundos.
2. Re-verificar los repos de **Rust** que esta KB o sus hermanas clasificaron "sin licencia" leyendo
   sólo `LICENSE`. Firma buscable: **`LICENSE` 404 en todas las ramas + repo vivo con tracción**.
3. Barrer los `NOASSERTION` pendientes leyendo el **manifiesto del gestor de paquetes** primero (T46).

## Decimocuarto pase (2026-11-21): "un repo, una licencia" es un supuesto, no un hecho — y el tamaño del archivo es el detector

**Titular del pase: tres repos de esta KB tienen una estructura de licencia que ningún instrumento
de SPDX único puede expresar, y uno de ellos cambia la arquitectura de un EMS de cliente.** La API
de GitHub, un badge de licencia y cualquier `grep` de identificador devuelven **un** valor por repo.
Este pase midió tres casos en los que **ese valor único es incompleto o engañoso**, y los tres se
detectaron por la misma señal barata: **el tamaño en bytes del archivo de licencia.**

### Las tres clases, con el caso medido

| Clase | Caso medido | Qué reporta el instrumento | Qué es en realidad |
|-------|-------------|----------------------------|--------------------|
| **1. Partida por componente** | `OpenEMS/openems` | `AGPL-3.0` (un solo valor) | **EPL-2.0** en Edge y Backend, **AGPL-3.0** sólo en la UI. Dos archivos: `LICENSE-EPL-2.0` (14.474 B) y `LICENSE-AGPL-3.0` (35.184 B) |
| **2. Obra colectiva con lista de materiales** | `openremote/core` | `AGPL-3.0` (correcto) | AGPL-3.0 **+ 2.697 líneas de inventario de licencias de dependencias**. `grep LESSER` → **35** aciertos, `grep "GNU GENERAL PUBLIC"` → **30**: un detector naíf la etiqueta LGPL o GPL |
| **3. Concesión en forma de "notice" corto** | `vodikus/ha_tarifas_energia_brasil` | `NOASSERTION` | **GPL-3.0-or-later válida**, expresada como el aviso corto de 715 B en vez del texto verbatim. La API no la reconoce porque **no es el texto canónico** |

A éstas se suma la clase que trajo el pase de automotive de la KB hermana —**concesión sólo en el
manifiesto** (`Apache-2.0` en `package.json`, sin ningún `LICENSE`)— con lo que van **cuatro formas
distintas en que la licencia real de un repo no coincide con el identificador que se publica.**

### El detector, y es de coste cero

**El tamaño del archivo de licencia es un discriminador de clase.** Medido repetidamente en este
pase y en los anteriores:

| Bytes | Lo que suele ser | Acción |
|-------|------------------|--------|
| **~1.000–1.100 B** | MIT o BSD-3 verbatim | Leer las 3 primeras líneas y listo |
| **~700 B** | **Aviso corto de GPL/LGPL**, no el texto completo | ⚠️ Leer entero: concesión válida que la API suele marcar `NOASSERTION` |
| **11.357 B** | Apache-2.0 verbatim | Constante delatora; aparece idéntica en repos sin relación |
| **14.474 B** | **EPL-2.0 verbatim** | Nuevo en este pase |
| **~35.000 B** | GPL-3.0 o **AGPL-3.0** verbatim | Distinguir con `grep -c affero` |
| **> 50.000 B** | **No es una licencia: es una lista de materiales** | Leer la cabecera para la concesión propia, y tratar el resto como inventario de dependencias |

> **Regla operativa nueva (T55), para toda la flota de KBs:**
> **Antes de escribir la licencia de un repo, mirar cuántos archivos de licencia tiene y cuánto pesan.**
> Un `LICENSE` de 1 KB y un `LICENSE` de 170 KB no son el mismo tipo de afirmación. Si hay **más de
> un** archivo `LICENSE-*`, **la licencia del repo no es un valor único** y hay que leer la sección
> *License* del `README` para saber **qué componente lleva cuál**.
> Corolario, que es el que duele: **el `LICENSE` 404 en todas las ramas no significa "sin licencia"**
> —regla que esta KB ya tenía— y aquí se refina: en `OpenEMS` el 404 ocurría porque **había dos
> archivos, ninguno llamado `LICENSE`.**

### Por qué esta clase de defecto es la más cara de todas

Las demás trampas de licencia de esta KB producen **falsos negativos**: un repo utilizable queda
fuera del catálogo. Ésta produce **las dos** a la vez y en la dirección peor:

- `OpenEMS` etiquetado `AGPL-3.0` **descartó de facto la plataforma EMS más desplegada de EMEA**
  (1.634 ★, utilities europeas) para cualquier producto propietario. Coste: una capability borrada.
- Si en cambio se hubiera creído la Receta 35 (`EPL-2.0` a secas), un equipo habría puesto la **UI
  AGPL** en un SaaS multi-tenant **sin ofrecer el código fuente**. Coste: un incumplimiento real.

**El mismo dato mal resumido produce o una oportunidad perdida o una infracción, según en qué
dirección se equivoque.** Por eso la licencia por componente se escribe por componente, con el byte-read
de cada archivo, y nunca como un identificador suelto en una celda.

## Los ceros re-medidos con consultas CORTAS: dos se rompen, uno se confirma

Aplicada la lección transferida del pase de automotive de la KB hermana —**`search/repositories`
indexa sólo nombre, descripción y topics, y hace AND de todos los términos, así que una frase larga
devuelve un cero literal**— se re-ejecutaron los ceros registrados de esta KB con consultas de una o
dos palabras. El resultado reproduce exactamente el patrón de la KB hermana.

| Cero registrado | Consulta corta | Resultado | Veredicto |
|-----------------|----------------|-----------|-----------|
| *"Optimización de BESS: **un** repo abierto con >25 ★ en toda la categoría. Gap de oferta, no de búsqueda"* | `bess stars:>25` / `topic:battery-energy-storage` | **3** repos >25 ★ utilizables, no uno | ❌ **era gap de búsqueda en parte** |
| *"Cumplimiento NERC CIP: **cero** herramientas del sector frente al plazo de diciembre de 2026"* | `topic:nerc-cip` | **21 repos**, ~8 energéticos MIT/Apache | ❌ **falso**; ver la forma del cero abajo |
| *"MDM / meter-to-cash: el mejor repo tiene 7 ★ y dos años sin push"* | `meter-to-cash` | 21 repos, **todos 0-1 ★ y sin licencia** | ✅ **confirmado, y ahora afirmable** |
| *"`gridfm-graphkit` no publica checkpoint preentrenado"* | lectura directa del `README` | Confirmado: todo `--model_path` es un artefacto **local de MLflow** | ✅ **confirmado por segunda vez** |
| *"CERO repos de origen LATAM en este barrido"* | `aneel` / `cammesa` / `cenace` | **Una capa entera** de acceso al dato del regulador | ❌ **falso**; ver `intel/market.md` |

**Tres de cinco ceros de esta KB eran artefactos del instrumento.** Es la misma proporción que midió
el pase de automotive, y confirma que el defecto **no era local a esa KB**: es una propiedad del
canal de búsqueda que afecta a toda la flota.

### La forma del cero de NERC CIP, que es lo que hay que decirle al cliente

El cero era falso, pero **la conclusión comercial apenas cambia**, y decirlo con precisión es más
valioso que el cero:

- `topic:nerc-cip` devuelve **21 repos**. Los energéticos relevantes van de **0 a 23 ★**.
- El de más tracción, [`ynotbhatc/rego_policy_libraries`](https://github.com/ynotbhatc/rego_policy_libraries)
  (**Apache-2.0** byte-read 11.357 B, 23 ★ / 2 forks / **17 issues abiertos**, push 2026-11-20), no
  es específico de energía: es una librería de **política de cumplimiento ejecutable en OPA Rego**
  (CIS Benchmarks, DISA STIGs, NIST) que **incluye** NERC.
- Los específicamente NERC CIP son **plantillas y checklists**, no herramientas: `nerc-cip-checklists`
  (MIT, 0 ★), `nerc-cip-readiness-evidence-bundle` (MIT, 1 ★), `energy-compliance-starter-kit`
  (MIT, 1 ★).

> **La frase correcta para una propuesta, que ya no es "no hay nada":** *"frente al plazo de
> diciembre de 2026 existen al menos ocho proyectos abiertos de cumplimiento NERC CIP con licencia
> permisiva; ninguno pasa de 23 estrellas y los específicos del estándar son plantillas, no
> herramientas ejecutables. **Hay material de arranque y no hay producto.**"*

Eso es exactamente la forma de cero que esta KB ya midió en agentes de operación de red: **el código
existe, la comunidad no.** Y es, otra vez, un hueco de producto —no de búsqueda— pero ahora
**cuantificado** en lugar de afirmado.

## T55 — La licencia de un repo no es necesariamente un valor único, y el tamaño del archivo lo delata

**Enunciado.** Un repositorio puede llevar **más de una licencia a la vez**, repartidas por
componente, y todo instrumento que reporte un único identificador SPDX (la API de GitHub, un badge,
cualquier `grep`) **es incapaz de expresarlo**. Antes de escribir la licencia de un repo en una
celda, comprobar **cuántos** archivos de licencia tiene y **cuánto pesan**.

**Procedimiento, en orden de coste creciente:**

1. `gh api search/repositories -f q="repo:OWNER/NAME"` → identificador de partida, **nunca la
   respuesta final** si el repo es una plataforma.
2. Listar archivos de licencia probando también los **nombres compuestos**: `LICENSE-EPL-2.0`,
   `LICENSE-AGPL-3.0`, `LICENSE-MIT`, `LICENSE-APACHE`. **Dos o más aciertos ⇒ licencia partida.**
3. Mirar el **tamaño**: ~1 KB = MIT/BSD; ~700 B = aviso corto de (L)GPL; 11.357 B = Apache-2.0;
   14.474 B = EPL-2.0; ~35 KB = GPL-3/AGPL-3; **> 50 KB = lista de materiales, no licencia.**
4. Si hay licencia partida, **leer la sección *License* del `README`**: es el único sitio donde se
   dice **qué componente lleva cuál**. Escribirlo por componente.
5. `grep -c affero` para separar AGPL-3.0 de GPL-3.0, y **buscar `LESSER` antes que
   `GNU GENERAL PUBLIC`** (el texto de LGPL contiene literalmente la cadena de GPL).

> ⚠️ **Defecto de numeración medido en este pase, y conviene arreglarlo antes de que crezca.**
> Contados los encabezados `## T<n>` de los ocho archivos: la serie llega a **T54** y **nueve
> identificadores están usados DOS VECES** para reglas distintas — **T31, T32, T33, T34, T35, T36,
> T46, T47 y T48**. Por ejemplo **T48** es a la vez *"el lado del activo de campo está vacío"* y
> *"un negativo nuevo no gana a un positivo verificado"*; **T47** es a la vez *"buscar la institución,
> no la cosa"* y *"la capa de medición concentra las licencias no-OSI"*.
>
> **Consecuencia inmediata: toda referencia cruzada a T31-T36 o T46-T48 en esta KB es ambigua hoy** — incluida la que aparece en las notas de rotación. Hasta reconciliar la serie, **citar
> siempre el número JUNTO AL ENUNCIADO abreviado**, nunca el número solo. Esta regla toma **T55**,
> el primer identificador libre, para no empeorar la colisión.
>
> *Tarea concreta y barata para un próximo pase:* renumerar los nueve duplicados por orden de
> aparición y dejar un índice de reglas al principio de `intel/trends.md`. Es mecánico y evita que la
> serie se vuelva inservible como sistema de referencia.

**Casos de referencia:** `OpenEMS/openems` (EPL-2.0 Edge+Backend / AGPL-3.0 UI),
`openremote/core` (AGPL-3.0 + 2.697 líneas de inventario de dependencias),
`vodikus/ha_tarifas_energia_brasil` (`NOASSERTION` que es GPL-3.0-or-later en 715 B).

**Coste de ignorarla, y es bidireccional —** la razón por la que esta regla es distinta de T46/T47:
resumir mal una licencia partida produce **o una capability borrada del catálogo** (`OpenEMS`
descartado como AGPL cuando su núcleo es EPL-2.0) **o un incumplimiento real** (la UI AGPL puesta en
un SaaS multi-tenant creyendo que todo el repo era EPL-2.0). Las demás trampas de licencia de esta
KB sólo producían falsos negativos; **ésta puede producir los dos, y el segundo llega con el cliente
dentro.**

---

## Pase 15 (2026-11-21) — la coordinación red–centro de datos se consolida como el frente de investigación, y el mercado publica su política de riesgo

### 1. El dato que ordena toda la conversación agéntica del sector

> **23% de los operadores de red de Asia Oriental usa IA en operación en tiempo real; 54% la usa en
> planificación del desarrollo de red.** La IEA atribuye la diferencia a **preocupaciones de
> fiabilidad**: el rechazo al tiempo real es **deliberado**, no un retraso de madurez.
> (IEA, *Energy and AI in East Asia*, abril 2026. ⚠️ Por snippet: `iea.blob.core.windows.net` **no
> resuelve** desde este entorno y el informe **sigue sin leerse byte a byte**.)

Es la **tercera confirmación independiente**, y la primera cuantificada, de la restricción de
arquitectura que esta KB impone desde sus primeras recetas:

| Canal | Pase | Qué dijo |
|-------|------|----------|
| Criterio propio de la KB | 1–13 | El agente es apoyo a la decisión; nunca controlador del lazo |
| **Regulador** (NERC, NA) | 14 | La IA en el sistema eléctrico debe ser apoyo a la decisión, no controlador autónomo |
| **Mercado** (IEA, Asia Oriental) + guía de práctica NA | **15** | **23% vs 54%**, por fiabilidad; y los agentes **sin credencial ni ruta de red** en la zona de control |

**Deja de ser una opinión de arquitectura y pasa a ser una descripción del mercado.** Para una
propuesta: el límite no se discute, se **cotiza** — y lo que se vende es la capa de planificación,
estudio y expediente, que es donde está el 54%.

### 2. El frente de investigación se desplazó a la coordinación red ↔ centro de datos

Nueve papers localizados en un solo barrido, todos de 2026, convergen en un problema que hace un año
no existía como categoría: **el centro de datos como recurso de red, no sólo como carga**.

> ⚠️ **Estado de verificación de estas nueve referencias: listadas por buscador, NO verificadas.**
> `arxiv.org` **está rechazado por la política de egreso de esta sesión** (403 del proxy, clase "host
> no permitido"), así que **ni un solo identificador de abajo pudo comprobarse** ni se leyó ningún
> resumen. Los títulos y los IDs vienen del listado del buscador. **Antes de citar cualquiera en
> material de cliente hay que resolverlo en un entorno con acceso a arXiv** — es el open item 15-R3.
> Se registran porque la *convergencia temática* de nueve resultados independientes es señal útil
> aunque cada identificador esté sin confirmar; no se registran como bibliografía.

| Referencia | Qué aporta |
|------------|------------|
| [arXiv 2607.28822](https://arxiv.org/pdf/2607.28822) | *Agentic AI for Power Systems*: estrategias para **identificar y cerrar brechas de capacidad** — el marco de madurez que faltaba |
| [arXiv 2609.40272](https://arxiv.org/pdf/2609.40272) | Agentes **basados en skills** para estudios de sistemas de potencia |
| [arXiv 2610.05502](https://arxiv.org/pdf/2610.05502) | Liberar capacidad de **interconexión** mediante flexibilidad **coordinada** red + centro de datos |
| [arXiv 2609.38020](https://arxiv.org/pdf/2609.38020) | Flexibilidad de demanda por **desplazamiento temporal de cargas batch** |
| [arXiv 2611.00462](https://arxiv.org/pdf/2611.00462) | **Localización y profundidad de recorte** como límites reales del margen de red disponible (nov-2026) |
| [arXiv 2609.03030](https://arxiv.org/pdf/2609.03030) | Capacidad de alojamiento con **voltage ride-through** del centro de datos |
| [arXiv 2610.09060](https://arxiv.org/pdf/2610.09060) | Revisión de desafíos de potencia y soluciones coordinadas |
| [arXiv 2609.11649](https://arxiv.org/pdf/2609.11649) | *From Grid to Chip*: arquitectura de potencia, estabilidad y flexibilidad |
| [arXiv 2606.09617](https://arxiv.org/pdf/2606.09617) | Compromisos para la transición energética **europea** y el net-zero |

**Lectura comercial:** la investigación ya trata la flexibilidad del centro de datos como
**producto**, y ENTSO-E (8-may-2026) publicó **quién puede venderlo**: los **hiperescala** están en
posición de prestar flexibilidad, los de **colocation** están **limitados por el control del
inquilino**. Ese límite es contractual y de software de coordinación, **no físico** — es un segmento
desatendido con causa nombrada.

### 3. Trampas de licencia: dos clases nuevas, y las dos nacen de leer mal un archivo que sí estaba

> **T56 — el incipit de MIT no identifica una licencia.** `Zara-Toorox/Solar-Forecast-ML` (**318 ★**)
> titula `PROPRIETARY AND NON-COMMERCIAL LICENSE` y **a continuación reproduce palabra por palabra**
> la frase de concesión de MIT. Un detector que busque esa frase lo marca MIT. Discriminadores de
> coste cero, en orden: **(1) primera línea no vacía; (2) tamaño** — MIT real mide ~1,05–1,09 kB, el
> impostor medía **2.646 B**.
>
> **T57 — cláusula de prohibición de entrenamiento de IA.** El mismo archivo prohíbe usar el código
> para **entrenar o afinar LLM** o sistemas de generación de código sin permiso escrito. Afecta al
> **uso interno de un estudio de IA**, no sólo a la redistribución, y **ningún campo SPDX la
> expresa**. Clase nueva, y previsiblemente creciente.
>
> **T59 — el EUPL enumera las licencias con las que es compatible.** `HVDC-Wise_lib` fue clasificado
> **LGPL** porque la cláusula de compatibilidad del EUPL nombra GPL, LGPL, AGPL y MPL. Es la misma
> familia que el defecto LGPL/GPL de la KB de automotive, pero el EUPL nombra **cinco o más**
> licencias ajenas.

**Y la quinta clase no-OSI de la capa de medición:** **Business Source License 1.1**
(`u9n/dlms-cosem`, 124 ★), detectada **sólo** por T46 (leer el manifiesto primero). Es la más
peligrosa de las cinco porque **se confunde con open source** y porque su conversión diferida hace
que "¿puedo usarlo?" tenga **respuestas distintas hoy y en cuatro años**. Las otras cuatro, del pase
13: fair-source con tope de usuarios, PolyForm no comercial, revocable, permisiva-bespoke no-OSI.

### 4. Lo que este pase aprende sobre su propio método

> **T58 — un inventario no es una cobertura.** 465 direcciones ya registradas no impidieron que **18
> consultas cortas** devolvieran **76 repos genuinamente nuevos**. El tamaño del inventario mide
> **esfuerzo acumulado**, no fracción del dominio cubierta. Y la proporción de nuevos **subió con el
> lote** (17 → 25 → 34) al pasar de términos descriptivos a **nombres de protocolo y de ontología**:
> **el vocabulario de la consulta pesa más que su número.** Toda KB de esta flota que informe un
> "techo de descubrimiento" debe re-sondearlo con **una palabra sobre un nombre propio** antes de
> creérselo.

**Instrumento:** `iea.blob.core.windows.net` se añade a los hosts primarios que **no resuelven**
desde este entorno. Y `gh api repos/<owner>/<repo>` **está denegado por el alcance de la sesión**
mientras `search/repositories` y `raw.githubusercontent.com` funcionan: **la rama por defecto no se
puede consultar**, hay que iterar `main`/`master`/`develop` a ciegas, y un `NO ARTEFACT` obtenido
por esa vía es **un fallo de permiso disfrazado de hallazgo**.
