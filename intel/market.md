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
*Investigado 2026-11-20 (dos pases). Cifras de consultoras: re-verificar antes de usar en propuesta.*

