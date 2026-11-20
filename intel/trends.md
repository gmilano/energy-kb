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

---
*Investigado 2026-11-20 en ocho pases. Lo verificado de primera mano es, sin excepción, lo que vive
en GitHub; todo lo regulatorio y de mercado es secundario y está marcado como tal.*
