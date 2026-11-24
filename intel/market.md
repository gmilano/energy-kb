---
industry: energy
region: Global
updated: 2026-11-24
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

**Actualización del sexto pase (2026-11-20) — la postura regulatoria norteamericana ya tiene una frase operativa**

- **La NERC dice que la IA debe asistir la decisión, no actuar de forma autónoma.** Es el hallazgo
  regulatorio más accionable de este pase para North America. Convierte la tesis *human-in-the-loop*
  de esta KB (pase 3: sin `operatorfabric-core` una demo agéntica de red no es desplegable) en un
  **requisito de cumplimiento** y no en una preferencia de arquitectura. En una propuesta a una
  utility de EE. UU., la capa de aceptación humana trazable no se negocia: se presupuesta.
- **Reparto de competencias, para saber a quién se le responde**: FERC y NERC fijan los estándares de
  fiabilidad y podrían extender ese papel a activos de red habilitados por IA; el DOE lleva la
  iniciativa en IA del sector energético; el NIST aporta el marco. Deloitte añade recomendaciones de
  gobernanza, ciberseguridad y **recuperación de costes** con supervisión humana — ese último punto
  es el que decide si un proyecto de IA entra en la base tarifaria.
- **Legislación estatal: existe una serie documental para citarla.** El NCSL publica *AI in Energy*
  en partes (Parte 2: *Challenges*; Parte 3: *Legislative Landscape*). Los pases anteriores
  registraron "al menos cinco estados con legislación pendiente" sin fuente localizable; ahora la
  serie del NCSL es el sitio donde verificarlo antes de afirmarlo ante un cliente.
- **Tensión federal-estatal, y es un riesgo de proyecto real**: borradores iniciales de la OBBBA
  incluían una **moratoria federal sobre normas estatales de IA** de al menos diez años; su estado
  lo recoge el informe del NCSL. En paralelo, un *Ratepayer Protection Pledge* de la Casa Blanca
  (marzo de 2026) y las reglas estatales de utilities inciden ambos sobre **quién paga la red que
  consume el datacenter**. Para un encargo plurianual, la jurisdicción aplicable puede cambiar a
  mitad del contrato: conviene cláusula de revisión regulatoria.
- **Consolidación del lado del cliente**: la fusión **NextEra–Dominion por 67.000 M USD** estaba bajo
  revisión regulatoria de 180 días en Virginia, Carolina del Norte y Carolina del Sur. Una fusión de
  ese tamaño congela decisiones de compra de software durante la revisión y las libera en bloque
  después: es calendario comercial, no sólo noticia sectorial.
- **El dinero que mueve la demanda**: Microsoft, Amazon, Alphabet y Meta planeaban más de
  **600.000 M USD** de inversión en IA en 2026. Deloitte proyecta que las empresas de petróleo y gas
  dedicarán **la mitad de su gasto en TI a IA y IA generativa para 2029**.
- **Programa federal nuevo para esta KB**: la propia hoja de ruta europea cita la **"Genesis mission"**
  de EE. UU. como el esfuerzo estatal comparable al chino. No aparecía en ningún pase anterior; queda
  anotada para verificación primaria en el próximo.
- ⚠️ **Lo que la adopción real dice, y matiza todo lo anterior**: las encuestas describen un uso
  desigual — los casos **analíticos** se adoptan, la **automatización en campo** no, y las utilities
  se declaran cautelosas con los usos operativos avanzados hasta estabilizar sus cimientos de datos.
  S&P Global reporta inversión agresiva **con retornos mixtos** y dificultad para incrustar contexto
  de dominio en los flujos de IA. **Ese es exactamente el trabajo que se vende**: no el modelo, la
  ingeniería de contexto de dominio a su alrededor.

#### Actualización del séptimo pase (2026-11-20): la regulación puso fecha, y eso crea una ventana con vencimiento

Lo que cambia respecto al sexto pase es que las obligaciones dejaron de ser orientaciones y pasaron a
tener **plazo**. Eso convierte el trabajo de cumplimiento en demanda datable.

| Hecho | Fecha | Por qué es oportunidad |
|-------|-------|------------------------|
| La **FERC** emitió órdenes de *show cause* bajo la sección 206 de la Federal Power Act a los seis operadores regionales (PJM, MISO, SPP, CAISO, ISO-NE, NYISO) | **18 jun 2026** | Cada RTO debe justificar o reformar **cómo se conectan las cargas grandes**. Seis procesos regulatorios simultáneos, cada uno con necesidad de estudio técnico |
| La FERC ordenó a la **NERC** crear estándares de fiabilidad **exigibles** para datacenters | plazo **31 dic 2026** | Un estándar exigible con fecha es un programa de cumplimiento con presupuesto |
| La NERC emitió una **alerta de Nivel 3** — la tercera en sus 58 años de historia | **may 2026** | Señal de severidad: la fiabilidad dejó de ser un tema de planificación |
| Guía **CISA / NSA** para infraestructura crítica: zero trust, defensa en profundidad, **mínimo privilegio** | **may 2026** | Es la base normativa del patrón *el agente propone, el humano acepta* |
| **DOE** seleccionó 31 proyectos en 26 estados vía el programa **SPARK** | **sep 2026** | Financiación pública ya asignada, con socios ejecutores por definir |

**El número que dimensiona el mercado, y que no es de una consultora:** las *investor-owned utilities*
tienen **capex planificado de al menos 1,4 billones de USD hasta 2030** (reporte de abril de 2026),
más de **21 % por encima** del plan del año anterior, y **más de 30** de esas utilities citan
datacenters como principal motor de crecimiento. En PJM —que incluye el corredor de datacenters del
norte de Virginia— hay **95 solicitudes de ajuste de carga grande por ~54 GW** acumuladas hasta
noviembre de 2025.

**Dónde está el trabajo proponible, en orden de cercanía al dinero:**

1. **Analítica de cola de interconexión y cargas grandes.** Ya es la *Receta 21*. Las órdenes de la
   FERC la convierten en obligación de seis operadores a la vez. Precedente citable: **AWS con Duke
   Energy** lanzó *Agentic Grid Planning*, con agentes que reducen la preparación de datos de los
   estudios de interconexión **de semanas a horas**, con los ingenieros tomando la decisión final.
   Ese es exactamente el patrón *asiste, no decide* — y lo validó un hiperescalador con una utility.
2. **Programa de cumplimiento NERC para datacenters**, contra el plazo del 31 de diciembre de 2026.
3. **Curtailment y flexibilidad de carga como producto de red** (*Receta 4*): las órdenes de la FERC
   mencionan explícitamente cómo se curtailan las cargas grandes cuando la red está estresada y que
   los datacenters paguen el **100 %** de las mejoras de red que causan.

⚠️ **Límite jurisdiccional que cambia la propuesta:** las órdenes de la FERC **no cubren ERCOT**, la
red principal de Texas, que está en gran medida fuera de su jurisdicción. Una propuesta para un
cliente tejano no puede apoyarse en este argumento regulatorio; hay que reconstruirlo sobre las reglas
de ERCOT. No proponer lo mismo en Houston que en Richmond.


#### Actualización del octavo pase (2026-11-20): de la orden regulatoria a la factura, y quién la paga

Lo que el octavo pase añade a las órdenes de la FERC ya registradas es **la pelea distributiva que
viene detrás**, que es la que un cliente de utility tiene hoy en la agenda:

- **Lo que las órdenes de la FERC explícitamente no resolvieron**: no abordan la **escasez de
  capacidad de generación** y no aprueban ningún datacenter concreto. Son reforma de **tarifa de
  conexión**, no de oferta. Una propuesta que prometa "resolver la interconexión" sobre este
  argumento se queda corta en la mitad del problema.
- **El servicio minorista es competencia estatal.** Las comisiones estatales aprueban las tarifas
  minoristas con las que una utility sirve a un datacenter, y **varios estados están escribiendo sus
  propias tarifas de carga grande**. Consecuencia directa: *no hay una propuesta nacional de EE. UU.*
  — hay tantas como comisiones estatales. Es el mismo límite jurisdiccional que ya se registró para
  ERCOT, generalizado.
- **Proyecto de ley federal pendiente**: la *Bipartisan American Affordability and Jobs Act of 2026*
  contendría protecciones obligatorias al contribuyente; su §2107 instruiría a la FERC a que las
  utilities cobren a los datacenters la transmisión a **coste incorporado e incremental**. Brookings
  señala que **con la ley actual la FERC no puede imponer esas medidas**. ⚠️ Pendiente: no citar como
  derecho vigente.
- **Investigación de Harvard** sostiene que las utilities ofrecen **contratos especiales secretos** a
  datacenters y aprovechan huecos entre regulación federal y estatal para desplazar costes a la
  factura del consumidor común. Es el riesgo reputacional del cliente: una propuesta que incluya
  **trazabilidad y auditabilidad de la asignación de costes** se vende sola en ese contexto.

**Dato de adopción que conviene llevar a una reunión** (National Grid Partners, *2026 Utility
Innovation Survey*): la **fiabilidad de red superó al net zero** como preocupación principal del
sector —del 43 % al **73 %** de los líderes que la ponen en su top 3—; el **74 %** dice que el
crecimiento de carga por datacenters de IA ya afecta la fiabilidad; y el **78 %** declara estar
**desplegando u operacionalizando al menos una aplicación de IA** para gestionar la demanda de
interconexión. Ese 78 % es el número que convierte esta KB en oferta: el comprador ya decidió.

**Precedente citable nuevo:** **Emerald AI** (del portafolio de National Grid Partners) corrió un
piloto en el Reino Unido con **National Grid y NVIDIA** en el que software de IA recortó el consumo
de un datacenter durante estrés de red simulado **en más de un tercio y en menos de un minuto**. Es
el caso de *flexibilidad de carga como producto de red* (*Receta 4*) con nombres propios.

⚠️ **Contrapeso de IDC que conviene decir antes de que lo diga el cliente**: según Gaia Gallotti, la
barrera para escalar IA agéntica en operaciones centrales de energía **no es la tecnología sino el
entorno de datos**, más la escasez de perfiles y una cultura sectorial cautelosa. Eso reordena la
propuesta: **la primera fase es ingeniería de datos**, y conviene venderla como tal en lugar de
prometer agentes en producción en el trimestre uno.


#### Noveno pase (2026-11-20) — el vacío regulatorio es la oportunidad, y la oferta abierta contra el plazo es cero

**El dato más vendible de la región: hay un vacío regulatorio declarado y un plazo encima.**

- **Ningún regulador estatal ha abordado la IA operativa de utilities.** Según el análisis de
  **Foley Hoag** (septiembre de 2026), al **agosto de 2026 ninguna comisión estatal de servicios
  públicos** había tratado específicamente la IA *operativa* de una utility. La **Arizona
  Corporation Commission** es la única que abrió un examen formal y está recabando datos de uso de
  IA de las utilities. La fuente lo llama literalmente un **vacío regulatorio**.
- **Y a la vez hay fecha límite.** Los estándares de **carga computacional de NERC** están
  previstos para **diciembre de 2026** (guía de NewGen Strategies & Solutions). NERC también estaría
  desarrollando estándares de IA en operación del sistema de potencia, con foco en ciberseguridad y
  **supervisión humana**.
- **FERC ya actuó por la vía de la carga, no de la IA**: órdenes de co-ubicación en PJM y órdenes de
  *show cause* sobre grandes cargas a los RTO/ISO.
- **Orden ejecutiva EO 14409 (junio de 2026)**: instruye a las agencias a atender riesgos
  habilitados por IA sobre infraestructura crítica (citada por Foley Hoag).
- **NIST** desarrolla un perfil de infraestructura crítica para su **AI RMF**, con energía como foco
  primario.
- **Estados y Congreso (NCSL)**: al menos **20 estados** con proyectos pendientes de ciberseguridad
  e infraestructura crítica; propuesta de **Colorado** que ata incentivos fiscales a datacenters a
  **certificaciones de eficiencia**; en el Congreso se discutió una **moratoria de 10 años** a las
  normas estatales y locales de IA.
- **Nueva York (NY PSC)**: orden del **17 de septiembre de 2026** con presentaciones debidas el
  **16 de noviembre de 2026**.
- **Dinero público al modelo de red**: el DOE financia **GridFM 2.0 con 11,5 M USD** para modelos de
  IA de planificación de red (vía Coherent Market Insights), y Avangrid amplía su uso de IA.

**La oportunidad, dicha con precisión.** El cruce de las dos primeras viñetas es el servicio: el
cliente tiene que demostrar cumplimiento ante un estándar que llega en diciembre de 2026, y **no
hay regulador que le haya dicho cómo**. Este pase midió además que **la oferta abierta contra ese
plazo es cero**: `"NERC CIP"` devuelve 573 repos y **ninguno es del sector** (lo único adyacente es
`argonne-citadel/grid-stix`, GPL-3.0, 2 ★). El expediente de cumplimiento es **trabajo de
consultoría facturable, no un repo que forkear** — exactamente lo que sostiene la *Receta 29*.

**Participación de mercado, con la dispersión de siempre:** North America ≈ **36 %** (openPR) y
**38,6 % en 2026** (Coherent Market Insights). Dos cifras para la misma región y el mismo año: citar
adopción, no tamaño (T8).

⚠️ **Precisión que conviene no perder:** el proyecto **GridFM 2.0 del DOE** y la organización
GitHub [`gridfm/*`](https://github.com/gridfm) (Apache-2.0, ya catalogada) **no se verificaron como
la misma cosa** en este pase. Son adyacentes por nombre y por tema; no afirmar la relación en una
propuesta sin comprobarla. Y del lado abierto hay un límite real: `gridfm-graphkit` **no publica
checkpoint preentrenado** — se entrena, no se descarga.


### Actualización del décimo pase (2026-11-20) — North America

**Hallazgo de oferta que cambia el posicionamiento en esta región.** Nueve pases construyeron la
tesis T2 ("los operadores de red se volvieron proveedores de open source") sobre casos **europeos**:
RTE (`Grid2Op`), Alliander (`power-grid-model`, `openstef`, `s4casting`), la familia LF Energy. La
consecuencia implícita era que el stack abierto de la energía es de origen EMEA y, por licencia,
**MPL-2.0** — copyleft por archivo.

**Norteamérica tiene su propia capa institucional y es más permisiva**: `epri-dev` (**59 repos**,
dominante **BSD-3-Clause**), `GridProtectionAlliance` (**66 repos**, dominante **MIT**, los diez
principales con push de noviembre de 2026) y el portafolio energético de `sandialabs` (**30 repos**,
BSD-3/MIT bajo un preámbulo de contrato DOE). Son ~125 repos que esta KB tenía catalogados con tres.

**Lo que habilita en una propuesta norteamericana**, y es una ventaja comercial concreta: se puede
ofrecer una base de **marca blanca** sin la obligación de MPL de liberar el motor modificado. Para un
cliente de utility que quiere producto propio, **BSD-3 de EPRI/Sandia y MIT de GPA son mejores
términos que MPL-2.0 de LF Energy.** Ver `repos/foundations.md` y **T47**.

**Contexto regulatorio añadido (fuentes secundarias, concordantes):**

- **Vacío regulatorio formal, con una excepción nombrada.** Según análisis de Foley Hoag, la
  **Arizona Corporation Commission es la única comisión estatal** que ha abierto un examen formal
  sobre el despliegue de IA en el sector eléctrico. El resto es ausencia de guía, no prohibición —
  lo que convierte el **expediente de justificación** en el entregable, no el modelo.
- **EO 14409 (junio de 2026)** instruye a las agencias a reforzar la infraestructura frente a
  riesgos cibernéticos habilitados por IA. Se suma al plazo de **diciembre de 2026** de los
  estándares de carga computacional de NERC que esta KB ya rastrea (Receta 29).
- **El DOE anunció ~11,5 M USD** para desarrollar **foundation models de IA para planificación de
  redes eléctricas**. Es financiación pública dirigida exactamente a la categoría que esta KB
  catalogó en el cuarto pase (`PowerFM`, `gridfm-*`) y clasificó como vía de **evaluación**, no de
  producción. Un cliente puede ahora apuntar a dinero público concreto para ese piloto.
- **Cuota de mercado**: las consultoras sitúan a Norteamérica en **~38,6 % del mercado global de IA
  en energía en 2026**. Como todas las cifras de este documento, es estimación de consultora: útil
  para dimensionar relativamente, no para firmar.

**Oportunidad nueva — "el lado del activo de campo está vacío".** Este pase midió con ocho consultas
que las cuatro categorías que una utility norteamericana compra primero **no tienen base open source
mantenida**: mitigación de riesgo de incendio/PSPS (**cero** repos del sector en tres ángulos de
consulta), salud de transformador por DGA (lo mejor: **MIT, 18 ★, 2022**), capacidad de alojamiento
de DER (**MIT, 7 ★, 2022**) e inspección de línea por visión (YOLO académicos de 34-37 ★, el de
145 ★ **sin licencia**). Es el perfil de demanda alta con oferta inexistente: **trabajo a medida y
por eso facturable**, y hay que presupuestarlo como desarrollo, nunca como integración. Ver
`repos/trending.md` (pase 10, Gap 3) y **T48**.



### Actualización del undécimo pase (2026-11-20) — North America

**La regulación federal nombró la categoría, y la oferta abierta que la implementa es de un TSO
noruego bajo MIT.** Entre las prioridades críticas que FERC publicó en **enero de 2026** figura, con
esas palabras, *"advanced demand response, **dynamic line ratings**, and emerging cybersecurity
technologies at the operational level"*. Esta KB había abierto el frente del "activo de campo" en el
pase 10 con ocho consultas y cuatro ceros — **y no había buscado DLR**. Existe:
[`statnett/linerate`](https://github.com/statnett/linerate) (MIT, CIGRE TB 601 + TB 207 + IEEE 738,
push 2026-11-20).

**Oportunidad concreta:** una oferta de DLR en la que las **ecuaciones no se escriben** —están
implementadas, trazables y referidas a la página del estándar— y lo facturable es telemetría
meteorológica, integración con el EMS y validación. Se puede defender ante un cliente citando a la
vez el estándar (CIGRE TB 601) y la prioridad del regulador (FERC, enero 2026).

**El contexto de demanda, actualizado con los movimientos de 2026:**

- **FERC, 18 de junio de 2026:** órdenes de *show cause* a los **seis** operadores regionales (PJM,
  MISO, SPP, CAISO, ISO-NE, NYISO), con 60 días para justificar o reformar las tarifas de conexión de
  grandes consumidores y 30 días para informar cómo garantizarán generación suficiente. ⚠️ **No crea
  una regla nacional de interconexión**: varias fuentes secundarias lo presentaron como regla final y
  eso es inexacto — fueron órdenes de *show cause*.
- **Detrás del medidor:** ~**48 GW** de capacidad propuesta de centro de datos con generación
  *behind-the-meter* a principios de 2026, frente a menos de 2 GW a finales de 2024. El límite de
  *netting* de PJM se presentó en febrero de 2026 y FERC lo aceptó en junio.
- **Coste y riesgo tarifario:** los centros de datos pagan su interconexión; el reparto del coste de
  transmisión sigue abierto. Un informe de la *Electricity Law Initiative* de Harvard Law sostiene que
  hay contratos especiales opacos que trasladan coste a la factura doméstica. Los reguladores
  estatales mantienen la tarifa minorista y varios estados están escribiendo **clases tarifarias de
  gran carga** propias.
- **Prioridad declarada por las *utilities*:** una encuesta de National Grid Partners sitúa la
  fiabilidad entre las tres primeras prioridades para el **73 %** de los encuestados, frente al 43 %
  en 2025. Y el **54 %** señala la **incertidumbre regulatoria** como su principal preocupación para
  desplegar IA agéntica.
- **Despliegue agéntico con cifra citable:** en **Duke Energy**, agentes de IA redujeron la
  preparación de datos para estudios de interconexión *de semanas a horas*, **con los ingenieros
  tomando todas las decisiones de ingeniería finales**. Esa última cláusula es la que hace el caso
  proponible en un sector regulado: es el patrón "humano autoriza" que el pase 9 ya identificó.
- Lanzamientos 2026 del lado vendor: **GE Vernova GridOS for Transmission** y **Delta Energy QORTEX**.

⚠️ **Dispersión de mercado, otra vez:** para IA agéntica en energía y *utilities* en 2026 las cifras
van de **~0,87 B USD** (Mordor) a **4,8 B USD** (Fact.MR) — un factor **5,5×** en el mismo año.
Consistente con la nota de método de este documento: **citar adopción y mandato regulatorio, no
tamaño de mercado.** Fact.MR sí aporta un reparto utilizable: **operación de red = 34 %** de la
demanda.

### Actualización del duodécimo pase (2026-11-20) — North America

**El dato regulatorio del año, con fecha y con instrumento: el 18 de junio de 2026 la FERC emitió
órdenes de *show cause* bajo la Sección 206 de la Federal Power Act a los seis operadores regionales
—PJM, MISO, SPP, CAISO, ISO-NE y NYISO— sobre cómo se conectan a la red las cargas grandes, es decir
los datacenter de IA.**

Qué exige y qué queda abierto:

- **Plazos: las fuentes se contradicen y hay que tratarlo como tal.** Una dice **60 días** para
  justificar o reformar las tarifas que rigen la conexión de datacenter, y **30 días** para informar
  de cómo garantizarán generación suficiente. Otra describe un único plazo de 30 días. **Citar el
  instrumento (órdenes del 18 de junio de 2026, §206 FPA), no el plazo**, mientras no se consulte el
  documento primario.
- **Asignación de costes: hay consenso en lo básico.** El datacenter paga **íntegramente** las mejoras
  de interconexión directamente atribuibles a su propia conexión, en vez de repartirlas entre la base
  de clientes. **Lo que sigue abierto** —y es donde se van a pelear los casos— es el reparto de las
  mejoras de *transmisión* entre el datacenter y los clientes existentes.
- **No es una regla nacional.** Las órdenes **no cubren ERCOT** (Texas), que queda en su mayor parte
  fuera de la jurisdicción de la FERC. Cualquier propuesta que hable de "regulación federal de cargas
  grandes en EEUU" tiene que excluir Texas explícitamente.
- **Antecedente de la cadena de mando:** el procedimiento arranca de una instrucción del Secretario
  de Energía Chris Wright a la FERC en **octubre de 2025** para que considerase acelerar la
  interconexión de cargas grandes.
- **Fiabilidad, con fecha límite dura:** en **julio de 2026** la FERC ordenó a la **NERC** crear
  estándares de fiabilidad **exigibles** para datacenter antes del **31 de diciembre de 2026**.
  (Fuente de menor autoridad; verificar contra NERC.) Esta fecha ya dirigía la **Receta 29** y queda
  reconfirmada.
- **Texas por vía legislativa, no regulatoria:** la **SB6** obliga a las cargas grandes a **recortar
  consumo durante emergencias de red**. En un modelo de ERCOT citado en el análisis, la respuesta de
  demanda **eliminó el deslastre forzoso en todos los escenarios probados**, con **menos del 5 % de
  la demanda del datacenter** a lo largo de **86 horas**. Es la cifra más útil del pase para vender
  flexibilidad: el coste de la flexibilidad necesaria es pequeño y acotado.
- **Capa estatal:** las comisiones estatales aprueban las tarifas minoristas con las que las
  utilities sirven al datacenter, y **varios estados ya están escribiendo tarifas de carga grande con
  clase de tarifa específica para hiperescala**. Es donde se decide el caso de negocio real, cliente
  por cliente.

**Oportunidad para Globant, concreta y con calendario:** los procedimientos contenciosos que siguen a
las órdenes tienen intervinientes con intereses opuestos (hiperescalares, utilities, defensores del
cliente, reguladores estatales) y **todos necesitan análisis cuantitativo de cola de interconexión y
de adecuación de generación** en plazos de 30–60 días. Eso es la **Receta 21** (analítica de cola de
interconexión) y la **Receta 29** (cumplimiento NERC), y la ventana de la segunda **se cierra el 31
de diciembre de 2026**.

**Lado open source de la región en este pase:** sin novedades institucionales. El barrido del pase 10
(`epri-dev`, `GridProtectionAlliance`, `sandialabs`) sigue siendo la cobertura buena, y el único
añadido es `ahmedelshazly27/opendss-mcp-server` (MIT, 4 ★), de autor individual, sobre OpenDSS de
EPRI. Se busca y no aparece **código abierto de ORNL para `Grid-Orch`** (arXiv 2605.12728), que
sería la pieza MCP más completa de distribución si se liberase: **36 herramientas en once
categorías** sobre OpenDSS, con dashboard QSTS. Hoy es un paper, no un cimiento.

#### Actualización del decimotercer pase (2026-11-20)

**Estado de ejecución de las órdenes de FERC de junio de 2026** — la KB ya registraba las órdenes;
lo nuevo es que **han empezado a producir expedientes concretos**, que es lo que crea trabajo:

- **MISO presentó revisiones tarifarias ante FERC el 28 de agosto de 2026** (expediente
  **ER26-3650**) para fijar requisitos de fiabilidad en la interconexión de **cargas grandes**.
  Un expediente abierto con número es un punto de entrada verificable, no una tendencia.
- Las órdenes exigieron a cada operador **justificar o reformar su tarifa de carga grande en 60
  días** y presentar **informe de adecuación de generación en 30 días**.
- El reparto de costes que se consolida: **el datacenter paga íntegro el refuerzo de red atribuible
  a su propia interconexión**. Eso convierte el *estudio de interconexión* en una pieza de
  negociación económica, no sólo técnica.
- **ERCOT queda en gran medida fuera de la jurisdicción de FERC**: Texas —uno de los mercados de
  datacenter más activos— **no** se rige por estas órdenes. Un encargo de EE. UU. no es un encargo
  homogéneo: hay que preguntar el mercado antes de prometer el marco.
- FERC pidió además considerar **"tecnologías alternativas de transmisión"** y mayor acomodo a la
  generación **detrás del medidor** (*behind-the-meter*).

⚠️ *Fuentes secundarias (prensa sectorial y blogs jurídicos). El expediente ER26-3650 y los textos
de las órdenes no se han leído en la fuente primaria de FERC. Verificar antes de citar un número
ante cliente.*

**Consecuencia directa de la corrección de licencia de este pase, y es específicamente de North
America:** **OpenADR es el protocolo de referencia de respuesta a la demanda de esta región**, y
esta KB afirmaba que su versión 3.0 no tenía implementación abierta licenciada. Era falso
(T45 derogada). **La capa 3.0 está disponible y es permisiva** —`openleadr-rs` (Apache-2.0 OR MIT),
`ElaadNL/openadr3-client` (Apache-2.0) y `eclipse-volttron/volttron-openadr-ven` (Apache-2.0, de
origen **North America**, PNNL)— de modo que una propuesta de agregador de respuesta a la demanda en
esta región **ya no tiene que ofrecerse sobre 2.0b ni presupuestar una reimplementación**. Es el
cambio de posición comercial más concreto que produce este pase.

### Actualización del decimocuarto pase (2026-11-21) — North America

**El hallazgo de la región es que el regulador escribió la regla de arquitectura que esta KB ya
exigía en sus recetas.** La guía de **NERC** sobre IA en el sistema eléctrico establece que la IA
debe funcionar como **herramienta de apoyo a la decisión (*decision-support*), no como controlador
autónomo**. Esa frase es exactamente la restricción que la Receta 46 de esta KB expresa como *"el
texto de razonamiento nunca llega al actuador"*.

Por qué importa comercialmente, y es un cambio de discurso: hasta este pase el *human-in-the-loop*
se vendía como **buena práctica de ingeniería**. Con la guía de NERC encima de la mesa pasa a ser
**la lectura del regulador de referencia de la región**. El argumento deja de ser "conviene" y pasa
a ser "es lo que espera NERC". Un diseño agéntico que escriba en el lazo de control en NA ya no es
sólo arriesgado: es **contrario a la guía publicada**, y conviene decirlo así en un SOW.

#### El contador de actividad regulatoria que NA no tenía

Los pases anteriores registraron que NA **no tiene contador de expedientes** y que por eso el
trabajo en la región es *advisory-shaped*. Eso se corrige en parte: la **NCSL** (National Conference
of State Legislatures) publica una serie **"AI in Energy"** (abril de 2026) cuya **Parte 3 es el
panorama legislativo** y la **Parte 2 los desafíos**. Es un **seguimiento estado por estado** de la
legislación de IA aplicada a energía, que es precisamente el instrumento que faltaba: en NA la
actividad regulatoria **no está en un registro federal, está en 50 legislaturas estatales**, y hay
quien las cuenta.

- Documentos localizados: `AI-in-Energy-Part-2-Challenges-web.pdf` y
  `AI-in-Energy-Part-3-Legislative-Landscape-web.pdf` (dominio `documents.ncsl.org`).
- La serie recoge además la **moratoria federal propuesta** sobre reglas estatales de IA que figuró
  en borradores iniciales de la ley presupuestaria de 2025, y que habría limitado la autoridad
  estatal y local **al menos 10 años**. No se aprobó en esa forma: **no presentarla como vigente.**
- ⚠️ **Snippet-sourced.** Ambos PDF se identifican por título y nombre de archivo; no se han leído
  desde este entorno. Ver la nota de instrumento del pase.

#### La cifra física citable de la región

**EIA** (consumo eléctrico total de EE.UU., miles de millones de kWh):

| Año | Consumo | Δ |
|-----|---------|---|
| 2025 | 4.195 | — |
| 2026 | 4.268 | +1,7 % |
| 2027 | 4.391 | +2,9 % |

Es una **proyección oficial, no una estimación de consultora**, y por eso es la cifra preferible
para abrir una conversación en NA — del mismo modo que esta KB prefiere citar adopción antes que
tamaño de mercado. Los datacenters de IA son el principal motor del incremento.

**Morningstar DBRS** añade el ángulo que le interesa a una utility: *la adopción de IA es nueva para
las autoridades regulatorias*, que ahora deben **evaluar la inversión en IA que las utilities
proponen**, no sólo revisar el desembolso de capex. Eso describe un entregable concreto y vendible:
**el expediente que justifica una inversión en IA ante el regulador tarifario** — no el modelo, el
expediente.


#### Actualización del decimoquinto pase (2026-11-21) — North America

**El hallazgo regulatorio es una distinción, y es la que decide la forma del encargo:** la FERC está
interviniendo la IA **por el lado de la carga**, no por el de la operación. Lo que ha hecho es
**ordenar a NERC que redacte reglas de fiabilidad para la integración de grandes cargas
computacionales** —centros de datos de IA y minería de criptoactivos— con **objetivo de cierre a
finales de 2026**; las propuestas en borrador salieron a comentario público en agosto y las
recomendaciones finales van a la FERC antes de fin de año. ⚠️ Fuentes secundarias (análisis
sectorial y blogs de cumplimiento); **no verificado contra documento primario de FERC o NERC desde
este entorno**.

> **La FERC no ha emitido guía específica sobre IA operativa de la utility.** Esa es la frase
> comercialmente relevante. Significa que en NA el trabajo de **agentes en operación sigue sin
> regulación propia**, y por tanto es **de forma asesora** —exactamente el mismo patrón que la KB
> hermana de automotive midió para NA (sin lista enumerada de alto riesgo y sin contador de
> expedientes). Lo que **sí** tiene fecha es la **interconexión de la carga grande**: ahí hay un
> plazo de 2026 y, con él, una ventana con vencimiento.

**El gancho de cumplimiento que necesitaba la receta 47.** Dos afirmaciones concurrentes, ambas
secundarias y ambas ⚠️ **sin verificar contra los documentos de NERC**:

- **NERC CIP asume un sistema de control operado por humanos** y **no aborda agentes autónomos**.
- Una herramienta de IA que toca un **BES Cyber System categorizado hereda las obligaciones de ese
  sistema**.

Si la segunda se sostiene, es el argumento de venta entero del expediente auditable: la pregunta del
cliente deja de ser "¿puedo usar IA?" y pasa a ser "¿qué obligaciones hereda lo que acabo de
conectar?", que es una pregunta de **alcance y evidencia** —el tipo de entregable que esta KB ya
tiene recetado. Verificar contra NERC primario es el **open item 15-R1**.

**Despliegues con nombre** (⚠️ todos de guía de práctica o material de proveedor, no de la utility):

- **Duke Energy** — planificación de red **agéntica** sobre AWS; se reporta que la preparación de
  datos para estudios de interconexión bajó **de semanas a horas** en 2026. La misma fuente advierte
  que sus cifras de reducción de cortes vienen de **automatización de red, no de IA**: no cruzar los
  dos números.
- **National Grid** — acuerdo de IA operativa con **Air Space Intelligence** para localización de
  DER, mapeo de cortes y despliegue de almacenamiento.

**La frontera de arquitectura, ahora también como guía de práctica de NA.** Los agentes **no entran
en la zona de control** —SCADA, EMS, funciones de control de ADMS, despacho DERMS, automatización de
subestación, PLC y sistemas de seguridad—: **sin herramienta, sin credencial y sin ruta de red**,
credenciales de sólo lectura por defecto y rutas de revocación explícitas. Tercera vía independiente
que llega a la misma frontera (ver `agents/trending.md`, pase 15).

**Primera oferta abierta permissiva de origen NA que engancha con el expediente CIP.** Hasta este
pase, la receta 47 no tenía **ninguna** pieza permisiva norteamericana:

- [`idaholab/CIEMAT`](https://github.com/idaholab/CIEMAT) — MIT, *Cyber-Informed Engineering
  Microgrid Analysis Tool*, **Idaho National Laboratory**.
- [`idaholab/CIEBAT`](https://github.com/idaholab/CIEBAT) — MIT, el equivalente para baterías.
- [`maxoliverbr/eia-api-ts`](https://github.com/maxoliverbr/eia-api-ts) — MIT, wrapper de la **EIA
  API v2** construido **para uso agéntico**: la pieza de acceso al dato público federal.
- [`mzy2240/ESA`](https://github.com/mzy2240/ESA) — Apache-2.0, automatiza PowerWorld desde Python.

*Cyber-Informed Engineering* es el marco con el que se argumenta ciberseguridad de OT ante el
regulador, y que venga de un laboratorio nacional con licencia MIT lo hace citable en una propuesta.

### Actualización del pase 16 (2026-11-24) — North America

**La normalización llega antes que la regulación, y escribe la restricción de arquitectura.**

El **NIST** desarrolla un **Trustworthy AI in Critical Infrastructure Profile** del AI RMF, dirigido
a operadores de infraestructura crítica, cuyas necesidades declaradas son **comportamiento
determinista, explicabilidad, degradación elegante y operación a prueba de fallos**. Hay una
*community of interest* abierta a comentarios. Para esta KB es la primera vez que la restricción que
sostiene desde el pase 1 aparece en **un borrador de organismo de normalización** y no en el análisis
de un consultor.
⚠️ **Estado del borrador no verificado** y **ninguna fuente lo vincula a la Genesis Mission**
(ítem 16-R1). Cobertura secundaria.

**El gancho comercial se desplaza.** La FERC **sigue sin emitir guía sobre IA operativa de utility**;
su actividad está en el lado de la demanda. Lo nuevo y fechado:

- **Junio de 2026: órdenes de *show cause* sobre grandes cargas a los seis RTO/ISO.** La FERC actúa
  sobre **cómo se conectan y se tarifan las cargas computacionales**, no sobre cómo se opera la red
  con IA.
- **Estándares de carga computacional de la NERC: vencimiento diciembre de 2026** — consistente con
  el «cierre a finales de 2026» que esta KB registró en el pase 15.
- **Deloitte** sostiene que la guía de la NERC trata la IA como **herramienta de apoyo a la decisión,
  y no como controlador autónomo**, con la supervisión humana en el centro. Cuarta confirmación
  analítica, ahora de una Big Four, de que **el producto vendible en NA es advisory-shaped**.
- **Legislación estatal (NCSL):** al menos **cinco estados** con proyectos de ley sobre IA y energía
  en la sesión de 2026. **Colorado y Virginia** proponen **atar incentivos fiscales de centros de
  datos a certificaciones de eficiencia energética** — es decir, convertir la eficiencia en
  **requisito documental**, que es trabajo de expediente.
- **Brookings:** un proyecto de permisos de 2026 instruiría a la FERC a cobrar a los clientes de
  centros de datos de IA **el coste incorporado y el coste incremental** del servicio de transmisión.

**Genesis Mission y los laboratorios nacionales como canal.** Más de **5.000 M USD** anunciados
(julio de 2026), con la **American Science and Security Platform** uniendo los **17 laboratorios
nacionales** del DOE, supercomputadores y datasets federales. **MOU NIST–DOE Office of Science de
agosto de 2026**; el NIST canaliza parte por sus **Centers for AI in Manufacturing and Critical
Infrastructure** (asociación público-privada con **MITRE**), e incluye un **AI Economic Security
Center** para acelerar **agentes de IA de detección y remediación de ciberamenazas**, con las **redes
eléctricas explícitamente en su alcance**.
⚠️ Una fuente observa que **el impacto del acuerdo sigue sin demostrarse**. Es un canal de
financiación y de credibilidad, no un cliente.

**Oportunidad concreta, por orden de madurez:**
1. **Expediente de conformidad contra el perfil NIST** (receta 55): los cuatro requisitos del perfil
   son auditables y el cliente no tiene cómo demostrarlos hoy. Se vende antes de que el perfil se
   publique, porque el borrador ya dice qué va a pedir.
2. **Expediente de carga computacional** para el plazo NERC de diciembre de 2026 y las órdenes de
   *show cause* de la FERC: es un trabajo de datos y documentación, no de control.
3. **Certificación de eficiencia de centro de datos** en Colorado y Virginia, atada a incentivo
   fiscal: tiene una contraparte que paga y una fecha.

⛔ **No citar `micro-ark.com`** (afirma que la FERC exige trazas de auditoría de IA «100 %
transparentes»): no verificable contra fuente primaria y contradictorio con el resto.

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

**Actualización del sexto pase (2026-11-20) — la UE pasó de principios a hoja de ruta sectorial, con fechas**

Este es el bloque regulatorio que más se mueve y el que más cuidado exige al citarlo (ver la nota de
verificación al final).

- **`Strategic Roadmap for Digitalisation and AI in the Energy Sector`, publicada el 3 de junio de
  2026.** Es una **comunicación de política, no legislación vinculante**, y esa distinción hay que
  decirla en la primera reunión. Señala cambio regulatorio significativo **hacia 2030** y se organiza
  en **tres pilares**:
  1. *Energy for AI* — cómo se alimenta la demanda de la IA.
  2. *Digitalisation and AI for the Energy System* — la IA aplicada a la operación del sistema.
  3. *Data for AI and the Energy System* — el acceso a datos, que es el cuello de botella real.
- **Encaje con el resto del aparato europeo**: se apoya en el *AI Continent Action Plan* y la *Apply
  AI Strategy*, y complementa el *Cloud and AI Development Act*.
- **Seguimiento legislativo con fecha**: el **17 de julio de 2026** se publicó una propuesta de
  **modificación del Reglamento del Mercado Eléctrico**. Aquí deja de ser declarativo: una
  modificación del EMR toca las reglas con las que opera un cliente TSO o DSO.
- **La línea que decide la arquitectura de un copiloto de red**: la Comisión **redactó guías de
  clasificación de sistemas de IA de alto riesgo conforme al artículo 6 del AI Act**. Si un asistente
  de operación de red entra en esa categoría, el *human-in-the-loop* deja de ser diseño y pasa a ser
  obligación — la misma conclusión que la guía de la NERC en North America, por vía legal distinta.
- **Financiación, con su tamaño real**: se reportan unos **75 M EUR** asignados a IA en energía, con
  apoyo de Horizon Europe. Es una cifra de programa, no de mercado: útil para encontrar consorcios y
  convocatorias, no para dimensionar un negocio.
- **Movimiento industrial organizado**: **catorce asociaciones industriales europeas** firmaron una
  declaración de intenciones, con un **acuerdo modelo previsto para la segunda mitad de 2026**. En
  paralelo, utilities y una empresa tecnológica lanzaron (junio de 2026) una **alianza de IA para
  descarbonizar los datacenters de la UE**. Son las puertas de entrada institucionales a un encargo
  europeo.
- **Por qué la adopción europea va lenta, en palabras de la propia Comisión**: la adopción sigue
  **desigual** por los **requisitos estrictos de seguridad de la infraestructura energética crítica**,
  la **gobernanza fragmentada** y el **acceso limitado a datos**. Las tres son restricciones de
  integración, no de modelo — es decir, son servicio.
- **El contrapunto que ya no es sólo técnico**: análisis de abril de 2026 advierten que la demanda de
  los datacenters amenaza los objetivos de descarbonización europeos. Y en versión de proveedor (hay
  que etiquetarla como tal): el CTO de Lenovo pronostica que **la energía superará al cómputo como
  restricción primaria de diseño** de la infraestructura de IA en EMEA en 2026.
- ⚠️ **Nota de verificación, sexto pase consecutivo con la misma limitación.** Todo lo anterior
  proviene de **fuentes secundarias** (análisis jurídicos, prensa sectorial, páginas vinculadas a la
  Comisión). El documento del Consejo **ST-10101-2026** existe y está referenciado, pero
  `data.consilium.europa.eu` **no resuelve desde este entorno** (igual que el intento previo a
  `conventuslaw.com`). **La verificación primaria del registro de la UE sigue siendo la restricción
  vinculante de esta KB.** Orientar estrategia con esto: sí. Citar un artículo o una fecha en un
  entregable contractual sin abrir el documento oficial: no.

#### Actualización del séptimo pase (2026-11-20): la Comisión puso cifras y fechas, y financia exactamente la capa que esta KB cataloga

El sexto pase registró la hoja de ruta de la Comisión Europea del 3 de junio de 2026 con sus tres
pilares y advirtió que no se pudo abrir el registro primario. El séptimo pase añade **el presupuesto y
el calendario**, que es lo que convierte una comunicación política en una oportunidad fechada. El
documento es **COM/2026/501**, presentado el **3 de junio de 2026** como parte del paquete de
soberanía tecnológica, con tres pilares: integrar los datacenters en el sistema energético, usar
digitalización e IA para optimizar la infraestructura, y mejorar el intercambio y disponibilidad de
datos energéticos europeos.

| Partida / hito | Cifra o fecha | Lectura para Globant |
|----------------|---------------|----------------------|
| Horizon Europe 2026-2027, soluciones avanzadas de red inteligente | **~100 M€** | Convocatorias con socio industrial requerido |
| Horizon Europe, aplicaciones de **IA en energía** | **~75 M€** | El encaje directo de esta KB |
| Dentro de esa partida: **foundation models para gestión y planificación de red** | **30 M€ (2026) + 20 M€ (2027)** | Financia la categoría que el pase 4 añadió (`gridfm`, `GridSFM`) |
| Soluciones digitales para renovables, edificios inteligentes y eficiencia | **~190 M€** | Encaje de las recetas de edificios y eficiencia |
| Comunidad de práctica **AI.grids** para modelos de IA de red | en lanzamiento | Foro donde hay que estar presente |
| Modelos de IA en **prueba de concepto** | **Q1 2027** | La ventana de preparación es **ahora** |
| Primeros modelos **operativos** | **fin de 2027** | Horizonte de proyecto plurianual |
| Contrato modelo para conexión de datacenters a la red | desde **mediados de 2026** | Instrumento contractual nuevo que alguien tiene que aplicar |
| **Foro anual de Digitalización Energética** | desde **2026** | Canal de posicionamiento |
| Declaración de intención inicial | **14 actores**, incl. **ENTSO-E**, **E.DSO** y **WindEurope** | Los decisores están identificados y son pocos |

**La cifra que la Comisión usa para justificar el gasto:** optimización de operación y mantenimiento
basada en IA podría ahorrar **hasta 94 000 M€ anuales para 2035** (≈110 000 M USD). ⚠️ Es una
**proyección de la Comisión**, no un resultado medido: citarla como lo que es.

**La consecuencia técnica que une esto con `repos/foundations.md`:** si la UE financia foundation
models de red con 50 M€ entre 2026 y 2027, esos modelos consumirán **CGMES** — el modelo de datos de
la red europea. El séptimo pase añadió once repos de la tubería CIM/CGMES, nueve de ellos permisivos
(Apache-2.0, BSD-3, MPL-2.0), con autoría de **Elia Group, Alliander, Statnett, PNNL y SOPTIM**.
**Quien controla la tubería de datos CGMES entra en estos proyectos; quien sólo tiene el modelo, no.**
Es la oportunidad EMEA más concreta de este pase.

⚠️ **Limitación de verificación, séptimo pase consecutivo:** el registro primario de la UE sigue
inaccesible desde este entorno. `eur-lex.europa.eu` **no resuelve** (`ENOTFOUND`), igual que
`data.consilium.europa.eu` en los pases 1-6. Todas las cifras de esta tabla provienen de **cobertura
secundaria** del mismo documento COM/2026/501 (despachos jurídicos y prensa sectorial). **No citar una
cifra presupuestaria ni una fecha de artículo en una propuesta sin abrir antes el documento oficial.**
Para que el próximo pase pueda cerrar esto, haría falta habilitar `eur-lex.europa.eu` en la política de
red de la sesión.


#### Actualización del octavo pase (2026-11-20): la hoja de ruta se vuelve instrumento, y el cuello de botella se cuantifica

- **Esquema europeo de calificación de datacenters, con umbral concreto.** El 21 de septiembre de
  2026 la Comisión propuso un esquema de *rating* para datacenters de **al menos 500 kW de potencia
  TI**, que calificaría eficiencia energética **y de agua**, estrés hídrico local, reutilización de
  calor residual y **cómo la instalación interactúa con la red eléctrica**. Las normas mínimas de
  desempeño están en **consulta hasta el 14 de diciembre de 2026** y la propuesta legislativa se
  planea para **2027**. ⚠️ Ese umbral de 500 kW es el dato operativo: define **qué clientes quedan
  dentro**, y la ventana de consulta abierta es una oportunidad de posicionamiento, no sólo de
  cumplimiento.
- **"Interacción con la red" como criterio calificable** es la novedad estratégica: convierte la
  flexibilidad de carga de un ahorro voluntario en un **atributo que se puntúa**. La *Receta 4* pasa
  de optimización a cumplimiento.
- **Acuerdos tripartitos de conexión a red** y un marco europeo de **intercambio transfronterizo
  simplificado de datos energéticos** son dos de las medidas clave de la hoja de ruta del 3 de junio
  de 2026 ya registrada (COM/2026/501). El segundo es el que habilita técnicamente el resto.
- **Financiación, con una cifra que amplía la ya registrada**: bajo **Horizon Europe** se habrían
  asignado alrededor de **75 M€ para tecnologías de IA en energía durante 2026 y 2027**. ⚠️ Esta KB
  tenía registrado 30 M€ (2026) + 20 M€ (2027) = 50 M€ para *foundation models* de gestión y
  planificación de red. Las dos cifras no se contradicen necesariamente —una es el subconjunto de
  *foundation models* y la otra el total de IA en energía— pero **ninguna está confirmada contra
  fuente primaria desde este entorno**. Citar el rango, no un número.
- **El cuello de botella, cuantificado**: más de **70 proyectos de datacenter europeos** fueron
  bloqueados, rechazados o fuertemente restringidos **en los primeros cuatro meses de 2026**,
  afectando una inversión estimada en **42.000 M USD**. En **Irlanda** los datacenters consumen ya
  en torno al **23 % de la electricidad** del país. **Energinet**, el operador danés, declaró en
  **marzo de 2026** una pausa temporal de nuevas solicitudes de conexión para vaciar el *backlog*.
- **Respuestas nacionales divergentes** (OCDE): Italia mejorando la planificación locacional, el
  Reino Unido reformando las colas de conexión, los Países Bajos usando **zonas de gestión de
  congestión**. Un regulador nacional exigiría a los datacenters nuevos instalar generación
  despachable o almacenamiento **en sitio**. ⚠️ La fuente no nombra el país en el extracto: verificar
  antes de usarlo en una propuesta concreta.
- **Posición competitiva, con sesgo declarado**: el *chief digital officer* de Schneider Electric
  sostiene que EE. UU. va claramente delante, seguido de China, con Europa rezagada y Medio Oriente
  creciendo más rápido. ⚠️ Schneider vende infraestructura: interés comercial en ese diagnóstico.

**Dónde está el trabajo proponible en EMEA, en orden de cercanía al dinero:**

1. **Expediente de *rating* de datacenter** contra el esquema de ≥500 kW: medición de eficiencia
   energética e hídrica, calor residual e **interacción con la red**. Es un entregable documental y
   analítico con plazo regulatorio, y hoy no tiene herramienta abierta de referencia.
2. **Analítica de cola de conexión para el modelo europeo**, que es donde el stack CIM/CGMES ya
   catalogado (`powsybl-core`, `entsoe/application-profiles-library`, `Talk2PowerSystem`) rinde de
   inmediato. El caso de Energinet demuestra que el *backlog* es el problema declarado del operador.
3. **Modelado de escenarios con datos nacionales ya publicados y permisivos**: `MAHTEP/TEMOA-Italy` y
   `TEMOA-Europe` (código MIT, datos CC-BY-4.0) eliminan el coste de construir el dataset del país
   en Italia y a escala europea.


#### Noveno pase (2026-11-20) — la fecha del AI Act para energía operativa se movió, y eso cambia el discurso comercial

**El hallazgo regulatorio más accionable del pase, y aplica a casi todo proyecto de IA energética
en EMEA.**

- **El *Digital Omnibus* corrió el plazo de alto riesgo.** Acuerdo político del **7 de mayo de
  2026**: la fecha de obligaciones para los sistemas de **alto riesgo del Anexo III** —que es donde
  cae **la mayor parte de la IA operativa de energía**— pasa del **2 de agosto de 2026** al
  **2 de diciembre de 2027** (Baker Botts).
- ⚠️ **Con una condición que hay que decir en la misma frase:** *hasta la adopción y publicación
  formales, las fechas originales siguen vigentes.* Es decir: **no es una prórroga que se pueda dar
  por firme**. El servicio correcto no es "relájense", es **preparar el expediente con la fecha
  original y capitalizar el margen si la prórroga se consolida**.
- **Hoja de Ruta Estratégica de Digitalización e IA en el Sector Energético**, publicada el
  **3 de junio de 2026**: es una **comunicación de política, no legislación vinculante**, y señala
  cambio regulatorio hacia 2030. Tres medidas con traducción directa a trabajo:
  **acuerdos tripartitos de conexión a red**, un **esquema europeo de calificación (*rating*) de
  datacenters**, y un **marco europeo de intercambio transfronterizo simplificado de datos
  energéticos**.
- **Otras obligaciones que ya están vigentes y se olvidan**: **NIS2** (la energía es servicio
  esencial) y **REMIT** (comercialización energética asistida por IA).
- **Reino Unido, fuera del régimen de la UE y con vía propia**: Ofgem publicó guía de IA ética en
  mayo de 2025 y **segunda edición en mayo de 2026**, con un **piloto de sandbox** previsto para
  **finales del otoño de 2026**. Es la jurisdicción donde hoy se puede probar con el regulador
  mirando.
- **Players recurrentes** en los informes de la región: Siemens y Siemens Energy, Schneider
  Electric, ABB, GE, Honeywell, IBM, Microsoft, Oracle, C3.ai, Vestas, EDF, Shell, National Grid.

⚠️ **Afirmación descartada en este pase.** Una fuente consultada atribuía a "Kelvin AI" una
**Serie D de 200 M £** y sostenía que las utilities polacas van **12-18 meses** por detrás de sus
pares de Europa occidental. **Ninguna de las dos tiene sustento verificable** en las fuentes
disponibles. No usar en material de cliente. Se registra para que un pase futuro no la reencuentre
y la crea nueva.

**Lectura de oferta que acompaña a la regulación:** la región sigue siendo donde está el código.
Este pase añadió, todo de origen EMEA: la pila **ISO 15118** (`ecog-io/*`, Apache-2.0), el stack
**EEBus** (`enbility/eebus-go` MIT y `NIBEGroup/openeebus` Apache-2.0, este último publicado por un
**fabricante**), la ingeniería **IEC 61850-6** (`openscd/open-scd`, Apache-2.0), el benchmark de
precio (`jeslago/epftoolbox`, Apache-2.0) y **`alliander-opensource/s4casting`** (MPL-2.0, push de
hoy) — tercera aparición de Alliander en esta KB.


### Actualización del décimo pase (2026-11-20) — EMEA

**Contexto regulatorio nuevo. ⚠️ Advertencia de método que esta región ya arrastra: ninguna de estas
fechas pudo verificarse en fuente primaria desde este entorno** — `eur-lex.europa.eu` y
`energy.ec.europa.eu` **no resuelven** (ver **T49**). Todo lo de abajo tiene concordancia de varias
fuentes secundarias y **sirve para planear, no para firmar**.

- **Hoja de ruta estratégica de digitalización e IA en energía, `COM(2026) 501`, presentada el 3 de
  junio de 2026.** Tres pilares; uno de ellos se titula **"Energy for AI"** y cubre explícitamente
  **conexión a red y emplazamiento (*siting*) de datacenters**. Es el instrumento europeo equivalente
  a las *show-cause orders* de FERC que esta KB ya rastrea en Norteamérica: misma preocupación, dos
  mecanismos distintos.
- **Acuerdo tripartito modelo**, previsto para publicarse y promoverse en el **segundo semestre de
  2026**, entre **operador de datacenter + parte energética + autoridad pública**. Esta es, de todo
  el paquete, **la pieza con forma de servicio facturable más clara**: un contrato modelo
  tripartito necesita, de cada parte, un expediente técnico —perfil de carga, flexibilidad
  comprometida, estudio de conexión— que nadie tiene preparado. Ver **T50**.
- **Horizon Europe destinaría ~75 M€ a tecnologías de IA en energía para 2026-2027.** Financiación
  concreta y con ventana: es el argumento para que un piloto europeo no salga del presupuesto
  operativo del cliente.
- **La Oficina Europea de IA tiene potestades de ejecución desde el 2 de agosto de 2026**, y los
  proveedores de modelos de propósito general deben **documentar el consumo energético de sus
  modelos**. Esto cierra el círculo de T16 ("lo que la IA consume ya es parte del alcance"): pasa de
  buena práctica a obligación documental del proveedor.
- **El plazo del Anexo III sigue sin ser firme.** Se mantiene íntegro lo establecido en **T41**: el
  *Digital Omnibus* (acuerdo político del 7 de mayo de 2026) correría la fecha al 2 de diciembre de
  2027, pero **hasta la publicación formal rigen el 2 de agosto de 2026 (Anexo III) y el 2 de agosto
  de 2027 (Anexo I)**. Preparar contra la fecha original; tratar la prórroga como margen.
- **Diagnóstico propio de la Comisión**: su informe sobre IA y IA generativa en redes inteligentes
  sitúa la **fragmentación** como la barrera principal, y plantea el equilibrio entre armonización a
  escala UE y autonomía regional. Es el argumento de venta de un integrador paneuropeo.

**Oportunidad nueva — calor de distrito.** Vertical ausente de esta KB durante nueve pases y
dominante en Escandinavia, Alemania, Polonia y los bálticos. Hay base **MIT** para el estudio
completo (`oemof/DHNx` 47 ★, `jylambert/topotherm` 37 ★, `oemof/tespy` 440 ★, `oemof/oemof-demand`
76 ★) y **nada** para la operación: no existe SCADA de calor, ni facturación de calor, ni gestión de
subestación térmica abierta. **Vender diseño y dimensionado; no vender operación.**

**Riesgo nuevo que hay que declarar en cualquier propuesta de interoperabilidad europea.** El
transporte real de modelos de red entre TSOs europeos (**EDX** y **OPDM** de ENTSO-E) está
implementado en MIT por **una sola cuenta individual** (`Haigutus`, 2-10 ★ por repo). Es la pieza que
hace operable el CGMES y el punto de fallo más concentrado que ha catalogado esta KB. Proponerlo como
acelerador internalizado, con plan de mantenimiento propio presupuestado.



### Actualización del undécimo pase (2026-11-20) — EMEA

**ENTSO-E convirtió al centro de datos en sujeto del sistema eléctrico, y eso crea un entregable
documental nuevo.** El informe de la asociación de TSOs europeos publicado el **8 de mayo de 2026**
(hay fuentes secundarias que lo fechan el 15; la nota de prensa primaria dice 8) sostiene que los
centros de datos *"se están convirtiendo en usuarios eléctricos sistémicamente relevantes cuyo
comportamiento influye cada vez más en la operación del sistema"*.

- **Demanda:** ENTSO-E espera que la demanda eléctrica de centros de datos en Europa crezca **más del
  50 % entre 2025 y 2030**. El material del propio informe da un rango de **199-254 TWh** para el año
  final, sin año explícito en la tabla citada — se registra con esa salvedad.
- **La advertencia operativa, que es el argumento de venta:** ENTSO-E alerta de que los operadores
  **podrían verse forzados a reducir la penetración de renovables** si el crecimiento de centros de
  datos no se gestiona. Es decir: el coste de no gestionar la flexibilidad se paga en renovable
  vertida.
- **Palanca regulatoria:** la **EU Cloud and AI Development Act** en preparación; la cobertura
  apunta a que podría triplicar el tamaño del mercado europeo de centros de datos en 5-7 años.
- **Peticiones de ENTSO-E a los legisladores:** legislar los beneficios de la flexibilidad y
  **actualizar los códigos de conexión** para que los centros de datos sostengan la seguridad de red.
  Un código de conexión actualizado es, otra vez, **expediente de cumplimiento facturable** — el
  patrón que T50 describe para EMEA.
- **Cuello de botella declarado por la industria:** la asociación europea de centros de datos sitúa
  el acceso a red como su principal problema (**67 %** de los operadores según un resumen
  secundario). Los retrasos de conexión afectan ya a planes de expansión de hiperescalares en Europa.

**Oportunidad concreta y nueva de este pase:** el patrón **NL→CIM trazable** tiene ahora plano y
dependencia, ambos de un TSO y ambos permisivos —
[`Talk2PowerSystem`](https://github.com/statnett/Talk2PowerSystem) (Apache-2.0, arquitectura:
*few-shot* con plantillas SPARQL + GraphDB) y [`cimsparql`](https://github.com/statnett/cimsparql)
(MIT, ejecutable). Para un TSO/DSO europeo con modelo CGMES, eso es una propuesta de "consulta en
lenguaje natural sobre tu propio modelo de red, con respuesta trazable al estándar IEC" cuyo
precedente lo firma un operador par, no un vendor. **Argumento de soberanía incluido: el stack es de
origen EMEA.**

⚠️ **Nota de oferta, y es una corrección sobre este propio documento:** la medición de oferta europea
de esta KB está sesgada a la baja. El código canónico de investigación europea vive en **GitLab
autoalojado** y GitHub indexa espejos que a veces pierden la licencia (ver T53, con evidencia en el
clúster eólico de DTU). Cualquier afirmación de "no hay oferta europea de X" en pases anteriores debe
leerse como "no hay oferta europea de X **indexada en GitHub**".

### Actualización del duodécimo pase (2026-11-20) — EMEA

**El paquete regulatorio europeo se completó en dos tiempos y ya tiene umbral numérico: a la
Hoja de ruta estratégica de digitalización e IA en energía del 3 de junio de 2026 le siguió, el
21 de septiembre de 2026, una propuesta de reglamento delegado que establece un esquema común de
calificación de la UE para datacenter con demanda de potencia de TI instalada de 500 kW o más.**

Lo que el esquema obliga a reportar, y que es la lista de requisitos de cualquier producto de
cumplimiento: **eficiencia energética, uso de agua, consumo de energía limpia, reutilización de
calor residual y flexibilidad**. Esas cinco métricas son el alcance funcional, no una enumeración
genérica.

Resto del cuadro, actualizado:

- **Las dos acciones bandera de la Hoja de ruta:** (1) un **acuerdo tripartito modelo** para integrar
  datacenter en la red, **voluntario**, entre autoridades públicas, operadores de datacenter,
  operadores de red y suministradores; (2) el esquema de calificación, con trabajo iniciado sobre
  **estándares mínimos de rendimiento energético**. **Catorce asociaciones industriales europeas**
  acordaron trabajar en el modelo tripartito bajo dirección de la Comisión. Se esperaba para el
  segundo semestre de 2026 y **no se ha confirmado su publicación** — comprobar en el pase 13.
- **Demanda, con cifras de la propia Comisión:** los datacenter europeos consumieron **~68 TWh en
  2024**, y la Comisión espera **114 TWh en 2030**, **más del 3 % de la demanda eléctrica total de la
  UE**. Es la serie más citable de este documento porque es del regulador, no de una consultora
  (comparar con T8 y con la dispersión de 4,6× del noveno pase).
- **Dinero concreto para IA en energía:** **~75 M€** asignados a tecnologías de IA en energía para
  **2026–2027** bajo **Horizon Europe**. Y la Comisión lanzó una **Community of Practice** bajo la
  iniciativa **AI.grids** para apoyar la gestión y planificación de red con IA — es decir, una puerta
  de entrada institucional, no sólo una convocatoria.
- **ACER** participa, con catálogos de indicadores de red inteligente a escala UE a finalizar **a
  mediados de 2026**.
- **Geografía del mercado (JLL, mitad de 2026):** los proyectos *greenfield* son el **39 % del
  pipeline 2026–2028** frente al **8 % de lo ya entregado**, y los emplazamientos hiperescalares
  *greenfield* están ahora a **175 km de media de una ciudad-hub**. Lectura: el datacenter europeo se
  está yendo a donde está la red y la energía, no a donde está el usuario — lo que **crea** el
  problema de conectividad y latencia que luego hay que resolver con ingeniería.
- **Contrapunto de seguridad energética (EUISS):** la UE afronta precios altos, restricciones de red
  y exposición a importaciones, mientras EEUU, China y el Golfo combinan ambición tecnológica con
  energía abundante y asequible. Útil como marco de por qué la eficiencia es obligatoria aquí y
  opcional en otras regiones.

**Oportunidad para Globant:** el esquema de calificación convierte **cinco métricas** en obligación
de reporte para todo datacenter ≥ 500 kW de TI. Eso es un producto de instrumentación, cálculo y
expediente auditable, y la métrica de **flexibilidad** es la que conecta con la red (Receta 4) y con
el acuerdo tripartito. Súmese la **Receta 27** (tubería CGMES, dirigida por COM/2026/501) y la
**Receta 2** (expediente AI Act).

**Lado open source de la región en este pase**, y es el más productivo:

- **`powsybl/pypowsybl-mcp` (MPL-2.0, RTE)** rompe el cero de agentes de operación de red. Un **TSO**
  publicando la capa agéntica sobre su propio motor de red es la confirmación ejecutable de T2, y el
  activo de referencia más vendible de la región (Receta 30).
- **Energinet (Dinamarca)** publica dos bancos de simulación: **`IMTB` (MPL-2.0, usable)** y **`MTB`
  (83 ★, ⛔ licencia revocable, no-OSI)**. Ver T33 — es una trampa de procurement, no una nota al pie.
- **`ClariGrid` (Apache-2.0)**: normalización de datos de mercado europeos entre fuentes. Autor
  individual, 3 ★: patrón a copiar.
- **Gaps declarados, con nombre:** **TenneT** tiene organización en GitHub (`tennet-nl-opensource`) y
  está **vacía — un solo repo, `.github`**, pese a declarar estrategia de open source alojada en LF
  Energy (ilustración exacta de T15). **Terna** y **Swissgrid** no tienen organización localizable y
  aparecen sólo como fuente de datos de terceros. **Fingrid** no publica repos propios pero expone
  API pública con clave gratuita.

#### Actualización del decimotercer pase (2026-11-20)

**Calendario del AI Act, con el matiz que importa para energía.** Fuentes de este pase (bufetes y
guías sectoriales, **todas secundarias**) coinciden en:

- El **Reglamento (UE) 2026/1744** se publicó en el **Diario Oficial el 24 de julio de 2026** y se
  aplica desde el **27 de julio de 2026**.
- Desplaza las obligaciones de **alto riesgo del Anexo III** —donde cae *la mayor parte de la IA
  operativa de energía*— de **2 de agosto de 2026** a **2 de diciembre de 2027**.
- Las de **IA embebida en productos del Anexo I** pasan a **2 de agosto de 2028**.
- **Precisión de alcance que corrige lecturas anteriores:** la guía de 2025 trataba el control de
  red y el mantenimiento predictivo como alto riesgo **en bloque**; la lectura posterior lo **estrecha
  a los sistemas en que un fallo de la IA pondría en peligro el suministro** (IA como *componente de
  seguridad* en electricidad, gas y calor). No todo modelo que toca la red es Anexo III, y afirmar lo
  contrario infla el presupuesto de cumplimiento de una propuesta.

⚠️ **Esta KB ha arrastrado tres calendarios del AI Act incompatibles durante varios pases, y sigue
sin leerse la fuente primaria.** El `automotive-kb` registró el mismo problema. **Recomendación
explícita para el próximo pase de energy: gastar el presupuesto en UNA fuente primaria (el texto del
Reglamento (UE) 2026/1744 en el Diario Oficial) en lugar de más lectura secundaria.** Es el único
ítem de este archivo cuya incertidumbre no baja buscando más.

**Hoja de ruta de la Comisión (3 de junio de 2026)** — la KB ya la menciona; se añaden dos
elementos accionables:

- Estructura en **tres pilares**, con **`AI.grids`** como eje de red.
- Incluye un **esquema europeo de clasificación de datacenters** sobre eficiencia energética, **uso
  de agua**, consumo de energía limpia, **reutilización de calor residual** y **flexibilidad**.
  Es un instrumento de *reporting*: produce **obligación de medir y declarar**, que es exactamente la
  forma de trabajo que un estudio de datos puede entregar. El pilar de flexibilidad y el de calor
  residual conectan con las recetas de DR y de edificios ya catalogadas.

**Hallazgo de oferta de este pase, y refuerza la tesis de soberanía de EMEA:** la **capa de medición
y de modelo de datos de DER es la capa más europea del stack**. De las 13 piezas nuevas con origen
identificable, **9 son EMEA** (Alemania, Países Bajos, Suecia, Dinamarca, Eslovenia) y 4 North
America. El motivo es regulatorio y no cultural: el **mandato de medidor inteligente** y el **derecho
de acceso local a los datos del hogar** son políticas europeas, y producen código. Sumado a lo que el
pase 12 ya registró, **un encargo EMEA puede montarse de punta a punta sobre código de origen EMEA,
desde el medidor hasta el motor de red** — `mbmd` / `iec62056-21` / `dsmr-p1-parser` (medición) →
`saref-linkml` (semántica) → `openleadr-rs` + `openadr3-client` (flexibilidad) → `pypowsybl` (red).
Eso responde la objeción de soberanía digital **sin ningún modelo ni librería de origen estadounidense
o chino en la ruta crítica**.

### Actualización del decimocuarto pase (2026-11-21) — EMEA

**Corrección de precisión, y es importante porque afecta a cómo se cita el AI Act en un entregable.**
Esta KB venía registrando **Reg (UE) 2026/1744** (OJ 24-jul-2026) como "el AI Act para energía". Ese
número **no es el AI Act**. Son dos instrumentos distintos y hay que nombrarlos por separado:

| Instrumento | Qué es | Papel |
|-------------|--------|-------|
| **Reg (UE) 2024/1689** | **El AI Act propiamente dicho.** Se aplica horizontalmente, energía incluida | La norma sustantiva: define sistema de alto riesgo y sus obligaciones |
| **Reg (UE) 2026/1744** | Instrumento **modificativo** (OJ 24-jul-2026) | Mueve las fechas: Anexo III → **2-dic-2027**, Anexo I → **2-ago-2028**, y estrecha el alcance |

**Consecuencia práctica:** citar "Reg (UE) 2026/1744" a secas como fundamento de una obligación es
un error de forma — la obligación nace de **2024/1689**; 2026/1744 dice **cuándo** empieza a
aplicarse. En un documento de cliente van los dos, y en ese orden. La pregunta sustantiva sigue
siendo la misma que esta KB viene registrando: **si un sistema energético concreto cae en "alto
riesgo"**, y la Comisión tiene guías de clasificación en borrador.

> **Regla de método que esto deja, y vale para toda la flota de KBs:** cuando una fecha de
> aplicación y una obligación vienen de **números de norma distintos**, registrar los dos números y
> cuál hace qué. Un pase que guarda sólo el instrumento modificativo pierde la base legal, y un pase
> que guarda sólo la norma base publica una fecha equivocada.

#### La hoja de ruta, ahora con el dinero desglosado

La **Strategic Roadmap for Digitalisation and AI in the Energy Sector** de la Comisión
(**3-jun-2026**, ya en la KB) es **comunicación de política, no legislación vinculante**, sobre tres
pilares: *Energy for AI*, *Digitalisation and AI for the Energy System*, *Data for AI*. El desglose
presupuestario localizado este pase:

- **~€ 75 M** asignados a **IA en energía**.
- **~€ 190 M** a **soluciones digitales de energía** en sentido amplio.
- Origen: **Horizon Europe**.

Eso confirma lo que el séptimo pase ya anotaba —la Comisión **financia exactamente la capa que esta
KB cataloga**— y ahora con la cifra separada entre lo estrictamente agéntico y lo digital-general.

#### Movimiento de industria, que es señal de dónde se va a contratar

- **Declaración de intención firmada por 14 asociaciones industriales europeas**, con un **acuerdo
  modelo esperado en el segundo semestre de 2026**. Un acuerdo modelo es una plantilla contractual:
  cuando aparece, el trabajo de integración se estandariza y se licita.
- **Alianza de utilities y tecnológicas para descarbonizar los datacenters de la UE** (jun-2026).
- Se menciona una **propuesta de modificación del Reglamento del Mercado Eléctrico** posterior a la
  hoja de ruta (fecha citada 17-jul-2026). ⚠️ **Fecha sin verificar** — no citarla sin comprobar.
- Barrera de adopción recurrente en las fuentes: requisitos estrictos de seguridad de la
  infraestructura crítica, **gobernanza fragmentada** y **datos poco compartidos**. Es la misma forma
  de *adopción-sin-consolidación* que esta KB ya midió en otras industrias.

⚠️ **Todo este bloque es snippet-sourced.** `eur-lex.europa.eu` sigue sin resolver desde este
entorno, por lo que **el texto primario del AI Act y de su instrumento modificativo continúa sin
leer** — el open item del pase 13 **sigue abierto**, y conviene que siga marcado como tal.


#### Actualización del decimoquinto pase (2026-11-21) — EMEA

**El operador de transmisión europeo publicó la segmentación comercial del producto de
flexibilidad, y es la mejor noticia del pase para EMEA.** ENTSO-E publicó el **8 de mayo de 2026**
*"Data centres and the power system: expected trends, challenges and opportunities"*. Lo sustantivo:

- Pide **actualizar los códigos de conexión** para que los centros de datos **sostengan** la
  seguridad y fiabilidad de la red, en vez de limitarse a consumir de ella.
- **Aconseja explícitamente no restringir la integración de renovables** para acomodar centros de
  datos, y en cambio **dirigir a los promotores a regiones con menos tensión de red**.
- Define una **ruta por etapas**: primero los sistemas de control garantizan operación segura para
  la red; **sólo después** la instalación puede ofrecer **servicios de flexibilidad**. La
  participación depende del **diseño de mercado de cada país**.

> **La frase que vale dinero:** los centros de datos **hiperescala** están en la mejor posición para
> prestar flexibilidad, mientras que los de **colocation** están **limitados por el control del
> inquilino**. Eso convierte la flexibilidad en colocation en un problema de **contrato y de
> software de coordinación entre operador e inquilinos** — no de hardware ni de red. Es precisamente
> la clase de problema que un estudio de software puede resolver, y define un segmento desatendido
> con una causa nombrada.

**Instrumento nuevo en el horizonte: la *Cloud and AI Development Act*.** El informe urge a los
legisladores a actuar **antes** de ella; se le atribuye el objetivo de **potencialmente triplicar el
tamaño del mercado europeo de centros de datos en 5–7 años**. ⚠️ **Estado de adopción no verificado
desde este entorno** — citarla como instrumento *en preparación*, nunca como derecho vigente.

**Corrección que se mantiene y se repite porque es la que más veces se ha torcido en esta KB:** el
AI Act es el **Reg. (UE) 2024/1689**; el **Reg. (UE) 2026/1744** es el instrumento que **mueve las
fechas**. No son el mismo texto y no se conflatan. El registro primario sigue **sin leerse** desde
este entorno (open item heredado del pase 13).

**La capa de oferta EMEA se extiende del contador al modelo de red.** La KB ya tenía una capa de
**medición** de origen europeo casi completa; este pase añade la de **intercambio de modelos de red
CIM/CGMES (IEC 61970)** y la de **subestación IEC 61850**, ambas permisivas y ambas europeas:

- [`sogno-platform/cimpy`](https://github.com/sogno-platform/cimpy) (Apache-2.0, RWTH Aachen),
  [`cim4j`](https://github.com/sogno-platform/cim4j) (Apache-2.0, activo),
  [`RWTH-IAEW/cimpyorm`](https://github.com/RWTH-IAEW/cimpyorm) (BSD-3-Clause).
- [`robidev/iec61850_open_server`](https://github.com/robidev/iec61850_open_server) (Apache-2.0,
  IED abierto) y [`beanit/iec61850bean`](https://github.com/beanit/iec61850bean) (Apache-2.0, pila
  MMS; ⚠️ sin push desde jul-2023).
- [`phasenexa/nexa-bidkit`](https://github.com/phasenexa/nexa-bidkit) (MIT) para ofertas
  *day-ahead* e intradiario en mercados europeos.
- [`jannickfahlbusch/ha-ppc-smgw`](https://github.com/jannickfahlbusch/ha-ppc-smgw) (Apache-2.0,
  SMGW alemán) y [`HandyHat/ha-hildebrandglow-dcc`](https://github.com/HandyHat/ha-hildebrandglow-dcc)
  (MIT, SMETS/DCC británico).

**Consecuencia de posicionamiento:** con medición + modelo de red + subestación + oferta de mercado
todos disponibles en licencia permisiva y **de origen europeo**, una propuesta en EMEA puede
responder la pregunta de soberanía **sin una sola dependencia estadounidense en la capa de datos**.
Eso era un argumento parcial en el pase 13 y ahora es un **stack completo**.

⚠️ **Nota de licencia europea, nueva:** aparece **EUPL-1.2** en proyectos financiados por la UE
(`HVDC-Wise_lib`). Es **copyleft débil con compatibilidad explícita**, no permisiva, y **engaña a
los detectores por palabra clave** porque su texto nombra GPL, LGPL, AGPL y MPL (ver T59 en
`repos/trending.md`). En EMEA hay que esperar encontrarla y clasificarla a mano.

### Actualización del pase 16 (2026-11-24) — EMEA

**La UE publicó la arquitectura completa de su política de IA en energía, y el plazo que bloqueaba
los proyectos operativos se movió dieciséis meses.**

**1. El plazo (el dato más vendible del pase).** El **Digital Omnibus on AI** es **derecho vigente**:
**Reglamento (UE) 2026/1744** — Parlamento **16-jun-2026**, Consejo **29-jun-2026**, DOUE
**24-jul-2026**, en vigor **27-jul-2026**.

| Obligación | Antes | **Vigente** |
|------------|-------|-------------|
| Alto riesgo **Anexo III** autónomo — incluye **suministro de electricidad, gas, calor y agua** | 2-ago-2026 | **2-dic-2027** |
| Alto riesgo **Anexo I** (IA embarcada en producto regulado) | — | **2-ago-2028** |
| **Artículo 50**, transparencia | 2-ago-2026 | **NO aplazado**, vigente desde 2-ago-2026 |

Aplaza el **Capítulo III, secciones 1-3**, salvo el artículo **6(5)**. **La IA que gestiona u opera
suministro eléctrico es Anexo III**, así que el expediente de alto riesgo vence el **2-dic-2027**.
⚠️ **Cómo venderlo sin equivocarse:** «hay tiempo para el expediente de alto riesgo, **no** para la
transparencia del artículo 50, que ya rige». Y, para esta KB: **2024/1689 es el AI Act; 2026/1744 es
el Omnibus que mueve sus fechas.** Una fuente de mayo de 2026 todavía decía que el Omnibus no estaba
adoptado: estaba desactualizada, no equivocada (T67).

**2. La hoja de ruta.** **Strategic Roadmap for Digitalisation and AI in the Energy Sector**,
**COM(2026) 501**, **3-jun-2026**. Tres pilares (*Energy for AI*; *Digitalisation and AI for the
energy system*; *Data for AI and the energy system*), **siete acciones faro**, ~**265 M€** de I+i y
~**75 M€** de Horizon Europe para IA en energía **2026-2027**. **Es una comunicación de política, no
legislación vinculante**, pero señala cambio regulatorio hacia 2030.

**3. La pieza que sí es vinculante y ya se movió.** **21-sep-2026**, *Data Centre Energy Efficiency
Package*: la Comisión propuso un **reglamento delegado** con un **esquema común de calificación de
centros de datos** para potencia TI instalada **≥ 500 kW**, más consulta sobre **estándares mínimos
de rendimiento**. Califica eficiencia energética, **eficiencia hídrica**, uso de renovables,
**reutilización de calor residual** y **flexibilidad**.

**4. Dos acciones faro que conectan con el inventario de esta KB.**
- **Acuerdo tripartito modelo** para integrar centros de datos en la red: la UE reconoce que la
  integración es **contractual y de coordinación**, exactamente lo que ENTSO-E dijo del *colocation*
  en el pase 15. **Refuerza la receta 50 con respaldo institucional.**
- **AI.grids**: marco piloto de **modelos fundacionales paneuropeos para gestión y planificación de
  red**. **Hay dinero público europeo detrás de la capa de *grid foundation models*** que esta KB
  inventaría (`gridfm`, `PowerFM`). Es el primer *pull* financiado de esa capa.

**5. Resto del marco, sin cambios de fondo:** **NIS2** (energía = servicio esencial), **GDPR** para
datos de consumo, **REMIT** para trading con IA. **Reino Unido:** guía de IA ética de **Ofgem**,
**2.ª edición mayo de 2026**, y **piloto de *sandbox*** previsto — vía de entrada de bajo riesgo
regulatorio para un primer proyecto británico.

**Oportunidad concreta:**
1. **Expediente de calificación de centro de datos ≥ 500 kW** (receta 54): hay umbral, hay criterios
   —incluida **flexibilidad**, que es donde esta KB tiene stack— y hay un reglamento delegado en
   curso. Contraparte que paga y fecha.
2. **Expediente de alto riesgo Anexo III con horizonte 2-dic-2027**: ahora es planificable, y el
   artículo 50 da un entregable inmediato.
3. **Posicionarse en AI.grids** como integrador de la capa de modelos fundacionales de red.

⚠️ **Procedencia declarada.** `energy.ec.europa.eu`, `data.consilium.europa.eu` y `www.twobirds.com`
**no resuelven DNS desde el egress de esta sesión**: **no se leyó texto primario**. Los puntos 2-4
están corroborados por **seis fuentes secundarias independientes** coincidentes en fecha, número de
documento, pilares y umbral (Legal500, Eversheds Sutherland, EUREC, Eurelectric, Conventus Law,
FSR-EUI). **Secundario convergente, no bibliografía primaria** (ítem 16-R2).
⚠️ Sin verificar: una consultora sitúa a las utilities polacas **12-18 meses por detrás** de sus
pares de Europa occidental en madurez de IA. Atribuible, no adoptable.

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

**Actualización del sexto pase (2026-11-20) — aparece el programa estatal chino, y una cifra de adopción que sirve de ancla**

- **China tiene un `National Plan for AI-Energy Integration`.** Lo cita la hoja de ruta de la Comisión
  Europea al enumerar los esfuerzos estatales comparables (junto a la *Genesis mission* de EE. UU.).
  Es la primera vez que esta KB registra un **programa nacional chino específico de integración
  IA-energía**, y encaja con lo que los pases anteriores ya habían anotado sobre China usando IA para
  mejorar la eficiencia renovable. Queda pendiente de verificación primaria.
- **La cifra de adopción que conviene llevar, porque es sobria**: un documento del **ADB** (*Enabling
  AI Implementation in the Energy Sector*, junio de 2026) cita una tasa de adopción de IA del **33 %**
  en el sector energético (atribuida a datos de la IEA de 2025), y señala como causas del resto
  **política, gobernanza y estándares débiles**. En el otro extremo del mismo sector, ABB reporta que
  el **71 %** de los líderes energéticos de Asia-Pacífico ven la IA y la automatización como
  habilitadores clave de la transición. La distancia entre 71 % de intención y 33 % de adopción es el
  mercado direccionable, y es un argumento mejor que cualquier proyección de tamaño.
- **Dónde no se adopta, y coincide con las otras dos regiones**: la IEA sostiene que la adopción sigue
  **limitada en la operación de red crítica para el sistema**. Un análisis de Temasek añade el motivo
  concreto: incrustar IA en sistemas físicos exige **datos específicos de dominio e integración con
  legado**. Tercera región consecutiva en la que la barrera es integración, no modelo.
- **El desfase temporal, en su versión APAC y descrito como agudo**: la infraestructura de IA se
  construye en **1–2 años** y la ampliación de red tarda **5–10**. Es la misma tesis central de esta
  KB, y la lectura regional es que en APAC la brecha es más pronunciada.
- **Capacidad anunciada, con fuente nombrada**: modelización de ArkTerra Partners cuenta **24,2 GW**
  de capacidad de datacenter anunciada en **nueve mercados APAC** para 2025–2030. El Singapore Green
  Finance Centre, con Standard Chartered y Temasek, estima **9–15 GW** de demanda en el Sudeste
  Asiático para 2030. Son dos recortes distintos (capacidad anunciada vs. demanda estimada): no
  sumarlos ni presentarlos como la misma magnitud.
- **Regulación concreta y accionable**: **Vietnam** introdujo en **enero de 2026** una **tarifa de dos
  partes para almacenamiento en baterías**. Es el elemento de política más específico del pase para
  APAC y afecta directamente al caso de negocio de un BESS (ver la Receta 13). Los analistas añaden
  que en almacenamiento APAC la **certeza de política pesa ya más que el coste** en la decisión de
  inversión, y un informe de ERM observa que los reguladores están saliendo del molde tradicional de
  EHS.
- **Competencia instalada que hay que asumir en una propuesta**: Siemens, GE, Schneider, ABB, IBM,
  Microsoft y Enel aparecen listados como los proveedores principales de IA aplicada en energía en la
  región; el ADB, Microsoft, KPMG y Banpu NEXT son además activos institucionalmente.
- ⚠️ **El gap de repos de origen APAC sigue abierto.** Este pase no encontró ninguno nuevo. Dado que
  LATAM se cerró buscando por **nombre de framework + país** (`pypsa-` + país), la acción concreta
  para el próximo pase es aplicar la misma receta aquí: `pypsa-india`, `pypsa-vietnam`,
  `pypsa-indonesia`, `pypsa-korea`, `calliope-` y `osemosys-` con sufijo de país asiático.

#### Actualización del séptimo pase (2026-11-20): APAC dejó de ser un gap de oferta, y el dato de adopción más útil de toda la KB es de aquí

**Primera corrección: APAC no carecía de repos, esta KB carecía del término de búsqueda.** Los pases
anteriores registraron la región como delgada. Buscando por el **instrumento regulatorio local** en
lugar de por el nombre de la región aparecen cuatro repos australianos reales y verificados:

| Repo | Licencia | ★ | Qué resuelve |
|------|----------|---|--------------|
| [longzheng/open-dynamic-export](https://github.com/longzheng/open-dynamic-export) | **MIT** | 57 | Control dinámico de exportación y curtailment de inversores bajo **CSIP-AUS / SEP2 / IEEE 2030.5** |
| [bje-/NEMO](https://github.com/bje-/NEMO) | ⚠️ GPL-3.0 | 55 | Optimizador del **National Electricity Market** |
| [UNSW-CEEM/NEMSEER](https://github.com/UNSW-CEEM/NEMSEER) | ⚠️ GPL-3.0 | 39 | Pronósticos del **AEMO** para el NEM (UNSW) |
| [ethanndickson/sep2_client](https://github.com/ethanndickson/sep2_client) | Apache-2.0 | 24 | Cliente IEEE 2030.5 en Rust |

`open-dynamic-export` es el accionable: **MIT**, mantenido, y atado al régimen de conexión
**obligatorio** en Australia. Una propuesta de agregación de DER en Australia ya no empieza de cero.

**Segunda, y el dato más valioso que este pase aporta a toda la KB: la IEA midió el hueco agéntico.**
Una encuesta de la **IEA a operadores de red de 13 países** —China y Japón incluidos— encuentra:

- **23 %** usa IA para **operación en tiempo real**
- **~70 %** la usa para **mantenimiento de activos y planificación de la operación**

Esto coincide exactamente con lo que esta KB medía contando repos: no hay agente de operación de red
proponible, y sí hay una capa madura de mantenimiento, forecasting y planificación. **El trabajo
vendible hoy está en el 70 %, no en el 23 %.** Usar este dato para reencuadrar cualquier conversación
en la que el cliente pida "autonomía": la industria entera está en el otro lado.

**Dimensión de la demanda:**

| Hecho | Cifra | Fuente |
|-------|-------|--------|
| Inversión anual en red de **China e India** | **> 300 000 M USD para 2030** | Bloomberg, vía DWS APAC CIO View |
| Crecimiento de demanda por datacenters en Asia-Pacífico | **790 TWh** | Wood Mackenzie, perspectiva 2026 |
| Participación de **India** en el crecimiento fuera de China | **~la mitad** | Wood Mackenzie |
| Datacenters en **Japón** | revierten **una década** de caída de demanda eléctrica | Wood Mackenzie |
| Plan de **Adani** (India) | **100 000 M USD**, hub de IA anclado en renovables | cobertura sectorial |

**Players con despliegue real, que son el precedente citable de la región:**

- **State Grid Corporation of China** construyó una plataforma de IA a escala de ciudad que integra
  **forecasting, trading, regulación y liquidación**, y usa IA para gestión de red en tiempo real. Es
  el despliegue más ambicioso del mundo en esta categoría.
- **TEPCO Power Grid** (Japón) desarrolla drones que recogen datos 3D de equipamiento.
- **Chubu Electric** (Japón) entrenó un modelo de red neuronal sobre datos de red de **30 segundos**.

**Oportunidad, y el límite que hay que decir en voz alta.** Las licitaciones nuevas de la región
exigen cada vez más **almacenamiento y flexibilidad de red** (Wood Mackenzie 2026) — ese es el encaje
de las recetas de BESS y flexibilidad. ⚠️ Pero expertos advierten que la **flexibilidad limitada de la
red china** podría anular las ganancias de eficiencia que la IA prometa: en China el cuello de botella
es físico, no algorítmico. Proponer optimización de despacho allí sin verificar la flexibilidad
disponible es proponer un resultado que la red no puede ejecutar.

⚠️ **Gap de este pase, declarado explícitamente:** las búsquedas no devolvieron **detalle regulatorio
concreto de China, India ni Japón** sobre IA en energía. Hay cifras de inversión y casos de
despliegue, pero no el equivalente de la orden de la FERC o de COM/2026/501. No se puede construir un
argumento de cumplimiento para esos tres países con lo que hay hoy en esta KB. Es un hueco de
investigación, no una ausencia de regulación.


#### Actualización del octavo pase (2026-11-20): el regulador deja de dar acceso y empieza a pedir contrapartida

- **Magnitud, con dos mediciones concordantes**: Wood Mackenzie (junio de 2026) cifra en más de
  **32 GW** la capacidad de datacenter planificada en más de **1.150 proyectos** presionando las
  redes de la región, y sostiene que **la disponibilidad de red es la restricción definitoria** del
  crecimiento. Oxford Economics reporta que el *pipeline* de desarrollo regional alcanzó un récord de
  **26,5 GW en el primer semestre de 2026**. Dos casas distintas, mismo orden de magnitud.
- **El giro regulatorio, y es el dato más accionable del pase para APAC**: los reguladores de la
  región se están alejando de los acuerdos tradicionales de utility hacia marcos que exigen a los
  datacenters **compartir responsabilidad** por fiabilidad, flexibilidad y descarbonización de la
  red. Wood Mackenzie agrupa las medidas en **cuatro categorías**, y conviene usarlas como checklist
  de propuesta:

  | Categoría de medida | Qué exige | Entregable que genera |
  |---------------------|-----------|----------------------|
  | **Acceso condicional** | La conexión se concede contra compromisos | Expediente de compromisos y su verificación |
  | **Diversificación geográfica** | Llevar el proyecto a donde hay red | Análisis locacional y de sitio |
  | **Requisitos de soporte a la red** | Flexibilidad, respuesta de demanda, almacenamiento | Diseño y operación de flexibilidad (*Receta 4*) |
  | **Controles de capacidad** | Topes y escalonamiento de la carga | Plan de rampa y modelado de escenarios |

- **Australia es el caso más avanzado**: el marco nacional obligaría a los grandes operadores a
  **financiar su propia generación y los costes de conexión**, e impondría estándares obligatorios de
  eficiencia energética y conservación de agua. JLL añade que la legislación esperada exigiría que
  los desarrolladores **garanticen generación renovable nueva que iguale la capacidad adicional**.
  ⚠️ Parte del detalle viene de un solo medio: verificar antes de apoyarse en ello. Es coherente, eso
  sí, con que Australia sea también la **única jurisdicción APAC con repos abiertos de su norma de
  conexión** (`CSIP-AUS`, `IEEE 2030.5`, `open-dynamic-export` MIT, `sep2_client` Apache-2.0).
- **El resto de mercados también aprieta**: en **Japón, India y Corea del Sur** los gobiernos empezaron
  a dirigir el desarrollo de datacenters hacia regiones con mejor disponibilidad de red y suministro
  más bajo en carbono. La actividad de protesta se extiende desde Corea del Sur hacia **Japón,
  Malasia, Indonesia e India**: es riesgo de licencia social, igual que en LATAM.
- **Efecto competitivo que conviene nombrar en una propuesta**: los requisitos de eficiencia, compra
  de renovable y evaluación de impacto en red **elevan la barrera de entrada y favorecen a los
  operadores grandes y bien capitalizados**. Y los inversores tratan ya el **estado de red y la
  ubicación como primer punto de *due diligence*** en mercados eléctricos liberalizados. Eso define
  el comprador: operadores grandes e inversores, no desarrolladores pequeños.
- **Infraestructura regional de largo plazo**: la **Pan-Asia Power Grid Initiative** del Banco
  Asiático de Desarrollo permitiría exportar electricidad entre países con exceso de solar, viento e
  hidro mediante redes de transmisión interconectadas, acompañada de un **Asia-Pacific Digital
  Highway** de 20.000 M USD para corredores de fibra, cables submarinos, satélite y datacenters
  regionales. ⚠️ Es **propuesta, no programa en operación**: no construir un caso de negocio sobre
  ella.

**Players nombrados en las fuentes de este pase**: Wood Mackenzie (analista Xiaonan Feng), JLL (James
Cameron, *APAC energy advisory*), Oxford Economics con AEMO, y el Banco Asiático de Desarrollo. Los
hiperescaladores invierten en Singapur, Malasia, Indonesia, Tailandia y Filipinas.


#### Noveno pase (2026-11-20) — T5 confirmado con los países asignados, y el instrumento multilateral que faltaba

**T5 de esta KB decía "tres regímenes divergentes". Este pase los asigna país por país**, que es lo
que hacía falta para elegir jurisdicción en un SoW (fuente: panorama regulatorio APAC de Latham &
Watkins):

| Régimen | Países | Qué implica para un proyecto |
|---------|--------|------------------------------|
| **Vinculante basado en riesgo** | **Corea del Sur**, **Vietnam** | Hay obligación formal: el expediente de conformidad es entregable |
| **Normas dirigidas (targeted)** | **China** | Obligación por caso de uso concreto, no marco horizontal |
| **Voluntario, basado en principios** | **Japón**, **Singapur**, **Australia** | No hay expediente obligatorio: el argumento es de gobernanza, no de cumplimiento |

- **Corea**: la **AI Basic Act** es descrita como **la primera ley integral de IA plenamente
  operativa de la región**, en vigor el **22 de enero de 2026**. ⚠️ Las fuentes discrepan sobre el
  día exacto de enero: verificar contra el texto oficial antes de citar la fecha en un contrato.
- **Vietnam**: ley de IA basada en riesgo con efecto el **1 de marzo de 2026**, y una **resolución
  energética 2026-2030** con mecanismos especiales para desatascar cuellos de botella históricos.
- **Indonesia**: regulación nacional de IA aún en elaboración según la fuente consultada.
- **Tailandia**: borrador de reglas que permitirían a los datacenters **contratar directamente con
  generadores renovables** — es el mismo instrumento de "acceso condicional" que T37 ya identificó
  como convergencia de las cuatro regiones.
- **APEC** publicó **Recomendaciones de Política sobre el Refuerzo Mutuo entre IA y Energía en
  Asia-Pacífico (2026-2030)**: **voluntarias**, piden alinear los planes de infraestructura de IA
  con los planes energéticos nacionales y mencionan posibles **benchmarks voluntarios IA-energía**.
  Es el primer instrumento multilateral específico IA-energía que registra esta KB.
- **Estructura de mercado (IBM)**: buena parte de la región depende de **monopolios de utility con
  respaldo estatal**, lentos para adoptar **tarifas flexibles** — el freno a cualquier producto de
  flexibilidad no es técnico, es tarifario. Hubs nombrados: **Singapur, India, Malasia**.
- **Soberanía de dato**: Malasia enmarca un ecosistema de nube **"seguro y soberano"** como base de
  su adopción de IA; se espera que la **localización de datos** siga siendo prioridad regional.
- Un informe de mercado sostiene que **APAC lidera la adopción** (openPR). Dato de adopción, no de
  tamaño (T8).

**Oferta de origen APAC añadida este pase**, que es lo que permite responder un engagement de la
región con código de la región: **`Ninemilo/OpenVigil`** (Apache-2.0, 180 ★) —la plataforma agéntica
de O&M eólico, con proveedores de modelo **SiliconFlow / Alibaba Bailian / DeepSeek**—,
**`waiwera/waiwera`** (LGPL-3.0, simulador geotérmico, Nueva Zelanda, push de hoy) y
**`kinverarity1/lasio`** (MIT, registros de pozo LAS, Australia).


### Actualización del décimo pase (2026-11-20) — APAC

**Contexto regulatorio nuevo. ⚠️ `apec.org` no resuelve desde este entorno** (ver **T49**): lo de
abajo es concordancia de fuentes secundarias.

- **La reunión ministerial de energía de APEC de 2026 respaldó recomendaciones de política que
  vinculan IA y energía**, y encargó a su **Energy Working Group** la creación de un **grupo de
  trabajo específico**. Los ministros instaron además a **coordinar la planificación de
  infraestructura energética y de cómputo** y a adoptar herramientas de IA para la **operación de
  sistemas eléctricos**. Es el primer instrumento multilateral de esta KB que pide explícitamente IA
  *en la operación* —justo la categoría donde esta KB lleva **seis ceros consecutivos** de oferta
  abierta proponible. Demanda institucional declarada contra oferta medida en cero: eso es alcance.
- **Singapur aprobó su *Digital Infrastructure Bill* el 7 de octubre de 2026**: licenciamiento
  obligatorio para datacenters grandes, con **referencias de eficiencia energética**. Los detalles de
  ejecución siguen pendientes. Es el régimen de **acceso condicional** que T37 describe, ahora con
  fecha de aprobación.
- **Tailandia habría pausado la aprobación de nuevos proyectos de datacenter** mientras redacta
  normas nacionales. Un freno administrativo es, para un cliente, un problema de *cronograma de
  conexión*, que es exactamente lo que un estudio de interconexión resuelve.
- **Corea del Sur: la *AI Basic Act* está en vigor desde el 22 de enero de 2026.** Japón sigue
  promoviendo IA **sin sanciones**. Las fuentes **discrepan** sobre qué países tienen estatuto
  vinculante (una lista incluye a Taiwán y Vietnam; otra deja a India sin ley alguna): tratar el
  estado país por país como **no asentado** y verificarlo en fuente primaria antes de comprometer
  cumplimiento.
- **Malasia: el build-out de Johor iría camino de ~1 GW a finales de 2026** (fuente secundaria).
  Combinado con la pausa tailandesa y el licenciamiento singapurense, el mapa APAC de carga de
  datacenter se está redibujando por **regulación**, no por demanda.

**Nota de oferta, sin cambios en este pase.** Las ~125 piezas institucionales encontradas son de
origen **norteamericano** (EPRI, GPA, Sandia) y las de calor de distrito, **europeas**. **Este pase
no encontró oferta nueva de origen APAC.** Se registra explícitamente como pase sin hallazgo
regional, no como cobertura: la credencial APAC verificable sigue siendo la del séptimo pase
—`open-dynamic-export` **MIT**, `sep2_client` Apache-2.0, `NEMSEER` y `NEMO` GPL-3.0, vía el
vocabulario **CSIP-AUS**— más `MyEMS` (MIT, origen China) y los proveedores de modelo de `OpenVigil`
(SiliconFlow, Alibaba Bailian, DeepSeek) del noveno pase.

**Precisión de vocabulario útil para APAC y NA a la vez, hallada en este pase:** la familia de normas
de conexión de DER se busca por **el nombre de la norma local** (T36) y los nombres son distintos en
cada región pero **comparten el estándar base IEEE 2030.5**: `CSIP-AUS` en Australia, `IEEE 2030.5`
en Norteamérica (cliente de referencia de EPRI, BSD-3, 96 ★). Buscar `CSIP` a secas devuelve clientes
**SIP de telefonía**.



### Actualización del undécimo pase (2026-11-20) — APAC

**APAC es donde el crecimiento de demanda es físico y donde la regulación ya obliga al centro de
datos a gestionar su propio impacto de red.**

- **Magnitud:** Wood Mackenzie proyecta un aumento de la demanda eléctrica global de **920 TWh en
  2026**, con **Asia-Pacífico aportando el grueso** del incremento (una fuente titula la cifra
  regional en **790 TWh**; se registran las dos, con la discrepancia a la vista).
- **China — el único caso de orquestación de red a escala de ciudad:** **State Grid** opera una
  plataforma de orquestación con IA que gestiona la red en tiempo real con foco en operación
  flexible y baja en carbono. En política, la iniciativa **"AI Plus"** sitúa la IA como herramienta de
  transformación económica incluida la energía, y el **Plan Quinquenal 2026-2030** apunta
  explícitamente a IA para **volatilidad de red y vertido de renovable**. Es la referencia global de
  IA aplicada a operación, y es de un operador estatal.
- **Japón:** foco en resiliencia de red, infraestructura inteligente y eficiencia. Los centros de
  datos están **revirtiendo por sí solos la tendencia de caída de demanda** eléctrica. Su mercado de
  futuros eléctricos se describe como el de derivados de electricidad de mayor crecimiento del mundo
  — base para casos de *trading* y cobertura. La **AI Promotion Act** es de corte promocional y, según
  fuente secundaria, **sin penalizaciones explícitas**.
- **India:** el límite no es la ambición sino la **entrega de red**: el objetivo de duplicar capacidad
  proyectada para el final del próximo ejercicio fiscal choca con retrasos severos de red. El
  mercado **IEX** opera *day-ahead* y *term-ahead*. Adopción empresarial citable: **Tata Power** con
  despliegue de Databricks en operaciones de renovable y red inteligente.
- **Regulación que crea trabajo, y es el dato más accionable:** **Singapur, Malasia y Corea del Sur**
  exigen a los promotores de centros de datos presentar **planes de almacenamiento en baterías y de
  gestión de curtailment junto con evaluaciones de impacto de red**. En **Johor** hay prohibición de
  construcción de instalaciones grandes por tensión hídrica.

**Oportunidad concreta:** el requisito regulatorio "evaluación de impacto de red + plan de BESS +
gestión de curtailment" es un **entregable técnico-documental repetible** por jurisdicción, y la KB
tiene con qué hacerlo: `pandapower`/`powsybl` para el estudio de red, el clúster de almacenamiento del
pase 10 (`snl-quest` BSD-3, `StorageVET`/`DER-VET` BSD-3) para el dimensionado y valoración del BESS,
y `HELICS` (BSD-3, nuevo en este pase) para acoplar los simuladores del estudio.

⚠️ Las cifras de tamaño de mercado APAC siguen divergiendo (una fuente da **9,45 B USD en 2025**,
otras bastante más). Citar la regulación y la demanda física, no el tamaño.

### Actualización del duodécimo pase (2026-11-20) — APAC

**El hallazgo de este pase en APAC no es regulatorio: es que la región tenía un ecosistema de código
abierto completo que esta KB no había visto. Australia pasa de 2 repos a más de 30, y el motivo de la
ceguera era el vocabulario — se nombran por el instrumento regulatorio local (`ISP` = Integrated
System Plan) y por el centro universitario (`CEEM`), no por el sector.**

#### El cuadro regulatorio, con los cuatro regímenes separados

- **Corea del Sur — el más duro y ya en vigor.** La **AI Basic Act** entró en vigor en **enero de
  2026** y es descrita como la primera legislación nacional integral de IA del mundo. Es el régimen
  que impone más carga de cumplimiento de la región.
- **China — el más estricto en contenido y registro.** Registro obligatorio, etiquetado de contenido
  y sanciones de hasta **50 millones de CNY**. Más de **550 servicios de IA generativa registrados a
  mediados de 2026**. En energía, **State Grid China** ya usa IA para reconocimiento de imagen y voz
  en gestión de activos, e IA generativa para detección de faltas — es el operador más avanzado del
  mundo en despliegue real, y no publica código.
- **Japón — *soft law* deliberado.** La **AI Promotion Act** (aprobada el 28 de mayo de 2025, en
  vigor el 4 de junio de 2025) es una ley marco **sin sanciones**. En energía, Japón anunció planes
  de **reubicar centros de datos junto a emplazamientos de eólica marina y nuclear**.
- **India — sin ley específica.** Guía nacional de gobernanza de IA de **noviembre de 2025** del
  MeitY, y **incentivos fiscales a datacenter en el presupuesto de 2026**.

#### La restricción física, que en esta región manda sobre la regulatoria

- **Esperas de conexión de red de 5 a 10 años** en muchas jurisdicciones de la región; las
  limitaciones de red alargan los plazos de desarrollo **varios años** en los mercados clave.
- **India, calidad de suministro:** la red varía **±5 % en tensión y ±1 Hz en frecuencia de forma
  rutinaria**. Consecuencia directa de diseño: cualquier carga sensible necesita acondicionamiento
  propio, y **Reliance Industries está construyendo plantas de generación cautiva** para su
  infraestructura de IA — lo que **fragmenta la red** y crea el problema de coordinación que luego
  hay que resolver.

**Cómo vender aquí, y es distinto de las otras regiones:** en North America y EMEA el gancho es el
**cumplimiento** (orden de la FERC, esquema de calificación de la UE). En APAC el gancho es la
**restricción física** — conexión, calidad de suministro, generación cautiva. La propuesta que entra
es la que reduce el plazo de conexión o sustituye red por flexibilidad, no la que produce un
expediente.

#### Lado open source: Australia es ahora la región mejor cubierta de APAC

- **`Open-ISP`** reimplementa en abierto la metodología del **Integrated System Plan de AEMO** —que
  AEMO **no publica**—: `ISPyPSA` (31 ★, push el día de este pase), `isp-trace-parser`,
  `isp-workbook-parser` (lee el **IASR** desde los Excel de AEMO). **Los tres GPL-3.0.**
- **`UNSW-CEEM`** (29 repos barridos) es de hecho el proveedor de datos abiertos del NEM:
  **`NEMOSIS`** (113 ★, GPL-3.0-or-later — la API decía `NOASSERTION`, ver T31), **`NEMSEER`**
  (GPL-3.0, pronósticos), **`nempy`** (71 ★, **BSD-3**, procedimiento de despacho), **`NEMED`**
  (**BSD-3**, emisiones), **`DER_disturbance_analysis`** (**MIT**).
- ⚠️ **La frontera de licencia es la decisión de arquitectura de cualquier proyecto australiano:**
  copyleft en la **capa de datos** (inevitable: no hay producto del NEM que no pase por `NEMOSIS`),
  permisivo en la **capa de modelo**. Aislar GPL tras un servicio separado y embeber sólo `nempy` y
  `NEMED`. Ver **T32** y **Receta 31**.
- **`UNSW-CEEM/Pacific_Islands_Energy_Balance`** es el único activo de esta KB que cubre los países
  insulares del Pacífico — **sin licencia declarada**, por tanto bloqueado, pero vale saber que
  existe.
- **Gaps declarados, con nombre:** **cero repos institucionales de Grid-India, AIST (Japón) y KEPCO
  (Corea).** De India sólo hay proyectos comunitarios de un autor
  (`randomaban-beep/india-power-demand-pipeline`, MIT, ingiere informes diarios y telemetría SCADA de
  Grid-India con ERA5; `carobashok/grid-india`, desde los PDF del NLDC). **No se encontró evidencia
  alguna de publicación de código por AIST ni por KEPCO** — se declara en vez de dejarlo en silencio.
  **State Grid China** despliega IA a gran escala y **no publica**: el mayor asimétrico de la región
  entre capacidad y apertura.

#### Actualización del decimotercer pase (2026-11-20)

**Tamaños de mercado nacionales (estimaciones de consultora, baja confianza).** Se registran porque
la KB no tenía cifra por país en APAC, con la advertencia habitual de este archivo —las consultoras
no concuerdan entre sí y estas cifras no están corroboradas por una segunda fuente independiente:

| País | IA en energía 2025 | 2026 (proyectado) |
|------|--------------------|-------------------|
| Japón | ~USD 1,31 B | ~USD 1,66 B |
| India | ~USD 1,19 B | ~USD 1,52 B |

⚠️ **Usar la forma, no el número**: ambos mercados crecen ~27 % interanual según la misma fuente, y
China sigue descrita como el mayor mercado de la región. Para una propuesta sirve el orden de
magnitud ("mercado nacional de mil millones de dólares, creciendo a dos dígitos altos"), no el decimal.

**Restricción estructural de Japón que cambia el diseño técnico:** la red japonesa está
**fragmentada y opera a dos frecuencias distintas** (50 Hz / 60 Hz). No es una curiosidad: significa
que un modelo de optimización o un agente de balance entrenado sobre un área **no se transfiere** a
la otra sin re-parametrizar, y que la interconexión entre áreas es un recurso escaso y caro. Cualquier
propuesta de "optimización nacional" en Japón que no nombre esta restricción se delata como genérica.
Utilities como **Chubu Electric** ya operan sistemas propios de IA para operación de red.

**India — los dos anclajes de política que dan presupuesto:** la **National Smart Grid Mission** y el
objetivo nacional de **500 GW de capacidad no fósil para 2030**. El crecimiento está acoplado a
**datacenters + renovables** (el plan de ~USD 100 B de Adani se presenta como ancla de infraestructura
de IA sobre energía renovable). La restricción declarada por las propias fuentes: **madurez desigual
de la red y huecos de infraestructura digital** — es decir, en India el trabajo previo a cualquier
agente es de **datos e instrumentación**, no de modelo.

**China:** la IA en energía está tratada como **prioridad estratégica nacional** con financiación
central para redes inteligentes e integración de renovables en el marco del **14.º Plan Quinquenal**.
Se mantiene lo que la KB ya registraba de las reglas de la NDRC/NEA.

📄 **Fuente primaria disponible y no leída (tarea concreta para el próximo pase):** la IEA publica
**"Energy and AI in East Asia"** (`iea.blob.core.windows.net`). Es un informe de agencia
intergubernamental, no de consultora — **la mejor fuente de esta región que esta KB tiene
identificada y aún no ha abierto**. Debería ser la primera lectura del próximo pase de APAC, por
delante de cualquier búsqueda nueva.

### Actualización del decimocuarto pase (2026-11-21) — APAC

**El gap regulatorio de APAC se cierra parcialmente, y con dos instrumentos fechados y de país.**
Los pases 12 y 13 registraron "cero texto regulatorio de nivel país alcanzable" en APAC y lo
anotaron como **no establecido, no como cobertura**. Ese cero se rompe:

| País | Instrumento | Fecha | Qué hace |
|------|-------------|-------|----------|
| **Vietnam** | **Tarifa de dos partes para almacenamiento en baterías** | **enero de 2026** | Separa **cargo por capacidad** y **cargo por energía** |
| **India** | **CEA Cyber Security in Power Sector Regulations, 2026** | 2026 | Regulación de ciberseguridad del sector eléctrico; existe *crosswalk* abierto a NIST CSF 2.0 |

Dos observaciones de método sobre **cómo** aparecieron, porque las dos son reutilizables:

1. La tarifa vietnamita apareció en prensa sectorial de **almacenamiento**, no en búsquedas de
   "regulación IA energía". **La regulación que importa para un proyecto de flexibilidad no se
   publica bajo la etiqueta "IA".** Se publica como tarifa, como código de red o como norma de
   ciberseguridad.
2. La regulación india apareció **dentro de GitHub**, en
   [`Johnbjoseph-cybersec/india-ot-regulation-crosswalk`](https://github.com/Johnbjoseph-cybersec/india-ot-regulation-crosswalk)
   (MIT) — un repo que **mapea la norma del CEA contra NIST CSF 2.0**. Es la primera vez en esta KB
   que **el canal que sí resuelve (GitHub) entrega texto regulatorio** que el canal web no entregaba.
   **Regla nueva: cuando el lado demanda no resuelve, buscar la norma como artefacto de cumplimiento
   en GitHub** (`crosswalk`, `mapping`, `checklist`, `compliance`), no sólo como documento.

#### La restricción estructural de la región, ahora desde fuente primaria y generalizada

La KB venía sosteniendo, a partir de Japón, que la **fragmentación de red** impide que los modelos
se transfieran entre áreas (el caso de las **dos frecuencias** japonesas). El informe **IEA "Energy
and AI in East Asia"** (anunciado **7-abr-2026**) lo eleva a rasgo **de toda la región**: *la falta
de interconexiones transfronterizas en East Asia* implica que la IA debe resolver la gestión del
sistema **dentro de cada país**.

**Eso deja de ser una curiosidad japonesa y pasa a ser la tesis de entrada en APAC:** en esta región
**no se vende una plataforma regional**, se vende **un despliegue por país**, porque el sistema
eléctrico no está acoplado. Es un argumento que sube el precio del proyecto y a la vez lo hace
defendible, y conviene decirlo literalmente en una propuesta.

Otras cifras del informe, todas snippet-sourced:

- El consumo eléctrico de los **datacenters de la región se espera que **más que se duplique**.
- **~6 de cada 10 chips** del mundo (GPU o CPU) se fabrican en la región: APAC es a la vez **demanda
  de electricidad y cuello de botella del suministro global de silicio**.
- Uso principal de IA identificado: **integración de renovables variables** (solar y eólica).
- Japón, Corea, China y Chinese Taipei tienen **objetivos de net zero** declarados.

#### El dato de adopción, y confirma el cero más persistente de esta KB desde el lado demanda

Presentación del **ADB** — *Enabling AI Implementation in the Energy Sector* (Asia Clean Energy
Forum, jun-2026):

- **33 % de adopción de IA** en el sector energético (atribuido a IEA, 2025).
- Causas del hueco: **falta de política, gobernanza y estándares**, y disponibilidad limitada de datos.
- **71 % de los pilotos se estancan** antes de producción (atribuido a McKinsey, 2025).
- La IEA añade la frase que importa: **la adopción de IA sigue siendo limitada en la operación de red
  crítica para el sistema**, aun donde el valor potencial es claro.

Esa última línea es **confirmación independiente y desde el lado institucional** del cero que esta
KB midió siete u ocho pases contando repos: no es que no se hayan encontrado los agentes de
operación de red — **es que la operación de red es donde la IA todavía no ha entrado**, y lo dice la
IEA. Cuando un cliente pregunte *"¿por qué no hay agentes de red open source?"*, hay ahora dos
mediciones independientes, una de oferta (GitHub) y una de demanda (IEA), que apuntan al mismo sitio.

- **ArkTerra Partners**: **24,2 GW** de capacidad de datacenter anunciada en **nueve mercados APAC**
  para 2025-2030, con el aviso de que **sin almacenamiento de larga duración** ese pipeline arriesga
  consolidar suministro respaldado por fósiles.

#### Lado open source: dos repos de origen APAC nuevos

- [`mesmo-dev/mesmo`](https://github.com/mesmo-dev/mesmo) — **MIT** (byte-read, 1.099 B), 67 ★ /
  17 forks / 15 issues. *Multi-Energy System Modeling and Optimization*. Origen **TUMCREATE
  (Singapur)**, según el copyright del propio `LICENSE`. ⚠️ **Sin push desde 2024-09-03**: es
  referencia de modelado multi-vector, no base viva.
- [`172629438/loomgrid`](https://github.com/172629438/loomgrid) — **MIT** (byte-read, 1.078 B), 2 ★.
  Dimensionamiento de almacenamiento comercial e industrial (C&I), descripción bilingüe
  chino/inglés. Origen **China**. Tracción nula: se registra por procedencia, no se recomienda.

⚠️ **Instrumento:** `iea.blob.core.windows.net` **no resuelve** desde este entorno (sexto host
primario confirmado muerto). El PDF del informe East Asia está **localizado pero no leído**: el open
item del pase 13 pasa de *"identificado, no leído"* a *"identificado, ilegible desde este entorno,
contenido snippet-sourced"*. **No es cobertura; es un gap con el límite medido.**


#### Actualización del decimoquinto pase (2026-11-21) — APAC

**El *open item* más antiguo de esta KB queda parcialmente cerrado, y el número que entrega es el
más importante de toda la serie para la capa agéntica.** El informe de la IEA **"Energy and AI in
East Asia"** —identificado pero sin leer desde el pase 13— sigue **sin poder leerse byte a byte**
(`iea.blob.core.windows.net` **no resuelve** desde este entorno; es otro host primario muerto
confirmado). Pero sus cifras llegaron por snippet de la propia comunicación de la IEA y de cobertura
secundaria:

> **Sólo el 23% de los operadores de red de Asia Oriental usa IA en operación en tiempo real,
> frente al 54% que la usa en planificación del desarrollo de la red.** La IEA atribuye la
> diferencia a **preocupaciones de fiabilidad**: muchos operadores **evitan deliberadamente** el uso
> en tiempo real.

**Por qué esto reorienta la propuesta en APAC.** La KB venía imponiendo la restricción de
arquitectura por criterio propio; el pase 14 la encontró publicada por NERC. Este dato la mide
**desde el lado de la demanda y con dos cifras comparables**: el mercado ya eligió, y eligió
planificación por más del doble. La consecuencia es direccional y se puede decir sin matizar: **en
APAC se vende agente de planificación, estudio y desarrollo de red; no agente de control en tiempo
real.** Y el 23% no es inmadurez del cliente a la que convencer — **es su política de riesgo**, que
coincide con la del regulador de NA. Discutirla es perder la reunión.

**Resto de lo que entrega el informe** (todo por snippet, ⚠️ sin lectura directa):

- Publicado en **abril de 2026**. Se reporta coproducción con el **Korea Energy Economics
  Institute** ⚠️ sin verificar.
- El consumo eléctrico de los centros de datos de la región **se espera que más que se duplique**.
- **Casi 6 de cada 10 chips** del mundo —GPU o CPU— se fabrican en la región: la exposición de APAC
  a la IA es **industrial además de eléctrica**.
- **KEPCO** (Corea, estatal) está desarrollando un modelo de IA para **optimización de red**: un
  incumbente regional con nombre, es decir un competidor y a la vez un comprador potencial de capa.
- **La falta de interconexiones transfronterizas** en Asia Oriental hace que el valor de la IA sea
  **intra-país**. Esto **generaliza a toda la región** lo que la KB tenía medido sólo para Japón (las
  dos frecuencias de red, pases 13–14): **los modelos no transfieren entre países**, y por tanto
  **se vende despliegue país por país, nunca una plataforma regional**.

**El gap regulatorio de APAC se cierra con un instrumento vinculante y fechado** —era el déficit
admitido de la región durante varios pases:

- **Corea del Sur** tiene el marco más duro de la región: la *Framework Act on the Development of
  Artificial Intelligence and the Creation of a Foundation for Trust* (**"AI Basic Act"**) **entró
  en vigor el 22 de enero de 2026**. Obliga a quien provee IA **de alto impacto** o generativa a
  **notificar al usuario con antelación** y a **etiquetar las salidas generativas**. Si la IA de red
  se lee como de alto impacto, **es el primer deber con forma de expediente de toda APAC** — y
  Corea es además donde está KEPCO.
- **Japón**: la *AI Promotion Act* sigue siendo de mano ligera. El **segundo AI Basic Plan** se
  aprobó en **julio de 2026**, pero es **documento de estrategia, no ley**.
- **India**: en **julio de 2026** el gobierno señaló que puede ir a **legislación de IA dedicada**,
  con modelo **basado en riesgo** esperado. Su presupuesto 2026 adoptó **incentivos fiscales para
  centros de datos**. ⚠️ Las fuentes se contradicen sobre el estado actual: una dice que no hay ley
  dedicada, otra reporta el giro. Registrar como **en transición**, no como régimen.
- Restricción física citable: las **esperas de conexión a red llegan a 5–10 años** en muchos
  mercados.

⚠️ **Lo que sigue sin establecerse:** no se encontró **ninguna regla específica de IA en sistemas de
energía** en Japón ni en Corea. La regulación que existe es **transversal de IA**, no sectorial
eléctrica. Eso es un hueco de conocimiento declarado, no cobertura.

**La oferta de origen APAC se mueve por segunda vez, ahora con licencia leída byte a byte:**
[`ruikelyu/Real-time-operation-strategy-of-virtual-power-plants`](https://github.com/ruikelyu/Real-time-operation-strategy-of-virtual-power-plants)
(MIT, 65 ★, push 2026-11-08) y
[`ronaldowzy/price_forecast`](https://github.com/ronaldowzy/price_forecast) (MIT, 25 ★, mercados
eléctricos de China). Sigue siendo una capa delgada y académica, pero el "cero de oferta APAC" ya no
se puede escribir.

### Actualización del pase 16 (2026-11-24) — APAC

**La región pasa de un instrumento vinculante a dos, y uno nombra al sector energético en su texto.**

- **Corea — AI Framework Act (AI Basic Act), en vigor 22-ene-2026.** Novedad de este pase sobre lo
  registrado en el pase 15: **obliga a desarrolladores y a implementadores (*deployers*)**, y los
  sectores que enumera incluyen **energía**, agua potable, salud y nuclear. **La energía está
  nombrada.** Corea es además donde **KEPCO** construye su propia IA de optimización de red.
- **Vietnam — primera ley de IA, en vigor 1-mar-2026**, basada en riesgo, con **decreto de
  implementación del 30-abr-2026**. Más la **Resolución 253/2025/QH15**, con mecanismos especiales
  para el desarrollo energético nacional **2026-2030**: ley de IA y política energética avanzando en
  paralelo en el mismo país.
- **China:** el marco más extenso vigente, por capas (recomendación algorítmica, *deepfakes*, IA
  generativa).
- **Indonesia:** hoja de ruta nacional de IA como Reglamento Presidencial, **pendiente**, esperada
  en el primer semestre de 2026.
- **Singapur:** MAS en consulta sobre **AI Risk Management Guidelines**; objetivo de **medición
  avanzada nacional en 2026**.
- **Australia:** la **AEMC** tiene regla de **medidores inteligentes universales en el NEM para
  2030** y está revisando cómo los datos de la era IA pueden sostener el sistema energético.
- **Tailandia:** borrador de reglas de centros de datos que permitiría a los promovidos por el **BOI
  contratar directamente con generadores renovables**, con transporte por la red (*wheeling*).

> **Matiz que se vende, y hay que mantenerlo exacto.** **Sigue sin existir norma de IA específica del
> sector energético en Japón o Corea.** Lo que hay es **ley transversal de IA que nombra la energía
> como sector cubierto**. La obligación llega por la vía horizontal: el expediente se construye
> contra la ley de IA del país, **no** contra el regulador eléctrico. Esa distinción es el encuadre
> correcto de una propuesta de cumplimiento en la región.

**Capa blanda regional, nueva.** **APEC AI Initiative (2026-2030)**, adoptada en la Declaración de
Líderes de **Gyeongju (2025)**. Los **ministros de Energía** reunidos en **Pekín** bajo la
presidencia china de 2026 respaldaron recomendaciones de cooperación IA-energía, con **tres hojas de
ruta de consenso hasta 2030**, y encargaron al **Energy Working Group** crear un grupo dedicado a IA
y energía. Metas reafirmadas: **duplicar la cuota de renovables respecto de 2010 para 2030** y
**-45 % de intensidad energética respecto de 2005 para 2035**. En **abril de 2026** el foro
**EGNRET** reunió siete economías APEC con **APERC, IEA e IRENA** sobre IA en **pronóstico,
optimización de red y energía inteligente**.
⚠️ Texto completo de las recomendaciones **no localizado**; fecha exacta de la reunión de Pekín y
contenido de las hojas de ruta **sin confirmar** (ítem 16-R3).

**La restricción física se reconfirma, con la misma magnitud.** **IBM**: la infraestructura de IA se
construye en **1-2 años** y las mejoras de red tardan **5-10 años**, desajuste que describe como
**agudo en APAC** — coincide con los «5-10 años de cola de conexión» que esta KB registró en el
pase 15 por otra fuente.

**Oportunidad concreta:**
1. **Agente de planificación, nunca de tiempo real** (receta 52, sin cambios): sigue siendo la
   lectura correcta, y el 23 % frente al 54 % del pase 15 sigue siendo el número que lo sostiene.
2. **Expediente de notificación previa y etiquetado** para Corea (alto impacto y IA generativa) y
   **expediente de riesgo** para Vietnam: **dos jurisdicciones con fecha y con deber de forma**.
3. **Despliegue país por país, nunca plataforma regional** — sin interconexiones transfronterizas,
   el valor es intra-país y los modelos no transfieren (pase 15, se mantiene).

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

**Actualización del sexto pase (2026-11-20) — el gap de oferta LATAM está cerrado, y el cuello de botella regional ya tiene cifra**

- **Cerrado: existen modelos de sistema eléctrico nacional de Chile y México con licencia MIT.** La
  recomendación con la que cerró el quinto pase —*buscar `PyPSA-CL`, `PyPSA-MX` y `PyPSA-BR` por
  nombre*— era correcta. Se encontraron **cuatro** modelos nacionales sobre PyPSA, **tres MIT**
  (`paredes-vergara/PyPSA-CL` 15 ★, `sanjaygrr/pypsa-chile`, `BrandolRuizOlmeda/pypsa-mexico_base`) y
  uno **sin licencia** (`leonardovbonatto/pypsa-meets-brazil`, SIN brasileño con física de hidráulica
  — el técnicamente más valioso y el inutilizable). Detalle completo en `repos/foundations.md`.
  **La frase "LATAM no produce repos energéticos" queda retirada de esta KB**: era un gap de
  vocabulario de búsqueda, sostenido durante cinco pases.
- **Lo que esto vale en una propuesta chilena o mexicana**: la topología, el parque generador y las
  series del **Coordinador Eléctrico Nacional**, la CNE y el Ministerio de Energía de Chile, y del
  **Mercado Eléctrico Mayorista** mexicano, ya están mapeados a un formato que `linopy` resuelve.
  Es el trabajo caro de las primeras semanas, hecho y público. No es comunidad (0–15 ★) y no debe
  venderse como tal: es **punto de partida verificable**.
- **La restricción regional, ahora con número**: Moody's sitúa la capacidad instalada de datacenter
  de la región en unos **2.340 MW a principios de 2026**, creciendo **15–20 % anual**, y —el punto
  importante— sostiene que la expansión de la IA en América Latina estará limitada **menos por la
  demanda, que es alta, y más por la capacidad de suministrar energía**. Es la tesis central de esta
  KB en su forma más nítida: en LATAM el cuello de botella es físico, no comercial.
- **Brasil, el dato que mejor explica el apetito**: los datacenters representaron **un tercio de los
  PPA bilaterales** del país en 2024. Corrobora lo que los pases anteriores ya registraron
  (85 % renovable, Eletrobras con C3.ai monitorizando fallos de red en tiempo real, 3,6 M de
  medidores inteligentes).
- **Chile, el caso de uso ya en producción**: integra **pronóstico renovable basado en IA** para
  optimizar el uso de energía limpia, con previsión de **irradiancia solar** aplicada al despacho.
  Brasil, Uruguay y México aplican IA a modernización de red y planificación de infraestructura.
  **Nótese la coincidencia**: el país con el caso de uso de despacho más maduro es el que acaba de
  aparecer con **dos modelos MIT de su propio sistema**. Chile es, por tanto, el mejor candidato de
  la región para un piloto agéntico de despacho con base open source verificable.
- **Gobernanza, y es una puerta de entrada**: un informe del **Stimson Center con CAF**, elaborado con
  Microsoft, define el despliegue responsable de IA en energía y sostiene que exige **gobernanza
  transparente, colaboración transfronteriza y planificación de infraestructura a largo plazo**.
  **OLADE** trata el tema en su semana de la energía ("de los datos a los megavatios") y enumera los
  huecos regionales: red, regulación, talento especializado, conectividad y sostenibilidad. CAF,
  OLADE, CENIA y Stimson son interlocutores institucionales reales para un encargo regional.
- **Las barreras, según quien pone el capital**: regulación, permisos, financiación y riesgo de
  ejecución; con una petición explícita de **regulación clara que garantice capacidad de potencia a
  las grandes cargas**. Ese es el expediente donde un estudio de IA puede aportar
  —modelado de impacto de una gran carga en el sistema— y los modelos MIT de arriba son precisamente
  la herramienta para hacerlo.
- ⚠️ **Lo que sigue sin existir en LATAM**: ningún repo institucional de utility u operador con
  tracción, en español o portugués. Lo que hay es **obra de individuos** (Ricardo L. Olsen en Brasil;
  los autores de los modelos PyPSA de Chile y México) y de **la academia**. La consecuencia práctica
  no cambia: la autoría regional existe y es citable, pero **no hay un proyecto regional al que
  sumarse**. Crearlo sigue siendo una oportunidad de posicionamiento abierta.

#### Actualización del séptimo pase (2026-11-20): LATAM tiene el detalle regulatorio más fino de las cuatro regiones, y el cuello de botella no es la red

El sexto pase cerró el gap de **oferta** (cuatro modelos nacionales, tres MIT). Este pase cierra el de
**demanda**: hay detalle regulatorio país por país, y apunta todo en la misma dirección.

**Brasil — líder regional y el regulador más activo:**

| Hecho | Cifra / fecha |
|-------|---------------|
| Participación de Brasil en la capacidad de cómputo identificada de la región | **~92 %** |
| Datacenters en operación | **205** |
| Solicitudes de acceso a la red | **38 GW** |
| Ley de modernización del marco regulatorio | **Ley 15.269**, nov 2025 |
| Marco regulatorio de **almacenamiento** | en redacción |
| Proyección del **ONS**: curtailment por desbalance estructural oferta-demanda para 2029 | **hasta 96 %** |

Ese **96 % de curtailment estructural para 2029** es el dato de venta de la región: no es un problema
de pronóstico ni de mantenimiento, es un problema de **flexibilidad y colocación de carga**, que es
exactamente la *Receta 4* (flexibilidad de carga de datacenter como producto de red). ⚠️ Una fuente
menciona que **REDATA** se promulgó en septiembre de 2026, pero **no se pudo confirmar de forma
independiente**: no citarlo.

**Chile — el perfil es estabilidad y sostenibilidad, no escala:**

- El Comité de Desafíos del Futuro del **Senado** aprobó **en general** el proyecto de ley de IA por
  **4-0 el 26 de octubre**, con **4 de diciembre** como plazo de indicaciones. Chile es el país de la
  región con la regulación de IA más avanzada en trámite.
- **Decreto 70** introdujo un mecanismo de **pago por capacidad** que da retornos predecibles al
  inversor en almacenamiento.
- ⚠️ Su restricción real es el **permisología ambiental**: licencias que han congelado o cancelado
  proyectos de alto perfil. Un cronograma de proyecto en Chile debe presupuestar permisos, no sólo
  ingeniería.

**México — el problema es el acceso a la red, y ahora también el agua:**

- El proceso de **interconexión** sigue siendo opaco en **costo y plazo** de los refuerzos de red.
- El **agua** emergió como restricción: el endurecimiento de las reglas de concesión de agua responde
  en parte a esta tensión.
- El almacenamiento se está escribiendo en la ley: requisitos incorporados a la **Ley para el
  Aprovechamiento de Energías Renovables**.

**El hallazgo transversal que reordena la propuesta regional.** Un análisis del sector lo dice
directamente: el límite **no es la red ni la economía subyacente** — las barreras son **regulación,
permisos, estructuras de financiamiento y riesgo de ejecución**. La región tiene **más de 10 GW de
capacidad renovable lista para red** que podría ponerse a disposición de cargas grandes en los
próximos dos o tres años. ⚠️ Esa cifra proviene del análisis de **un solo desarrollador**: tratarla
como indicativa.

**Lo que eso significa para Globant, dicho sin adornos:** en LATAM el trabajo de mayor valor **no es
optimización algorítmica** sino **ingeniería de viabilidad** — análisis de cola de interconexión,
expedientes de permisos, modelado de escenarios de curtailment y casos de inversión. Las piezas ya
están en la KB: los cuatro modelos nacionales MIT del pase 6 (`PyPSA-CL`, `pypsa-chile`,
`pypsa-mexico_base`, `PyPSA-AR`, `pypsa-meets-brazil`), `gridstatus` y las APIs de XM. La *Receta 24*
(copiloto de despacho sobre el modelo nacional publicado) y la *Receta 7* (sandbox de mercado para
decisiones de inversión y política) son las dos que este detalle regulatorio vuelve inmediatamente
vendibles.

⚠️ **Nota de política pública que conviene conocer antes de una reunión:** un digest regional señala
que los incentivos propuestos **no exigen** a las empresas reservar capacidad de cómputo para uso
local ni divulgar consumo de energía y agua. Es un punto de fricción pública creciente, y un cliente
que anuncie un datacenter sin una respuesta preparada sobre energía y agua tendrá un problema de
licencia social.


#### Actualización del octavo pase (2026-11-20): Brasil ya es escala, México es el cuello de botella, Argentina es la apuesta

**Brasil — pasó de promesa a capacidad instalada, y el límite es la entrega de red.**

- Cruzó el umbral de **1 GW comisionado** en el primer trimestre de 2026, con São Paulo, **Campinas**
  y **Fortaleza** como anclas.
- El Ministerio de Minas y Energía reportó **205 datacenters en operación en junio de 2026** y
  **38 GW en solicitudes de parecer de acceso a red**. ⚠️ **Los 38 GW son solicitudes, no capacidad
  construida** — la distancia entre ambas cifras *es* el mercado de ingeniería de viabilidad.
- Red limpia como ventaja vendible: entre **80 % y 90 % renovable** según fuente, con del orden de
  **12 GW de capacidad de transmisión disponible**.
- **Regulación que habilita**: **REDATA** promulgada como **Lei 15.504 el 15 de septiembre de 2026**;
  y en septiembre de 2026 **ANEEL autorizó acceso directo a la red de alta tensión**, con un proyecto
  que planifica **1,8 GW de demanda para 2033**.
- **Contratos con nombre propio**: Microsoft, con dos salas nuevas en São Paulo dentro de un
  compromiso de **2.700 M USD**; **Equinix** con un **PPA con Auren Energia** por eólica y solar; y
  **ByteDance** con un compromiso de **200 MW** en Fortaleza en un sitio que **Omnia Data Centers**
  empezó a construir en el primer trimestre.

**México — la demanda existe, la red y el permiso no acompañan.**

- **Querétaro concentra en torno al 70 %** de los datacenters del país, incluidos sitios de AWS y
  Google, con una red que no fue diseñada para cargas así. En **El Marqués** las autoridades están
  **programando cortes de energía** para evitar el colapso del sistema.
- **Tiempos de conexión**: un desarrollador cita **al menos ocho meses** en circunstancias normales
  para obtener un contrato de conexión eléctrica.
- **Proyección de demanda**: la industria espera **1.730 MW para 2031**, unas **6,2 veces** la
  capacidad instalada reportada de **279 MW en 2026**.
- **Matriz**: la electricidad mexicana proviene de forma abrumadora de **gas natural**, y las
  asociaciones empresariales argumentan que hace falta mucha más renovable para atraer inversión de
  IA. La **Asociación Mexicana de Data Centers (MEXDC)** advierte que proyectos se están **desplazando
  a Brasil y Chile** por el retraso de la planificación energética.
- **Coordinación institucional nueva**: **CFE y MEXDC** establecieron un arreglo de coordinación en
  **septiembre de 2026** para planificar el suministro de los sitios nuevos. Es la puerta de entrada
  institucional para trabajo de planificación en México.
- ⚠️ **Los conteos de instalaciones varían entre fuentes** (71 vs. 66 para México; 225 vs. 218 para
  Brasil). Usar el orden de magnitud y la proporción —Brasil es ~3× México—, no la cifra exacta.

**Argentina — una sola apuesta, muy grande y aún no firme.**

- **OpenAI y Sur Energy** firmaron en octubre una carta de intención por un proyecto de hasta
  **25.000 M USD en Patagonia**, que se construiría bajo el régimen de incentivos **RIGI**.
- ⚠️ **Es carta de intención, no inversión comprometida.** El dato útil no es la cifra sino **qué
  habilita el RIGI**: un cliente argentino preguntará por la estructura del incentivo antes que por
  la arquitectura.

**Lo que esto cambia en la propuesta LATAM, y es un cambio real respecto de pases anteriores.** La KB
venía diciendo que en LATAM el trabajo de mayor valor es **ingeniería de viabilidad** y no
optimización algorítmica. Este pase lo confirma y lo especializa por país:

| País | El problema del cliente | El entregable que lo resuelve |
|------|------------------------|------------------------------|
| **Brasil** | 38 GW de solicitudes contra 12 GW disponibles; acceso directo a AT recién autorizado | Priorización de cola de acceso y casos de PPA (`pypsa-ppa` MIT + `pypsa-meets-brazil`) |
| **México** | Querétaro saturado, 8 meses de conexión, matriz de gas | Análisis locacional alternativo y modelado de escenarios (`pypsa-mexico_base` MIT) vía la mesa CFE-MEXDC |
| **Chile** | Receptor del desplazamiento desde México | Estudio de viabilidad comparada (`PyPSA-CL`, `pypsa-chile` MIT) |
| **Argentina** | Estructura de incentivo RIGI antes que tecnología | Caso de inversión y modelado de escenarios (`PyPSA-AR` MIT) |

⚠️ **Y la advertencia de licencia social que ya estaba, ahora con evidencia regional**: un informe
sostiene que los datacenters latinoamericanos se **venden como renovables y se alimentan de fósiles**.
Un cliente que anuncie un datacenter sin una respuesta preparada sobre energía y agua tendrá un
problema público — y la respuesta preparada es un entregable.


#### Noveno pase (2026-11-20) — el número que abre la conversación en Brasil, y el mapa regulatorio contado

**El dato de apertura comercial de la región: Brasil tiró el 20,6 % de su generación eólica y
solar.** El *curtailment* alcanzó el **20,6 % del total de generación eólica y solar en 2025** (New
Energy Events). Es exactamente el problema que resuelve la pila que esta KB ya tiene catalogada
—forecasting (`openstef`, `epftoolbox`), flexibilidad (`FlexMeasures`) y despacho (`PyPSA`)— y se
puede plantear como ahorro medible, no como modernización abstracta.

Alrededor de ese número:

- **REDATA**: régimen tributario especial **propuesto** que suspendería impuestos federales y
  derechos de importación sobre equipamiento de datacenter (servidores, transformadores). Es
  **propuesta, no ley**: condiciona el *business case*, no lo garantiza.
- **Ventana declarada**: "**10 GW en 18 meses**" es como el sector enmarca la oportunidad
  latinoamericana de alimentar la era de la IA (New Energy Events).
- **Costa Rica** tiene marco legal establecido para renovables y generación distribuida, con
  procedimientos que los analistas piden simplificar.

**Mapa regulatorio de IA, que en esta región es fragmentación y conviene tenerlo ordenado:**

- **716 instrumentos regulatorios de IA en 23 países y territorios**, más del **80 % iniciados desde
  2023** (estudio 2026 de la Universidad de los Andes). La consecuencia práctica: no existe "el
  marco LATAM", existe el marco del país del cliente.
- **Perú es el único con ley de IA promulgada**: **Ley N° 31814**, publicada en *El Peruano* el
  **5 de julio de 2023**; autoridad nacional **PCM-SGTD**.
- **Brasil**: **PL 2338/2023**, enfoque basado en riesgo, con versiones aprobadas por el Senado en
  **diciembre de 2024**; el sistema nacional lo coordinaría la **ANPD** junto a reguladores
  sectoriales. **Pendiente.**
- **Colombia**: política nacional de IA vía **CONPES 4144**, **febrero de 2025**.
- **Uruguay**: **primer país de LATAM en firmar** el Convenio Marco del Consejo de Europa sobre IA y
  derechos humanos.
- **México**: varios proyectos federales presentados, **ninguno aprobado**.
- **OCDE**: Argentina, Brasil, Chile, Colombia, Costa Rica, México y Perú adoptaron formalmente los
  Principios de IA. Foro regional: grupo de trabajo de IA de la **CEPAL** bajo eLAC.

⚠️ **Precisión que vale dinero y que surge de cruzar esta región con EMEA.** Varias fuentes
latinoamericanas advierten del alcance extraterritorial del **AI Act** citando que "el grueso de las
obligaciones entra en vigor el **2 de agosto de 2026**". Pero el *Digital Omnibus* (acuerdo político
del 7 de mayo de 2026) **movió el alto riesgo del Anexo III al 2 de diciembre de 2027** —y esa
prórroga **no es firme hasta su adopción formal**. Para un exportador LATAM que sirve usuarios en la
UE: **la fecha a planificar sigue siendo la original**, y la prórroga es margen, no plan. Decirlo
así es asesoría; repetir una sola de las dos fechas es un error.

**Oferta de origen LATAM: ya son dos repos institucionales, y el segundo es de hoy.**

| Repo | Licencia | Qué es | ★ | Push | País |
|------|----------|--------|---|------|------|
| [batuenergy/atlas-sen](https://github.com/batuenergy/atlas-sen) | **MIT** (rescatada en `LICENSE` crudo; la API dice `NOASSERTION`) | Atlas abierto del **Sistema Eléctrico Nacional** mexicano: generación y transmisión | 10 | **2026-11-20** | **México** |
| `riclolsen/json-scada` + `OSHMI` *(ya catalogados)* | GPL-3.0 | SCADA/EMS y HMI de subestación | 513 / 467 | 2026-11-17 | **Brasil** |

Y dos matices honestos sobre la misma búsqueda:

- **El scraper de CENACE está muerto**: `AngelCarballoCremades/CENACE-Scraper-Dashboard`, **sin
  licencia**, 7 ★, **sin push desde 2021**. La vía viva para México es `atlas-sen`.
- [`Mcp-Brasil/mcp-brasil`](https://github.com/Mcp-Brasil/mcp-brasil) (**MIT**, 1.867 ★, 293 forks)
  es un servidor MCP para **70 APIs públicas brasileñas** y es, con diferencia, el MCP de origen
  LATAM con más tracción. ⚠️ **No se verificó que incluya APIs energéticas** (ANEEL, ONS, CCEE): es
  un candidato a puerta de entrada de dato público brasileño, no un hallazgo energético confirmado.
  Comprobarlo es una tarea de un pase futuro, barata y de alto retorno.


### Actualización del décimo pase (2026-11-20) — LATAM

**Contexto regulatorio nuevo (fuentes secundarias):**

- **Un estudio de la Universidad de los Andes de 2026 contabiliza 716 instrumentos regulatorios
  relacionados con IA en 23 países y territorios** de la región, la mayoría iniciados **desde 2023**.
  El dato importa por su forma: no es ausencia de regulación, es **volumen sin armonización**. Para
  un cliente regional multipaís, el entregable no es "cumplir la ley de IA" —no hay una— sino un
  **mapa de obligaciones por jurisdicción**, que es trabajo de consultoría recurrente.
- **Uruguay fue el primero de la región en firmar el convenio de IA del Consejo de Europa.** Es la
  vía por la que un requisito de tipo europeo entra en la región sin pasar por el AI Act, y es
  relevante para un exportador de servicios.
- **Colombia optó por política nacional (CONPES 4144) con presupuesto hasta 2030** en lugar de reglas
  vinculantes inmediatas. Encaja con lo que esta KB ya registró: Colombia es la credencial
  **institucional** LATAM verificable (`API_XM`, de XM).
- **Argentina, Brasil, Chile, Colombia, Costa Rica, México y Perú** han adoptado los principios de
  IA de la OCDE. El WEF señala la **demanda energética** como el desafío nuevo de la región y pide
  reglas armonizadas y predecibles.
- **México: el crecimiento de datacenters en Querétaro está levantando preguntas de energía y agua.**
  Es el mismo nudo que NA y APAC —carga de datacenter contra red— con una variable añadida que en las
  otras regiones aparece menos: **agua**. Un estudio de emplazamiento mexicano que no modele agua
  está incompleto.
- **Adopción sectorial reportada**: Chile usa IA para **pronóstico y despacho de renovables**; la
  generación distribuida de Brasil empujó medidores inteligentes y gestión de energía en nube;
  Brasil, Uruguay y México aplican IA a **modernización de red**. Jugadores privados nombrados:
  **Niko Energy** (México, mapeo de techos para solar y VPP), **Ainwater** (Chile, software de IA
  para utilities de agua).

⚠️ **Una de las fuentes de adopción encontradas (`nivelics`) contiene marcadores `[VERIFY]` sin
rellenar en lugar de cifras.** No se cita ningún número de esa página. Se registra porque es el
caso más limpio de T8 que ha visto esta KB: una página que *parece* dato de adopción y es una
plantilla sin terminar.

**Oferta: Ecuador entra, Argentina sigue en cero.**

- **Ecuador aparece por primera vez**:
  [`wilianguamancuenca/EC-PowerSystems`](https://github.com/wilianguamancuenca/EC-PowerSystems) —
  **MIT, 21 ★ y 39 forks**. El ratio fork:★ de **1,86** es el más alto medido en este pase: material
  que se usa, no que se estrella. ⚠️ Último push **2024-05-02**, 18 meses. La credencial LATAM
  verificable pasa a ser **Brasil, Colombia, Chile, México y Ecuador**.
- **Argentina: cero, por sexta medición consecutiva.** `Argentina energia OR electrico
  in:name,description,readme stars:>2` → 4.358 resultados, **todos** listas genéricas globales
  (`public-apis`, `awesome-go`, `awesome-mcp-servers`). Sumado a las búsquedas previas por
  institución (CAMMESA) y por término de dominio, el gap argentino está medido desde **seis ángulos
  distintos**. No es un gap de consulta: **no hay oferta open source argentina con tracción en
  energía.** En una propuesta para Argentina, la base técnica es regional o europea, y conviene
  decirlo antes de que lo pregunten.

**Lo que el hallazgo principal de este pase significa para LATAM, dicho sin adornos:** las ~125
piezas institucionales encontradas son de **EPRI, Grid Protection Alliance y Sandia** — las tres
norteamericanas. **Son usables en LATAM** (BSD-3 y MIT no discriminan por geografía) y de hecho son
la mejor base disponible para un proyecto de utility latinoamericano: `openHistorian` para el
histórico, `openMIC` para recolección de medidores, `DLMS-COSEM` para el protocolo, `snl-quest` para
almacenamiento. Lo que **no** aportan es dato local ni modelo de red local, y eso sigue viniendo de
`API_XM` (Colombia), `atlas-sen` (México), `PyPSA-CL` (Chile), `pypsa-meets-brazil` y ahora
`EC-PowerSystems` (Ecuador). **La arquitectura correcta para LATAM es stack norteamericano permisivo
+ capa de datos local.**



### Actualización del undécimo pase (2026-11-20) — LATAM

**La tesis de este pase para LATAM, y tiene fuente: el freno no es la demanda, es la capacidad.**
Moody's sostiene que la expansión de la IA en América Latina está limitada *"no tanto por la demanda
sino por la capacidad de suministro y de ampliación de la red"*. Eso convierte el trabajo de red —
estudio de conexión, flexibilidad, almacenamiento— en la vía de entrada, por delante del caso de uso
de IA.

- **Dónde está la capacidad instalada:** a comienzos de 2026 la región albergaba unos **2.340 MW** en
  centros de datos, creciendo **15-20 % anual**. Reparto: **Brasil ≈49 %**, **México ≈27 %**,
  **Chile ≈9 %**. Moody's ve a **Brasil y Chile mejor posicionados** y advierte que las limitaciones
  eléctricas de **México** amenazan con frenar su desarrollo de IA.
- **Brasil:** el **3 de junio de 2026** ANEEL aprobó el **marco regulatorio de sistemas de
  almacenamiento**, que fija requisitos de conexión a la red. Es un mandato nuevo, con fecha, y abre
  trabajo de dimensionado y cumplimiento de BESS.
- **Chile:** 2026 es, según Garrigues, **un punto de inflexión en la regulación de BESS**. Hay además
  proyecto de ley de IA en tramitación con enfoque de riesgo similar al AI Act europeo.
- **México:** continúa la implementación de la reforma energética de 2025, con la **Ley de Planeación
  y Transición Energética** y el **Plan de Fortalecimiento y Expansión del Sistema Eléctrico Nacional
  2025-2030**. Proyectos de ley de IA en trámite (la "Ley Nahui" se menciona sin confirmar).
- **Brasil** ya cuenta con ley de IA de 2025 con marco de riesgo.

**El hallazgo más vendible del pase para LATAM, y es de ciberseguridad OT, no de IA:** un estudio de
**ADELAT** mide que el **46 % de las empresas no supervisa sus redes de operación** y que sólo el
**21 % cuenta con protección activa de los dispositivos de campo**. Y, en paralelo, la ciberseguridad
de redes eléctricas **carece de reconocimiento tarifario específico en once países de América
Latina**: el gasto no tiene vía de recuperación regulatoria. Brasil, Chile y Colombia tienen los
marcos más desarrollados — en Chile, la **Ley 21.663 (2024)** y los estándares del Coordinador
Eléctrico Nacional imponen obligaciones de protección y notificación de incidentes.

**Cómo se convierte eso en oferta:** un 46 % sin monitorización OT es una línea base de observabilidad
—no un proyecto de IA— y la KB tiene con qué atacarla con licencia permisiva: la plataforma de datos
operativos del pase 10 (`openHistorian` MIT + `openXDA` MIT + `PQDashboard` BSD-3 + Grafana) y, nuevo
en este pase, [`idaholab/STIG`](https://github.com/idaholab/STIG) (BSD-3, grafo STIX de inteligencia
de amenazas). **El argumento comercial tiene que incorporar la falta de reconocimiento tarifario**:
si el regulador no permite recuperar el gasto, la propuesta debe justificarse por riesgo evitado y
continuidad, no por retorno tarifario. Decirlo primero es lo que la hace creíble.

⚠️ **Oferta de origen LATAM: sin cambio en este pase.** El barrido por institución de este pase cubrió
organizaciones de Norteamérica (`GMLC-TDC`, `idaholab`, `pnnl`) y EMEA (`statnett`, `DTUWindEnergy`).
**No se ejecutó un barrido equivalente de instituciones LATAM** (CEPEL, ONS, XM, Coordinador Eléctrico
Nacional, CENACE, universidades) — y eso es una tarea pendiente concreta para el próximo pase, no un
cero medido. La KB ya tiene `equipoanaliticaxm` (XM, Colombia) y los `pypsa-{país}` del sexto pase,
lo que indica que la vía institucional **sí rinde** en la región.

### Actualización del duodécimo pase (2026-11-20) — LATAM

**Dos novedades, y la segunda corrige un diagnóstico que esta KB arrastraba: (1) Brasil pasó de
promesa a régimen legal con el REDATA; (2) el gap de código abierto de la región **ya no es de
existencia, es de licenciamiento** — hay repos activos de los operadores, y están sin licencia.**

#### Brasil: el único marco legal de datacenter de la región, con número e instrumento

- **REDATA promulgado como la Lei 15.504, el 15 de septiembre de 2026.** Es el régimen específico de
  datacenter, y el instrumento que hay que citar.
- **En septiembre de 2026 ANEEL autorizó el acceso directo a la red de transmisión de alta tensión**,
  con planificación de proyecto para **1,8 GW de demanda a 2033**. Esto es lo que de verdad desbloquea
  hiperescala: acceso directo sin pasar por la distribuidora.
- **Cuántos hay, y las fuentes discrepan — citar el rango, no un número:** una fuente sitúa la cuota
  brasileña por encima del **40 %** de la inversión en datacenter de LATAM; otra dice que Brasil aloja
  **225 de los más de 500** datacenter de la región; el **Ministério de Minas e Energia** reportó
  **205 emplazamientos operativos en junio de 2026**.
- **El riesgo real es municipal, no federal:** las aprobaciones municipales son un riesgo recurrente
  en la elección de emplazamiento por parte de los hiperescalares. Un proyecto se gana en el
  ayuntamiento, no en Brasilia.

#### México: la red es la restricción, y ya es visible en la calle

- **Querétaro: las autoridades están programando cortes de energía** para evitar el colapso del
  sistema en una localidad. Es el dato más duro del pase sobre el estado de la red mexicana.
- **La interconexión es opaca en coste y en plazo**, y las leyes locales no se han actualizado para
  facilitar los permisos de construcción de datacenter.
- México **debate reglas de uso de electricidad y de agua**; sigue **sin ley horizontal de IA** (la
  restricción es de energía y de permisos, no de IA).
- Lectura de mercado: **México corre riesgo de quedarse fuera** del auge de datacenter de IA por la
  restricción energética, justo cuando la cercanía a EEUU debería ser su ventaja.

#### Chile: el cuello es transmisión, no generación

- La **Comisión Nacional de Energía** advierte de que la expansión de la red **no sigue el ritmo** de
  la demanda de datacenter.
- **El licenciamiento ambiental ya congeló o canceló proyectos de alto perfil**, y la disponibilidad
  de agua es la otra preocupación. En Chile el riesgo de proyecto es **permisológico y social**, no
  de recurso: generación renovable hay.

#### El cuadro regional, con las cifras citables

- **Más de 10 GW** de capacidad lista para red en LATAM en los próximos **dos o tres años**, con el
  argumento de que **los barreras reales son regulación, permisos y financiación, no la red en sí**.
- **LATAM absorbió 328 MW en el 1T de 2026, casi el doble del total de todo 2025.** Es la cifra de
  aceleración más fuerte que esta KB tiene de la región.
- La ventana se describe como **"10 gigavatios, 18 meses"**, y se plantea explícitamente como
  oportunidad de capturar el rechazo social al datacenter en EEUU.

#### Lado open source: el muro se movió, y eso cambia la acción

Se barrieron los operadores de la región (CAMMESA Argentina, CENACE México, CENACE Ecuador,
Coordinador Eléctrico Nacional de Chile) y **hay repos activos**:

| Repo | Licencia | Push | Qué es |
|---|---|---|---|
| [`daniraggio/cammesa-dashboard`](https://github.com/daniraggio/cammesa-dashboard) | ⛔ sin licencia | 2026-11-20 | Mercado mayorista argentino; Actions cada 10 min contra `api.cammesa.com`. **Excluye demanda y generación** (CORS, sin auth documentada) |
| [`zyangarduno/CENACE-CHALLENGE`](https://github.com/zyangarduno/CENACE-CHALLENGE) | ⛔ sin licencia | 2026-11-17 | Precio marginal local, nodos de la zona de carga de Monclova (México) |
| [`pabesjimenez/cenace-monitor`](https://github.com/pabesjimenez/cenace-monitor) | ⛔ sin licencia | 2026-11-20 | CENACE de **Ecuador**: producción y demanda cada 30 min |
| [`fcingolani/cammesa-api`](https://github.com/fcingolani/cammesa-api) | **MIT** ✅ | **2017-07-28** | API no oficial de CAMMESA. Licencia limpia, **nueve años parado** |

**Tres de cuatro, bloqueados por ausencia de licencia (T20). El diagnóstico correcto ya no es "LATAM
no tiene repos": es "LATAM no licencia sus repos".** Y a diferencia de un gap de existencia, **esto
es accionable a coste cero**: son proyectos de autor individual, y abrir un *issue* pidiendo licencia
desbloquea la pieza. Ver **T36**.

- **Señal de mercado nueva:** [`saptiva-ai/octavius-energy-lab`](https://github.com/saptiva-ai/octavius-energy-lab)
  (Apache-2.0, empresa mexicana de IA) se propone como banco de evaluación de *agent harnesses* sobre
  datos de **CENACE**. Leído el README: **el dominio energético "no está todavía en este árbol"** —
  es andamiaje de plataforma, no producto. Vale como evidencia de que se está intentando desde la
  región con licencia permisiva; **no** como cimiento reutilizable hoy. Re-medir en el pase 13.
- **Brasil sigue en cero, y es el gap de mayor valor de la región:** no se encontró presencia de
  código abierto del **ONS** tras doce pases, en el mayor mercado de datacenter de LATAM.
- El único activo de origen **institucional** usable sigue siendo `equipoanaliticaxm/api_xm`
  (XM, Colombia), del sexto pase.

**Oportunidad para Globant:** Brasil es el único país de la región con régimen legal (REDATA) y con
acceso directo a transmisión autorizado — es donde el proyecto de datacenter es financiable. México y
Chile son mercados de **ingeniería de restricción**: estudio de interconexión, flexibilidad y
expediente ambiental, no de capacidad. Y con `api_xm` (Colombia) y el modelo nacional chileno ya
publicado, las **Recetas 10, 16 y 24** siguen siendo las vías de entrada con cimiento regional real.

#### Actualización del decimotercer pase (2026-11-20)

**Despliegue de referencia regional, y es el más citable que tiene esta sección:** **Eletrobras**
—la transmisora de control estatal brasileña— está desplegando la plataforma **Grid Intelligence de
C3 AI sobre toda su red de transmisión**, bajo una iniciativa propia llamada **"Eletro.ia"**. El
objetivo declarado es reforzar la fiabilidad y prepararse para la entrada creciente de eólica y
solar; las fuentes describen identificación de fallos de red **en tiempo real**.

Por qué importa más que una cifra de mercado, y conviene decirlo tal cual en una propuesta:

1. **Es la prueba de que el presupuesto existe en LATAM** y que se gasta en IA de red a escala de
   sistema nacional, no en pilotos.
2. **Es un competidor concreto y nombrado** en el *market map* regional: C3 AI, no un genérico
   "hiperescalador". Esta sección tenía despliegues europeos y norteamericanos nombrados y **ninguno
   brasileño**; ahora lo tiene.
3. **Define el hueco de Globant por contraste.** C3 AI entra con plataforma propietaria de extremo a
   extremo en la **transmisora**. Lo que queda abierto es (a) la **distribución** y el
   *meter-to-cash*, (b) la **capa agéntica y de integración encima** de plataformas ya compradas, y
   (c) el expediente regulatorio. Es la misma posición que el "Posicionamiento Globant" de más abajo
   ya defiende — ahora con un caso regional que la sostiene.

**Regulación: el primer instrumento brasileño con número que esta sección puede citar.** El
**Ministério de Minas e Energia** abrió **consulta pública para acelerar la adopción de medidor
inteligente**, con una propuesta que **obligaría a las distribuidoras a instalar medidores para al
menos el 4 % de sus clientes en el primer año**. Almacenamiento y generación distribuida siguen en
discusión.

Si se confirma, es **el driver regional más fuerte de esta sección**, por la misma razón que el pase
de automotive identificó en CONTRAN 962: **un mandato crea base instalada con fecha**, y una base
instalada de medidores es precisamente lo que la **capa de medición abierta de este pase** sabe leer
(`iec62056-21`, `smartmeter-obis`, `dsmr-p1-parser`, `mbmd` — todos permisivos). Es la primera vez
que una oportunidad LATAM de esta KB tiene **mandato regulatorio + stack abierto correspondiente**
en la misma frase.

⚠️ **Estado de verificación, sin adornos:** consulta **en curso**, porcentaje **propuesto**, no
norma vigente. Fuente secundaria (prensa sectorial de conferencia, **páginas promocionales** en
varios casos). **No presentar el 4 % como obligación en vigor.** Tarea para el próximo pase: buscar
el número de consulta pública del MME y, si existe, la Resolução Normativa de ANEEL asociada.

**Cifra regional, con la salvedad de siempre:** LATAM ≈ **USD 1,69 B en 2025** para IA en *power
utilities*, ≈ **9,77 % de los ingresos globales** (una sola consultora, sin corroborar). Brasil
domina la inversión regional en datacenters, lo que acopla la demanda de IA a la tensión de red; su
ventaja declarada es **energía renovable abundante y barata** y su restricción, **la capacidad de red**.

**Hueco de oferta que sigue abierto, medido otra vez:** el barrido de este pase por protocolo
(`SunSpec`, `IEC 62056`, `SAREF`) devolvió **cero repos de origen LATAM** — 9 EMEA, 4 North America.
No se re-midió con vocabulario español/portugués porque **esta KB ya lo hizo cuatro veces con
resultado cero**, y repetirlo no añade información. La conclusión se mantiene y se refuerza: en la
capa de medición **no hay ecosistema abierto regional con el que competir**, y por tanto **publicar
una pieza propia sigue siendo la jugada más barata de posicionamiento** en la región.

### Actualización del decimocuarto pase (2026-11-21) — LATAM

**El hallazgo del pase invierte un cero que esta KB midió cuatro veces.** El pase 13 anotó *"CERO
repos de origen LATAM en este barrido, vocabulario es/pt NO re-ejecutado porque ya se midió cero
4×"*. Aplicando la lección transferida del pase de automotive —**un cero medido con consultas largas
o genéricas es una afirmación sobre el instrumento, no sobre el sector**— se re-ejecutó la búsqueda
con **el nombre propio del operador o del regulador**, que es el discriminador que esta KB ya sabía
que funciona (T43).

Resultado: **no hay un cero. Hay una capa entera**, y tiene una forma muy definida.

| Repo | Licencia | País | Qué hace | ★ / forks |
|------|----------|------|----------|-----------|
| [`Mcp-Brasil/mcp-brasil`](https://github.com/Mcp-Brasil/mcp-brasil) | **MIT** | Brasil | **Servidor MCP de 70 APIs públicas brasileñas, 533 tools.** Incluye sección *Energia e Infraestrutura* con feature `aneel` (**4 tools**: SIGA, generación distribuida, tarifas, banderas) | **1.868** ★ |
| [`eniocc/bdgd-tools`](https://github.com/eniocc/bdgd-tools) | **MIT** (byte-read 1.074 B) | Brasil | **Convierte la BDGD de ANEEL a elementos OpenDSS.** El puente entre el dato regulatorio de distribución y el simulador | 10 ★ / **9 forks** / 16 issues |
| [`riclolsen/json-scada`](https://github.com/riclolsen/json-scada) | GPL-3.0 | Brasil | SCADA completo (ya en la KB; **slug correcto registrado este pase**) | 513 ★ |
| [`GuilhermeBarros12/rag_aneel`](https://github.com/GuilhermeBarros12/rag_aneel) | **MIT** (byte-read 1.100 B) | Brasil | RAG sobre normativa de ANEEL. Push 2026-11-14 | 3 ★ |
| [`nightcrowsgui5-netizen/radar-curtailment-sin`](https://github.com/nightcrowsgui5-netizen/radar-curtailment-sin) | **MIT** (byte-read 1.080 B) | Brasil | Cuantifica el **curtailment renovable por *constrained-off*** sobre datos abiertos del ONS | 0 ★ |
| [`brenoloureiro/ons-energy-viz`](https://github.com/brenoloureiro/ons-energy-viz) | **MIT** | Brasil | Visualizador de generación del ONS | 0 ★ |
| [`fcingolani/cammesa-api`](https://github.com/fcingolani/cammesa-api) | **MIT** | Argentina | API/CLI para series de CAMMESA (ya en la KB). ⚠️ **sin push desde 2017** | 9 ★ |
| [`batuenergy/atlas-sen`](https://github.com/batuenergy/atlas-sen) | MIT (rescatada en pase previo) | México | Atlas del SEN. **Push de hoy, 2026-11-21** | 11 ★ |

#### La caracterización, que es lo vendible

**El open source energético de LATAM no es una capa de modelado ni agéntica: es una capa de
acceso al dato del regulador.** Casi todo lo encontrado hace lo mismo —leer ANEEL, el ONS, CAMMESA,
CENACE y volverlo consultable— y casi nada construye por encima. Eso tiene dos consecuencias
directas y opuestas, y conviene presentar las dos:

1. **A favor:** el trabajo de *plumbing* regional **ya está hecho y es permisivo**. No hay que
   construir el conector a ANEEL: hay un MCP de 1.868 ★ con 4 tools de ANEEL y un conversor
   BDGD→OpenDSS con 9 forks. Un proyecto LATAM arranca **por encima** del dato, no en él.
2. **En contra, y es el hueco de Globant:** **no hay nada por encima.** La capa de optimización, de
   pronóstico operativo y agéntica sobre ese dato **no existe en la región**. El pase 13 ya definió
   el hueco como *"distribución / capa agéntica / dossier"*; este pase lo confirma **con el
   inventario delante** en lugar de por ausencia de resultados.

#### Dos avisos de licencia, los dos importantes

- **`mcp-brasil` separa licencia de código y licencia de dato, y lo dice su propio README:** el MIT
  cubre **sólo el código**; cada fuente tiene su licencia (`SOURCES.md`) y hay una
  `ACCEPTABLE_USE.md` que el README pide leer **antes de uso comercial, periodístico o decisorio**.
  Para el feature que nos ocupa, `SOURCES.md` dice: `aneel`, `antt` → *"open data; atribuição"*.
  **Traducción operativa: utilizable comercialmente, con atribución.** Está limpio — pero la
  comprobación había que hacerla, porque **MIT en el repo no dice nada del dato que el repo
  descarga**.

  > **Clase de riesgo nueva y general para toda la flota:** un cliente MCP permisivo sobre datos de
  > terceros tiene **dos licencias, no una**. Verificar la del dato, no sólo la del código. Un
  > conector MIT a una fuente con dato restringido es un problema contractual que ningún
  > verificador de SPDX detecta.

- [`vodikus/ha_tarifas_energia_brasil`](https://github.com/vodikus/ha_tarifas_energia_brasil) (33 ★,
  tarifas y banderas de ANEEL para Home Assistant): la API reporta **NOASSERTION**, pero el byte-read
  devuelve **GPL-3.0-or-later** (715 B, 0 coincidencias de `LESSER`). **No es permisivo: excluido**
  de las tablas recomendadas. Ver la clase de licencia "notice corto" en `intel/trends.md`.

#### Contexto de mercado de la región

- **Moody's**: el **suministro eléctrico y la capacidad de red —no la demanda—** son la restricción
  principal a la expansión de IA en América Latina. Es la misma tesis central que esta KB sostiene a
  nivel global, y en LATAM es donde muerde antes.
- Capacidad de datacenter de la región: **~2.340 MW a principios de 2026**, creciendo **15-20 % anual**.
- **Eletrobras** sigue siendo el despliegue nombrado de referencia (con C3.ai, monitorización de red).
- Chile aplica IA a **pronóstico de renovables**; Brasil, Uruguay y México a modernización de red y
  planificación de infraestructura.
- Huecos declarados de la región: red, regulación, talento especializado y conectividad.

⚠️ Fuentes de este bloque: prensa sectorial y páginas de evento (BNamericas, Moody's vía prensa,
DCPI-LATAM, OLADE). **No se localizó norma primaria de IA-energía de 2026 en la región**; lo que hay
son marcos de datacenter y la consulta del MME brasileño ya registrada (**consulta, no ley** — el
aviso del pase 13 sigue en pie).


#### Actualización del decimoquinto pase (2026-11-21) — LATAM

**El mejor gancho comercial de la región es una cifra de desperdicio.** Se reporta que Brasil
**recortó (curtailment) el 20,6% de su producción solar y eólica en 2025**. ⚠️ Fuente de análisis
sectorial, no del operador; verificar contra ONS antes de usarla con cliente. Si se sostiene, es el
argumento más directo que existe en LATAM para el stack que esta KB cataloga: un recorte de ese
tamaño **no es un problema de generación sino de pronóstico, despacho y flexibilidad**, que es
exactamente la capa abierta y permisiva que la KB tiene inventariada. Se vende como reducción de
desperdicio medible, no como "transformación digital".

**Movimiento de mercado y de regulación** (⚠️ todo de comentario sectorial; el pase no alcanzó
documento de regulador):

- **Brasil** — **subasta de capacidad de reserva récord de 19,5 GW**, orientada a fiabilidad en un
  sistema **hidro-dominante y muy expuesto al clima**. Las **aprobaciones municipales** siguen
  siendo un riesgo recurrente de localización para hiperescaladores. Se referencia una ley de
  incentivos a centros de datos, **REDATA**; ⚠️ una fuente fecha su promulgación en **septiembre de
  2026**, lo que es **inconsistente** con otras — **no citar la fecha**.
- **Chile** — se consolida como **líder regional en almacenamiento en baterías**, y a la vez su
  **licenciamiento ambiental ha congelado o cancelado proyectos** de alto perfil. Otra fuente lo
  describe como destino de **menor volatilidad** para capital de infraestructura de IA de larga
  duración, por estabilidad política y previsibilidad regulatoria. Las dos cosas son compatibles:
  **riesgo de permisos alto, riesgo de régimen bajo**. Se reporta que Chile ya integró **pronóstico
  renovable con IA**.
- **México** — reformas regulatorias amplias, pero el **proceso de interconexión sigue siendo opaco
  en coste y en plazo**, y el crecimiento en **Querétaro** ha traído retrasos de expansión del
  sistema y de energización de edificios de centro de datos.
- **Brasil, Uruguay y México** aplicando IA a modernización de red y planificación de
  infraestructura.
- "**Más de 10 GW** de capacidad lista para conectar en 2–3 años en mercados latinoamericanos":
  ⚠️ **análisis interno de un desarrollador** (Atlas Renewable). Atribuir siempre; no adoptar como
  dato de mercado.

**La cadena de oferta LATAM se completa, y es el cambio estructural del pase para la región.** El
pase 14 descubrió que el "cero de repos LATAM" era un artefacto del instrumento y encontró una capa
de **acceso al dato del regulador**. Este pase cierra el eslabón siguiente: **del dataset del
regulador al modelo de red ejecutable**.

| Pieza | Licencia | Qué resuelve |
|-------|----------|--------------|
| [`mpfarias/tarifas-energia-api`](https://github.com/mpfarias/tarifas-energia-api) | **ISC** (manifiesto, 463 B) | Tarifas eléctricas de ANEEL como API |
| [`eniocc/bdgd-tools`](https://github.com/eniocc/bdgd-tools) | MIT (ya en la KB) | Utilidades sobre la BDGD de ANEEL |
| [`PauloRadatz/bdgd2opendss`](https://github.com/PauloRadatz/bdgd2opendss) | MIT (leída, 1.069 B) | **Convierte la BDGD de ANEEL en elementos OpenDSS**: el dato del regulador se vuelve modelo simulable |

Tres piezas permisivas de origen brasileño sobre el **mismo dato regulatorio**, encadenables. Es la
primera vez que LATAM aporta una **cadena** y no piezas sueltas, y permite proponer un piloto de
distribución en Brasil **sin dependencia de proveedor y sin dato propietario**. **ISC** es permisiva
aprobada por OSI (equivalente funcional de MIT) y es su **primera aparición** en esta KB.

⚠️ **Gap que sigue abierto, declarado:** **ningún repo de origen LATAM en la capa agéntica/LLM**. La
oferta regional es de **acceso a datos y modelado**, no de agentes. El vocabulario agéntico en
español y portugués **no se re-ejecutó en este pase** —se midió cero cuatro veces en pases
anteriores, pero **eso fue con el instrumento largo** y T58 obliga a re-sondearlo corto: es el
**open item 15-R2** y hoy es el candidato más probable a falso cero de toda la KB.

### Actualización del pase 16 (2026-11-24) — LATAM

**El cambio de fondo del pase: LATAM deja de ser una región de consumo de tecnología agéntica y
pasa a publicar la suya, desde el operador del sistema y con licencia permisiva.**

**1. El ONS brasileño publica su capa agéntica, Apache-2.0.**
[`ONSBR/TIAGO-Dados-Abertos`](https://github.com/ONSBR/TIAGO-Dados-Abertos) es el **servidor MCP
oficial** de `dados.ons.org.br`. **Es el primer servidor MCP publicado por el operador de un sistema
eléctrico nacional que esta KB registra, en cualquier región.** Arquitectura: capa semántica **ODCS
v3.1.0** en YAML que declara schema, unidades y **aditividad por columna**; el servidor rutea, valida
y ejecuta; **el modelo del cliente escribe el SQL**; **ningún LLM corre en el servidor**; y cuando no
puede probar un dato **declara desconocido en vez de deducir**. Motor **DuckDB**, paquete en PyPI.

**Esto cierra el ítem abierto 15-R2** («cero repos agénticos de origen LATAM»), y lo cierra el
**idioma**: la consulta que lo encontró tiene cuatro palabras en portugués (`ons dados abertos mcp`,
`total_count: 1`). El cero anterior era del instrumento (T63).

**2. Y detrás había una organización entera.** Las **13 direcciones de `ONSBR`** estaban ausentes de
un inventario de 500. Incluyen los **modelos del operador, permisivos**: `smapOnsR` (**MIT**, SMAP/ONS
de afluencias, en R), `PrevCargaDESSEM` (**MIT**, previsión de carga, copyright **CEPEL + ONS**) y
`prevcarga` (**Apache-2.0**, reescritura con push del **23-nov-2026**).
⚠️ `ONSBR/DadosAbertos` es el más estrellado (43 ★) y **el único sin licencia**: inutilizable.

> **Brasil queda como la única región de esta KB donde el operador del sistema publica, a la vez y
> permisivamente, sus modelos de previsión y su capa de acceso agéntica.** Eso cambia el punto de
> partida de un *engagement*: no se propone construir el modelo, se propone **operacionalizar,
> validar y poner interfaz al modelo que el operador ya publica** — defendible ante el regulador
> precisamente por eso.

**3. TIAGO como despliegue, con las fechas en conflicto declarado.** TIAGO = *Tecnologia de
Inteligência Artificial Generativa do ONS*, sobre **AWS Bedrock**, contra el Portal de Dados Abertos
(**85 datasets**). ⚠️ **Fechas inconsistentes entre fuentes**: una sitúa el lanzamiento el
**17-ago-2026** y otra lo da «en operación desde julio». Existe además **otro TIAGO anterior**,
herramienta interna de búsqueda documental reportada en **noviembre de 2024**, y el nombre aparece
escrito también como «Thiago». **No fijar una fecha única.** El ONS publica su propia advertencia de
que la herramienta puede producir imprecisiones y que para posición institucional hay que usar los
canales oficiales — esa frase es **un activo de venta**: el operador ya escribió la frontera que el
cliente va a querer oír. Hay además una herramienta separada del ONS para consultar **Procedimentos
de Rede**.

**4. Confirmación de arquitectura de origen regional.** Un artículo de **PSR** (julio de 2026)
propone un agente que interactúa con un **modelo hidrotérmico** únicamente a través de **capacidades
de dominio controladas y tipadas**, y deja escrito que **el agente no reemplaza al solver de
optimización**. Misma frontera que TIAGO implementa. ⚠️ Es **opinión técnica**, no norma ni
despliegue: vale como precedente de que el patrón es consenso regional.

**5. El entorno regulatorio: fragmentación medida.** Un estudio de la **Universidad de los Andes
(2026)** cuenta **716 instrumentos, normas y proyectos de ley sobre IA en 23 países y territorios**,
la mayoría iniciados desde 2023, y describe la región como **derivando hacia la fragmentación**.
**Siete países** adoptaron formalmente los **Principios de IA de la OCDE** (Argentina, Brasil, Chile,
Colombia, Costa Rica, México, Perú). **Colombia** optó por política nacional (**CONPES 4144**,
feb-2025, hasta 2030) en vez de obligaciones horizontales inmediatas. **Brasil** tiene reglas firmes
de IA en el poder judicial; **Chile** modernizó protección de datos y ciberseguridad.
**Consecuencia comercial: en LATAM el expediente es por país, y la fragmentación es el argumento para
vender una capa de cumplimiento reutilizable** — exactamente lo contrario de APAC, donde lo que no
transfiere es el modelo técnico.

**6. Infraestructura y energía para IA.** **México** debate requisitos de **consumo eléctrico y de
agua** para centros de datos; **Argentina** evalúa incentivos para grandes inversiones de
infraestructura de IA, con **Vaca Muerta** como atractivo de gas; **Chile** aporta renovables,
almacenamiento y experiencia atrayendo centros de datos, pero con **restricciones de transmisión y
disponibilidad de agua** (consistente con el riesgo de permisos alto / riesgo regulatorio bajo del
pase 15). Competencia geopolítica en **Brasil**: **Huawei e iFlytek** en infraestructura de
supercomputación en Río de Janeiro y **Nvidia** esperada en Río Grande do Norte. **Paraguay**: el
desarrollador **Araico** con una compañía estadounidense de infraestructura para nube de IA
alimentada por **Itaipú**.

**7. Startups regionales nombradas:** **Niko Energy** (México, visión por computador para evaluar
solar en tejado, camino a *virtual power plants*) y **Ainwater** (Chile, IA para el consumo
energético de utilities de agua).

**8. Lo que se mantiene del pase 15:** Brasil **curtailed el 20,6 % de solar+eólica en 2025**
(análisis sectorial, verificar contra ONS) — sigue siendo el gancho comercial más directo de la
región, porque ese desperdicio es un problema de **pronóstico, despacho y flexibilidad**, y ahora
**los modelos de pronóstico del propio operador están disponibles con licencia MIT**. La combinación
de ambos hechos es la propuesta LATAM más fuerte que esta KB ha podido formular.

**Oportunidad concreta:**
1. **Compuerta de contratos de datos sobre portal de regulador u operador** (receta 53): el ONS
   publicó el servidor Apache-2.0; el trabajo facturable es **escribir los contratos ODCS del dominio
   del cliente**, que es consultoría de dominio. Replicable sobre ANEEL, CAMMESA, CEN de Chile.
2. **Reducción de *curtailment*** con `smapOnsR` + `prevcarga` del operador, más el stack de
   pronóstico ya inventariado.
3. **Capa de cumplimiento reutilizable país por país**, justificada por los 716 instrumentos.

⛔ **No citar las cifras de `nivelics.com`**: el texto publicado contiene marcadores **`[VERIFY]` sin
rellenar** donde deberían ir sus estadísticas de adopción.
⚠️ **WEF**: la adopción creciente **todavía no produce impacto medible**, y muchas organizaciones no
alcanzan escala. Contrapeso honesto a los puntos anteriores.

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


### Actualización del séptimo pase: la dispersión del dato agéntico es de 5,3× en el mismo año

Dos fuentes publicadas en 2026 dimensionan el **mismo** mercado de IA agéntica en energía para el
**mismo año** así:

| Fuente | Valor 2026 |
|--------|-----------|
| Estimación A | **4 800 M USD** |
| Estimación B | **897 M USD** |

Son **5,3×** de diferencia sobre el mismo objeto y el mismo ejercicio. Confirma por tercer pase
consecutivo la regla del trend T8: **en este sector se cita el dato de adopción, nunca el de tamaño.**
Los números citables de este pase son todos de adopción o de capex comprometido, no de tamaño de
mercado: 1,4 billones USD de capex de IOU hasta 2030 (+21 % interanual), 95 solicitudes por ~54 GW en
PJM, IEA 23 % / ~70 %, Grant Thornton 38 % en piloto y 32 % estancado tras aprobarlo, 73 % que pone
fiabilidad entre sus tres prioridades frente a 43 % en 2025 (National Grid Partners 2026).

⚠️ Se omiten deliberadamente los nombres de las dos firmas de investigación: ninguna de las dos cifras
es verificable desde este entorno y nombrarlas daría una falsa sensación de procedencia.


### Actualización del noveno pase (2026-11-20): la dispersión llegó a 4,6× y apareció una cifra física que sí es citable

Tres consultoras más, mismo sector, y el rango se vuelve a abrir:

| Fuente | Cifra 2026 | Proyección | CAGR |
|--------|-----------|-----------|------|
| The Business Research Company | **27,89 B USD** | 60,6 B USD a 2030 | 21,4 % |
| Coherent Market Insights | **6,04 B USD** | 22,15 B USD a 2033 | — |
| openPR (vía informe de mercado) | — | **85,5 B USD a 2034** | 18,2 % |

**27,89 / 6,04 = 4,6×** para el mismo sector y el mismo año. Esto **confirma por quinta vez** la
regla de T8: *en este sector el dato de tamaño de mercado no es confiable y el de adopción sí.* No
poner una de estas cifras en una propuesta sin la otra al lado.

**La excepción, y es la cifra que conviene usar:** el consumo eléctrico de datacenters es una
magnitud **física**, medida por la **IEA**, y los números convergen en vez de dispersarse — más de
**500 TWh globales en 2026**, ≈ **2 % de la electricidad mundial**, con el escenario base de la IEA
implicando ~**15 % de crecimiento anual hasta 2030**, y la IEA señalada como la fuente que llama a
la IA el mayor impulsor del crecimiento eléctrico de los datacenters. **Es la cifra sobre la que se
puede construir un argumento sin exponerse**: no es una estimación de mercado, es energía medida.

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


