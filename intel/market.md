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

---
*Investigado 2026-11-20. Cifras de consultoras: re-verificar antes de usar en propuesta.*
