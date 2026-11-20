---
industry: energy
region: Global
updated: 2026-11-20
---

# 🧩 Patrones de composición — Energy

> Recetas concretas: repos nombrados, licencias declaradas, cableado explícito.
> Todos los componentes verificados contra la GitHub REST API el **2026-11-20**.

## Regla de arquitectura que atraviesa todas las recetas

El vertical energético es **copyleft** (AGPL/GPL) y la capa de agentes es **MIT**. Por eso toda
receta separa los dos con un límite de proceso:

```
[Plataforma vertical open source — AGPL/GPL, contenedor aislado]
                     ↕  (sólo su propia API / protocolo)
[Capa de herramientas MCP — MIT/BSD]
                     ↕
[Agentes + orquestación — código del cliente, propietario]
                     ↕
[UI conversacional / API]
```

Y la regla de seguridad heredada del pase de automotive, que aquí aplica igual:
**el texto del razonamiento del agente se loguea para el operador y nunca llega al actuador.**
En energía el actuador es un setpoint, un breaker o un despacho: el agente propone, el sistema de
control valida y ejecuta.

---

### Receta 1 — Copiloto de estudios de interconexión de carga grande

**Para**: utilities y RTOs de North America bajo las *show-cause orders* de FERC del 18-jun-2026
(PJM, MISO, SPP, CAISO, ISO-NE, NYISO), y para desarrolladores de datacenter en cola.

- **Punto de partida**: [`e2nIEE/pandapower`](https://github.com/e2nIEE/pandapower) (BSD-3-Clause,
  1331 ★) para load flow y OPF de distribución; [`PyPSA/PyPSA`](https://github.com/PyPSA/PyPSA)
  (MIT, 2248 ★) para escenarios de transmisión y expansión.
- **Agentes**: [`Power-Agent/PowerMCP`](https://github.com/Power-Agent/PowerMCP) (MIT) expone los
  solvers como tools; [`Power-Agent/PowerWF`](https://github.com/Power-Agent/PowerWF) (MIT) encadena
  el workflow de estudio; [`Power-Agent/PowerAgentBench`](https://github.com/Power-Agent/PowerAgentBench)
  (MIT) para medir si el agente realmente acierta antes de mostrarlo a un cliente.
- **Cableado**: el agente recibe el pedido de interconexión en lenguaje natural → `PowerWF` arma el
  caso → `PowerMCP` invoca `pandapower`/`PyPSA` con los escenarios N-1 → el agente redacta el
  informe regulatorio citando cada corrida. **Los números salen del solver, nunca del modelo.**
- **Entregable**: informe de estudio con trazabilidad de cada corrida + paquete de escenarios
  reproducible.
- **Licencias**: todo BSD/MIT. **Sin restricción de distribución.**
- **Tiempo estimado**: 6–9 semanas para un piloto de una jurisdicción.

---

### Receta 2 — Expediente de cumplimiento AI Act para forecasting de red (EMEA)

**Para**: TSO/DSO europeos. Gestión de red y load forecasting se tratan generalmente como **alto
riesgo** del Anexo III; obligaciones desde el **2-dic-2027** (Reglamento (UE) 2026/1744). En
Alemania supervisa **BNetzA** desde el 29-jul-2026.

- **Punto de partida**: [`OpenSTEF/openstef`](https://github.com/OpenSTEF/openstef) (**MPL-2.0**,
  183 ★) — pipeline de forecasting de corto plazo ya en producción en utilities europeas, de LF
  Energy. Baseline estadístico obligatorio con
  [`Nixtla/statsforecast`](https://github.com/Nixtla/statsforecast) (Apache-2.0, 4980 ★).
- **Agentes**: agente de documentación que genera el expediente técnico desde los artefactos del
  pipeline (datasets, métricas, drift, decisiones de modelo) — no un agente que *haga* el forecast.
- **Cableado**: `openstef` emite forecast + métricas versionadas → el agente compila el expediente
  del Art. 11 (gestión de riesgos, gobernanza de datos, supervisión humana, exactitud) → revisión
  humana obligatoria antes de firmar. El agente **nunca** altera un forecast.
- **Por qué funciona comercialmente**: `openstef` es MPL-2.0 y de autoría de los propios operadores
  (Alliander + RTE) → responde soberanía digital y procedencia del código en la misma propuesta.
- **Licencias**: MPL-2.0 (copyleft por archivo, no contamina el resto) + Apache-2.0.
- **Tiempo estimado**: 10–14 semanas; tiene **fecha límite legal**, lo que facilita la aprobación.

---

### Receta 3 — Modernización de centro de control con stack de origen regional (LATAM)

**Para**: utilities de Brasil, Chile, México. Diferenciador: software de control de red de
**autoría brasileña verificable** (Ricardo L. Olsen, Porto Alegre, desde 1998).

- **Punto de partida**: [`riclolsen/json-scada`](https://github.com/riclolsen/json-scada)
  (**GPL-3.0**, 513 ★) — SCADA/EMS/IIoT con IEC 61850, ICCP, IEC 60870-5-101/104, DNP3, OPC-UA,
  OPC-DA, Modbus, MQTT/Sparkplug B sobre MongoDB + PostgreSQL/TimescaleDB + Grafana.
  HMI de subestación con [`riclolsen/OSHMI`](https://github.com/riclolsen/OSHMI) (GPL-3.0, 467 ★).
- **Agentes**: capa de asistente de operador **en proceso separado**, leyendo el histórico
  (TimescaleDB) y escribiendo **sólo** vía la API de json-scada.
- **Cableado**: `json-scada` sigue siendo el sistema de registro y el único que habla con campo →
  el agente consulta histórico y propone → el operador aprueba → la acción entra por la API del
  SCADA con su propia validación. El agente **no** tiene ruta al protocolo de campo.
- **⚠️ Licencia, y es la decisión central**: GPL-3.0. Contenedor aislado + comunicación por API
  **no** deriva obra; enlazarlo en el producto propietario del cliente **sí**. Este límite es el
  diseño, no un detalle.
- **Tiempo estimado**: 8–12 semanas para un piloto de un centro de control.

---

### Receta 4 — Flexibilidad de carga de datacenter como producto de red

**Para**: operadores de datacenter negociando interconexión (los seis RTOs de FERC; Brasil, Chile,
México con colas de interconexión) y utilities que quieren comprar flexibilidad en vez de construir
planta.

- **Punto de partida**: [`dos-group/vessim`](https://github.com/dos-group/vessim) (MIT, 103 ★)
  simula el sistema energético del datacenter (carbono, batería, PV on-site);
  [`hubblo-org/scaphandre`](https://github.com/hubblo-org/scaphandre) (Apache-2.0, 2019 ★) mide el
  consumo real del cómputo; [`Green-Software-Foundation/carbon-aware-sdk`](https://github.com/Green-Software-Foundation/carbon-aware-sdk)
  (MIT, 600 ★) desplaza carga según intensidad de carbono.
- **Agentes**: agente de negociación de flexibilidad que, dado el perfil medido, cuantifica cuántos
  MW y por cuántas horas puede ofrecer el sitio, y a qué costo de SLA.
- **Cableado**: `scaphandre` → métricas reales a Prometheus → `vessim` simula escenarios de
  curtailment con batería y PV → `carbon-aware-sdk` ejecuta el desplazamiento de carga diferible →
  el agente redacta la oferta de flexibilidad con datos propios, no supuestos.
- **Por qué ahora**: un estudio comisionado por Duke indica que cargas flexibles evitarían decenas
  de miles de millones en plantas nuevas; es argumento con contraparte compradora.
- **Licencias**: MIT + Apache-2.0. **Empotrable sin restricción.**
- **Tiempo estimado**: 5–8 semanas.

---

### Receta 5 — Agente de eficiencia de edificios sobre modelo calibrado

**Para**: portfolios inmobiliarios corporativos, campus, retail y hospitales (aplica en las cuatro
regiones; el vertical con el camino más corto a ahorro demostrable).

- **Punto de partida**: [`NatLabRockies/EnergyPlus`](https://github.com/NatLabRockies/EnergyPlus)
  (BSD-3 **+ cláusula de marca**, 1623 ★) como motor de simulación;
  [`MyEMS/myems`](https://github.com/MyEMS/myems) (MIT, 763 ★) como EMS de registro para
  electricidad, agua, gas, frío y calor.
- **Agentes**: [`LBNL-ETA/EnergyPlus-MCP`](https://github.com/LBNL-ETA/EnergyPlus-MCP) (BSD
  modificada, 130 ★) — **35 tools** para cargar/validar IDF, inspeccionar zonas, schedules y cargas,
  modificar iluminación/equipos/infiltración, correr simulación y graficar. Para control aprendido:
  [`ugr-sail/sinergym`](https://github.com/ugr-sail/sinergym) (MIT, 242 ★).
- **Cableado**: `MyEMS` provee consumo medido → `EnergyPlus-MCP` deja al agente calibrar el modelo
  IDF contra ese consumo real → el agente propone retrofits y **cuantifica cada uno con una corrida
  de simulación** → `sinergym` entrena la política de HVAC si se avanza a control.
- **⚠️ Dos cuidados de licencia**: (1) EnergyPlus prohíbe usar "EnergyPlus", "E+" o nombres
  confundibles en nombre de empresa, producto o publicidad sin consentimiento escrito del U.S. DOE
  → relevante si el entregable es marca blanca. (2) `EnergyPlus-MCP` **no tiene archivo `LICENSE`**
  (README declara BSD modificada, texto en `License.txt`), versión **0.1.0** → revisión legal antes
  de producción, contacto IPO@lbl.gov.
- **Tiempo estimado**: 6–10 semanas por portfolio piloto.

---

### Receta 6 — Agregador de carga de EV y V2G (EMEA primero, luego APAC)

**Para**: utilities, retailers de energía y operadores de flota. Es el vertical con **más masa
crítica de comunidad** de todo el ecosistema energético open source.

- **Punto de partida**: [`evcc-io/evcc`](https://github.com/evcc-io/evcc) (MIT, **7638 ★ / 1649
  forks**) para carga inteligente con excedente solar y tarifa dinámica;
  [`steve-community/steve`](https://github.com/steve-community/steve) (GPL-3.0, 1151 ★) como backend
  OCPP; [`mobilityhouse/ocpp`](https://github.com/mobilityhouse/ocpp) (MIT, 1052 ★) si se
  implementa el protocolo a medida.
- **Optimización**: [`Akkudoktor-EOS/EOS`](https://github.com/Akkudoktor-EOS/EOS) (Apache-2.0,
  1731 ★) resuelve el despacho con PV, batería y precio horario.
- **Agentes**: agente de planificación que negocia entre confort del usuario, precio y señal de red;
  en APAC, mismo patrón que **ITOCHU + Lunar con Gridshare** para baterías residenciales en Japón.
- **Cableado**: `steve`/`ocpp` hablan con los cargadores → `evcc` decide por sitio → `EOS` optimiza
  la cartera agregada contra precio y restricción de red → el agente explica al usuario por qué su
  auto cargará a las 3am y permite override.
- **Licencias**: `evcc`/`ocpp`/`EOS` permisivas; **`steve` es GPL-3.0** → aislar como servicio.
- **Tiempo estimado**: 8–12 semanas para un piloto de agregación.

---

### Receta 7 — Sandbox de mercado eléctrico para decisiones de inversión y política (EMEA / LATAM)

**Para**: generadores, retailers de energía, reguladores y fondos de infraestructura que necesitan
responder "¿qué pasa con mi margen si cambia la regla / entra 2 GW de solar / sube el CO₂?".
Reemplaza al consultor que entrega un Excel que nadie puede re-correr.

- **Motor de mercado**: [`assume-framework/assume`](https://github.com/assume-framework/assume)
  (**MIT**, 128 ★, push 2026-11-19) — agentes que representan actores de mercado con sus propias
  estrategias de oferta. Fraunhofer IEE / INATECH / TU Dresden.
- **Red detrás del mercado**: [`PyPSA/PyPSA`](https://github.com/PyPSA/PyPSA) (MIT, 2248 ★) para la
  restricción física, y [`e2nIEE/pandapower`](https://github.com/e2nIEE/pandapower) (BSD-3, 1331 ★)
  si el estudio baja a nivel de red real.
- **Datos de precio reales como condición de contorno**: Europa con
  [`JaccoR/hass-entso-e`](https://github.com/JaccoR/hass-entso-e) (Apache-2.0, 280 ★) o
  [`acruzgarcia/OMIEData`](https://github.com/acruzgarcia/OMIEData) (MIT, 38 ★, mercado ibérico);
  Colombia con [`EquipoAnaliticaXM/API_XM`](https://github.com/EquipoAnaliticaXM/API_XM) (MIT, 75 ★).
- **Baseline obligatorio antes de cualquier modelo**:
  [`Nixtla/statsforecast`](https://github.com/Nixtla/statsforecast) (Apache-2.0, 4980 ★).
- **Cableado**: `API_XM`/`entso-e` cargan el histórico de precio y demanda → `assume` corre los
  escenarios de oferta → `PyPSA` valida factibilidad física → el agente LLM **redacta el informe de
  escenarios y explica la sensibilidad**, con los números saliendo del simulador y nunca del modelo.
- ⚠️ **Límite que hay que escribir en la propuesta**: esto **simula**, no opera. Ningún componente
  coloca ofertas en un mercado real, y no existe open source que lo haga. Si el cliente pide un bot
  de trading, el proyecto es otro y la base no es ésta.
- **Licencias**: todo **MIT / Apache-2.0 / BSD-3** → empotrable en producto de cliente.
- **Tiempo estimado**: 8–12 semanas para el primer escenario reproducible.

---

### Receta 8 — Analítica de flota de activos renovables (aplica en las cuatro regiones)

**Para**: operadores de parques eólicos y solares, fondos que los tienen en cartera, y aseguradoras.
Pregunta real del cliente: *"¿este parque rinde menos por el recurso, por suciedad, por degradación
o porque algo está roto?"* — cuatro causas con cuatro respuestas comerciales distintas.

- **Eólico**: [`NatLabRockies/OpenOA`](https://github.com/NatLabRockies/OpenOA) (**BSD-3**, 259 ★) —
  metodologías de *operational assessment*: AEP, pérdidas, disponibilidad e incertidumbre. Es el
  estándar que una due diligence reconoce.
- **Datos eólicos para calibrar y entrenar**:
  [`sltzgs/OpenWindSCADA`](https://github.com/sltzgs/OpenWindSCADA) (GPL-3.0, 259 ★) — datasets
  abiertos de SCADA. ⚠️ **GPL-3.0**: usar los *datos* y el método; no empotrar su código.
- **Fotovoltaico**: [`NatLabRockies/rdtools`](https://github.com/NatLabRockies/rdtools) (MIT, 190 ★)
  para tasa de degradación y suciedad, y [`pvlib/pvanalytics`](https://github.com/pvlib/pvanalytics)
  (MIT, 145 ★) para control de calidad previo — sin este paso, la degradación medida es ruido.
- **Modelo de referencia de lo que *debería* producir**:
  [`pvlib/pvlib-python`](https://github.com/pvlib/pvlib-python) (BSD-3, 1730 ★).
- **Cableado**: `pvanalytics` limpia y etiqueta → `pvlib` genera el esperado → `rdtools`/`OpenOA`
  separan recurso de pérdida real → el agente **escribe el informe por activo y prioriza
  intervenciones**, citando siempre la métrica y el método que la produjo. El agente no recalcula
  performance: la lee.
- **Por qué funciona comercialmente**: el output es un número que la industria ya acepta
  (*operational assessment*, *performance loss rate*), no un score propietario que haya que
  defender. Eso acorta la discusión técnica con el cliente a la mitad.
- **Licencias**: BSD-3 + MIT en el código; GPL-3.0 sólo en datasets.
- **Tiempo estimado**: 6–10 semanas por tecnología (eólico o PV), no por parque.

---

### Receta 9 — Estudio de alimentador de distribución con DER (North America primero)

**Para**: DSOs y cooperativas eléctricas que reciben solicitudes de conexión de solar en techo,
baterías y cargadores y necesitan responder *"¿entra en este alimentador?"* en días, no en meses.

- **Motor de distribución**:
  [`dss-extensions/OpenDSSDirect.py`](https://github.com/dss-extensions/OpenDSSDirect.py)
  (**BSD-3 + derechos del gobierno de EE. UU.**, 119 ★) sobre el motor OpenDSS de EPRI, que es el
  que el regulador y la ingeniería del cliente ya reconocen.
- **Alternativa / contraste de resultados**:
  [`e2nIEE/pandapower`](https://github.com/e2nIEE/pandapower) (BSD-3, 1331 ★) y
  [`PowerGridModel/power-grid-model`](https://github.com/PowerGridModel/power-grid-model) (MPL-2.0,
  262 ★, Alliander). Correr dos motores y comparar **es** el entregable de calidad.
- **Acoplamiento con edificios y mercado** (si el estudio lo pide):
  [`gridlab-d/gridlab-d`](https://github.com/gridlab-d/gridlab-d) (221 ★) — ⚠️ **licencia propia
  Battelle v5.3, no OSI ni SPDX**: resolver con legal **antes** de incluirlo, porque un gate
  automático de compliance la marcará como desconocida.
- **Ejecución en el borde si el proyecto llega a control**:
  [`VOLTTRON/volttron`](https://github.com/VOLTTRON/volttron) (**Apache-2.0**, 504 ★) — aloja agentes
  junto al equipo sin cláusula de red.
- **Cableado**: el agente recibe la solicitud de interconexión → arma el caso en `OpenDSSDirect.py`
  → corre el escenario (tensión, desbalance, sobrecarga, flujo inverso) → **un segundo motor valida**
  → el agente redacta el informe con el diagnóstico y las mitigaciones. Toda decisión de aprobar o
  rechazar queda con firma humana.
- **Por qué funciona comercialmente**: el cuello de botella de los DSOs es volumen de estudios
  repetitivos con criterio estable — exactamente lo que se automatiza bien y lo que es defendible
  ante un regulador porque el motor es el estándar de la industria.
- **Tiempo estimado**: 10–14 semanas; la calibración del modelo del alimentador es el riesgo, no el
  software.

---

### Receta 10 — Agente de inteligencia de mercado sobre datos del operador (LATAM, Colombia primero)

**Para**: generadores, comercializadores y grandes consumidores en Colombia; replicable en Brasil con
las fuentes del ONS. Es la receta con la **oferta más corta y la demanda ya visible**.

- **Sustrato de datos, publicado por la institución**:
  [`EquipoAnaliticaXM/API_XM`](https://github.com/EquipoAnaliticaXM/API_XM) — **MIT**,
  `Copyright (c) 2020 XM S.A. E.S.P.`, 75 ★, push 2026-11-10. XM es el **operador del Sistema
  Interconectado Nacional y administrador del mercado**. Más el org `datasets` (histórico, push
  2026-11-19).
- **Modelo de dominio reutilizable**:
  [`rebase-energy/energydatamodel`](https://github.com/rebase-energy/energydatamodel) (MIT, 99 ★)
  para no reinventar las estructuras de activo/serie/mercado en cada proyecto.
- **Forecast con baseline honesto**:
  [`Nixtla/statsforecast`](https://github.com/Nixtla/statsforecast) (Apache-2.0, 4980 ★); el modelo
  pesado sólo si gana al baseline, y se reporta por cuánto.
- **Escenarios de sistema**: [`calliope-project/calliope`](https://github.com/calliope-project/calliope)
  (Apache-2.0, 380 ★) o [`TemoaProject/temoa`](https://github.com/TemoaProject/temoa) (MIT, 116 ★).
  ⚠️ **No usar `pypsa-earth` para esto**: es **AGPL-3.0-or-later** y obliga a liberar el servicio si
  se expone por red. Es el error más caro disponible en esta categoría.
- **Capa agéntica**: agente que responde en lenguaje natural sobre precio de bolsa, demanda,
  generación por tecnología y emisiones; cita **siempre** la consulta a la API que produjo el número
  y el timestamp; nunca interpola ni redondea.
- **Cableado**: `API_XM` → almacenamiento de series → `energydatamodel` como esquema →
  `statsforecast` para proyección → agente para consulta y reporte, con la cita de la fuente en cada
  respuesta.
- **Por qué funciona comercialmente, y es el argumento fuerte**: ya existen proyectos personales
  haciendo esto **sin licencia y sin soporte** (`energyagent-colombia`, `tablero-xm` con push del
  2026-11-20). Hay demanda demostrada y ninguna oferta profesional. Y la procedencia es inatacable:
  *el operador del sistema publica el cliente bajo MIT*.
- **Licencias**: MIT + Apache-2.0 en todo el stack. Sin copyleft.
- **Tiempo estimado**: 6–8 semanas al primer agente con citación de fuente.

---

### Receta 11 — Red de gas / hidrógeno acoplada a la red eléctrica (EMEA)

**Para**: operadores de red de gas, utilities multi-energía y proyectos de hidrógeno industrial que
necesitan evaluar conversión o mezcla sin comprar una suite propietaria.

- **Flujo en tuberías**: [`e2nIEE/pandapipes`](https://github.com/e2nIEE/pandapipes)
  (**BSD-3-Clause** resuelta en el `LICENSE` crudo, 247 ★, Fraunhofer IEE) — gas, **hidrógeno** y
  calor, con el mismo diseño de API que `pandapower`.
- **Lado eléctrico**: [`e2nIEE/pandapower`](https://github.com/e2nIEE/pandapower) (BSD-3, 1331 ★).
  Misma casa, misma convención: el acoplamiento sectorial no requiere pegamento ad hoc.
- **Planificación por encima**: [`oemof/oemof-solph`](https://github.com/oemof/oemof-solph)
  (**MIT**, resuelta vía SPDX en `pyproject.toml`, 430 ★) para el despacho LP/MILP del sistema
  acoplado.
- **Cableado**: `oemof-solph` decide el despacho entre vectores → `pandapipes` verifica factibilidad
  hidráulica → `pandapower` verifica la eléctrica → el agente **documenta el caso y las
  violaciones**, no las resuelve.
- **Por qué este trío y no otro**: las tres licencias son permisivas y dos de las tres salen del
  mismo instituto, así que el modelo de datos ya es compatible. Es la combinación con menos
  integración inventada de toda esta página.
- **Tiempo estimado**: 8–12 semanas.

---

### Receta 12 — Modelo de yacimiento asistido por agentes (O&G, EMEA/LATAM)

**Para**: operadoras de upstream con simulación de yacimientos interna. Subsector que esta KB no
había cubierto, y el patrón de integración es **distinto a todo lo anterior**.

- **Simulador**: [`OPM/opm-simulators`](https://github.com/OPM/opm-simulators) (**GPL-3.0**, 182 ★) —
  OPM Flow, la referencia open source de simulación de yacimientos.
- **Orquestación de ensembles y asimilación de datos**:
  [`equinor/ert`](https://github.com/equinor/ert) (**GPL-3.0**, 167 ★) — herramienta de producción de
  Equinor para correr ensembles de modelos dinámicos.
- **Visualización**: [`equinor/webviz-subsurface`](https://github.com/equinor/webviz-subsurface)
  (**GPL-3.0**, 62 ★).
- ⚠️ **La restricción define la arquitectura, y no hay alternativa**: los tres son **GPL-3.0** y **no
  se encontró ningún equivalente permisivo con tracción** en upstream. El entregable propietario del
  cliente sólo existe si el simulador queda como **sistema de registro en contenedor aparte**, con
  intercambio por archivos o API. Enlazarlo en el binario del cliente deriva obra.
- **Cableado**: el agente prepara casos y perturbaciones → `ert` corre el ensemble invocando
  `OPM Flow` **como proceso externo** → el agente lee resultados y **redacta el informe de
  incertidumbre**, sin tocar la física ni ajustar parámetros por su cuenta.
- **Por qué funciona comercialmente**: el trabajo tedioso del ingeniero de yacimientos es preparar y
  comparar cientos de corridas. Eso se automatiza sin pedirle al agente ninguna decisión técnica.
- **Tiempo estimado**: 12–16 semanas; **incluir revisión legal de GPL en la semana 1**, no en la
  última.

---

### Receta 13 — Dimensionamiento y garantía de vida de un BESS (APAC primero, aplica en las cuatro regiones)

**Para**: desarrolladores de datacenter y de renovables que tienen que **demostrar** el
comportamiento de la batería, no estimarlo. En Singapur, Malasia y Corea el plan de almacenamiento y
vertido es condición de permiso del datacenter: esto deja de ser ingeniería de detalle y pasa a ser
el documento que desbloquea el proyecto.

- **Física de celda**: [`pybamm-team/PyBaMM`](https://github.com/pybamm-team/PyBaMM) (**BSD-3**,
  1737 ★) — modelos DFN/SPMe para degradación por ciclado y calendario bajo el perfil de uso real.
- **Del modelo de celda al sistema**:
  [`pybamm-team/liionpack`](https://github.com/pybamm-team/liionpack) (MIT, 120 ★) — desbalance
  térmico y de corriente en packs serie/paralelo; es donde aparecen los problemas que la celda sola
  no muestra.
- **Caso de negocio**: [`NatLabRockies/SAM`](https://github.com/NatLabRockies/SAM) (BSD-3, 498 ★)
  para el modelo tecno-económico, o su motor [`ssc`](https://github.com/NatLabRockies/ssc) si hay
  que embeberlo sin GUI.
- **Perfil de operación del que salen los ciclos**:
  [`citylearn-project/CityLearn`](https://github.com/citylearn-project/CityLearn) (MIT, 662 ★) o la
  serie real del cliente.
- **Efecto en red**: [`e2nIEE/pandapower`](https://github.com/e2nIEE/pandapower) (BSD-3) para el
  punto de conexión.
- **Cableado**: `CityLearn`/serie real genera el perfil de ciclado → `PyBaMM` lo convierte en
  degradación año a año → `liionpack` verifica que el pack aguanta → `SAM` traduce la curva de
  capacidad en flujo de caja y LCOS → `pandapower` confirma el punto de conexión. El agente
  **orquesta el barrido de escenarios** (química, C-rate, profundidad de descarga, temperatura) y
  redacta el expediente; no inventa la física.
- **Por qué funciona comercialmente**: el entregable es una **curva de capacidad garantizada con
  método trazable**, que es exactamente lo que piden un financiador y un regulador de permisos.
- **Licencias**: BSD-3 + MIT en todo el camino. Entregable propietario sin fricción.
- **Tiempo estimado**: 6–9 semanas.

---

### Receta 14 — Optimización de parque eólico: del recurso a la maniobra (North America y EMEA)

**Para**: operadores de parques eólicos que ya tienen SCADA y quieren saber si pueden extraer más
energía del mismo activo mediante control, antes de gastar en hardware.

- **Recurso de alta resolución**:
  [`NatLabRockies/sup3r`](https://github.com/NatLabRockies/sup3r) (BSD-3, 144 ★) — GAN de
  super-resolución que densifica el reanálisis climático en espacio y tiempo. Aquí el modelo
  generativo **es** el producto energético.
- **Estelas y control**: [`NatLabRockies/floris`](https://github.com/NatLabRockies/floris) (BSD-3,
  302 ★) — wake steering y optimización de layout; es el que dice cuánto se gana desalineando.
- **Validación aeroelástica**: [`OpenFAST/openfast`](https://github.com/OpenFAST/openfast)
  (**Apache-2.0**, 991 ★) — comprueba que la estrategia de control no come vida de componente.
  Saltarse este paso es cómo se regala una garantía.
- **Contraste con producción real**:
  [`NatLabRockies/OpenOA`](https://github.com/NatLabRockies/OpenOA) (BSD-3, 259 ★).
- **Emplazamiento, si hay expansión**: [`NatLabRockies/reV`](https://github.com/NatLabRockies/reV)
  (BSD-3, 144 ★).
- **Cableado**: `sup3r` densifica el recurso → `floris` propone la estrategia de wake steering →
  `OpenFAST` verifica cargas y fatiga → `OpenOA` mide contra la producción histórica para cerrar el
  lazo. El agente **gestiona la campaña de simulación y explica la recomendación por turbina**,
  citando ganancia estimada y coste en fatiga.
- **La honestidad que lo hace vendible**: la ganancia de wake steering es real pero de un dígito
  bajo porcentual, y **tiene contrapartida en fatiga**. Presentar ambas cifras juntas es lo que
  separa esta propuesta de la de un vendedor de software.
- **Licencias**: BSD-3 + Apache-2.0. Todo permisivo.
- **Tiempo estimado**: 8–12 semanas.

---

### Receta 15 — Agregador de flexibilidad que habla el protocolo de la utility (North America primero)

**Para**: agregadores, retailers y grandes consumidores que quieren participar en programas de
respuesta de demanda. La diferencia con un piloto de flexibilidad cualquiera: **este se integra con
el programa del operador** en vez de quedarse en el dashboard del cliente.

- **El protocolo**: [`OpenLEADR/openleadr-python`](https://github.com/OpenLEADR/openleadr-python)
  (**Apache-2.0**, 161 ★) — OpenADR 2.0b, la señalización estándar utility ↔ recurso. Es la pieza
  que esta KB no tenía y sin la cual el piloto no sale del laboratorio.
- **Ejecución en el borde**: [`VOLTTRON/volttron`](https://github.com/VOLTTRON/volttron)
  (Apache-2.0, 504 ★) — agentes corriendo junto al equipo, no en la nube.
- **Política de respuesta**: [`citylearn-project/CityLearn`](https://github.com/citylearn-project/CityLearn)
  (MIT, 662 ★) para entrenar y evaluar antes de tocar un edificio real.
- **Carga de EV como recurso flexible**: [`evcc-io/evcc`](https://github.com/evcc-io/evcc) y
  [`mobilityhouse/ocpp`](https://github.com/mobilityhouse/ocpp).
- **Verificación en el edificio**: [`ugr-sail/sinergym`](https://github.com/ugr-sail/sinergym) (MIT)
  sobre EnergyPlus.
- **Cableado**: la utility emite un evento OpenADR → `openleadr-python` lo recibe y lo traduce a
  objetivo de reducción → el agente reparte el objetivo entre recursos (HVAC vía `VOLTTRON`, EV vía
  `evcc`) según una política entrenada en `CityLearn` → `openleadr-python` **reporta la entrega** de
  vuelta a la utility, que es lo que se factura.
- **Por qué funciona comercialmente**: el valor no está en reducir consumo sino en **poder
  demostrar la reducción en el formato que el programa exige**. Ese reporte es el producto.
- **Licencias**: Apache-2.0 + MIT de punta a punta.
- **Tiempo estimado**: 10–14 semanas, más el ciclo de certificación del programa de la utility
  (variable y fuera de control del proyecto: declararlo en la propuesta).

---

### Receta 16 — Stack comercial para utility descentralizada o mini-red (LATAM y mercados de acceso)

**Para**: operadores de mini-redes, cooperativas y distribuidoras pequeñas que necesitan cobrar.
Responde a la pregunta que ninguna receta anterior de esta KB respondía: *"¿cómo factura esto?"*.

- **Dominio energético de fábrica**:
  [`EnAccess/micropowermanager`](https://github.com/EnAccess/micropowermanager) (**MIT**, 30 ★) —
  clientes, medidores, tarifas, prepago y cobro para utilities descentralizadas.
- **Motor de facturación si se necesita escala y robustez**:
  [`killbill/killbill`](https://github.com/killbill/killbill) (**Apache-2.0**, 5858 ★).
- **Agregación de consumo medido**:
  [`openmeterio/openmeter`](https://github.com/openmeterio/openmeter) (**Apache-2.0**, 2457 ★).
- **Lectura de medidores en campo**:
  [`volkszaehler/mbmd`](https://github.com/volkszaehler/mbmd) y, donde aplique,
  [`riclolsen/json-scada`](https://github.com/riclolsen/json-scada) (origen Brasil).
- **Cableado**: medidor → `mbmd`/`json-scada` → `openmeter` agrega el consumo por cliente y período
  → `killbill` aplica catálogo tarifario y emite factura → `micropowermanager` da la capa de
  dominio (prepago, corte, recarga). El agente **atiende la consulta del cliente sobre su factura**
  con acceso de lectura a esa cadena, y **detecta anomalías de consumo y de cobro**.
- **La decisión de arquitectura que hay que tomar al inicio**: `micropowermanager` solo, si la
  escala es de mini-red (es MIT y entiende el dominio, pero 30 ★ significa sin comunidad que
  sostenga un incidente: hay que asumir soporte propio). `killbill` + `openmeter`, si la escala lo
  justifica — a cambio de que **toda la lógica tarifaria regulatoria es desarrollo propio**, porque
  ninguno de los dos sabe de energía. Presupuestarla explícitamente.
- **Lo que no se debe proponer aquí**: ERPNext + `navariltd/utility-billing`. Es **GPL-3.0 +
  AGPL-3.0**; en un SaaS activa la cláusula de red. Sólo si el cliente ya vive en ERPNext y acepta
  las consecuencias.
- **Licencias**: MIT + Apache-2.0 en el camino recomendado.
- **Tiempo estimado**: 10–16 semanas según si hay integración con medición existente.

---

### Receta 17 — Proyecto de eficiencia con ahorro **demostrable** (las cuatro regiones)

La receta que esta KB no tenía y que convierte un piloto de optimización en una factura.

**Problema del cliente**: "optimizamos con IA y ahorramos un 12 %" — y el CFO, el regulador o el
cliente final no lo aceptan, porque no hay método reconocido detrás del número.

**Componentes:**

| Capa | Repo | Licencia | Papel |
|------|------|----------|-------|
| Decisión | [FlexMeasures/flexmeasures](https://github.com/FlexMeasures/flexmeasures) | Apache-2.0 | planifica *cuándo* mover carga (batería, EV, bomba de calor) con forecasting integrado |
| Verificación | [opendsm/opendsm](https://github.com/opendsm/opendsm) | Apache-2.0 | calcula consumo normalizado (NMEC) y **ahorro medido** con métodos estándar (linaje OpenEEmeter/CalTRACK) |
| Lectura de campo | [Gurux/Gurux.DLMS.Python](https://github.com/Gurux/Gurux.DLMS.Python) | ⚠️ GPL-2.0 | pila DLMS/COSEM para leer el medidor inteligente — **proceso aislado** |
| Meteo | proveedor del cliente, o [open-meteo](https://github.com/open-meteo/open-meteo) | ⚠️ AGPL-3.0 | normalización por clima (ver aviso abajo) |
| Capa agéntica | [Power-Agent/PowerSkills](https://github.com/Power-Agent/PowerSkills) | MIT | explicación en lenguaje natural del resultado y de la cadena de cálculo |

**Cableado:**

1. `Gurux` corre como **servicio separado** (es GPL-2.0) y publica lecturas a una cola; nunca se
   enlaza en el producto.
2. `FlexMeasures` ingiere lecturas + precio + pronóstico y emite el plan de despacho.
3. Tras el periodo, `opendsm` toma la **línea base** pre-intervención y el consumo post-intervención
   y produce el ahorro normalizado por clima y ocupación. **Este es el entregable que se firma.**
4. La capa agéntica MIT explica el resultado y responde preguntas; **no** recalcula el ahorro — el
   número viene del método, no del modelo.

**Por qué este orden importa**: si el agente produce la cifra de ahorro, la cifra es tan auditable
como un LLM. Si la produce `opendsm` y el agente sólo la explica, es auditable como un método
estándar. Es la misma distinción que `operatorfabric-core` introduce en operación de red: el modelo
recomienda, otra cosa decide y registra.

⚠️ **Aviso de licencia, día uno**: `open-meteo` es **AGPL-3.0** y su servicio público es *free for
non-commercial use*. Un piloto que pega a `api.open-meteo.com` y luego pasa a producción comercial
cambia de régimen sin que nadie lo note. Decidir al inicio: plan comercial de Open-Meteo, proveedor
meteorológico del cliente, o aceptar AGPL con auto-hospedaje aislado.

**Entregable**: motor de despacho + informe de ahorro con método reconocido + explicación
conversacional. Núcleo **100 % Apache-2.0**, empotrable en producto cerrado.

### Receta 18 — Observabilidad de red de alta resolución sin plataforma propietaria (North America primero)

**Problema del cliente**: quiere analítica de eventos y estabilidad sobre datos de PMU, y la oferta
que conoce es propietaria (OSI PI, e-terra) con licencia por punto.

**Componentes:**

| Capa | Repo | Licencia | Papel |
|------|------|----------|-------|
| Ingesta de fasores | [GridProtectionAlliance/openPDC](https://github.com/GridProtectionAlliance/openPDC) | **MIT** | concentrador de datos de fasores (IEEE C37.118): ingiere, concentra y encamina en tiempo real |
| Base de aplicación | [GridProtectionAlliance/gsf](https://github.com/GridProtectionAlliance/gsf) | **MIT** | *Grid Solutions Framework*: series temporales, adaptadores, transporte |
| Dinámica / validación | [JuliaEnergy/PowerDynamics.jl](https://github.com/JuliaEnergy/PowerDynamics.jl) | **MIT** | modelo dinámico contra el que contrastar el evento observado |
| Estabilidad con electrónica | [Future-Power-Networks/Simplus-Grid-Tool](https://github.com/Future-Power-Networks/Simplus-Grid-Tool) | BSD-3 | análisis de impedancia y modos con alta penetración de inversores |
| Pruebas sin hardware | [suoten/ProtoForge](https://github.com/suoten/ProtoForge) | **MIT** | simula los 28 protocolos de campo para probar la cadena sin subestación |
| Seguridad | [mitre/caldera-ot](https://github.com/mitre/caldera-ot) | Apache-2.0 | emulación de adversario OT en el plan de pruebas |
| Capa agéntica | [Power-Agent/PowerMCP](https://github.com/Power-Agent/PowerMCP) + [PowerSkills](https://github.com/Power-Agent/PowerSkills) | MIT | consulta y narración del evento |

**Cableado:**

1. `ProtoForge` genera el flujo sintético: se construye y prueba la cadena completa **antes** de
   tener acceso al equipo del cliente. Esto es lo que permite cotizar con riesgo acotado.
2. `openPDC` sobre `gsf` ingiere y archiva.
3. Detección de evento → `PowerDynamics.jl` / `Simplus-Grid-Tool` contrastan contra el modelo.
4. `PowerMCP` expone el histórico y los modelos al agente, que redacta el informe del evento.
5. `caldera-ot` corre en el plan de pruebas de seguridad, no al final.

**Lo que hace vendible esta receta**: el stack central —`openPDC`, `gsf`, `PowerDynamics.jl`,
`ProtoForge`— es **todo MIT**. Se puede empotrar en un producto del cliente y cerrarlo. Es inusual en
el sector eléctrico (ver T9: el perfil de licencia cambia por subsector) y es exactamente el
argumento frente a una licencia por punto de medida.

### Receta 19 — Evaluación de foundation model de red (vía de evaluación, no de producción)

**Problema del cliente**: le han dicho que "hay modelos fundacionales de red" y quiere saber si
sirven para su caso antes de financiar un proyecto de ML.

**Componentes:**

| Capa | Repo | Licencia | Papel |
|------|------|----------|-------|
| Datos de entrenamiento | [gridfm/gridfm-datakit](https://github.com/gridfm/gridfm-datakit) | Apache-2.0 | sintetiza casos de flujo de potencia desde la topología del cliente |
| Modelo | [gridfm/gridfm-graphkit](https://github.com/gridfm/gridfm-graphkit) | Apache-2.0 | entrena / fine-tunea el GNN fundacional |
| Alternativa | [microsoft/GridSFM](https://github.com/microsoft/GridSFM) | MIT | *small foundation models* de red (⚠️ sin push desde 2026-07-15) |
| Topología real | [PowerGridModel/power-grid-model](https://github.com/PowerGridModel/power-grid-model) + [power-grid-model-ds](https://github.com/PowerGridModel/power-grid-model-ds) | MPL-2.0 | motor de cálculo de grado producción y puente a pandas |
| Vara de medir | [emarche/RL2Grid](https://github.com/emarche/RL2Grid) | MIT | benchmark estandarizado; y `Power-Agent/PowerAgentBench` (MIT) para tareas agénticas |
| Línea base obligatoria | [OpenSTEF/openstef](https://github.com/OpenSTEF/openstef) | MPL-2.0 | forecasting clásico de operador de red: **si no se le gana, no hay proyecto** |

**Cableado:**

1. Topología del cliente → `gridfm-datakit` genera el corpus de flujo de potencia.
2. `gridfm-graphkit` hace fine-tuning sobre ese corpus.
3. **Se compara contra `openstef`**, no contra nada. `openstef` es lo que un operador de red ya usa.
4. `RL2Grid` / `PowerAgentBench` dan la cifra comparable.
5. Entregable: informe de viabilidad con números, y una recomendación de seguir o parar.

⚠️ **Cómo presentarla con honestidad**: 58–177 ★ y una categoría de siete meses de vida. Esto es una
**fase de evaluación acotada** (semanas), no una plataforma. Vender un foundation model de red como
base de producción en 2026 es sobrevender; vender la evaluación rigurosa de si lo será es un encargo
real, corto y con resultado útil en cualquiera de los dos sentidos.

**El paso 3 es el que protege la relación con el cliente.** Sin la línea base `openstef`, cualquier
resultado parece bueno. Con ella, el informe dice algo.

### Receta 20 — Agregador V2G de flota (EMEA primero, replicable en APAC)

Amplía la Receta 6 (carga de EV) del nivel hogar al nivel **flota**, que es donde está el negocio.

**Componentes:**

| Capa | Repo | Licencia | Papel |
|------|------|----------|-------|
| Simulación V2G a escala | [StavrosOrf/EV2Gym](https://github.com/StavrosOrf/EV2Gym) | **MIT** | entorno de optimización de carga de **flotas** de EV, no un vehículo |
| Optimización de flexibilidad | [FlexMeasures/flexmeasures](https://github.com/FlexMeasures/flexmeasures) | Apache-2.0 | scheduling con precio y restricción de red |
| Protocolo de carga | [mobilityhouse/ocpp](https://github.com/mobilityhouse/ocpp) | MIT | OCPP contra las estaciones |
| Señal de red | [OpenLEADR/openleadr-rs](https://github.com/OpenLEADR/openleadr-rs) | **doble MIT / Apache-2.0** | **OpenADR 3.0** (la versión nueva; `openleadr-python` es 2.0b) |
| Operación en campo | [evcc-io/evcc](https://github.com/evcc-io/evcc) | MIT | 7638 ★: el componente con más tracción real del sector |
| Sitio y flota | [TUMFTM/REVOL-E-TION](https://github.com/TUMFTM/REVOL-E-TION) | Apache-2.0 | optimización a nivel de sitio con integración de flota EV (TU München) |

**Cableado:**

1. `EV2Gym` dimensiona y entrena la política de agregación **offline**, con la flota real del cliente.
2. `FlexMeasures` la ejecuta contra precio y límites de red.
3. `openleadr-rs` recibe la señal de respuesta de demanda del operador — **OpenADR 3.0**, que es lo
   que se está desplegando ahora.
4. `ocpp` / `evcc` actúan sobre las estaciones.
5. `opendsm` (Receta 17) certifica el ahorro y el servicio prestado a la red.

**Nota de licencia favorable, poco habitual**: todo el stack es **MIT o Apache-2.0**. Es el vertical
más limpio de esta KB, y además el de mayor masa crítica comunitaria (T7). Para un primer encargo
energético con un cliente nuevo, es el de menor riesgo técnico y legal.

### Receta 21 — Analítica de cola de interconexión y grandes cargas (North America, dirigida por la orden de la FERC)

**Disparador comercial concreto:** el 2026-06-18 la FERC emitió *show-cause orders* a **seis**
operadores regionales (PJM, MISO, SPP, CAISO, ISO-NE, NYISO). Cada uno tiene que justificar o
reformar cómo conecta grandes cargas. Esos seis, más ERCOT, son **exactamente** los siete que
`gridstatus` lee con una sola interfaz.

**Stack, todo permisivo:**

1. [`gridstatus/gridstatus`](https://github.com/gridstatus/gridstatus) (**BSD-3-Clause**, 456 ★) —
   ingesta homogénea de los siete ISO/RTO: carga, precios nodales, mix de generación.
2. [`singularity-energy/open-grid-emissions`](https://github.com/singularity-energy/open-grid-emissions)
   (**MIT**, 96 ★) — convierte generación horaria en **intensidad de carbono horaria**.
3. [`NatLabRockies/ReEDS-2.0`](https://github.com/NatLabRockies/ReEDS-2.0) (**BSD-3**, 176 ★) o
   [`sylvan-energy/gridpath`](https://github.com/sylvan-energy/gridpath) (**Apache-2.0**, 138 ★) —
   escenarios de expansión bajo la nueva carga.
4. [`sandialabs/quest_planning`](https://github.com/sandialabs/quest_planning) (ya en la KB) —
   planificación de almacenamiento como alternativa al refuerzo de red.
5. [`Green-Software-Foundation/carbon-aware-sdk`](https://github.com/Green-Software-Foundation/carbon-aware-sdk)
   (**MIT**, ya en la KB) — desplaza cómputo flexible a las horas limpias.

**Cómo se cablea:** `gridstatus` escribe series horarias normalizadas en un almacén temporal →
`open-grid-emissions` las enriquece con factor de emisión por hora y región →
`ReEDS-2.0`/`gridpath` consume el perfil de carga nueva como escenario → el resultado alimenta un
informe de localización (*dónde conectar cuesta menos y emite menos*). El `carbon-aware-sdk` cierra
el lazo del lado del cliente de datacenter.

**Entregable que se vende:** un informe comparativo de **siete mercados con el mismo método**. Hoy
cada ISO se analiza con su propio *scraper* ad hoc; la homogeneidad es el producto.

⚠️ **Límites que hay que decir en la propuesta:** ERCOT queda en gran medida **fuera** de la
jurisdicción de la FERC, así que no se puede prometer un marco regulatorio homogéneo entre los siete.
Y los plazos de las órdenes **discrepan entre fuentes secundarias** (60 días vs. informes a 30):
no comprometer fechas.

---

### Receta 22 — Del dimensionado del activo a la verificación del ahorro, en una sola cadena (las cuatro regiones)

**El hueco que cierra:** esta KB sabía operar un activo (`OpenEMS`, `FlexMeasures`) y sabía certificar
un ahorro (`opendsm`, Receta 17), pero no sabía **decidir qué activo instalar**. Esa es la primera
pregunta de todo encargo de energía distribuida y ahora tiene motor abierto.

**Cadena completa, cuatro etapas:**

1. **Decidir el activo** — [`NatLabRockies/REopt_API`](https://github.com/NatLabRockies/REopt_API)
   (BSD-3 + marca REopt®, 128 ★, 70 forks): mezcla óptima de solar + BESS + genset contra la tarifa
   real del emplazamiento. Es el motor de `reopt.nrel.gov`, no una reimplementación.
2. **Modelar el edificio si la carga es térmica** —
   [`NatLabRockies/OpenStudio`](https://github.com/NatLabRockies/OpenStudio) (BSD-3 + marca, 660 ★)
   sobre `EnergyPlus` (ya en la KB), y `sinergym` si se quiere control por RL.
3. **Operar** — `OpenEMS` (EPL-2.0) o `FlexMeasures` (Apache-2.0), ya en la KB, con
   [`Enapter/marketplace`](https://github.com/Enapter/marketplace) (**MIT**) para la integración de
   dispositivos heterogéneos.
4. **Certificar el ahorro** — [`opendsm/opendsm`](https://github.com/opendsm/opendsm)
   (**Apache-2.0**, 244 ★): métodos estándar NMEC. Sin esta etapa el proyecto produce un número que
   nadie firma.

**Previsión como entrada transversal:** `openstef` (MPL-2.0) en EMEA,
[`NatLabRockies/BuildingsBench`](https://github.com/NatLabRockies/BuildingsBench) (**BSD-3**, 123 ★)
como *benchmark* para justificar la elección de modelo de carga.

**Por qué esta receta cierra una venta mejor que las anteriores:** es la única que va de la pregunta
inicial del cliente (*¿qué instalo?*) a la factura final (*¿cuánto ahorré, demostrado?*) sin ningún
componente propietario en medio.

⚠️ **Dos cláusulas de marca en la cadena.** `REopt®` y `OpenStudio®`: el producto de Globant **no
puede llamarse** con esos nombres, ni usarlos en promoción, y una versión modificada debe citar el
original. Resolver el *naming* al principio del proyecto, no al final.

---

### Receta 23 — Entrenar un modelo de carga en EMEA sin tocar datos personales de medición

**El problema real, declarado por el propio regulador:** el informe de la Comisión Europea sobre IA en
redes inteligentes señala **GDPR**, la recolección de datos y el preprocesado extenso como obstáculos
para entrenar modelos. Un cliente europeo que no puede exportar curvas de carga de sus consumidores
no puede entrenar nada — y ésa es la objeción que mata el proyecto en la fase legal, no en la técnica.

**Secuencia que la resuelve:**

1. [`OpenSynth-energy/OpenSynth`](https://github.com/OpenSynth-energy/OpenSynth) (**Apache-2.0**,
   77 ★, cohorte LF Energy) — genera perfiles **sintéticos** de consumo de contador. No son de ningún
   consumidor, así que no hay titular de datos.
2. [`NatLabRockies/BuildingsBench`](https://github.com/NatLabRockies/BuildingsBench) (**BSD-3**,
   123 ★) — preentrena y **mide** el modelo de previsión de carga contra un banco estándar.
3. [`OpenSTEF/openstef`](https://github.com/OpenSTEF/openstef) (**MPL-2.0**, ya en la KB) — lleva el
   modelo a producción con el pipeline que ya usan Alliander y RTE.
4. **Afinado en sitio** con los datos reales del cliente, que **nunca salen** de su perímetro.
5. [`fboerman/entsoe-py`](https://github.com/fboerman/entsoe-py) (**MIT**, 745 ★) — aporta precio y
   generación de mercado, que son datos públicos y no personales.

**El argumento de venta es jurídico antes que técnico:** se entrena fuera con datos que no son de
nadie, se afina dentro con datos que no se mueven. Es una arquitectura que pasa revisión legal, y
ésa es la razón por la que el cliente la compra.

**Dónde encaja la familia `energnn`:** si el cliente es un operador con modelo de red en PowSyBl o
pandapower,
[`energnn/pypowsybl-to-energnn`](https://github.com/energnn/pypowsybl-to-energnn) y
[`energnn/pandapower-to-energnn`](https://github.com/energnn/pandapower-to-energnn) (**MPL-2.0**)
convierten ese modelo en grafo entrenable sin rehacerlo. Son de 0-3 ★: **vía de evaluación**, igual
que la Receta 19, no base de producción.

⚠️ **MPL-2.0 en `openstef` y en `energnn`**: copyleft por archivo. Integrar sí; marca blanca con el
motor modificado, no.

---

### Receta 24 — Copiloto de despacho sobre el modelo nacional ya publicado (LATAM: Chile primero, México después)

**Por qué esta receta existe y por qué ahora.** Hasta este pase, cualquier propuesta de planificación
o despacho en LATAM empezaba por construir el modelo de red del país: semanas de trabajo caro, no
facturable como innovación y con riesgo de datos. **Eso ya está hecho y publicado con licencia MIT
para Chile y México.** Esta receta es la cadena completa desde ese punto de partida.

**Cliente típico**: coordinador/operador, generador con portafolio renovable, o un gran consumidor
—incluido un datacenter— que necesita demostrar al regulador el impacto de su carga en el sistema.

**Piezas, todas verificadas en este pase:**

| Papel | Repo | Licencia | Nota |
|------|------|----------|------|
| Modelo del sistema chileno (SEN) | [paredes-vergara/PyPSA-CL](https://github.com/paredes-vergara/PyPSA-CL) | **MIT** | Inversión a largo plazo + *unit commitment* + despacho económico; datos del Coordinador Eléctrico Nacional, CNE y Ministerio de Energía. 15 ★ |
| Segundo modelo chileno, para contraste | [sanjaygrr/pypsa-chile](https://github.com/sanjaygrr/pypsa-chile) | **MIT** | Despacho del SEN. Push 2026-11-16 |
| Modelo del mercado mexicano (MEM) | [BrandolRuizOlmeda/pypsa-mexico_base](https://github.com/BrandolRuizOlmeda/pypsa-mexico_base) | **MIT** (rama `master`) | Fase 2 de la receta |
| Motor de optimización | [PyPSA/linopy](https://github.com/PyPSA/linopy) | **MIT** | Backend del ecosistema PyPSA |
| Núcleo PyPSA | [PyPSA/PyPSA](https://github.com/PyPSA/PyPSA) | **MIT** | — |
| Capa agéntica sobre el modelo | [open-energy-transition/pypsa-mcp](https://github.com/open-energy-transition/pypsa-mcp) | **MIT** | Expone PyPSA a un LLM: escenarios conversacionales |
| Aceptación humana trazable | [opfab/operatorfabric-core](https://github.com/opfab/operatorfabric-core) | **MPL-2.0** | Obligatoria, no opcional (ver T28) |

**Cómo se conecta, en orden:**

1. **Reproducir el caso base y declarar la discrepancia.** Correr `PyPSA-CL` tal cual y comparar su
   despacho con el publicado por el Coordinador para un período histórico. El entregable de la
   semana 1 **no** es un agente: es un informe de ajuste del modelo contra la realidad del operador.
   Sin ese número, nada de lo que sigue es defendible.
2. **Cruzar los dos modelos chilenos.** Hay dos modelos MIT independientes del mismo sistema. Correr
   ambos sobre el mismo período y comparar es validación cruzada **gratis** — y el tipo de rigor que
   un coordinador exige antes de escuchar una propuesta de IA.
3. **Parametrizar los escenarios con `linopy`**, no a mano: la gran carga nueva (datacenter), el
   retiro de una térmica, la entrada de un bloque solar con su perfil de irradiancia.
4. **Poner `pypsa-mcp` delante.** Aquí es donde el encargo deja de ser un estudio y pasa a ser
   producto: el planificador pregunta *"¿qué pasa si entran 300 MW de carga firme en esta barra en
   2028?"* y el agente arma el escenario, lo resuelve y devuelve el diferencial de costo marginal y de
   congestión. El modelo nacional es el que da credibilidad a la respuesta.
5. **Depositar la recomendación en `operatorfabric-core`**, nunca en el actuador. En Chile el caso de
   uso de pronóstico renovable para despacho ya está en producción: la recomendación entra en un
   proceso que una persona acepta. Ver T28 — en las cuatro regiones hay ahora una fuente normativa que
   lo exige.
6. **Replicar en México** reapuntando los pasos 1–5 a `pypsa-mexico_base`. La arquitectura no cambia;
   cambian el modelo y el regulador.

**Lo que hay que decir al cliente, sin adornos.** Estos repos tienen entre **0 y 15 ★** y entre 0 y 2
forks. **No son software mantenido por una comunidad y no deben presentarse como tal.** Lo que se
compra es que la topología, el parque generador y las series del operador nacional ya están mapeadas a
un formato resoluble. Presupuestar explícitamente: validación del modelo contra datos del operador,
actualización del parque generador, y mantenimiento propio del *fork*. El ahorro es de semanas de
arranque, no del ciclo de vida.

⚠️ **Brasil queda fuera de esta receta, y conviene explicar por qué.**
`leonardovbonatto/pypsa-meets-brazil` modela el SIN con física de hidráulica y valores de agua
estocásticos —exactamente el problema difícil brasileño— y **no tiene archivo de licencia en `main` ni
en `master`**. Sin concesión expresa es copyright exclusivo del autor: **no empotrable en un
entregable**. Para Brasil, la vía sigue siendo `{json:scada}` / `OSHMI` en la capa de control (GPL-3.0,
con sus consecuencias) o construir el modelo de sistema desde `pypsa-earth` asumiendo
**AGPL-3.0-or-later**. Acción barata: abrir issue pidiendo licencia explícita al autor; si responde,
la receta cubre los tres mercados grandes de la región en el próximo pase.

### Receta 25 — Evaluación de forecasting agéntico con control de producción (las cuatro regiones)

**El hueco que cierra:** los pases 4-6 declararon ausente la capa agéntica energética. El séptimo
encontró que existe **para forecasting**, no para operación. Esta receta la pone a trabajar **en vía
de evaluación**, con una línea base honesta, que es la única forma defendible de proponerla hoy.

**Stack, todo permisivo:**

1. [`TimeCopilot/timecopilot`](https://github.com/TimeCopilot/timecopilot) (**MIT**, 643 ★) —
   orquestador agéntico: el LLM selecciona y combina modelos, y **explica** el pronóstico.
2. [`amazon-science/chronos-forecasting`](https://github.com/amazon-science/chronos-forecasting)
   (**Apache-2.0**, 6328 ★) — foundation model de series temporales, zero-shot.
3. [`arnaud-vs/open-predico`](https://github.com/arnaud-vs/open-predico) (**Apache-2.0**, 54 ★) —
   el puente explícito TSFM→energía.
4. [`williamhobbs/hefty`](https://github.com/williamhobbs/hefty) (**BSD-3-Clause**, 85 ★) —
   **la línea base a batir**: forecasting clásico de corto plazo solar, viento y carga.
5. [`OpenSTEF/openstef`](https://github.com/OpenSTEF/openstef) (**MPL-2.0**, 184 ★) —
   **el control de producción**: el único del conjunto con operación real en utility (Alliander, RTE).
6. [`gridstatus/gridstatus`](https://github.com/gridstatus/gridstatus) (**BSD-3**) o las APIs de
   **XM** / `entsoe-py` ya catalogadas — el dato histórico de entrada según la región.

**Cómo se cablea:** una sola serie histórica (carga o precio nodal) se divide en train/test →
corren **en paralelo** cuatro predictores sobre la misma ventana: `hefty` (baseline clásico),
`chronos` (zero-shot), `open-predico` (TSFM ajustado) y `openstef` (pipeline de utility) →
`timecopilot` actúa como **capa de selección y explicación** sobre los cuatro, no como un quinto
predictor → se publica una tabla de error (MAE/pinball por horizonte) y, junto a ella, la
**explicación en lenguaje natural** de por qué eligió cada modelo en cada régimen.

**Entregable que se vende:** no un modelo, sino un **veredicto con trazabilidad**: "para esta serie,
en este mercado, el agente aporta X % sobre el baseline y Y % sobre el pipeline de producción, y aquí
está el registro de por qué". Para un cliente que ya tiene forecasting, ése es el único argumento que
justifica cambiarlo.

⚠️ **Límites que hay que decir en la propuesta:** `timecopilot` y `chronos` son de **propósito
general**, no energéticos; lo verificable es que la cadena existe y es permisiva, **no que esté
validada en despacho**. Esta receta es una **vía de evaluación**, igual que la Receta 19 para
foundation models de red: no proponerla como reemplazo de un pipeline operativo en la primera fase.
Si el cliente opera en EMEA, el expediente de la *Receta 2* (AI Act) aplica también aquí.

---

### Receta 26 — Plataforma de operador de carga de EV, probada sin hardware (EMEA primero, replicable en las cuatro regiones)

**Disparador comercial concreto:** las licitaciones europeas de carga ya exigen **OCPP 2.0.1**, y el
séptimo pase verificó que existe un CSMS **Apache-2.0** que lo habla. Es el único subsector energético
donde esta KB puede afirmar que existe el equivalente de un producto vertical customizable.

**Stack, y la decisión de entrada:**

- Si el cliente **gestiona una red** de estaciones de terceros →
  [`citrineos/citrineos-core`](https://github.com/citrineos/citrineos-core) (**Apache-2.0**, 309 ★)
  como CSMS.
- Si el cliente **fabrica u opera** la estación →
  [`EVerest/EVerest`](https://github.com/EVerest/EVerest) (**Apache-2.0**, 298 ★, **proyecto LF
  Energy**) como stack integral, con
  [`ChargeLab/OpenOCPP`](https://github.com/ChargeLab/OpenOCPP) (**Apache-2.0**) en el firmware.

Alrededor, la capa de prueba, que es lo que vuelve el proyecto demostrable en días:

1. [`SAP/e-mobility-charging-stations-simulator`](https://github.com/SAP/e-mobility-charging-stations-simulator)
   (**Apache-2.0**, 231 ★) — miles de estaciones OCPP-J sintéticas contra el CSMS.
2. [`monta-app/ocpp-emulator`](https://github.com/monta-app/ocpp-emulator) (**Apache-2.0**, 182 ★) —
   emulador de escritorio: la demo que corre en una laptop en la reunión.
3. [`tommymalmqvist/rust-ocpp`](https://github.com/tommymalmqvist/rust-ocpp) (**Apache-2.0**, 106 ★) —
   la única librería del conjunto que ya cubre **OCPP 2.1**: es el argumento de longevidad.
4. [`lbbrhzn/ocpp`](https://github.com/lbbrhzn/ocpp) (**MIT**, 415 ★) — piloto residencial vía Home
   Assistant, coste cero.
5. [`shiv3/ocpp-cp-simulator`](https://github.com/shiv3/ocpp-cp-simulator) (**Apache-2.0**, 48 ★) —
   se declara *for AI agent testing*: el banco donde se prueba el agente de la capa siguiente.
6. [`evcc-io/evcc`](https://github.com/evcc-io/evcc) (**MIT**, 7639 ★, ya en la KB) — carga
   inteligente del lado del usuario.
7. [`IZIVIA/ocpi-toolkit`](https://github.com/IZIVIA/ocpi-toolkit) (**MIT**, 39 ★) — roaming entre
   operadores.

**Cómo se cablea:** `citrineos-core` expone OCPP 2.0.1 → el simulador de SAP genera flota sintética y
carga de estrés → `ocpi-toolkit` conecta el roaming con otros operadores → `evcc` o `lbbrhzn/ocpp`
cubren el extremo de usuario → sobre el CSMS se añade la capa de optimización tarifaria, y el agente
de esa capa se prueba contra `shiv3/ocpp-cp-simulator` antes de tocar una estación real.

**Entregable que se vende:** un CSMS operativo con flota simulada y un informe de conformidad OCPP
2.0.1, **sin haber instalado un cargador**. El riesgo de ejecución del piloto es casi nulo, y eso es
lo que cierra la venta.

⚠️ **Dos trampas de licencia que ya costarían dinero:**
[`steve-community/steve`](https://github.com/steve-community/steve) (1151 ★) es **GPL-3.0** y OCPP
1.6 — la opción obvia por tracción es la bloqueante por licencia y la atrasada por protocolo;
`dallmann-consulting/OCPP.Core` (304 ★) también es **GPL-3.0**. Y
[`ocpi/ocpi`](https://github.com/ocpi/ocpi) (602 ★) tiene licencia **NOASSERTION**: usar
`IZIVIA/ocpi-toolkit` (MIT) para el roaming, no el repo de la especificación.

---

### Receta 27 — Tubería CGMES para foundation models de red (EMEA, dirigida por COM/2026/501)

**Disparador comercial concreto:** la hoja de ruta de la Comisión Europea del **3 de junio de 2026**
asigna **30 M€ en 2026 y 20 M€ en 2027** a foundation models para gestión y planificación de red, con
prueba de concepto en **Q1 2027**. Esos modelos consumen **CGMES**. Hay muchos equipos capaces de
entrenar un GNN de red; hay pocos que sepan ingerir, **validar con SHACL** y versionar el CGMES de un
TSO. La tubería es el diferencial, no el modelo.

**Stack, nueve de once piezas permisivas:**

1. [`alliander-opensource/pycgmes`](https://github.com/alliander-opensource/pycgmes) (**Apache-2.0**) —
   dataclasses CGMES 3 + RDFS + **SHACL**: la puerta de entrada y la validación.
2. [`entsoe/application-profiles-library`](https://github.com/entsoe/application-profiles-library)
   (**Apache-2.0**, ya en la KB) — los perfiles oficiales contra los que se valida.
3. [`SOPTIM/OpenCGMES`](https://github.com/SOPTIM/OpenCGMES) (**Apache-2.0**) y
   [`SOPTIM/RDFArchitect`](https://github.com/SOPTIM/RDFArchitect) (**Apache-2.0**) — suite RDFS/SHACL/CIMXML
   y editor de esquemas con extensiones CIM.
4. [`PNNL-CIM-Tools/CIM-Graph`](https://github.com/PNNL-CIM-Tools/CIM-Graph) (**BSD-3-Clause**) —
   el modelo como **grafo de propiedades en memoria**: la forma que un GNN quiere consumir.
5. [`powsybl/pypowsybl`](https://github.com/powsybl/pypowsybl) (**MPL-2.0**) — cálculo de flujo y
   contingencias sobre el modelo ya cargado.
6. [`powsybl/powsybl-diagram`](https://github.com/powsybl/powsybl-diagram) (**MPL-2.0**) —
   unifilares en SVG: la capa que hace auditable el resultado ante un ingeniero.
7. [`eliagroup/ToOp`](https://github.com/eliagroup/ToOp) (**MPL-2.0**) — optimización de **topología**
   con DC load flow en GPU y validación AC. Autoría de un **TSO** (Elia Group).
8. [`gridfm/gridfm-datakit`](https://github.com/gridfm/gridfm-datakit) (**Apache-2.0**, ya en la KB) —
   generación de datos de flujo para entrenar el modelo.
9. [`statnett/Talk2PowerSystem`](https://github.com/statnett/Talk2PowerSystem) (**Apache-2.0**) —
   **precedente citable**, no dependencia: un TSO poniendo un LLM sobre su grafo CIM.

**Cómo se cablea:** el CGMES del cliente entra por `pycgmes` → se valida con SHACL contra los
perfiles de `application-profiles-library` (este paso es el entregable, no un detalle: un modelo que
no valida no entrena) → `CIM-Graph` lo convierte en grafo de propiedades → `gridfm-datakit` genera
los casos de flujo de entrenamiento → el modelo entrenado propone maniobras → `ToOp` las optimiza y
**valida en AC** → `powsybl-diagram` dibuja el unifilar resultante → `operatorfabric-core` registra la
aceptación humana.

**Entregable que se vende:** un *data pipeline* CGMES validado y versionado, con informe de calidad
del modelo de red del cliente. Es el prerrequisito de cualquier convocatoria de AI.grids, y casi
ninguna utility lo tiene hoy en condiciones.

⚠️ **Límites:** todas las cifras presupuestarias de COM/2026/501 provienen de **cobertura secundaria**
— `eur-lex.europa.eu` no resuelve desde este entorno, séptimo pase consecutivo. **No citar cifras ni
fechas de artículo en una propuesta sin abrir el documento oficial.** Y la validación AC de `ToOp`
no sustituye un estudio de estabilidad: para eso siguen estando `dpsim` y `PowerDynamics.jl`.

---

### Receta 28 — Agregación de DER bajo el régimen de conexión australiano (APAC, Australia primero)

**Disparador comercial concreto:** Australia tiene un régimen de exportación dinámica
**obligatorio** (**CSIP-AUS**, perfil de IEEE 2030.5), y el séptimo pase encontró que ya existe una
implementación **MIT** y mantenida. APAC deja de ser un gap de oferta para este caso de uso concreto.

**Stack:**

1. [`longzheng/open-dynamic-export`](https://github.com/longzheng/open-dynamic-export) (**MIT**, 57 ★) —
   control dinámico de exportación y curtailment de inversores bajo **CSIP-AUS / SEP2 / IEEE 2030.5**.
   Es la pieza que habla el protocolo que el regulador exige.
2. [`ethanndickson/sep2_client`](https://github.com/ethanndickson/sep2_client) (**Apache-2.0**, 24 ★)
   y `sep2_common` (**Apache-2.0**, 14 ★) — cliente IEEE 2030.5 en Rust, si hace falta implementación
   propia en el borde.
3. [`FlexMeasures/flexmeasures`](https://github.com/FlexMeasures/flexmeasures) (**Apache-2.0**, 217 ★,
   ya en la KB) — motor de agregación y programación de la flexibilidad.
4. [`VOLTTRON/volttron`](https://github.com/VOLTTRON/volttron) (**Apache-2.0**, ya en la KB) —
   ejecución en campo.
5. [`UNSW-CEEM/NEMSEER`](https://github.com/UNSW-CEEM/NEMSEER) (⚠️ **GPL-3.0**, 39 ★) — pronósticos
   del **AEMO** para el NEM, **sólo como fuente de datos y validación**.
6. [`bje-/NEMO`](https://github.com/bje-/NEMO) (⚠️ **GPL-3.0**, 55 ★) — optimizador del NEM, **sólo
   como referencia de mercado**.
7. [`pvlib/pvlib-python`](https://github.com/pvlib/pvlib-python) (**BSD-3**, ya en la KB) — recurso
   solar para anticipar el techo de exportación.

**Cómo se cablea:** `pvlib` + `open-meteo` estiman generación esperada → `FlexMeasures` programa la
flexibilidad del portafolio → `open-dynamic-export` traduce la instrucción al protocolo **CSIP-AUS**
y la aplica al inversor, respetando el límite dinámico que publica la DNSP → `volttron` ejecuta en el
borde → `NEMSEER` aporta el pronóstico del AEMO como contexto de mercado y como validación posterior.

**Entregable que se vende:** un agregador de DER **conforme al régimen de conexión australiano**, con
el cumplimiento del protocolo demostrado, no afirmado.

⚠️ **Límite de licencia que define la arquitectura:** `NEMSEER` y `NEMO` son **GPL-3.0**. Pueden
usarse como herramienta interna de análisis y validación, pero **no pueden integrarse en el producto
entregado al cliente** si éste es cerrado. La frontera hay que dibujarla en el diseño, no descubrirla
en la auditoría: el producto se construye sobre `open-dynamic-export` (MIT) y `FlexMeasures`
(Apache-2.0), y los dos GPL quedan del lado del estudio.

---

### Receta 29 — Programa de cumplimiento NERC para carga de datacenter (North America, contra el plazo del 31 de diciembre de 2026)

**Disparador comercial concreto, con fecha:** en julio de 2026 la FERC ordenó a la **NERC** crear
estándares de fiabilidad **exigibles** para datacenters con plazo al **31 de diciembre de 2026**, tras
una **alerta de Nivel 3** de la NERC en mayo de 2026 — la tercera en 58 años. Un estándar exigible con
fecha es un presupuesto de cumplimiento aprobado.

**Stack, todo ya catalogado en esta KB:**

1. [`gridstatus/gridstatus`](https://github.com/gridstatus/gridstatus) (**BSD-3**, 456 ★) — estado y
   precios de los siete ISO/RTO.
2. [`NatLabRockies/PowerGridworld`](https://github.com/NatLabRockies/PowerGridworld) (**BSD-3**) y
   [`dos-group/vessim`](https://github.com/dos-group/vessim) (**MIT**, 103 ★) — el datacenter como
   **activo de red simulable**: `vessim` modela específicamente sistemas energéticos de datacenter.
3. [`e2nIEE/pandapower`](https://github.com/e2nIEE/pandapower) (**BSD-3**) — estudio de la conexión y
   del curtailment bajo contingencia.
4. [`GridProtectionAlliance/openPDC`](https://github.com/GridProtectionAlliance/openPDC) (**MIT**,
   159 ★) y [`GridProtectionAlliance/gsf`](https://github.com/GridProtectionAlliance/gsf) (**MIT**,
   179 ★) — medida sincrofasorial: la evidencia de comportamiento que un estándar exigible va a pedir.
5. [`opfab/operatorfabric-core`](https://github.com/opfab/operatorfabric-core) (**MPL-2.0**) — registro
   trazable de aceptación humana, alineado con la guía **CISA/NSA** de mínimo privilegio.
6. [`mitre/caldera-ot`](https://github.com/mitre/caldera-ot) (**Apache-2.0**, 265 ★) — validación de
   la postura de seguridad OT que la misma guía exige.
7. [`lf-energy/lfe-oss-benefit-cost-framework`](https://github.com/lf-energy/lfe-oss-benefit-cost-framework)
   (**Apache-2.0**) — el anexo que justifica ante el regulador por qué el stack es open source.

**Cómo se cablea:** `vessim` + `PowerGridworld` modelan el perfil de carga flexible del datacenter →
`pandapower` evalúa su efecto en el alimentador y las condiciones de curtailment → `openPDC`/`gsf`
instrumentan la medida real una vez conectado → `operatorfabric-core` registra cada maniobra aceptada
→ `caldera-ot` valida la segmentación OT → el marco de LF Energy acompaña el expediente económico.

**Entregable que se vende:** un **expediente de cumplimiento** con modelo, instrumentación, registro
de decisiones y postura de seguridad, listo para el estándar que la NERC publique. Quien empieza en
diciembre llega tarde.

⚠️ **Límite jurisdiccional, el mismo de la Receta 21:** las órdenes de la FERC **no cubren ERCOT**.
Para un cliente en Texas este expediente hay que reconstruirlo sobre las reglas de ERCOT, y el
argumento comercial es distinto. Y los plazos citados provienen de **fuentes secundarias** que
discrepan entre sí: no comprometer fechas contractuales sin leer la orden en el expediente de la FERC.

---

## Qué **no** proponer (gaps medidos, actualizado en el tercer pase del 2026-11-20)

Buscado y no encontrado — declarado para que nadie prometa lo que no tiene base. **Tres entradas de
esta lista se cayeron hoy**; se registran como cerradas para que no se arrastren:

| Lo que decía el primer pase | Estado al cierre del día |
|-----------------------------|--------------------------|
| "Trading / mercados: cero repos. **No hay punto de partida**" | 🟡 **Hay punto de partida para simular** (`assume` MIT 128 ★, `elecsim` MIT 61 ★, datos vía `hass-entso-e` y `API_XM`). **Sigue sin haberlo para ejecutar**: ningún repo coloca ofertas reales |
| "Mantenimiento predictivo renovable: sólo datasets" | ✅ **Cerrado** (`OpenOA` BSD-3 259 ★, `rdtools` MIT 190 ★, `pvanalytics` MIT 145 ★) → Receta 8 |
| "Gemelo digital de distribución: sólo piezas" | 🟡 **Cinco piezas**, aún sin plataforma integrada → Receta 9, presupuestada como integración |

**Lo que sigue sin base y no se debe proponer:**

- **Bot de trading mayorista.** Existe la simulación, **no la ejecución**. Si el cliente pide colocar
  ofertas, no hay base open source: es desarrollo desde cero más integración con el operador de
  mercado.
- **Plataforma de gemelo digital de distribución "lista".** Hay motores (`OpenDSS`, `pandapower`,
  `power-grid-model`, `gridlab-d`, `dpsim`) y **ninguna plataforma end-to-end**. Proponerlo es
  trabajo de integración y de calibración del modelo de red. Presupuestar en consecuencia.
- **Modelos de foundation energéticos con licencia de pesos verificada.** `huggingface.co` devuelve
  **403 del proxy** (séptimo pase consecutivo). `Power-Agent/PowerFM` (MIT, 59 ★) es el único punto
  de entrada verificable y es incipiente. **No prometer pesos preentrenados.**
- **"Base open source local" en APAC.** Verificado: `MyEMS` (MIT, 763 ★) y `price_forecast`
  (MIT, 25 ★). La hipótesis de que el resto está en Gitee **no es testeable** desde este entorno
  (`gitee.com` → 403). No afirmar cobertura local en una propuesta APAC.
- **Credencial regional en Argentina, Chile o México.** Buscado por institución (CAMMESA,
  Coordinador Eléctrico Nacional, CENACE) y por término de dominio: **cero repos institucionales con
  tracción**. La credencial LATAM verificable es **Brasil** (`json-scada`, `OSHMI`, autor individual)
  y **Colombia** (`API_XM`, institucional).
- **"Plataforma OpenGrid" como base técnica.** Anuncio institucional de 2026 (Linux Foundation).
  Buscado en GitHub: **sin repo de código localizable**. Seguirlo, no comprometerlo en alcance.
- **`CommonGrid` como dataset empotrado — corregido en el octavo pase (2026-11-20).** Los pases
  anteriores registraron "sin repo de código localizable": **era un error de vocabulario de
  organización**. El repo existe y es [`TextureHQ/commongrid`](https://github.com/TextureHQ/commongrid)
  (14 ★, push 2026-11-19); `user:texture-hq` devuelve HTTP 422 porque la organización es `TextureHQ`,
  sin guion. **La advertencia de licencia se confirma y se endurece** desde el `LICENSE` crudo: *Open
  Data Commons Open Database License (ODbL) v1.0, Copyright (c) 2025-2026 Texture, Inc.* Es licencia
  de **base de datos** con obligación de compartir los derivados de la base. Utilizable **como fuente
  consultada**; **no empotrable** como dataset dentro de un entregable cerrado sin análisis legal.
- **Modelo de estela de DTU vía `PyWake` en GitHub.** Lo que hay allí es un **espejo** del GitLab de
  DTU: licencia `null` y último push 2024-11-25. Usar `floris` (BSD-3) salvo que el cliente exija
  DTU, en cuyo caso la fuente es GitLab y la licencia hay que resolverla aparte.
- **"Un Odoo de la energía".** No existe un sistema open source único que cubra ERP + CRM +
  facturación + gestión de datos de medición. Hay piezas componibles (Receta 16) y **la lógica
  tarifaria regulatoria siempre es desarrollo propio**. Prometer un COTS configurable es prometer lo
  que no hay.
- **Upstream de O&G empotrado en producto propietario.** Todo lo encontrado es **GPL-3.0** sin
  alternativa permisiva. El límite de proceso es la condición del entregable, no una recomendación.
- **Compromisos de cumplimiento con fecha firmada del AI Act.** La fecha (2-dic-2027, Reglamento (UE)
  2026/1744) tiene concordancia de **nueve fuentes secundarias** y **cero** confirmación primaria:
  `eur-lex.europa.eu` devuelve 403 desde este entorno. Sirve para planear; **no** para firmar.

### Actualización del cuarto pase (2026-11-20)

**Nuevos "no proponer", medidos en este pase:**

- **Un foundation model de subsuelo.** `douyimin/GEM` existe, hace exactamente lo que un cliente de
  O&G pediría, y **no tiene archivo de licencia en ninguna rama**. No es un gap de oferta: es un gap
  de permiso. No incluir en alcance hasta que el autor publique licencia.
- **Un "ERP/CRM energético open source".** Verificado como respuesta negativa: no existe con licencia
  MIT/Apache. Proponer `OFBiz` + `killbill` + `openmeter` (todas permisivas) **más desarrollo propio
  de la lógica tarifaria regulada**, y presupuestar ese desarrollo explícitamente.
- **Una plataforma DERMS open source.** Hay piezas (`FlexMeasures`, `OpenLEADR`, `power-grid-model`);
  no hay sistema. Un DERMS es integración, no instalación.
- **Un foundation model de red como base de producción.** Ver Receta 19: es vía de **evaluación**.
  58–177 ★ y siete meses de vida no sostienen un SLA.
- **Cualquier fila basada sólo en stars.** Dos repos de forecasting de carga con 1764 ★ / 0 forks y
  1627 ★ / 0 forks (cuenta `KEV0143`) habrían encabezado la tabla de esta KB. Comprobar
  `forks_count` e `open_issues_count` antes de comprometer alcance sobre un repo de >1000 ★.

### Trampas de licencia que ya costarían dinero hoy

| Repo | Parece | Es | Consecuencia si se asume mal |
|------|--------|----|------------------------------|
| `pypsa-earth` (384 ★) | sin licencia (API dice `null`) | **AGPL-3.0-or-later** (SPDX en `README`) | Obligación de liberar el servicio en un SaaS de cliente |
| `gridlab-d` (221 ★) | BSD | **licencia propia Battelle v5.3, no OSI/SPDX** | Gate de compliance la marca como desconocida; cláusula de nombre y derechos gov. |
| `oemof-solph` (430 ★) | sin licencia (API dice `null`) | **MIT** (SPDX en `pyproject.toml`) | Se descarta un repo perfectamente usable |
| `u9n/dlms-cosem` (124 ★) | open source | **Business Source License 1.1** | No es permisiva; pasa por open source en una revisión superficial |
| `EnergyPlus` | BSD-3 | **BSD-3 + cláusula (4) de marca del DOE** | Prohibido usar "EnergyPlus"/"E+" en nombre de producto o promoción |
| `GenXProject/GenX.jl` (370 ★) | universitario y muy citado → "será MIT" | **GPL-2.0** | Copyleft fuerte en el entregable de planificación |
| `open-meteo/open-meteo` (6.703 ★) | API de clima gratuita, muy usada en forecasting renovable | **AGPL-3.0** y API pública *non-commercial use* | Dos restricciones distintas; ambas muerden en un SaaS de cliente |
| `openmc-dev/openmc` (1.147 ★) | API dice `NOASSERTION` → "sin licencia" | **MIT** (texto verificado) | Descartarlo sería perder la única base nuclear abierta |
| `idaholab/moose` (2.409 ★) | laboratorio nacional → "permisivo" | **LGPL-2.1** | Modificaciones al propio MOOSE deben liberarse |
| `navariltd/utility-billing` (70 ★) | app de facturación sobre ERPNext | **AGPL-3.0** sobre ERPNext **GPL-3.0** | Cláusula de red en cualquier SaaS de utility |
| Familia LF Energy (`Grid2Op`, `PowSyBl`, `operatorfabric-core`, `ExpertOp4Grid`, `power-grid-model-ai`) | "open source europeo" | **MPL-2.0** de forma consistente | Copyleft por archivo: integración sí, marca blanca con motor modificado no |


### Actualización del quinto pase (2026-11-20)

**Entradas que se caen de la lista "no proponer":**

| Lo que decía un pase anterior | Estado al quinto pase |
|-------------------------------|------------------------|
| (implícito) "la ingesta de datos de mercado es desarrollo propio" | ✅ **Falso para EMEA y North America.** `entsoe-py` (MIT, 745 ★) y `gridstatus` (BSD-3, 456 ★). Sigue siendo cierto en **LATAM y APAC** |
| "Dimensionar el activo es desarrollo propio" | ✅ **Cerrado.** `REopt_API` es el motor real de NREL (BSD-3 + marca) → Receta 22 |

**Nuevos "no proponer", medidos en este pase:**

- **Un bot de pujas mayoristas.** Reafirmado por quinta vez y ahora con la frontera dibujada (T25):
  *leer* el mercado es MIT/BSD y maduro; *pujar* no tiene base en ninguna región. 15 resultados de
  `day-ahead bidding`, ninguno por encima de 12 ★, casi todos sin licencia.
- **Huella de carbono horaria fuera de EE. UU.** `open-grid-emissions` (MIT) cubre **sólo** la red
  estadounidense. Prometer intensidad de carbono horaria verificable en EMEA, APAC o LATAM es
  prometer desarrollo de la capa de factores de emisión. **Gap nuevo de este pase.**
- **Una plataforma geotérmica.** Hay **un** repo usable (`GEOPHIRES-X`, MIT, 67 ★) y es un simulador
  técnico-económico, no una plataforma. Y cuidado: `GEOPHIRES-v2` es **GPL-3.0** — mismo simulador,
  licencia distinta según versión.
- **Un ecosistema de hidrógeno.** Tres repos permisivos (`electrolyzer` Apache-2.0 35 ★, `HOPP`
  BSD-3 41 ★, `AlphaPEM` BSD-3 49 ★) más `pandapipes`. Base para un estudio; no para un producto.
- **`PyPSA-AR` en un entregable para Argentina.** Existe (10 ★) y **no tiene archivo de licencia**
  en ninguna rama. Es el caso `GEM` otra vez: gap de permiso, no de oferta.
- **Nada basado en `resstock` para un cliente académico o sin ánimo de lucro** sin revisión legal
  previa. Ver la tabla de trampas.

### Actualización del séptimo pase (2026-11-20)

**Gaps que este pase CERRÓ:**

- ~~No existe agente energético proponible~~ → existe **para forecasting**
  (`timecopilot` MIT + `chronos` Apache-2.0 + `open-predico` Apache-2.0). Sigue sin existir para
  **operación de red**, y ahora con medición externa: IEA, **23 %** de operadores en tiempo real.
- ~~APAC es un gap de oferta~~ → cuatro repos australianos verificados
  (`open-dynamic-export` **MIT**, `sep2_client` Apache-2.0, `NEMSEER` y `NEMO` GPL-3.0). Era un gap
  de **vocabulario**: el término es el nombre de la norma de conexión (**CSIP-AUS**), no "APAC".
- ~~Carga de EV catalogada a medias~~ → once repos nuevos, nueve permisivos, stack completo y probable
  sin hardware (Receta 26).
- ~~Falta la tubería CGMES~~ → once repos, nueve permisivos (Receta 27).
- ~~Hidrógeno y electroquímica delgados~~ → `openFuelCell2`, `BattMo` (ambos GPL-3.0),
  `MacroEnergy.jl` (**MIT**), `openTEPES` (AGPL-3.0), `FINE` (NOASSERTION). El "gap" anterior era en
  parte un **artefacto de sintaxis de búsqueda** (ver T35).
- ~~No hay forma de justificar open source ante una utility regulada~~ →
  `lf-energy/lfe-oss-benefit-cost-framework` (Apache-2.0, creado 2026-09-08).
- ~~Falta predicción de intensidad de carbono~~ → `CarbonCast` (Apache-2.0).

**Gaps que SIGUEN abiertos, declarados sin adornos:**

- **Agente de operación de red en lazo cerrado: no existe, y no debe proponerse.** Cuarto pase
  consecutivo sin candidato. Confirmado por la IEA (23 %), por la posición escrita de la NERC (la IA
  asiste, no decide) y por la guía CISA/NSA de mayo de 2026 (mínimo privilegio).
- **Detalle regulatorio de China, India y Japón sobre IA en energía: ausente.** Hay cifras de
  inversión y casos de despliegue (State Grid, TEPCO, Chubu), pero **no** el equivalente de la orden
  de la FERC o de COM/2026/501. No se puede construir un argumento de cumplimiento para esos tres
  mercados con lo que hay hoy en esta KB.
- **Registro primario de la UE: inaccesible, séptimo pase consecutivo.** `eur-lex.europa.eu` no
  resuelve (`ENOTFOUND`); `data.consilium.europa.eu` tampoco en los pases 1-6. Todas las cifras de
  COM/2026/501 son de cobertura secundaria. Para cerrarlo haría falta habilitar el dominio en la
  política de red de la sesión.
- **Pesos de modelo sin licencia verificada:** `huggingface.co` no resuelve desde este entorno. No se
  puede afirmar la licencia de los pesos de ningún foundation model de red.
- **Nuclear y geotermia: sin reconsultar correctamente.** Las búsquedas de este pase volvieron a
  usar sintaxis sospechosa para nuclear (cero filas). Dado T35, **no declarar estos dos como gaps
  reales** hasta reconsultarlos sin paréntesis. Lo catalogado sigue siendo `openmc`, `moose` y
  `GEOPHIRES-X`.
- **Tamaño de mercado: no citable.** Dispersión de **5,3×** en el mismo año para el mismo objeto.
  Citar adopción y capex, nunca tamaño.

**Lo que el próximo pase debería hacer primero**, en orden:

1. Reconsultar nuclear y geotermia **sin paréntesis** en la consulta (T35) — puede haber una categoría
   entera oculta tras un error de sintaxis.
2. Buscar por norma de conexión en los mercados aún cerrados: **CEI 0-21** (Italia),
   **VDE-AR-N 4105** (Alemania), **G99** (Reino Unido), **PRODIST** (Brasil), **NOM-001-SEDE**
   (México), **GB/T 19964** (China). Es el método que abrió LATAM en el pase 6 y APAC en el 7.
3. Recorrer [`juherr/awesome-ev-charging`](https://github.com/juherr/awesome-ev-charging) (CC0-1.0) y
   [`lf-energy/lfenergy-landscape`](https://github.com/lf-energy/lfenergy-landscape) (Apache-2.0)
   como índices de descubrimiento: ambos son mapas vivos de categorías que esta KB ya sabe que son
   ricas.
4. Pedir que se habilite `eur-lex.europa.eu` y `huggingface.co` en la política de red, que son los dos
   techos de verificación que quedan.

### Actualización del sexto pase (2026-11-20)

**Un gap se cierra y hay que retirarlo de la lista.** "No hay modelos de sistema eléctrico de origen
LATAM" **es falso desde este pase**: existen `PyPSA-CL` y `pypsa-chile` (Chile) y `pypsa-mexico_base`
(México), los tres **MIT**. La Receta 24 es la cadena que los usa. Lo que queda de ese gap es
específico y menor: **Brasil** sigue sin modelo de sistema usable (el que existe no tiene licencia).

**Gaps que siguen abiertos, medidos otra vez en este pase:**

- **Cola de interconexión y *siting* de datacenter**: el pase 5 lo marcó "a vigilar"; se buscó y sigue
  vacío. `interconnection queue in:name,description` devuelve simuladores de redes de paquetes y
  pipelines de datos de Steam; lo único temáticamente correcto es
  `selormdzakpasu/gen_interconnection_queues` (las colas de los siete ISO) con **1 ★ y sin licencia**.
  **No proponer producto; proponer desarrollo a medida** — la demanda es alta y la oferta open source
  no existe, que es justamente por lo que es facturable.
- **Agente energético open source de propósito general**: tercer pase consecutivo sin nada. La
  búsqueda global de agentes 2026 devuelve `OpenClaw`, `OpenHands`, `CrewAI`, `LangGraph` — ninguno
  energético. Lo proponible sigue siendo lo institucional (`PowerMCP`, `EnergyPlus-MCP`, `pypsa-mcp`).
- **Repos de origen APAC**: sin novedad. Pero ahora hay una consulta concreta que probar (T27):
  `pypsa-india`, `pypsa-vietnam`, `pypsa-indonesia`, `pypsa-korea`, `calliope-*`, `osemosys-*`.
- **ERP/CRM/MDM energético permisivo**: confirmado inexistente por segundo pase. Los resultados de
  búsqueda son productos comerciales; **"Open" en un nombre de producto no es una licencia** (*Neta
  Open Suite*). La excepción real sigue siendo `EnAccess/micropowermanager` (MIT) para mini-red.
- **Ejecución de trading mayorista**: sin cambios, no hay base open source en ninguna región (T25).
- **Verificación primaria regulatoria**: **sigue siendo la restricción vinculante.** Este pase añadió
  mucha superficie regulatoria (hoja de ruta de la CE del 3 de junio de 2026, modificación del EMR del
  17 de julio, guías del artículo 6 del AI Act, guía de la NERC, plan nacional chino, tarifa vietnamita
  de almacenamiento) y **todo es secundario**. `data.consilium.europa.eu` no resuelve desde este
  entorno, igual que `eur-lex.europa.eu` devuelve 403. Sirve para orientar; **no para firmar**.

### Trampas de licencia añadidas en el quinto pase

| Repo | Parece | Es | Consecuencia si se asume mal |
|------|--------|----|------------------------------|
| `NatLabRockies/resstock` (147 ★) | laboratorio nacional → "BSD permisiva" | **BSD-3 + copyleft condicionado al TIPO DE REDISTRIBUIDOR + marca ResStock™** | **Si el cliente es universidad, laboratorio nacional u ONG, hay que publicar todo el código correspondiente de la redistribución, modificada o no.** Se activa por quién es el cliente, no por lo que se hace |
| `NatLabRockies/REopt_API` (128 ★) | BSD-3 | **BSD-3 + cláusula de designación `REopt®` + no-endoso DOE** | La versión modificada no puede llamarse REopt® y **debe** citar el original como REopt® |
| `NatLabRockies/OpenStudio` (660 ★) | BSD-3 | **BSD-3 + marca `OpenStudio®`** | Igual que `EnergyPlus`: el nombre no puede ir en producto ni promoción |
| `richard-weinhold/pomato` (101 ★) | la API dice `NOASSERTION` → "sin licencia" | **LGPL-3.0** declarada en `LICENSE.md` | Se descartaría un repo usable; y es copyleft de biblioteca (sin push desde 2025-08) |
| `NatLabRockies/electrolyzer` (35 ★) | la API dice `NOASSERTION` | **Apache-2.0** limpia | Se descartaría la única base permisiva de electrolizador |
| `PyPSA/pypsa-eur` (640 ★) | la API dice `null` → "sin licencia" | **Código MIT + documentación/datos CC-BY-4.0** (esquema REUSE, `LICENSES/`) | Se descartaría el modelo europeo de referencia |
| `PyPSA/PyPSA-China` (49 ★) | la API dice `null` | **MIT** (README + `LICENSES/MIT.txt`) | Se descartaría la única pieza APAC con licencia verificada |
| `FTDT-PyPSA/PyPSA-AR` (10 ★) | "es un PyPSA, será MIT" | **sin licencia alguna** | Se incluiría en un entregable argentino sin derecho a hacerlo |
| `energnn/energnn` (34 ★) y familia | un `grep` del texto dice **AGPL-3.0** | **MPL-2.0** | Falso positivo: la MPL-2.0 **nombra la AGPL en su cláusula 1.12**. Se inventaría una obligación de liberar el servicio |
| `jo20ow/Obsyd` (12 ★) | "el GridStatus europeo" | **AGPL-3.0** | Cláusula de red en un SaaS de cliente |

**La lección transversal del ecosistema PyPSA**: usa el esquema **REUSE** (licencias en `LICENSES/`
y cabeceras SPDX), por lo que la API de GitHub devuelve `null` para casi toda la familia mientras el
código es perfectamente usable. Resultado medido en cinco repos: **`pypsa-eur` MIT+CC-BY-4.0 ·
`PyPSA-China` MIT · `PyPSA-GB` MIT · `pypsa-earth` AGPL-3.0-or-later · `PyPSA-AR` sin licencia**.
Mismo ecosistema, **cinco resultados distintos**. Nunca inferir la licencia de un `PyPSA-*` por
familia: hay que leer cada uno.

## Recetas del octavo pase (2026-11-20)

### Receta 30 — Estructurador de PPA: del dato de mercado al contrato firmable

**El problema del cliente.** Un comprador corporativo (datacenter, industria, retail) tiene que
firmar energía renovable a largo plazo y la pregunta que trae a la primera reunión es *¿a qué precio
y con qué riesgo firmo?*. Hasta este pase esta KB tenía el **dato de mercado** del PPA y ninguna
herramienta para estructurarlo.

**Las piezas, todas verificadas y permisivas:**

| Capa | Repo | Licencia | Rol |
|------|------|----------|-----|
| Motor de red y despacho | [PyPSA/PyPSA](https://github.com/PyPSA/PyPSA) | MIT | Optimización del sistema; ya catalogado |
| Escenarios de PPA | [open-energy-transition/pypsa-ppa](https://github.com/open-energy-transition/pypsa-ppa) | MIT | Simula y optimiza estructuras de PPA bajo escenarios |
| Modelo del país | `pypsa-meets-brazil`, `PyPSA-CL`, `pypsa-mexico_base`, `PyPSA-AR` | MIT | Red real del país en lugar de un sistema de juguete |
| Perfil de recurso | [pvlib/pvlib-python](https://github.com/pvlib/pvlib-python) + [NatLabRockies/floris](https://github.com/NatLabRockies/floris) | BSD-3 | Generación solar y eólica esperada |
| Baseline de forecast | [williamhobbs/hefty](https://github.com/williamhobbs/hefty) | BSD-3 | Pronóstico corto honesto contra el que medir |
| Datos de EE. UU. | [catalyst-cooperative/pudl](https://github.com/catalyst-cooperative/pudl) | MIT | Formularios FERC/EIA/EPA como tablas, si el caso es norteamericano |

**Cómo se cablea.** `pypsa-ppa` define las estructuras contractuales candidatas (*pay-as-produced*,
*pay-as-consumed*, *baseload* con firmeza, con o sin tope) y las evalúa sobre el modelo PyPSA del
país; `pvlib`/`floris` generan los perfiles horarios del recurso del sitio concreto; `hefty` aporta
la banda de error de pronóstico que fija el coste de desbalance. La salida es una **tabla de
estructuras con su precio esperado, su exposición a desbalance y su peor escenario**, no un número
único. El LLM redacta la memoria de supuestos y la compara entre estructuras; **no elige la
estructura**.

⚠️ **Lo que hay que decirle al cliente.** `pypsa-ppa` tiene **8 ★ y push de 2026-11-09**: es MIT y
resuelve el problema correcto, pero **no hay comunidad detrás**. Tratarlo como punto de partida de un
acelerador propio. La dependencia sólida es PyPSA. Y el resultado es **un análisis de decisión, no
asesoría financiera ni legal**: la estructura la firma el cliente con sus asesores.

**Dónde se vende hoy, con el dato que lo justifica.** Brasil (Equinix firmó PPA con Auren; 38 GW de
solicitudes de acceso contra ~12 GW disponibles), LATAM en general (PPAs bajo 0,06 USD/kWh) y EMEA,
donde el esquema de calificación de datacenters puntúa el abastecimiento renovable.

### Receta 31 — Expediente de interacción con la red para el *rating* europeo de datacenters

**El problema del cliente.** La Comisión propuso el 21 de septiembre de 2026 un esquema de
calificación para datacenters de **≥500 kW de potencia TI** que puntúa eficiencia energética e
hídrica, estrés hídrico local, reutilización de calor residual y **cómo la instalación interactúa con
la red**. Las normas mínimas están en **consulta hasta el 14 de diciembre de 2026** y la propuesta
legislativa se planea para **2027**. Ningún operador tiene hoy ese expediente armado, y **no existe
herramienta abierta de referencia para producirlo**.

**Las piezas:**

| Capa | Repo | Licencia | Rol |
|------|------|----------|-----|
| Modelo de red europeo | [powsybl/powsybl-core](https://github.com/powsybl/powsybl-core) | MPL-2.0 (verificada 2026-11-20) | Cálculo de flujos sobre el modelo CGMES |
| Perfiles CGMES | [entsoe/application-profiles-library](https://github.com/entsoe/application-profiles-library) | ver ficha | El formato que el operador europeo habla |
| Flexibilidad de carga | [OpenADR](https://github.com/oadr3-org) / `OpenLEADR` | Apache-2.0 | Señal de respuesta de demanda demostrable |
| Simulación del edificio/instalación | [NatLabRockies/EnergyPlus](https://github.com/NatLabRockies/EnergyPlus) + [LBNL-ETA/EnergyPlus-MCP](https://github.com/LBNL-ETA/EnergyPlus-MCP) | BSD | Eficiencia y calor residual, con el MCP para iterar conversacionalmente |
| Escenarios de sistema | [MAHTEP/TEMOA-Europe](https://github.com/MAHTEP/TEMOA-Europe) | MIT (código) + CC-BY-4.0 (datos) | Contexto europeo con datos ya publicados |
| Trazabilidad del modelo | [open-energy-transition/gridlens](https://github.com/open-energy-transition/gridlens) | MIT | **Patrón**, no dependencia: qué modelo sostiene qué afirmación del expediente |

**Cómo se cablea.** `EnergyPlus` (vía su MCP, 35 herramientas) produce las métricas de eficiencia y
el balance de calor recuperable; `powsybl-core` sobre el modelo CGMES del nodo de conexión cuantifica
el impacto en red y el efecto de curtailar; `OpenADR` demuestra que la flexibilidad es **despachable
y verificable**, no declarativa. El agente compone el expediente y **cita cada número con el modelo y
la versión que lo produjo** — que es el patrón que `gridlens` nombra y que un regulador exige.

⚠️ **Dos advertencias.** (1) El esquema está **en consulta**: el entregable de hoy es un expediente
*preparatorio* y una posición para la consulta, no cumplimiento de una norma vigente. Venderlo como lo
segundo es un error. (2) El umbral de 500 kW define qué clientes quedan dentro: **verificarlo por
cliente** antes de proponer.

### Receta 32 — Inventario de la generación distribuida que la distribuidora no sabe que tiene

**El problema del cliente.** Una distribuidora no conoce cuánta solar en tejado está conectada a sus
circuitos. Eso rompe el forecast, la planificación de capacidad de alojamiento y la gestión de
tensión — y es un problema universal, no regional.

**Las piezas, todas MIT:**

| Capa | Repo | Licencia | Rol |
|------|------|----------|-----|
| Detección desde satélite gratuito | [open-energy-transition/earthpv](https://github.com/open-energy-transition/earthpv) | MIT | Mapeo de solar en tejado desde imagen satelital libre |
| Detección a escala regional | [open-energy-transition/rooftopsenti](https://github.com/open-energy-transition/rooftopsenti) | MIT, ⚠️ **archivado** | Instalaciones grandes con Sentinel-2 a escala país/estado |
| Activos de red desde OSM | [open-energy-transition/osm-powerplants](https://github.com/open-energy-transition/osm-powerplants) | MIT | Centrales eléctricas desde OpenStreetMap |
| Topología de red | [open-energy-transition/MapYourGrid](https://github.com/open-energy-transition/MapYourGrid) + [grid-mapping-starter-kit](https://github.com/open-energy-transition/grid-mapping-starter-kit) (⚠️ archivado) | CC-BY-4.0 / CC0-1.0 | A qué circuito pertenece cada cosa |
| Flujos de distribución | [pandapower](https://github.com/e2nIEE/pandapower) | BSD-3 | Impacto en tensión y capacidad de alojamiento |
| Producción esperada | [pvlib/pvlib-python](https://github.com/pvlib/pvlib-python) | BSD-3 | Convertir el área detectada en energía horaria |
| Control de reactiva (Alemania) | [KIT-IAI/PIDE](https://github.com/KIT-IAI/PIDE) | MIT | Referencia de método para control autónomo de reactiva bajo VDE-AR-N |

**Cómo se cablea.** `earthpv`/`rooftopsenti` detectan el área de paneles; `pvlib` la convierte en
perfil horario; `MapYourGrid` asigna cada detección a un circuito; `pandapower` calcula tensión y
capacidad de alojamiento restante por alimentador. La salida es un **mapa de DER oculta por
alimentador con su capacidad de alojamiento remanente** — directamente accionable para la cola de
conexión y para la respuesta al cliente que pide conectar más.

⚠️ **Límites que conviene fijar por contrato.** `earthpv` tiene 22 ★ y push del 2026-11-20: es la
pieza viva de la receta. **`rooftopsenti` y `grid-mapping-starter-kit` están ARCHIVADOS** (verificado
2026-11-20): su código es MIT/CC0 y sigue siendo legible y forkeable, pero **no recibirán arreglos** —
tratarlos como referencia a vendorizar, no como dependencia mantenida. La precisión de detección
depende de la resolución satelital y hay que **validarla contra una muestra terreno del cliente antes
de comprometer un número**. Y la salida es un **inventario estimado**, no un censo regulatorio:
decirlo en el entregable.

---
*Verificado 2026-11-20 en ocho pases (32 recetas). Re-verificar licencias y stars antes de
comprometer alcance.*
