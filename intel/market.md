---
industry: energy
region: Global
updated: 2026-11-20
---

# 🗺️ Mapa de mercado — Energy

> Key players, market map y oportunidades **por región**.
> Investigado 2026-11-20. Las cifras de mercado provienen de consultoras y prensa sectorial:
> se citan con su fuente porque **no concuerdan entre sí** (ver advertencia abajo).

## La tesis central de 2026: la red es el cuello de botella de la IA

El driver dominante no es "IA aplicada a energía" sino lo inverso: **la demanda de los datacenters
de IA está reconfigurando la planificación eléctrica**, y eso abre el presupuesto.

- **Deloitte**: la demanda de datacenters podría llegar a **176 GW hacia 2035**, ~5× el nivel de 2024.
- **Gartner**: el consumo eléctrico de datacenters crece **~26-27 % en 2026**, hasta **132 GW**
  (desde 104 GW en 2025).
- **BofA** (vía Utility Dive): la demanda de datacenters **excede en más de 100 GW** las adiciones
  de capacidad ya planificadas por las utilities hasta 2030.
- **IBM**: un datacenter se construye en **1–2 años**; una ampliación de red tarda **5–10 años**.
  Ese desfase *es* la oportunidad de consultoría.
- **National Grid Partners** (encuesta 2026): la **confiabilidad de red desplazó al net zero** como
  principal preocupación del sector, y **78 %** de los líderes de innovación de utilities en EE.UU.
  ya usan IA para gestionar la demanda creciente.
- **American Action Forum**: la capacidad de gas natural planificada subió de **11,1 % (2024) a
  18,1 % (2026)** del mix — la respuesta inmediata no es renovable.

⚠️ **Advertencia sobre tamaño de mercado**: las estimaciones de "AI in energy" para 2026 van de
**USD 7,86 B** a **USD 12,53 B** según la consultora — un spread de ~1,6×. Un pase anterior de esta
KB registró además "Agentic AI in Energy USD 656,6 M (2025) → 14,9 B (2035), CAGR 36,65 %". **No
usar estas cifras como dato duro en una propuesta**: citar la *adopción* (el 78 % de utilities, los
GW de cola de interconexión), que es verificable, en lugar del tamaño de mercado, que no lo es.

## Players globales

| Empresa | Tipo | Fortaleza | Debilidad |
|---------|------|-----------|-----------|
| Siemens / Siemens Energy | Incumbente industrial (EMEA) | Grid software + hardware de subestación integrados; presencia en todos los TSO europeos | Stack propietario; ciclos de venta y de release lentos |
| Schneider Electric | Incumbente industrial (EMEA) | EcoStruxure como capa DERMS/EMS; fuerte en edificios y microgrids | Lock-in; la capa de IA llega como add-on, no como arquitectura |
| ABB | Incumbente industrial (EMEA) | Automatización de subestación y electrificación industrial | Débil en software de datos/IA frente a nativos digitales |
| GE Vernova | Incumbente (North America) | GridOS para ADMS/DERMS; relación directa con ISOs/RTOs | Integración costosa; dependiente de proyectos plurianuales |
| AspenTech / Emerson | Software industrial (North America) | Optimización de activos y operaciones | Foco en oil & gas más que en red eléctrica |
| C3.ai | Software AI vertical (North America) | Casos de referencia en utilities; despliegues grandes | Modelo cerrado y caro; dependencia de un solo proveedor |
| Palantir | Plataforma de datos (North America) | Integración de datos operativos heterogéneos | Costo y percepción política; no es software de dominio eléctrico |
| RTE / Alliander / Elia | TSO/DSO que **publican open source** (EMEA) | Grid2Op, powsybl, power-grid-model, openSTEF: código de producción auditado | Construido para su propia regulación; adaptar a otra jurisdicción es trabajo real |
| Hitachi Energy | Incumbente (APAC/EMEA) | Lídera HVDC y equipamiento de red | Software como complemento del hardware |
| Enel / Iberdrola | Utility global con brazo digital (EMEA/LATAM) | Operan en Europa **y** LATAM: puente natural de un engagement regional | Prioridades de TI centralizadas en matriz europea |

**Lectura para Globant**: los incumbentes venden plataforma cerrada; los TSO europeos regalan el
núcleo técnico en MPL-2.0. El espacio defendible es **la integración y la capa agéntica sobre ese
núcleo abierto**, no competir con GridOS.

## Opportunities by region

### North America

**Contexto regulatorio (verificado)**: el **18 de junio de 2026** FERC emitió *show-cause orders* a
seis operadores de red — **PJM, MISO, SPP, CAISO, ISO-NE y NYISO** — dándoles **60 días** para
defender o reformar sus marcos de interconexión de cargas grandes. **No se creó una regla nacional
única**: cada RTO/ISO mantiene su propio marco (ERCOT incluido). Reportes indican que los
datacenters pagarían el costo íntegro de las mejoras de red atribuibles a su interconexión.

- **Oportunidad 1 — "Large-load interconnection studies as a service"**: seis marcos regulatorios
  divergiendo a la vez es demanda de consultoría pura. Automatizar estudios de interconexión
  (load flow + escenarios + documentación regulatoria) con `pandapower`/`PyPSA` + `PowerMCP`.
- **Oportunidad 2 — Flexibilidad de carga de datacenters**: un estudio comisionado por Duke indica
  que cargas flexibles podrían evitar decenas de miles de millones en plantas nuevas. `vessim`
  simula exactamente esto (carbono + batería + PV on-site de datacenter).
- **Oportunidad 3 — Agentes de sistemas de potencia sobre base nacional**: `Power-Agent` (Harvard
  SEAS) y `EnergyPlus-MCP` (LBNL) son MIT/BSD y de origen estadounidense: hablan el idioma
  regulatorio y de laboratorio del cliente norteamericano.
- **Riesgo**: cumplimiento **NERC CIP** para cualquier cosa que toque el bulk electric system. Una
  afirmación que circula en blogs —que FERC exigiría modelos de IA "100 % transparentes"— **no pudo
  verificarse**: no citarla.


**Actualización del segundo pase (2026-11-20)** — fuentes secundarias (snippets de prensa; el fetch
directo de páginas falla en este entorno, ver nota de método al pie):

- **Referencia de producción que se puede citar**: **CAISO**, con **OATI**, tiene una arquitectura
  multi-agente ("Genie") **en entorno de producción** para **gestión de interrupciones (outage
  management)**, con **humano en el bucle**. La misma fuente describe la estrategia de CAISO en tres
  niveles: **Embed → Specialize → Customize**. Fecha aproximada: **agosto de 2026**. Es el caso de
  North America más cercano a "agentes en operación real de red", y el patrón que replica —humano
  validando la acción crítica— coincide con la regla de arquitectura de `compose/patterns.md`.
- **El expediente FERC siguió moviéndose**: hay cobertura del **10 de noviembre de 2026** sobre un
  "fast track de 60 días" para la conexión de datacenters de IA, continuación de las *show-cause
  orders* del 18 de junio. Además, FERC habría instruido a **PJM** a crear opciones de servicio de
  transmisión para **cargas co-localizadas que puedan limitar su retiro de energía de la red** — eso
  es exactamente el producto de flexibilidad de la Oportunidad 2, pero ahora con forma tarifaria.
- **Riesgo político nuevo, y es el que puede frenar un proyecto**: un informe de la **Electricity Law
  Initiative de Harvard** sostiene que los usuarios residenciales están **subsidiando** el costo de
  energía de los datacenters, y pide más supervisión de los contratos utility-datacenter. En el
  Congreso, el **Bipartisan American Affordability and Jobs Act of 2026** incluiría protecciones
  obligatorias al ratepayer; se reporta que FERC **no puede imponerlas** con la ley actual.
- **Lectura para una propuesta**: el discurso "aceleramos tu interconexión" ya tiene contrapeso
  político. El encuadre que resiste es **"demostramos que la carga no la pagan los hogares"**:
  trazabilidad de costo, atribución de refuerzos de red y evidencia auditable. Eso es trabajo de
  datos, y es facturable.


#### Actualización del tercer pase (2026-11-20)

- **El regulador federal se movió y creó trabajo facturable.** FERC emitió en **junio de 2026** un
  conjunto de órdenes dirigidas a los operadores regionales (PJM, ERCOT, SPP, MISO y otros) sobre
  interconexión de **cargas grandes**, en el expediente **RM26-4-000**. Las fuentes secundarias
  discrepan sobre si fijó reglas nuevas o exigió a cada operador explicar su plan: lo segundo es lo
  más repetido. Efecto práctico igual en ambos casos: **cada RTO tiene que producir y defender una
  metodología de estudio**, y eso es análisis, datos y documentación.
- **Precedente concreto de agentes en ese hueco**: AWS y **Duke Energy** presentaron *Agentic Grid
  Planning*, donde los agentes reducen la preparación de datos de los estudios de interconexión de
  **semanas a horas**, con el ingeniero tomando toda decisión final. Es exactamente la Receta 1 de
  esta KB, ya validada por un tercero — se puede citar como precedente, no como capacidad propia.
- **GE Vernova lanzó GridOS for Transmission (junio 2026)**: el espacio tiene producto propietario
  consolidándose. Competir de frente es caro; integrarse o complementar es más realista.
- **Señal de demanda**: se reporta que **78 % de las utilities de EE. UU.** despliegan al menos una
  aplicación de IA para gestionar la demanda de interconexión de datacenters.
- **Riesgo legislativo a vigilar**: el proyecto **DATA Act** crearía la figura de *consumer-regulated
  electric utility*, eximiendo de buena parte de la Federal Power Act a instalaciones totalmente
  desconectadas de la red. Es **propuesta, no ley**. Si avanzara, abre un mercado de diseño de
  sistemas aislados; no conviene presupuestar sobre ello todavía.

#### Actualización del cuarto pase (2026-11-20)

**El vacío regulatorio es, literalmente, el producto.** Un análisis jurídico de septiembre de 2026
(Foley Hoag) sostiene que la **Arizona Corporation Commission es la única comisión estatal** que ha
abierto un examen formal del despliegue de IA en el sector energético, y describe el resultado como
un *"regulatory vacuum"* para la IA operativa en la industria eléctrica. Al mismo tiempo:

- **FERC no tiene norma sobre IA operativa**, pero sí emitió órdenes de co-ubicación en PJM y
  **órdenes de *show cause* sobre grandes cargas a los seis RTO/ISO**.
- **NERC: estándares de carga computacional previstos para diciembre de 2026.**
- **NIST** desarrolla un *perfil de infraestructura crítica* para su AI Risk Management Framework,
  con la energía **identificada explícitamente como foco primario**.
- Al menos **cinco estados** tienen legislación pendiente sobre IA y energía en la sesión 2026.
- **EO 14409** (junio de 2026) instruye a las agencias a reforzar la infraestructura federal frente
  a riesgos habilitados por IA.

**Oportunidad 4 — Preparación para el perfil NIST de infraestructura crítica.** La secuencia es
inusualmente favorable: existe un marco (AI RMF), se está escribiendo el perfil sectorial, y no hay
todavía norma vinculante de FERC. Un cliente que llegue con gobernanza alineada al perfil antes de
que cierre, llega con ventaja y sin coste de remediación. El entregable —inventario de sistemas de
IA, clasificación de riesgo, trazabilidad de decisión, plan de pruebas— es consultoría pura y no
depende de que el perfil final cambie en los detalles.

**Oportunidad 5 — Siting de datacenter como herramienta consultable.**
[azmartone67/dchub-mcp-server](https://github.com/azmartone67/dchub-mcp-server) (MIT) publica un
*Data Center Power Index* diario sobre **300+ mercados**, expuesto por MCP. Tiene 3 ★ y es
irrelevante como producto; es relevante como **prueba de que el patrón funciona**. La pregunta
"¿dónde puedo enchufar 500 MW?" es la pregunta de 2026 en Norteamérica, y convertirla en una
herramienta que un agente consulta —sobre datos del cliente y de los seis ISO— es un encargo
delimitado y vendible.

⚠️ **Dato que no pudimos verificar**: un blog afirma mandatos NERC CIP-011/CIP-014 para sistemas de
IA en 2026. No se encontró fuente primaria. **No usar en una propuesta** sin consultar los dockets de
NERC/FERC directamente.

#### Actualización del quinto pase (2026-11-20)

**El regulador nombró a los operadores, y existe una librería BSD-3 que lee a todos.** El
2026-06-18 la FERC emitió *show-cause orders* bajo la §206 de la Federal Power Act a **seis
operadores regionales** —PJM, MISO, SPP, CAISO, ISO-NE y NYISO— cubriendo, según el anuncio, unos
200 millones de personas en más de 30 estados, a petición del Secretario de Energía. La coincidencia
operativa es el dato aprovechable: **esos seis, más ERCOT, son exactamente los siete ISO/RTO que
[`gridstatus`](https://github.com/gridstatus/gridstatus) (BSD-3-Clause, 456 ★) extrae con una sola
interfaz** (ver `repos/foundations.md`).

Matices que cambian el alcance de una propuesta:

- **No es una norma nacional.** La FERC actuó por órdenes, no por reglamento final: **no** se crea una
  regla única de interconexión para datacenters. Las fuentes secundarias **discrepan** sobre los
  plazos (unas hablan de 60 días para justificar o reformar tarifas, otras de informes a 30 días);
  tratar la fecha como indicativa.
- **ERCOT queda en gran medida fuera** de la jurisdicción de la FERC. Un alcance "EE. UU." que
  prometa homogeneidad regulatoria entre ERCOT y los demás es incorrecto.
- **El coste de conexión lo paga el datacenter**, incluidas las mejoras asociadas a su propia
  conexión, bajo el marco descrito.
- **NERC emitió una alerta de Nivel 3 en mayo de 2026** — la tercera en sus 58 años de historia — y
  la FERC le encargó desarrollar reglas de fiabilidad para **grandes cargas computacionales**, con
  recomendaciones finales previstas para finales de 2026.
- **DOE, septiembre de 2026:** 31 proyectos en 26 estados seleccionados en el programa **SPARK**
  (reconductorado acelerado y tecnologías avanzadas de transmisión).

**Oportunidad concreta, no genérica:** analítica de **cola de interconexión y de grandes cargas** para
los seis operadores nombrados. La base de datos es `gridstatus` (BSD-3), el dimensionado del recurso
en sitio es `REopt_API` (BSD-3 + marca), y la huella horaria es `open-grid-emissions` (MIT). Los tres
son nuevos en esta KB y los tres son de origen norteamericano.

**Reserva de método:** todo lo regulatorio de este bloque viene de fuentes secundarias (prensa
especializada, blogs jurídicos y notas de análisis). Las órdenes de la FERC y los expedientes de
NERC son las referencias autoritativas y **no se han podido abrir desde este entorno**. Sirve para
planear; no para firmar un compromiso de cumplimiento con fecha.

### EMEA

**Contexto regulatorio (verificado con matices)**: la Comisión publicó en **junio de 2026** la
hoja de ruta **COM(2026) 501** de digitalización e IA en energía, que compromete construir
**foundation models para gestión y planificación de red**, con financiación modesta de
**~EUR 75 M para 2026-2027**. Un marco de intercambio transfronterizo de datos energéticos se
desarrollaría **desde 2027**. Sobre el **AI Act**: el Digital Omnibus movió el calendario y las
obligaciones de alto riesgo del Anexo III aplicarían desde el **2 de diciembre de 2027**
(Reglamento (UE) 2026/1744); la guía de clasificación de la Comisión seguía en **borrador**, con
versión final esperada a fines de 2026. En **Alemania, BNetzA asumió la supervisión de IA el 29 de
julio de 2026**.

- **Oportunidad 1 — Conformidad AI Act para operadores de red**: gestión de red y load forecasting
  se tratan generalmente como **alto riesgo**. Hay una ventana de ~12 meses antes de diciembre de
  2027 para construir el expediente técnico, la gestión de riesgos y la supervisión humana. Es
  trabajo de ingeniería facturable con fecha límite legal.
- **Oportunidad 2 — Integración del stack de origen EMEA**: `powsybl` (RTE), `power-grid-model`
  (Alliander), `openSTEF` (LF Energy), `Grid2Op` (RTE), `dpsim` (RWTH Aachen) son todos MPL-2.0 y
  escritos por los propios operadores. Responden la pregunta de **soberanía digital** antes de que
  el cliente la haga.
- **Oportunidad 3 — Movilidad eléctrica**: `evcc` (7638 ★) y `SteVe` muestran dónde está la masa
  crítica real de la comunidad europea. Agregación de carga y V2G sobre base probada.
- **Players a tener en cuenta**: Enedis, E.ON, Stedin e i-DE ya exploran IA; **Eurelectric** corre
  un workstream de IA y digitalización llamado **Digitopia**.
- ⚠️ Las fechas del AI Act provienen de blogs de consultoría y **se contradicen entre sí**
  (varias fuentes antiguas decían agosto de 2026). Verificar contra el Diario Oficial antes de
  comprometer un plan de cumplimiento.


**Actualización del segundo pase (2026-11-20)** — segunda confirmación independiente, y un límite
de verificación que hay que dejar de pedir:

- **El AI Act: la fecha queda confirmada por búsqueda independiente** (nueve fuentes secundarias
  concordantes). El **Digital Omnibus on AI, Reglamento (UE) 2026/1744**, se publicó en el Diario
  Oficial el **24 de julio de 2026** y entró en vigor el **27 de julio de 2026**. Mueve el alto
  riesgo **autónomo del Anexo III** del 2 de agosto de 2026 al **2 de diciembre de 2027**, y el
  **embebido en productos regulados del Anexo I** al **2 de agosto de 2028**. **Difiere la
  aplicación, no los requisitos.**
- ⚠️ **La verificación primaria que pidió el pase anterior no es posible desde este entorno**:
  `eur-lex.europa.eu` devuelve **HTTP 403 del proxy** (política de red), igual que `huggingface.co`
  y `gitee.com`. No es un fallo transitorio: **dejar de pedirla en cada pase** y marcar la fecha como
  "concordancia de múltiples fuentes secundarias", que es lo que es. Si un cliente firma un plan de
  cumplimiento, la cita debe salir del Diario Oficial consultado **fuera** de esta KB.
- **Dos ventanas con fecha propia, ambas vendibles**: (1) el **modelo de contrato de conexión a red
  para datacenters** comprometido por la Comisión para el **segundo semestre de 2026**, respaldado
  por una declaración de intención de **catorce asociaciones industriales europeas**; (2)
  **AI.grids**, iniciativa para construir un **modelo de IA compartido para operación de red**,
  lanzada con acuerdo de proyecto el **3 de junio de 2026**. La segunda es la que puede convertirse
  en estándar de facto: estar dentro vale más que venderle a un TSO aislado.
- **Contrapeso que conviene decir en la reunión**: la prensa del **19 de noviembre de 2026** describe
  proyectos de IA frenados en Europa por red tensionada, competencia por agua y electricidad y
  oposición local, y las cinco "AI gigafactories" de la UE con disponibilidad energética limitada y
  huecos de financiación. La restricción europea **no** es el modelo: es el punto de conexión.
- **Precedente regulatorio nacional a vigilar**: en **Polonia**, el operador de transmisión exige
  **aprobación previa** para sistemas de IA que influyan en el despacho. Una fuente de vendor estima
  **3–6 meses** adicionales de plazo; el número es de vendor, el requisito es el dato. Si otro TSO
  copia el mecanismo, el cronograma de cualquier piloto de despacho cambia.


#### Actualización del tercer pase (2026-11-20)

- **Hay una política industrial europea explícita para IA en energía, con dinero asignado.** La
  Comisión publicó el **Strategic Roadmap for Digitalisation and AI in the Energy Sector**,
  referenciado como **COM(2026) 501, de 3 de junio de 2026**, que incluye una iniciativa insignia
  **`AI.grids`** para un modelo de IA compartido de operación de red. Un documento del Consejo
  (ST-10101-2026) cifra en torno a **75 M€ de Horizon Europe para 2026–2027** dirigidos a redes,
  autoconsumo y almacenamiento, más un marco de intercambio transfronterizo de datos energéticos y
  entrenamiento de modelos **a desarrollar desde 2027**.
- **Por qué importa para posicionarse**: un roadmap con fondos y una iniciativa nombrada es un
  calendario de licitaciones. El socio natural no es el cliente final sino el consorcio.
- **Regulación nacional que ya añade plazo**: se reporta que el TSO polaco **PSE** exige aprobación
  previa para sistemas de IA capaces de influir en el despacho, con **3–6 meses** de impacto en
  cronograma. En Alemania aplican los requisitos de **Bundesnetzagentur** y el régimen **KRITIS** de
  infraestructura crítica. Esto se presupuesta como fase, no como trámite.
- **El AI Act sigue sin confirmación primaria desde este entorno** (ver "Gaps declarados"): el
  desplazamiento del alto riesgo de Anexo III de **2-ago-2026 a 2-dic-2027** vía Digital Omnibus
  tiene concordancia de múltiples fuentes secundarias; una de ellas data el Reglamento (UE)
  2026/1744 como vigente desde el **27-jul-2026**, y no se pudo verificar. Sirve para planear,
  **no para firmar un compromiso de cumplimiento**.

#### Actualización del cuarto pase (2026-11-20)

**Hay dinero asignado, con fecha y cifra.** La *Strategic Roadmap for Digitalisation and AI in the
Energy Sector* de la Comisión Europea (publicada el **3 de junio de 2026**) es una comunicación de
política, **no legislación vinculante** — pero su financiación es concreta: **Horizon Europe
financiará modelos de IA para gestión de red con convocatorias de 30 M€ en 2026 y 20 M€ en 2027**.

**El calendario del AI Act se movió, y esto cambia la conversación con el cliente.** Según Baker
Botts, un acuerdo político del **7 de mayo de 2026** desplaza el plazo de cumplimiento de los
sistemas de alto riesgo del Anexo III del **2 de agosto de 2026 al 2 de diciembre de 2027**.
⚠️ **Condición crítica**: la adopción formal estaba **pendiente**, y hasta su publicación en el
Diario Oficial **los plazos originales siguen en vigor**. Un cliente que ya planificó para agosto de
2026 no debe desmovilizar basándose en un acuerdo político.

Marcos que se acumulan sobre el mismo sistema: **AI Act + NIS2 + REMIT** (bajo REMIT, el trading
energético con IA debe ser transparente, auditable y libre de manipulación de mercado), y en Reino
Unido la guía de **Ofgem *"Ethical AI use in the energy sector"*, segunda edición de mayo de 2026**.

**Oportunidad 4 — Conformidad multi-marco como un solo entregable.** Lo que un operador europeo
necesita no es cumplir el AI Act: es cumplir AI Act, NIS2 y REMIT **sobre el mismo sistema de IA**,
con una sola trazabilidad. Esa consolidación es el trabajo facturable, y el desplazamiento del plazo
a diciembre de 2027 abre la ventana para hacerlo bien en lugar de a la carrera.

**Oportunidad 5 — Captura de Horizon Europe.** 50 M€ en dos convocatorias, dirigidas
específicamente a modelos de IA para gestión de red. El stack de origen EMEA que esta KB ya
documenta —`powsybl`, `power-grid-model`, `Grid2Op`, `openSTEF`, `operatorfabric-core`, todos
MPL-2.0 y todos de operadores de red europeos— es exactamente el perfil que esas convocatorias
esperan. Posicionarse como integrador en un consorcio es una vía de entrada con financiación
pública, no con presupuesto de cliente.

**La oferta sigue siendo EMEA-dominante.** De los repos nuevos de este pase, los de origen EMEA
incluyen `FlexMeasures` (LF Energy), `iec104-python` (Fraunhofer FIT), `Gurux` DLMS,
`JutulDarcy.jl` y `ecalc`/`xtgeo`/`resdata` (Equinor), `PowerDynamics.jl`, `Simplus-Grid-Tool`,
`RL2Grid`, `EV2Gym`, `open-meteo` y los MCP de NESO. **Es la región con mayor oferta open source
del sector, por un margen amplio** — argumento de soberanía tecnológica utilizable tal cual.

#### Actualización del quinto pase (2026-11-20)

**Hay hoja de ruta europea de IA en energía, hay dinero asignado, y la barrera declarada es de
datos — que es precisamente lo que un repo nuevo de esta KB resuelve.**

- **Hoja de ruta de IA para la energía (Comisión Europea).** Alcance declarado: conexiones de red,
  abastecimiento de energía limpia, **servicios de flexibilidad** y recuperación de calor residual.
- **Horizon Europe: ~75 M€ para tecnologías de IA en energía en 2026-2027** (documento del Consejo
  ST-10101-2026, 4 de junio de 2026), con foco en **redes, autoconsumo y almacenamiento**. Es la
  cifra de financiación más concreta que esta KB ha podido situar en EMEA.
- **Legislación prevista en 2026** para acelerar el despliegue de contadores inteligentes y
  establecer **indicadores de rendimiento de red inteligente a escala UE**.
- **Esquema de calificación de datacenters** (eficiencia energética, agua, energía limpia,
  reutilización de calor residual y **flexibilidad**); el acuerdo modelo se esperaba para el segundo
  semestre de 2026.
- **Recomendación regulatoria explícita:** integrar la gestión energética basada en IA **dentro** de
  la regulación de red, y construir un marco UE unificado para **flexibilidad de demanda dirigida por
  IA**.
- **Utilities nombradas** en el informe de la CE como exploradoras de IA: **Enedis, E.ON, Stedin e
  i-DE**. Son nombres accionables para prospección, no un mercado abstracto.

**El dato de adopción, que es el que vale.** Según la lectura de una consultora del *summit* de
utilities de Ámsterdam (marzo de 2026): las utilities europeas se desplazan hacia sistemas basados en
flexibilidad **pero carecen de vías claras de monetización**, y siguen desplegando IA como
**soluciones puntuales aisladas**, con poca integración en sistemas y flujos de trabajo centrales.
Eso describe un mercado de **integración**, que es exactamente lo que esta KB sostiene que es
proponible, y no un mercado de modelos.

**La barrera declarada tiene una respuesta técnica nueva.** El informe de la CE sobre IA en redes
inteligentes cita el cumplimiento de **GDPR**, la recolección de datos y el preprocesado extenso como
obstáculos para **entrenar** modelos. [`OpenSynth-energy/OpenSynth`](https://github.com/OpenSynth-energy/OpenSynth)
(**Apache-2.0**, 77 ★, cohorte LF Energy) publica modelos generadores de **perfiles sintéticos de
consumo de contador**: datos que no pertenecen a ningún consumidor. Para un cliente europeo que no
puede exportar datos de medición, va **antes** de `openstef` en el pipeline. Es el encaje
regulación→repo más limpio de este pase.

**Capa de datos de mercado:** [`fboerman/entsoe-py`](https://github.com/fboerman/entsoe-py) (**MIT**,
745 ★, 270 forks) es el cliente canónico de la API de ENTSO-E y **el repo con más estrellas añadido
en cinco pases**. La alternativa "GridStatus europeo", `jo20ow/Obsyd` (37 zonas de oferta), es
**AGPL-3.0**: no usarla en un SaaS de cliente.

**Lo que sigue sin equivalente abierto en EMEA:** emisiones horarias de red. `open-grid-emissions`
(MIT) sólo cubre EE. UU. Gap medido, no omisión.

### APAC

**Contexto regulatorio (verificado)**: en **diciembre de 2025**, la **NDRC y la NEA de China**
emitieron guía sobre el uso de IA en planificación de red, gestión de equipamiento, operación y
seguridad — es la política pública más explícita del mundo sobre IA en red eléctrica. En general,
la regulación de IA en APAC apunta a **usuarios y deployers** más que a desarrolladores de modelos,
con aplicación desigual entre países.

- **Oportunidad 1 — Escala de medición inteligente**: India aprobó **más de 200 millones** de
  medidores inteligentes; Singapur apuntaba a **medición avanzada nacional en 2026**. Eso es
  ingeniería de datos y NILM a escala poco común. Recursos: `zhgqcn/awesome-NILM-with-code`,
  `MyEMS` (MIT, de origen chino, ya hablando el idioma del mercado).
- **Oportunidad 2 — Gestión de baterías residenciales agregadas**: en Japón, **ITOCHU y Lunar**
  usan IA para gestionar baterías residenciales mediante la plataforma **Gridshare** — patrón
  replicable con `EOS` + `evcc`.
- **Oportunidad 3 — Herramientas internas tipo "Discom GPT"**: **Apraava Energy** lanzó en India
  una herramienta Discom GPT reconocida por el Ministerio de Energía. Asistentes de dominio sobre
  datos de distribuidora, replicables en toda la región.
- **Players**: ABB, GE, Schneider Electric y Siemens aparecen como proveedores dominantes; utilities
  regionales como Chubu Electric Power figuran en material del IEA.


**Actualización del segundo pase (2026-11-20)** — fuentes secundarias (IEA citada de segunda mano):

- **La asimetría que define todo el negocio en APAC**: un datacenter se construye en **1–2 años**;
  una ampliación de red tarda **5–10**. En muchas jurisdicciones la espera por conexión llega a
  **5–10 años**. Eso convierte **flexibilidad, co-localización y generación on-site** en el producto,
  no en la alternativa.
- **India — el país con el sustrato de datos más grande de la región**: más de **200 millones** de
  medidores inteligentes aprobados bajo el **RDSS**, incentivos fiscales a datacenters en el
  **presupuesto 2026**, y una calidad de red que es **restricción de diseño**: se reportan
  variaciones rutinarias de **±5 % en tensión y ±1 Hz en frecuencia**. Un modelo entrenado con
  supuestos europeos de estabilidad **no transfiere**; la oportunidad es justamente la robustez.
- **Japón** — red partida en **dos frecuencias** (50/60 Hz), **TEPCO Power Grid** usando **drones con
  IA** para diagnóstico de equipamiento, y electricidad industrial reportada en torno a
  **USD 0,25/kWh** por dependencia de LNG importado. Precio alto + activos envejecidos = inspección
  asistida y eficiencia tienen ROI calculable, no especulativo.
- **China** — **State Grid** opera una plataforma de orquestación con IA **a escala de ciudad** en
  tiempo real. Es la mayor referencia de despliegue del mundo y, a la vez, **el mercado menos
  accesible**: régimen estricto de registro y evaluaciones de seguridad para servicios de IA.
- ⚠️ **El gap de repos APAC sigue abierto y ahora se sabe por qué no se puede cerrar desde aquí**:
  la hipótesis del pase anterior era "están en Gitee, no en GitHub". **`gitee.com` devuelve HTTP 403
  del proxy** en este entorno, así que la hipótesis **no es testeable** con las herramientas de esta
  KB. Lo único verificado de origen APAC sigue siendo `MyEMS` (MIT, 763 ★) y
  `ronaldowzy/price_forecast` (MIT, 25 ★, forecasting de precio spot para mercados chinos). Un
  engagement en APAC que dependa de "base open source local" necesita verificación **fuera** de esta
  KB.
- **Patrón regulatorio regional**: las reglas de IA de APAC apuntan mayoritariamente a **usuarios y
  deployers**, no a desarrolladores de modelos, y lo específico del sector energético está poco
  desarrollado. Para un cliente eso significa que **la obligación cae sobre él**, no sobre el
  proveedor del modelo — argumento directo para vender gobernanza.


#### Actualización del tercer pase (2026-11-20)

- **El dato de adopción más útil del pase, y es un dato de freno**: una encuesta a operadores de red
  de **13 países** (China, Japón y Corea incluidos) encuentra que sólo **23 % usa IA en operación en
  tiempo real**, frente a **~70 % en mantenimiento de activos y planificación operativa**. La
  conclusión comercial es directa: en APAC el encargo vendible hoy es **activos y planificación**,
  no sala de control. Vender tiempo real es vender contra la evidencia.
- **Escala de demanda**: Wood Mackenzie proyecta que los datacenters impulsen un alza de **790 TWh**
  en los mercados de APAC, con 2026 como año bisagra. APAC se estima en torno a **9,45 B USD en
  2025** (~28 % del mercado global de IA en energía); Japón ~**1,66 B USD en 2026**. Cifras de
  investigación de mercado: direccionales, no exactas.
- **China**: State Grid aplica aprendizaje por refuerzo a programación y modos de operación, y el
  plan quinquenal **2026–2030** apunta explícitamente a IA para volatilidad de red y vertido
  renovable. Es el mayor desplegador y el menos accesible como cliente.
- **Japón**: la restricción es acceso a potencia de red, que se estrecha en 2026; los datacenters
  revierten una década de caída de demanda eléctrica. Mercado de derivados eléctricos en
  crecimiento rápido.
- **India**: concentración en datacenters (Hyderabad como foco) con retrasos severos de entrega de
  red; mercado spot vía **IEX** (day-ahead y term-ahead).
- **Condicionamiento regulatorio nuevo**: se reporta que **Singapur, Malasia y Corea del Sur** exigen
  a los desarrolladores de datacenter planificar **almacenamiento en baterías y vertido** junto con
  la evaluación de impacto en red; **Johor** restringió ciertos proyectos por consumo de agua. Eso
  convierte el dimensionamiento de BESS en requisito de permiso — y conecta con `PyBaMM` y `SAM`
  (ver `repos/foundations.md`).

#### Actualización del cuarto pase (2026-11-20)

**Marco regional específico de IA y energía, y es nuevo.** APEC publicó las *Policy Recommendations
on the Mutual Enhancement Between AI and Energy in the Asia-Pacific (**2026–2030**)*: **voluntarias**,
piden planificación **coordinada** de instalaciones de cómputo e infraestructura energética y
mencionan posibles *benchmarks* IA-energía. Es el único instrumento regional que trata IA y energía
como un problema conjunto en lugar de dos políticas separadas.

**Leyes de IA que ya están en vigor** (no futuras — varias fuentes las describen como pendientes y
han quedado desactualizadas):

- **Corea del Sur**: *AI Basic Act* **en vigor desde el 22 de enero de 2026**; el ministerio plantea
  2026 como **año piloto con aplicación limitada**.
- **Vietnam**: ley de IA **efectiva el 1 de marzo de 2026**, regulador Ministerio de Ciencia y
  Tecnología.
- **China**: el marco más extenso ya existente. **Indonesia**: reglas vía Regulación Presidencial.
  **Singapur**: consulta sobre guías de gestión de riesgo de IA, posible cierre a finales de 2026.

**Energía y datacenter**: **Singapur** apunta a medición avanzada **nacional en 2026**. **Tailandia**
tiene reglas en borrador para que datacenters promovidos por el **BOI** contraten directamente con
generadores renovables, con *wheeling* por la red. Análisis de IBM señala el freno estructural: buena
parte de la región depende de **monopolios de utility respaldados por el Estado**, lentos en adoptar
tarifas flexibles. **Malasia** enmarca un ecosistema cloud *"seguro y soberano"* como base de la
adopción de IA.

**Oportunidad 4 — Soberanía de datos como requisito de arquitectura, no como preferencia.** Entre la
ley coreana, las reglas indonesias, el encuadre soberano de Malasia y el marco chino, un despliegue
de IA energética multinacional en APAC necesita diseño **por jurisdicción** desde el inicio:
residencia de datos, modelos desplegables on-premise, trazabilidad local. Es trabajo de arquitectura
y de compliance, y es facturable precisamente porque no se puede resolver con un SaaS único.

**Oportunidad 5 — PPA directo para datacenter en Tailandia.** Si la regla del BOI se confirma,
habilita contratación directa datacenter↔renovable con *wheeling*. Modelar, optimizar y verificar ese
contrato es un encargo concreto, y la combinación `FlexMeasures` + `opendsm` (ambas Apache-2.0) es el
punto de partida que lo cubre.

**Oferta open source de origen APAC — medida, y es escasa.** En las once consultas de este pase, los
únicos repos energéticos de origen APAC fueron `MyEMS` (MIT, China, ya en esta KB),
`stevenjoezhang/hass-state-grid` (MIT, 72 ★, consumo de State Grid), `GeoBrain` (Apache-2.0, 88 ★,
subsuelo) y `douyimin/CIG-bench` (MIT, 66 ★). **El hueco es de oferta, no de demanda**: APAC es, según
un informe, la región que lidera la *adopción*. Para un encargo APAC se integra stack EMEA o
norteamericano; no hay base regional sobre la que construir.

#### Actualización del quinto pase (2026-11-20)

**La asimetría temporal es el argumento comercial de la región, y ahora tiene cifra.** Según la
lectura de los informes de la AIE: la capacidad de IA se construye en **1-2 años**, las mejoras de
red tardan **5-10 años**, y **la brecha es más ancha en APAC que en ninguna otra región**. Todo lo
que esta KB propone —previsión, flexibilidad, optimización de lo existente— vive dentro de esa
brecha, porque es lo único que se puede desplegar en el plazo corto.

**El dato de adopción más riguroso que esta KB ha encontrado en cinco pases.** Encuesta de la AIE a
operadores de red de **13 países**, China y Japón incluidos:

| Uso de IA | Operadores que lo aplican |
|-----------|---------------------------|
| **Operación en tiempo real** | **23 %** |
| Planificación de desarrollo de red | 54 % |
| Mantenimiento de activos y planificación operativa | ~70 % |

Leído para una propuesta: el mantenimiento y la planificación ya están adoptados —ahí se compite
contra incumbentes—, y **el tiempo real está casi vacío**. También explica por qué
`operatorfabric-core` (capa *human-in-the-loop*) importa: el salto de 54 % a 23 % es el salto de
recomendar a actuar, y ningún operador lo da sin trazabilidad.

**Demanda y mercado (fuentes de consultora, indicativas):**

- **790 TWh** de incremento atribuido a datacenters; fuera de China, **India concentra ~50 %** del
  crecimiento regional de demanda y el **Sudeste Asiático ~25 %**.
- En **Japón**, los datacenters están **revirtiendo una década de caída** de la demanda energética.
- **China:** State Grid opera IA en red; se describe una plataforma de orquestación a escala de
  ciudad que integra **previsión, *trading*, regulación y liquidación en un solo sistema operativo**.
  Advertencia recogida: la **falta de flexibilidad** de las redes chinas podría anular las ganancias
  de eficiencia de la IA.
- **India:** más de **200 millones de contadores inteligentes** aprobados bajo el RDSS; plan de Adani
  de ~100 000 M USD de infraestructura de IA anclada en renovables.
- **Japón:** TEPCO Power Grid desarrolla drones automatizados para captura 3D de equipos; Chubu
  Electric entrenó un modelo de red neuronal sobre datos de red a **30 segundos** de resolución.
- **Diseño de mercado:** licitaciones que **exigen cada vez más almacenamiento y flexibilidad** en
  2026; China despliega *Green Power Direct Connection* a escala completa; **Tailandia y Vietnam**
  avanzan marcos de PPA directo.

**El gap de repos de origen APAC se mueve, poco pero verificado.**
[`PyPSA/PyPSA-China`](https://github.com/PyPSA/PyPSA-China) es un modelo del sistema energético chino
con **licencia MIT confirmada** (declarada en README y en `LICENSES/MIT.txt`; la API de GitHub dice
`null` por el esquema REUSE). 49 ★, 15 forks, push 2026-07-14. Con `MyEMS` (MIT, 763 ★) y
`price_forecast` (MIT, 25 ★) del cuarto pase, **ya son tres piezas permisivas y verificadas** con
alcance APAC.

**Precisión obligada:** `PyPSA-China` vive bajo la organización `PyPSA`, de liderazgo europeo. Es un
modelo **de** China, no necesariamente un repo **de origen** chino. La hipótesis de que el ecosistema
local está en Gitee **sigue sin ser testeable** desde este entorno (`gitee.com` → 403, octavo pase
consecutivo). **No afirmar cobertura local en una propuesta APAC.**

### LATAM

**Hallazgo de oferta — se rompe el patrón "LATAM no produce repos"**: pases anteriores de esta
rotación registraron, industria tras industria, **cero repos de origen LATAM**. En energy eso es
**falso**. `{json:scada}` (**513 ★**, GPL-3.0) y `OSHMI` (**467 ★**, GPL-3.0) son de
**Ricardo L. Olsen, Porto Alegre, Brasil** — desarrollador open source independiente, trabajando en
software de control del sector eléctrico **desde 1998** (verificado en su perfil de GitHub). Casi
**1.000 ★ combinadas** de software de control de red de autoría brasileña, con IEC 61850, ICCP,
IEC 60870-5-101/104, DNP3, OPC-UA y Modbus. **Es la credencial técnica regional más fuerte que esta
KB ha encontrado en cualquier industria.** Úsese en pitch regional.

**Contexto de mercado (verificado, con cautelas de fuente)**:
- **Brasil**: mayor mercado de datacenters de la región, **>40 %** de la inversión en datacenters de
  LATAM; ~**12 GW** de capacidad de transmisión disponible y mix **~83 %** renovable (una fuente
  anterior decía 85 %: el rango real es 83-85 %). Subasta de **Capacidad de Reserva de 19,5 GW**,
  récord, reconfigurando la inversión; se preparan contratos de hasta **15 años** para baterías.
  Restricción real: demoras de aprobación e interconexión.
- **Chile**: líder regional en almacenamiento. La **Comisión Nacional de Energía** corre la
  **Licitación de Suministro 2026/01** con contratos a **15 años**. Red unificada desde **2019**
  (interconexión SIC–SING). Cuello de botella: **transmisión** — genera más energía limpia que la
  que su red puede llevar a donde están los datacenters.
- **México**: el estrés de red es el más visible. En **El Marqués, Querétaro** se programan cortes
  para evitar el colapso del sistema. La **SENER** abrió en **mayo de 2026** una convocatoria de
  proyectos estratégicos de generación y almacenamiento, con registro de almacenamiento abierto
  hasta el **30 de octubre de 2026**. El proceso de interconexión sigue siendo **opaco en costo y
  plazos**. Una investigación de Thomson Reuters Foundation halló que la capacidad renovable no
  crece al ritmo de la demanda de IA y que varios operadores recurren de nuevo a fósiles.
- **Adopción**: un informe de Stimson Fellows y **CAF**, desarrollado con Microsoft, identifica IA
  en forecasting renovable, modelos descentralizados, mantenimiento predictivo, digital twins y
  gestión avanzada de red. **Chile** ya integra forecasting renovable basado en IA.
- ⚠️ La afirmación de que Brasil, Chile y Paraguay pueden ofrecer renovable **bajo USD 0,06/kWh**
  proviene del análisis interno de **un solo desarrollador**, no de datos independientes. Un pase
  anterior la registró como "LATAM 10GW PPA <$0.06/kWh": **no citarla como dato de mercado**.

- **Oportunidad 1 — Modernizar SCADA sobre base regional**: `json:scada` + `OSHMI` permiten
  proponer modernización de centro de control con software de autoría regional y protocolos
  estándar. Diferenciador frente a propuestas que sólo revenden plataforma del norte.
- **Oportunidad 2 — Interconexión y colas de datacenter**: Brasil, Chile y México comparten el
  mismo cuello de botella (transmisión y plazos de interconexión) con marcos distintos. Es el mismo
  servicio que en North America, con menos competencia instalada.
- **Oportunidad 3 — Dimensionamiento de BESS para licitaciones**: Chile (15 años) y Brasil (hasta
  15 años para baterías) tienen licitaciones activas con contratos largos. `PyPSA` + `EOS` modelan
  el caso de negocio.
- **Riesgo**: `json:scada` y `OSHMI` son **GPL-3.0**. Ejecutar como sistema aislado detrás de su
  API; no enlazar en producto propietario del cliente.


**Actualización del segundo pase (2026-11-20)** — un hallazgo de oferta verificado en GitHub y
contexto regulatorio de fuentes secundarias:

- 🎯 **El operador del sistema colombiano publica código MIT.**
  [`EquipoAnaliticaXM/API_XM`](https://github.com/EquipoAnaliticaXM/API_XM) — **MIT**,
  `Copyright (c) 2020 XM S.A. E.S.P.`, **75 ★ / 38 forks**, push **2026-11-10** — es el cliente de
  consulta de datos del mercado eléctrico colombiano (generación, demanda, precio de bolsa,
  emisiones) publicado por **XM**, operador del Sistema Interconectado Nacional y administrador del
  mercado. El org mantiene además `datasets` (histórico, push **2026-11-19**), `Chatbot_XM` (MIT) y
  `documentacion_emisionesCO2` (MIT).
  **Por qué cambia el argumento regional**: el hallazgo brasileño (`json-scada`, `OSHMI`) es de **un
  autor individual**; este es **institucional**, con copyright corporativo en el `LICENSE`. Son dos
  tipos de evidencia distintos, y el segundo es el que un comité de compras acepta.
- **Ya hay demanda visible aguas abajo, sin oferta profesional**: `Cdhernandezr/energyagent-colombia`
  (agente de IA sobre el mercado eléctrico colombiano, LangGraph + FastAPI, **sin licencia**, 0 ★) y
  `CAINavy/tablero-xm` (tablero sobre datos de XM, push **2026-11-20**). Alguien está construyendo
  esto hoy, en proyectos personales y sin licencia. Ese es el hueco exacto.
- **El gap LATAM, ahora medido por país y no por región**: cerrado para **Brasil** (dos repos de
  autor individual) y **Colombia** (institucional). **Argentina (CAMMESA), Chile (Coordinador
  Eléctrico Nacional) y México (CENACE)**: se buscó por nombre de institución y por término de
  dominio en español y portugués — **cero repos institucionales con tracción**; lo que aparece son
  tableros personales de 0 ★. Eso no es "LATAM no produce": es que la producción está en dos países.
- **Brasil — el marco se cerró y tiene números**: la **Lei 15.504** creó el régimen de datacenters
  **REDATA**, promulgada el **15 de septiembre de 2026**; **ANEEL** autorizó **acceso directo a la
  red de alta tensión**, con un proyecto planificando **1,8 GW de demanda hacia 2033**. El Ministerio
  reportó **205 datacenters en operación** en junio de 2026 y **38 GW** en solicitudes de opinión de
  acceso. Antes, la **Lei 15.269** (noviembre de 2025) reformó el marco del sector eléctrico, con
  subasta de capacidad de reserva en **marzo de 2026**. Riesgo declarado por analistas: **curtailment
  significativo**.
- **Chile y México: la restricción no es la misma, y confundirlas arruina una propuesta.** Chile es
  **líder regional en almacenamiento**, y su freno es el **permisológico/ambiental** (proyectos
  congelados o cancelados; la Comisión Nacional de Energía advierte que la expansión de
  infraestructura no sigue el ritmo de la demanda de datacenters). México tiene el freno en el
  **acceso a la red**: proceso de interconexión **opaco en costo y plazo** de los refuerzos, con
  demoras de energización en **Querétaro**, su principal hub. Chile se vende con **licenciamiento y
  evidencia ambiental**; México con **modelado de interconexión y escenarios de plazo**.
- **Contrapeso de fuente**: la cifra regional de "**>10 GW** de capacidad lista para red en 2–3 años"
  proviene de un **desarrollador con interés comercial** y nombra como barreras reales la
  regulación, el permisado, la estructura de financiamiento y el riesgo de ejecución — **no** la
  capacidad. Usarla como contexto, nunca como dato propio.


#### Actualización del tercer pase (2026-11-20)

- **Brasil es el mercado con cifras oficiales y es el que hay que usar como ancla.** El Ministerio
  de Minas y Energía reportó **205 datacenters en operación en junio de 2026** y **38 GW** en
  solicitudes de opinión de acceso a red. Ese segundo número es la oportunidad: 38 GW de solicitudes
  es una cola de estudios de interconexión que nadie puede procesar manualmente.
  ⚠️ **Los conteos varían entre fuentes** (205, 206 y 225 para Brasil; 71 para México): citar el
  dato del MME y la fecha, nunca un número suelto.
- **Chile convirtió el datacenter en materia ambiental reglada**: el regulador ambiental adoptó un
  **criterio de evaluación específico para datacenters, en vigor desde el 25 de febrero de 2026**, y
  hay proyectos congelados o cancelados por licenciamiento. La Comisión Nacional de Energía advirtió
  que la expansión de infraestructura eléctrica no sigue el ritmo de la demanda. Servicio implicado:
  expediente ambiental y de red, no sólo diseño técnico.
- **México es el caso de oportunidad perdida** y conviene decirlo con franqueza: permisos lentos y
  red envejecida están desincentivando inversión pese a la ventaja geográfica; Querétaro concentra
  lo existente con infraestructura no diseñada para cargas intensivas.
- **PPA renovable como vía de entrada**: en marzo de 2026 **Equinix firmó un PPA con Auren Energia**
  (eólica y solar, Brasil). Un análisis sectorial —**fuente promocional, cifra no verificada**—
  habla de **>10 GW** de capacidad renovable lista para red que podría alcanzar grandes cargas en
  2–3 años.
- **Señal institucional regional**: **CAF** coordina una red regional de cómputo de alto rendimiento
  que arranca en **Chile y República Dominicana**. Es un interlocutor multilateral, no un cliente
  corporativo, y financia infraestructura.
- **Contrapeso que evita sobrevender**: un informe (BISI) sostiene que la región se vende como
  renovable pero opera con respaldo fósil. Para una propuesta de sostenibilidad, la medición de
  factor de emisión horario es parte del alcance, no un supuesto.

#### Actualización del cuarto pase (2026-11-20)

**Oferta open source de origen LATAM: medida de nuevo, y el resultado hay que decirlo con precisión
porque "cero" sería falso.** Once consultas en este pase (incluida una dirigida a `ONS`, `CAMMESA`,
`XM` y `energia`) **no encontraron ningún repo energético de origen LATAM nuevo**. Los que esta KB ya
tiene siguen siendo los únicos, y son reales y sustanciales:

| Repo | Licencia | ★ | Qué es |
|------|----------|---|--------|
| [riclolsen/json-scada](https://github.com/riclolsen/json-scada) | GPL-3.0 | 513 | SCADA/EMS/IIoT completo, **origen Brasil** |
| [riclolsen/OSHMI](https://github.com/riclolsen/OSHMI) | GPL-3.0 | 467 | HMI de subestación, **origen Brasil** |
| [EquipoAnaliticaXM/API_XM](https://github.com/EquipoAnaliticaXM/API_XM) | MIT | 75 | Datos del mercado eléctrico colombiano, publicados por el **operador del SIN** |

Por tanto el enunciado honesto es: **la oferta LATAM existe, está concentrada en tres repos de dos
autores, y no creció en este pase.** Un `json-scada` de 513 ★ con cobertura de IEC 61850, DNP3,
ICCP y OPC-UA, escrito en Brasil, es un activo regional real — y es GPL-3.0, lo que determina la
arquitectura (proceso aislado detrás de su API, nunca enlazado).

**Adopción: la demanda sí se mueve.** BNamericas documenta petroleras y energéticas regionales
profundizando el uso de IA para mantenimiento predictivo y eficiencia, con **Petrobras** y **Prio**
nombradas. **Chile** aplica IA a **despacho y pronóstico de irradiancia solar**. En **Brasil**, el
crecimiento de generación distribuida empujó medidores inteligentes y plataformas cloud de gestión
energética. El WEF advierte que la demanda energética de la IA es un desafío nuevo para la región, y
que las brechas de infraestructura digital siguen siendo agudas.

**Regulación: fragmentada y en movimiento.**

- **Perú**: uno de los primeros países de la región con **ley general de IA y mecanismos de
  implementación**; acuerdo de cooperación con la Embajada de EE. UU. que cubre regulación,
  datacenters y cloud.
- **Brasil**: la **ANPD** pasó a ser **agencia reguladora plena el 25 de febrero de 2026**, con mayor
  autoridad técnica, administrativa y financiera. **PL 2338** seguía pendiente.
- **Colombia**: **CONPES 4144**, política de gobierno con acciones y **presupuesto hasta 2030**.
- Un estudio de 2026 contabiliza **716 instrumentos regulatorios, normas y propuestas legislativas
  sobre IA en 23 países y territorios**, la mayoría desde 2023.

**Oportunidad 4 — El constreñimiento LATAM no es ley de IA: es protección de datos y red.** Igual que
concluyó el pase de automotive, lo vinculante aquí es **LGPD** (con una ANPD ahora con dientes) y la
capacidad física de red, no una ley horizontal de IA. Una propuesta que llegue hablando de AI Act
europeo está mal calibrada; una que llegue con gobernanza LGPD y un caso de mantenimiento predictivo
medible está calibrada.

**Oportunidad 5 — Exportar el activo brasileño.** `json-scada` + `OSHMI` cubren el núcleo SCADA/HMI
con protocolos de red completos. La capa agéntica MIT de esta KB se monta encima **sin tocar el
código GPL**, como servicio separado. Es una oferta con componente regional genuino —no una
importación— y aplicable a utilities medianas de toda la región.

#### Actualización del quinto pase (2026-11-20)

**Brasil pasó de intención a precedente regulatorio, y apareció una cifra que es directamente un
encargo.**

- **Precedente de acceso a red:** en **septiembre de 2026 ANEEL autorizó la conexión directa de
  Scala a la red de alta tensión de 525 kV**. Es el primer precedente citable de conexión directa de
  un datacenter en la región.
- **Escala de la cola:** el Ministerio de Minas y Energía reportó **205 datacenters en operación** en
  junio de 2026 y **38 GW en solicitudes de parecer de acceso**.
- **Brasil concentra más del 40 %** de la inversión en datacenters de América Latina.
- **La cifra que es un encargo: el *curtailment* alcanzó el 20,6 % de la generación eólica y solar
  total en 2025 — unos 20 TWh de electricidad limpia desperdiciada.** Eso no es un problema de
  capacidad instalada: es un problema de previsión, despacho y flexibilidad, que es exactamente lo
  que esta KB sabe componer con repos permisivos (`openstef` MPL-2.0, `atlite` MIT, `OpenOA` BSD-3,
  `PyPSA` MIT, `FlexMeasures` Apache-2.0).
- **Riesgo recurrente:** las aprobaciones **municipales** siguen siendo un punto de fallo para la
  elección de emplazamiento.

**México — la restricción más dura de la región.** Las autoridades de **Querétaro programaron cortes
de energía** para evitar el colapso del sistema. La capacidad renovable no crece al ritmo de la
demanda inducida por IA, y los **costes y plazos de interconexión no están claros**. Para una
propuesta: México es un mercado de **eficiencia y gestión de demanda en sitio**, no de nueva carga.

**Chile — la restricción es permisología, no recurso.** El criterio específico del Servicio de
Evaluación Ambiental para datacenters **entró en vigor el 25 de febrero de 2026**. La Comisión
Nacional de Energía advierte que la expansión de infraestructura eléctrica no sigue el ritmo de la
demanda de datacenters. El cuello de botella chileno es **transmisión y permisos**.

- **Ventana regional citada por la industria:** ~**10 GW en 18 meses** como oportunidad de América
  Latina para alimentar la era de la IA. Cifra de evento sectorial: usar como marco narrativo, no
  como dato.
- **Contrapunto honesto, y conviene llevarlo en la propuesta:** un análisis independiente describe
  los datacenters latinoamericanos como *"vendidos como renovables, alimentados con fósiles"*. Un
  discurso de descarbonización sin medición verificable es atacable; con `opendsm` (Apache-2.0,
  Receta 17) y huella horaria, es defendible.

**El gap de repos LATAM cambia de naturaleza: ya no es de oferta, es de permiso.**
[`FTDT-PyPSA/PyPSA-AR`](https://github.com/FTDT-PyPSA/PyPSA-AR) — "PyPSA Argentina" — **existe**: 10 ★,
1 fork, creado 2026-03-04, push 2026-04-30. Los cuatro pases anteriores registraron "cero repos
institucionales con tracción" para Argentina. Ahora hay un modelo del sistema argentino, y **no tiene
archivo de licencia en ninguna rama** (verificado: sin `LICENSE`, sin SPDX en README, sin
`LICENSES/`). No se puede incluir en un entregable.

| País | Credencial verificable | Estado al quinto pase |
|------|------------------------|------------------------|
| **Brasil** | `json-scada`, `OSHMI` (autor individual) | Sin cambios; sigue siendo la credencial más fuerte |
| **Colombia** | `API_XM`, `datasets` (institucional, XM) | Sin cambios; la única institucional de la región |
| **Argentina** | `PyPSA-AR` (10 ★, **sin licencia**) | **Nuevo**: existe el modelo, falta el permiso |
| **Chile** | — | **Cero.** Búsqueda por "Coordinador Eléctrico Nacional" y por dominio: nada con tracción |
| **México** | — | **Cero.** Búsqueda por "CENACE": nada energético con tracción |

**Por qué las búsquedas de Chile y México no encuentran nada (para no repetirlas).** El término
`eléctrico` está inutilizado en GitHub: `CENACE OR coordinador electrico in:name,description`
devuelve un contenedor de apps Electron (`electrico`, 809 ★), patinetes eléctricos, cargadores y
trabajos de curso. Es el mismo fenómeno que `hydrogen`. Lo que **sí** funcionó para Argentina fue
buscar por **nombre de modelo** (`pypsa`), no por institución ni por dominio. **Recomendación para el
próximo pase: buscar `PyPSA-CL`, `PyPSA-MX` y `PyPSA-BR` por nombre.**

## Posicionamiento Globant

1. **No competir con GridOS ni EcoStruxure.** Posicionarse como el integrador que pone una capa
   agéntica MIT sobre el núcleo abierto que los propios TSO europeos publican.
2. **Vender el desfase temporal**, no el tamaño de mercado: 1–2 años para construir un datacenter
   contra 5–10 para ampliar la red. Esa brecha es presupuesto aprobado hoy.
3. **Llevar la cláusula de licencia a la conversación técnica temprano.** El vertical energético es
   AGPL/GPL dominante y la capa de agentes es MIT. Saber dónde va el límite de proceso es un
   diferenciador real frente a competidores que descubren el problema en auditoría.
4. **Usar la credencial brasileña en LATAM.** Autoría regional verificable en software de control
   de red cambia la conversación en una licitación de utility latinoamericana.
5. **En EMEA, liderar con cumplimiento.** El AI Act con fecha de diciembre de 2027 convierte el
   forecasting de red en trabajo regulado y por tanto financiado.
6. **Usar la credencial colombiana como par de la brasileña.** `API_XM` es **MIT y de la
   institución** (XM S.A. E.S.P., operador del SIN). Frente a un comité de compras, "el operador del
   sistema publica esto bajo MIT y nosotros construimos sobre ello" pesa más que un repo de autor
   individual, por bueno que sea.
7. **En North America, cambiar el encuadre de velocidad a legitimidad.** Con el informe de Harvard
   sobre subsidio cruzado al ratepayer y un proyecto de ley bipartidista en curso, el entregable que
   se vende no es "conectamos antes" sino **"probamos que el costo no lo pagan los hogares"**:
   atribución de costos, trazabilidad y evidencia auditable.
8. **En O&G, cambiar el patrón de integración, no el discurso.** Todo el upstream open source
   encontrado es **GPL-3.0** (`OPM Flow`, `equinor/ert`). El entregable propietario sólo existe si
   el simulador queda como sistema de registro aparte. Presupuestar la integración desde el día uno.

## Tamaño de mercado: la dispersión es el dato (actualizado en el cuarto pase, 2026-11-20)

Cuatro fuentes consultadas en este pase dan cifras **irreconciliables** para el mismo mercado
("AI in Energy"). Se listan juntas a propósito, porque la conclusión útil no es ninguna de ellas:

| Fuente | Cifra | Horizonte | CAGR |
|--------|-------|-----------|------|
| GlobeNewswire / informe "AI in Energy Market 2026" | **22,82 B USD (2025) → 60,6 B USD (2030)** | 2030 | 21,4 % |
| Coherent Market Insights | **6,04 B USD en 2026** | — | — |
| openPR | **85,5 B USD para 2034** | 2034 | 18,2 % |
| (pases anteriores) Agentic AI in Energy | 656,6 M USD (2025) → 14,9 B USD (2035) | 2035 | 36,65 % |

**La cifra de 2026 varía casi 4× entre fuentes** (6,04 B vs. ~27 B implícito en la serie de 22,82 B
para 2025 con 21,4 %). Esto reproduce exactamente el patrón que el pase de automotive registró.

**Regla que esta KB mantiene**: en una propuesta, **citar adopción, no tamaño**. "Seis RTO/ISO
recibieron órdenes de *show cause* sobre grandes cargas", "Horizon Europe asigna 30 M€ en 2026 a
modelos de IA de red" y "Singapur apunta a medición avanzada nacional en 2026" son hechos
verificables con fuente. "El mercado vale X" no lo es, y un cliente del sector lo sabe.

⚠️ **Contradicción regional directa entre fuentes**: Coherent Market Insights afirma que
**Norteamérica domina con 38,6 % de cuota en 2026**; openPR titula que **Asia-Pacífico lidera la
adopción**. Ambas no pueden ser la misma métrica. Probablemente una mide ingresos de vendors y la
otra ritmo de despliegue — pero ninguna lo aclara. **No usar ninguna de las dos como afirmación de
liderazgo regional.**


### Actualización del quinto pase: la dispersión ahora es de 5,5× en el mismo año

Dos consultoras, el mismo segmento (**IA agéntica en energía y utilities**), el mismo año:

| Fuente | 2026 | Horizonte | CAGR | Nota |
|--------|------|-----------|------|------|
| Fact.MR | **4,8 B USD** | 36,2 B USD (2036) | — | Atribuye el **34 %** de la demanda a operación de red |
| Mordor Intelligence | **0,87 B USD** | 4,11 B USD (2031) | 36,35 % | — |

**5,5× de diferencia para 2026.** Es una ratificación más fuerte de la regla que esta KB ya aplica:
**citar adopción, no tamaño**. La cifra de adopción utilizable es la de la AIE en el bloque APAC
(23 % tiempo real / 54 % planificación / ~70 % mantenimiento).

**Dos datos de adopción que sí son accionables, y ambos son advertencias:**

- **Sólo la mitad de las utilities que han adoptado IA reportan ROI positivo** (análisis de un
  integrador global, 2026). Es el dato que hay que poner encima de la mesa en una primera reunión:
  la conversación no es "si IA", es "por qué la mitad no lo recupera".
- **El 54 % de los encuestados del sector energético señala la incertidumbre regulatoria y de
  cumplimiento como su principal preocupación** para desplegar IA agéntica (encuesta de una auditora,
  2026). Encaja con la posición de esta KB: lo que se vende es integración y trazabilidad, no
  autonomía.

**Movimiento de incumbentes (para saber contra qué se compite):** en mayo de 2026 Siemens añadió
capacidades agénticas a su plataforma **Gridscale X** para planificación de transmisión. Y los
*foundation models* de red que el cuarto pase encontró en GitHub (`gridfm-datakit`,
`gridfm-graphkit`) tienen ahora respaldo institucional identificado: se reporta que **IBM, LF Energy,
Hydro-Québec y ETH Zúrich** desarrollan **GridFMs**. Eso explica la relación fork/star anómala que el
cuarto pase midió en `gridfm-graphkit` (0,36): no es moda, es un consorcio.

**Reserva:** todas las cifras de este bloque son de consultora o de nota de prensa. Ninguna se ha
podido confirmar contra fuente primaria desde este entorno.

## Nota de método sobre las fuentes de este documento

Lo verificado de **primera mano** en esta KB es exclusivamente lo que vive en GitHub: licencias,
stars, forks y fecha de último push, consultadas vía `gh api search/repositories` y, para licencias,
leyendo el archivo crudo en `raw.githubusercontent.com`.

Todo lo regulatorio, de mercado y de prensa es **secundario**, obtenido de *snippets* de búsqueda.
En este pase, el fetch directo de páginas falló por completo: `arxiv.org`, `www.oati.com` y
`www.twobirds.com` no resuelven, y `eur-lex.europa.eu`, `www.utilitydive.com`, `huggingface.co` y
`gitee.com` devuelven **HTTP 403 del proxy**. En consecuencia:

- **No citar una cifra de mercado de este documento en una propuesta** sin re-verificarla contra la
  fuente original fuera de esta KB.
- Las **fechas regulatorias** (AI Act, FERC, Lei 15.504) tienen concordancia entre varias fuentes
  secundarias independientes, lo que es razonable para orientar una estrategia y **no** para firmar
  un plan de cumplimiento.
- Los **nombres propios de despliegues** (CAISO/OATI, TEPCO, State Grid, Apraava) provienen de
  prensa y páginas de vendor. Verificar antes de usarlos como referencia ante un cliente.

---
*Investigado 2026-11-20 (cuatro pases). Cifras de consultoras: re-verificar antes de usar en propuesta.*


