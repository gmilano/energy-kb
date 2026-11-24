---
industry: energy
region: Global
updated: 2026-11-24
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
3. **Operar** — `OpenEMS` (**EPL-2.0 en Edge y Backend**, que son los componentes que se despliegan
   aquí; la UI Angular es AGPL-3.0 y se sustituye o se aísla) o `FlexMeasures` (Apache-2.0), ya en
   la KB, con
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

## Recetas del noveno pase (2026-11-20)

### Receta 33 — O&M de parque eólico con autorización humana auditable (las cuatro regiones)

**Problema que resuelve.** El operador tiene SCADA, tiene alarmas y tiene un EAM, y entre la alarma
y la orden de trabajo hay una persona leyendo pantallas. Quiere agentes, y no puede aceptar que un
agente mande a un técnico a una góndola sin traza.

**Punto de partida — y esto es una plantilla, no un producto a desplegar:**
[`Ninemilo/OpenVigil`](https://github.com/Ninemilo/OpenVigil) (**Apache-2.0**, 180 ★, 37 forks).
Aporta la estructura que hay que copiar: **22 agentes en tres capas separadas** (decisión → revisión
→ ejecución), runtime de 16 tools, catálogo SQL gobernado de 18 tools sobre **LangGraph**, y
conectores SCADA / MQTT / HTTPS / **EAM**.

**Cableado:**

```
[SCADA + CMS + meteorología]  ──┐
                                ├─> ingesta (TimescaleDB) ─> detección de anomalía
[documentos: PDF/DOCX/MD]  ─────┘        │                   (benchmark CARE v6, offline)
   via Docling (OCR)                     │
                                         v
                         [capa de DECISIÓN: agentes proponen alternativas]
                                         │
                                         v
                         [capa de REVISIÓN: contraste + evidencia citada]
                                         │
                                         v
                    ╔═══════════════════════════════════════╗
                    ║  AUTORIZACIÓN HUMANA (alto riesgo)    ║  <-- el límite no negociable
                    ╚═══════════════════════════════════════╝
                                         │
                                         v
                         [capa de EJECUCIÓN: orden de trabajo al EAM]
                                         │
                                         v
                         [evidencia de campo -> actualización de conocimiento]
```

**Piezas complementarias ya catalogadas:** `OpenFAST` (Apache-2.0) y
[`IEAWindSystems/IEA-15-240-RWT`](https://github.com/IEAWindSystems/IEA-15-240-RWT) (Apache-2.0,
314 ★) para el modelo del activo; `NatLabRockies/ROSCO` (Apache-2.0) para el controlador;
`sltzgs/OpenWindSCADA` (GPL-3.0 — aislar) para datasets de referencia;
[`ebranlard/welib`](https://github.com/ebranlard/welib) (MIT) para análisis; `PML-UCF/pinn_wind_bearing`
(MIT) para vida de rodamiento con red neuronal informada por física.

**Lo que hay que decir en la propuesta, textualmente:**

- `OpenVigil` **se declara** *"production candidate implementation, not a system already deployed in
  production"*, y marca **UNVERIFIED** exactitud de campo, calibración, operación en sombra y
  calificación de release. **No prometer su desempeño: no publica ninguno.**
- Su demo corre con **fixtures deterministas**, no con modelos en vivo. Lo que se reutiliza es
  **la arquitectura**, y el esfuerzo real está en los **contratos de datos** SCADA/CMS/EAM.
- El benchmark **CARE v6** (Fraunhofer IEE, 95 eventos, 36 activos) es **CC BY-SA 4.0 y no viene en
  el repo**: lo aporta el cliente, y su licencia *share-alike* contamina derivados del dataset.
- **No nombra ningún protocolo industrial** (ni OPC UA ni IEC 61400-25): la integración de campo es
  alcance a presupuestar, no capacidad heredada.
- 180 ★ con **0 issues abiertas** en 2,5 meses: verificar mantenimiento antes de depender del
  upstream. Plan B: quedarse con el patrón y reimplementar sobre LangGraph propio.

**Regla de arquitectura aplicada:** el texto de razonamiento del agente se registra para el operador
y **nunca viaja al actuador**. Aquí el actuador es una orden de trabajo y una consigna de turbina.

### Receta 34 — Plug & Charge sin licenciar pila propietaria y sin tocar GPL (EMEA primero)

**Problema que resuelve.** Un operador de carga quiere ofrecer **Plug & Charge** (ISO 15118) y le
cotizan una pila propietaria; o la alternativa abierta que encuentra es GPL y su producto es
propietario.

**La combinación permisiva, verificada licencia por licencia:**

| Capa | Pieza | Licencia | ★ |
|------|-------|----------|---|
| Poste / "SO" de la estación | [`ecog-io/josev`](https://github.com/ecog-io/josev) | **Apache-2.0** | 164 |
| Protocolo vehículo↔cargador | [`ecog-io/iso15118`](https://github.com/ecog-io/iso15118) (-2, -20, -8) | **Apache-2.0** | 250 |
| Stack de carga / back-office | `EVerest/EVerest` *(ya catalogado)* | **Apache-2.0** | 297 |
| Simulación sin hardware | `SAP/e-mobility-charging-stations-simulator` *(ya catalogado)* | **Apache-2.0** | 231 |
| Optimización doméstica | `evcc-io/evcc` *(ya catalogado)* | **MIT** | 7.640 |

```
[vehículo] ──ISO 15118 (-2/-20/-8)──> [ecog-io/iso15118]
                                            │
                                      [ecog-io/josev]  (SO de la estación)
                                            │ OCPP
                                      [EVerest]  (back-office permisivo)
                                            │
                     [tarifa / flexibilidad: evcc (MIT) | FlexMeasures (Apache-2.0)]
```

**Toda la cadena es Apache-2.0 o MIT: no hay límite de proceso obligatorio**, lo que la hace apta
para un entregable propietario de marca blanca. Es la diferencia con `steve` (GPL-3.0), que sigue
siendo válido pero exige aislamiento.

**Decisiones y advertencias que cambian el presupuesto:**

- **No comprometer `matth-x/MicroOcpp` en firmware** sin auditar antes sus **135 issues abiertas** y
  sus **~12 meses sin push**, aunque sea MIT y la referencia de la categoría en microcontroladores.
- `SwitchEV/RISE-V2G` (MIT, 261 ★) es **referencia de lectura**: 11 meses sin push.
- Validar con el simulador **antes** de comprar postes; es la lección de la *Receta 26*, aquí con la
  capa de protocolo añadida.
- Para flexibilidad del lado del hogar en EMEA, el puente al equipo es `enbility/eebus-go` (MIT) o
  `NIBEGroup/openeebus` (Apache-2.0) — y si el cliente exige el estándar **S2**, decirle que el
  tooling existe (`flexmeasures-s2`, Apache-2.0) y tiene **2 estrellas**.

### Receta 35 — Respuesta a la demanda en North America con OpenADR 3.0 *(premisa corregida en el pase 13)*

> ⚠️ **Esta receta se escribió sobre un hecho falso y queda rectificada.** La versión anterior
> decía que `openleadr-rs` no tenía archivo de licencia y que por tanto **"OpenADR 3.0 no tiene
> implementación abierta licenciada"**. Es incorrecto: el pase 13 verificó que `Cargo.toml` declara
> `license = "Apache-2.0 OR MIT"` y que `LICENSE-MIT` y `LICENSE-APACHE` devuelven **200** en `main`
> y en `master`. **No hay que elegir 2.0b, ni negociar licencia, ni implementar 3.0 desde cero.**

**Problema que resuelve.** El cliente pide un agregador de respuesta a la demanda que hable
**OpenADR**, el protocolo de referencia de North America, en su versión **3.0**.

**El hecho, verificado en el pase 13 contra tres canales independientes:**

| Pieza | Versión | Licencia | Estado |
|-------|---------|----------|--------|
| [`OpenLEADR/openleadr-rs`](https://github.com/OpenLEADR/openleadr-rs) | **3.0** (VTN + VEN, Rust) | **Apache-2.0 OR MIT** (doble) | ✅ **Usable** (107 ★, 30 forks, push 2026-11-20) |
| [`ElaadNL/openadr3-client`](https://github.com/ElaadNL/openadr3-client) | **3.0** (cliente BL + VEN, Python) | **Apache-2.0** | ✅ Usable (6 ★, push 2026-11-19) |
| [`eclipse-volttron/volttron-openadr-ven`](https://github.com/eclipse-volttron/volttron-openadr-ven) | VEN sobre VOLTTRON | **Apache-2.0** | ✅ Usable (6 ★, push 2026-07-21) |
| [`OpenLEADR/openleadr-python`](https://github.com/OpenLEADR/openleadr-python) | **2.0b** | **Apache-2.0** | Usable, pero versión anterior (161 ★, 67 forks) |

**La vía recomendada, que ya no es un compromiso:**

1. **Entregar sobre 3.0 con `openleadr-rs` como VTN/VEN de referencia** (doble Apache-2.0/MIT). Es
   la misma organización —Stichting ElaadNL— que publica el cliente Python `openadr3-client`, de
   modo que hay **dos piezas del mismo origen** que hablan la misma versión del protocolo.
2. **Si el equipo del encargo es Python y no Rust**, montar el lado cliente con
   `ElaadNL/openadr3-client` (Apache-2.0) y dejar `openleadr-rs` como VTN de pruebas.
3. **`openleadr-python` (2.0b) sólo si el cliente ya tiene una flota 2.0b desplegada.** Es
   compatibilidad hacia atrás, no la opción por defecto.

**Lo que hay que decirle al cliente, y conviene decirlo:** la capa 3.0 existe, es permisiva y está
viva (push del mismo día del pase), pero tiene **107 ★ y 30 forks**: es infraestructura joven. El
riesgo real no es de licencia —ése era el dato equivocado— sino de **madurez y de tamaño de
comunidad**, y se gestiona con pruebas de conformidad propias, no con una cláusula legal.

**El resto de la receta, con lo ya catalogado:**

```
[señal de programa / precio]
   ├─ OpenADR 2.0b: openleadr-python (Apache-2.0)
   ├─ tarifa CA: MIDAS (CEC) ⚠️ SIN LICENCIA -> consultar, no redistribuir
   └─ carbono: grid-intensity-go (Apache-2.0) | CarbonCast (Apache-2.0)
                           │
                           v
            [FlexMeasures (Apache-2.0)]  <- programación y forecast de flexibilidad
                           │
         ┌─────────────────┼──────────────────┐
         v                 v                  v
 [CityLearn MIT]    [vinerya/virtual-     [evcc MIT / eebus-go MIT]
 (simular distrito)  power-plant MIT]      (activos reales)
                           │
                           v
            ╔═══════════════════════════════════╗
            ║  consigna propuesta -> validación  ║
            ║  del sistema de control del cliente║
            ╚═══════════════════════════════════╝
```

**Advertencias de cumplimiento que pertenecen a esta receta en North America:**

- El programa cae bajo el plazo de **estándares de carga computacional de NERC de diciembre de
  2026** si el recurso es carga de datacenter → encadenar con la *Receta 29*, y recordar que la
  oferta abierta de cumplimiento NERC CIP medida en este pase es **cero**.
- Hay **vacío regulatorio declarado**: a agosto de 2026 ninguna comisión estatal había tratado la IA
  operativa de una utility, y sólo **Arizona** abrió examen formal. Eso **no** significa libertad:
  significa que el expediente de gobernanza lo escribe el proveedor, y conviene que lo escriba
  Globant.
- `MIDAS` es dato **oficial** de la California Energy Commission y **no tiene licencia**: consultarlo
  sí, redistribuirlo no.

---
*Verificado 2026-11-20 en nueve pases (35 recetas). Re-verificar licencias y stars antes de
comprometer alcance.*

## Recetas del décimo pase (2026-11-20)

> Las seis se apoyan en la capa institucional norteamericana (EPRI, Grid Protection Alliance,
> Sandia) y en la familia `oemof`, catalogadas en este pase. Todas las licencias verificadas en el
> `LICENSE`/`LICENSE.txt` crudo, no en la etiqueta de la API.

### Receta 36 — Plataforma de analítica operativa **sin migrar el histórico del cliente**

**Para quién:** utility con PI System (AVEVA/OSIsoft) instalado que quiere IA sobre sus datos
operativos y **no** va a cambiar de histórico. Es el escenario más común y el que mataba propuestas.

**Por qué funciona:** el punto de entrada no es el historiador, es el **puente**.

| Pieza | Repo | Licencia | Papel |
|-------|------|----------|-------|
| Puente al histórico propietario | [osisoftpi-grafana](https://github.com/GridProtectionAlliance/osisoftpi-grafana) | **Apache-2.0** | Lee el PI que ya existe, sin migración |
| Histórico abierto (sólo lo nuevo) | [openHistorian](https://github.com/GridProtectionAlliance/openHistorian) | **MIT** | Series nuevas y de alta frecuencia, sin tocar el PI |
| Analítica de perturbaciones | [openXDA](https://github.com/GridProtectionAlliance/openXDA) | **MIT** | Eventos, faltas, perturbaciones |
| Calidad de onda | [PQDashboard](https://github.com/GridProtectionAlliance/PQDashboard) | **BSD-3** | Vista de sistema |
| Analítica en el lazo | [openECA](https://github.com/GridProtectionAlliance/openECA) | **MIT** | Punto de inserción de modelos |
| Capa de pregunta | `PowerMCP` + LLM | **MIT** | Consulta en lenguaje natural sobre lo anterior |

**Cableado:** Grafana con el plugin PI como capa de lectura unificada → `openHistorian` recibe las
series nuevas (fasorial, alta cadencia) → `openXDA` procesa eventos y escribe resultados al
histórico → `openECA` expone el punto donde entra el modelo → `PowerMCP` sobre las dos fuentes para
la capa conversacional. **La persona autoriza; el agente no actúa sobre el lazo** (regla de
arquitectura).

**Qué presupuestar y qué no:** el puente y los dashboards son configuración. **La calibración de
`openXDA` contra los eventos reales del cliente es el trabajo**, y hay que estimarla por número de
tipos de evento, no por número de subestaciones. ⚠️ Stack **.NET/Windows** en origen: validar el
plan de despliegue antes de prometer contenedores Linux. ⚠️ `openECA` tiene **20 issues abiertas**,
`PQDashboard` **21**.

### Receta 37 — Valoración y dimensionado de BESS con base institucional

**Sustituye el veredicto de la Receta 13.** El pase 9 midió la oferta en **un** repo y concluyó
"ingeniería de modelo desde cero". Con la búsqueda por institución son cinco herramientas
permisivas, y la receta cambia de forma.

| Pieza | Repo | Licencia | Papel |
|-------|------|----------|-------|
| Valoración de almacenamiento | [epri-dev/StorageVET-deprecated](https://github.com/epri-dev/StorageVET-deprecated) | **BSD-3** | Modelo de valoración de EPRI (StorageVET 2.0) |
| Valoración de DER | [epri-dev/DER-VET](https://github.com/epri-dev/DER-VET) | **BSD-3** | Cartera DER, no sólo batería |
| Plataforma de análisis | [sandialabs/snl-quest](https://github.com/sandialabs/snl-quest) | **BSD-3** *(rescatada)* | QuESt: aplicación modular de Sandia |
| Fiabilidad con almacenamiento | [sandialabs/snl-progress](https://github.com/sandialabs/snl-progress) | **BSD-3** *(rescatada)* | ProGRESS: aporte del BESS a fiabilidad |
| Degradación / ciclado | [oemof/cydets](https://github.com/oemof/cydets) | **MIT** | Detección de ciclos en la serie real |
| Precio de entrada | `gridstatus` (NA) · `entsoe-py` (EMEA) · `API_XM` (CO) | BSD-3 / MIT | Serie de precio por región |
| Arbitraje de referencia | `BigdogManLuo/DBESS-Arbitrage` | Apache-2.0 | Único optimizador sectorial permisivo con tracción |

**Cableado:** `gridstatus`/`entsoe-py` alimenta la serie de precio → `StorageVET` o `DER-VET`
calcula el valor por flujo de ingreso → `snl-quest` como entorno de escenarios → `snl-progress` si
el cliente necesita el argumento de **fiabilidad** (regulador o ISO) → `cydets` sobre la serie real
de operación para contrastar la degradación supuesta con la medida.

**Advertencias que van en la propuesta, no en una nota al pie:** ⚠️ `StorageVET-deprecated` **se
llama *deprecated*** y tiene push de hace cuatro semanas — hay que resolver con EPRI qué lo
reemplaza antes de comprometerlo. ⚠️ `snl-quest` tiene **44 issues abiertas**. ⚠️ `DER-VET-GUI`
(la interfaz) está **sin licencia**: usar la librería, no la GUI.

### Receta 38 — Cadena meter-to-cash: la frontera nueva, con el presupuesto redibujado

**Qué cambia respecto del octavo pase:** el protocolo de medidor y la recolección **ya no son
desarrollo propio**. El MDM y la tarifa siguen siéndolo.

| Capa | Repo | Licencia | Estado |
|------|------|----------|--------|
| Protocolo de medidor (EMEA) | [epri-dev/DLMS-COSEM](https://github.com/epri-dev/DLMS-COSEM) + [dlms-access-point](https://github.com/epri-dev/dlms-access-point) | **BSD-3** | ✅ permisivo |
| Traducción a modelo de red | [epri-dev/dlms-cim](https://github.com/epri-dev/dlms-cim) | **BSD-3** | ✅ DLMS → CIM |
| Recolección | [openMIC](https://github.com/GridProtectionAlliance/openMIC) | **MIT** | ✅ vivo (push 2026-11-15) |
| Almacenamiento de la serie | [openHistorian](https://github.com/GridProtectionAlliance/openHistorian) | **MIT** | ✅ |
| Motor de facturación | `killbill` | Apache-2.0 | ✅ genérico: **no conoce una tarifa eléctrica** |
| Medición de consumo | `openmeter` | Apache-2.0 | ✅ genérico |
| **MDM** | — | — | ❌ **ausente** (medido: lo mejor tiene 7 ★ y dos años sin push) |
| **Lógica tarifaria regulada** | — | — | ❌ **desarrollo propio, siempre** |

**Cableado:** medidor → `DLMS-COSEM`/`dlms-access-point` (o ANSI C12 en NA, con la advertencia de
licencia de `c12test`) → `openMIC` recolecta → `dlms-cim` normaliza a CIM → `openHistorian` guarda
la serie → **capa de MDM y tarifa a construir** → `killbill` emite.

**Cómo presupuestarlo con honestidad:** dos de las siete capas son desarrollo completo y están
nombradas arriba. La diferencia con el presupuesto del octavo pase es que **ya no hay que escribir
el protocolo ni la recolección**, que eran las dos capas que más se subestiman. ⚠️ `DLMS-COSEM` no
tiene push desde 2024-11 y `dlms-cim` desde 2021-01: son **referencias de protocolo** (los
protocolos no cambian), no software mantenido; auditar antes de empotrar.

### Receta 39 — Estudio completo de red de calor de distrito, todo MIT

**Para quién:** municipio, utility de calor o promotor en Escandinavia, Alemania, Polonia o los
bálticos. Vertical ausente de esta KB durante nueve pases.

| Pieza | Repo | Licencia | Papel |
|-------|------|----------|-------|
| Demanda de calor | [oemof/oemof-demand](https://github.com/oemof/oemof-demand) | **MIT** | Perfiles horarios desde valores anuales |
| Topología de la red | [jylambert/topotherm](https://github.com/jylambert/topotherm) | **MIT** | Qué trazado, qué diámetros (TU München) |
| Hidráulica y térmica de la red | [oemof/DHNx](https://github.com/oemof/DHNx) | **MIT** | Optimización y simulación de la red |
| Generación (bomba de calor, CHP) | [oemof/tespy](https://github.com/oemof/tespy) | **MIT** | Ciclo termodinámico del lado de producción |
| Exergía | [oemof/exerpy](https://github.com/oemof/exerpy) | **MIT** | Dónde se pierde calidad de energía, no sólo cantidad |
| Despacho del sistema | `oemof-solph` | **MIT** *(SPDX en `pyproject.toml`)* | Optimización del conjunto |
| Telemetría de bomba de calor | [raomin/ESPAltherma](https://github.com/raomin/ESPAltherma) | **MIT** | Lectura de equipo Daikin instalado |

**Cableado:** `oemof-demand` genera el perfil → `topotherm` decide trazado → `DHNx` dimensiona y
simula → `tespy` modela la central → `exerpy` audita la calidad → `oemof-solph` despacha el conjunto.

**El límite, declarado:** esto es un **estudio de diseño y dimensionado**, completo y permisivo. **No
es operación**: no existe SCADA de calor, ni facturación de calor, ni gestión de subestación térmica
en open source. Vender diseño; no vender operación. ⚠️ `DHNx` tiene 35 issues abiertas.

### Receta 40 — Expediente para el **acuerdo tripartito** europeo de conexión de datacenter

**Para quién:** operador de datacenter que necesita conexión a red en la UE, o la parte energética
del otro lado de la mesa. Instrumento previsto para el segundo semestre de 2026 (ver **T50**;
fuente secundaria, ver **T49**).

El contrato tiene tres firmantes, así que el entregable son **tres expedientes que tienen que
cuadrar entre sí** — y eso es lo que lo hace un proyecto y no un informe.

| Expediente | Qué tiene que demostrar | Con qué se construye | Licencia |
|-----------|------------------------|---------------------|----------|
| **Del datacenter** | Perfil de carga y **flexibilidad comprometida** | `dos-group/vessim` + `FlexMeasures` + `OpenLEADR` | MIT / Apache-2.0 / Apache-2.0 |
| **Del datacenter** | Plan de eficiencia y huella | `carbon-aware-sdk` + `scaphandre` + `ecologits` | MIT / Apache-2.0 / MPL-2.0 |
| **De la parte energética** | Estudio de conexión e impacto en red | `pandapower` + `PyPSA` + `power-grid-model` | BSD-3 / MIT / MPL-2.0 |
| **De la parte energética** | Escenarios de planificación | `plexos2duckdb` si el cliente ya usa PLEXOS | **BSD-3** |
| **De la autoridad** | Trazabilidad y auditoría continua | `openHistorian` + `openXDA` como registro; `opendsm` para M&V | MIT / MIT / Apache-2.0 |

**Cableado:** `vessim` produce el perfil de carga flexible → `FlexMeasures` lo convierte en
compromiso despachable y `OpenLEADR` en señal ejecutable → `pandapower`/`PyPSA` evalúan el impacto
del perfil comprometido → `openHistorian` registra lo que realmente pasó y `opendsm` verifica que la
flexibilidad entregada es la firmada.

**Por qué se vende mejor que un proyecto de cumplimiento:** el cumplimiento es gasto a minimizar; la
conexión es la **condición de existencia** del datacenter. Y la flexibilidad firmada hay que
**medirla y verificarla de forma continua**, lo que convierte el expediente en plataforma con
mantenimiento recurrente (la misma conversión que T18 identificó para el ahorro energético).

### Receta 41 — Conformidad de interconexión de DER (IEEE 1547 / IEEE 2030.5)

**Para quién:** DSO, agregador o fabricante de inversor que tiene que demostrar comportamiento
normativo del DER en Norteamérica (y, con el mismo estándar base, en Australia vía CSIP-AUS).

| Pieza | Repo | Licencia | Papel |
|-------|------|----------|-------|
| Comportamiento normativo del inversor | [epri-dev/OpenDER](https://github.com/epri-dev/OpenDER) | **BSD-3** *(rescatada)* | Modelo conforme a **IEEE 1547-2018** |
| Comunicación con el DER | [epri-dev/IEEE-2030.5-Client](https://github.com/epri-dev/IEEE-2030.5-Client) | **BSD-3** | Cliente **IEEE 2030.5** |
| Variante australiana | `longzheng/open-dynamic-export` + `ethanndickson/sep2_client` | MIT / Apache-2.0 | **CSIP-AUS** sobre el mismo estándar base |
| Red de distribución | `OpenDSS` / `pandapower` | BSD-3 | Dónde se conecta el DER |
| Señal de demanda | [epri-dev/OpenADR-Virtual-End-Node](https://github.com/epri-dev/OpenADR-Virtual-End-Node) + `openleadr-python` | BSD-3 / Apache-2.0 | VEN y VTN de OpenADR |

**Cableado:** `OpenDER` da el comportamiento esperado del inversor bajo norma → `IEEE-2030.5-Client`
(o `open-dynamic-export` en Australia) es el canal de control → `OpenDSS`/`pandapower` modela el
alimentador → el par VEN/VTN de OpenADR cierra el lazo de señal de demanda.

**El hueco que hay que decir en voz alta en esta receta:** falta la pieza de **capacidad de
alojamiento** (*hosting capacity*), que es la pregunta que el DSO hace primero: *¿cuánto DER aguanta
este alimentador?* La oferta abierta medida es `PauloRadatz/HostingCapacity_OpenDSS` (**MIT, 7 ★,
sin push desde 2022-11**). Es decir: el análisis de capacidad de alojamiento **es desarrollo propio
sobre `OpenDSS`**, y hay que presupuestarlo como tal. ⚠️ `IEEE-2030.5-Client` no tiene push desde
2023-02 y `OpenADR-Virtual-End-Node` desde 2023-04: referencias de protocolo, auditar antes de
empotrar.

## Actualización del décimo pase a "qué no proponer" (2026-11-20)

**Entradas que se caen de la lista:**

| Lo que decía un pase anterior | Estado al décimo pase |
|-------------------------------|------------------------|
| "**Optimización de BESS**: la oferta abierta es **un** repo; presupuestar como ingeniería de modelo desde cero" | ✅ **Corregido.** Cinco herramientas permisivas de valoración y dimensionado: `StorageVET` y `DER-VET` (EPRI, BSD-3), `snl-quest`, `snl-progress`, `snl-pstess` (Sandia, BSD-3/MIT) → **Receta 37**. La medición del pase 9 era correcta; la conclusión, falsa por vocabulario (T47) |
| "Hablar **DLMS/COSEM** obliga a licencia comercial (`u9n/dlms-cosem` es BSL)" | ✅ **Falso.** `epri-dev/DLMS-COSEM` y `dlms-access-point` son **BSD-3**, y `dlms-cim` traduce a CIM → **Receta 38** |
| (implícito) "No hay histórico de series temporales abierto para la red" | ✅ **Cerrado.** `openHistorian` **MIT, 207 ★, push 2026-11-15**, con puente Apache-2.0 al PI System instalado → **Receta 36** |
| (implícito) "El calor de distrito no está cubierto" | ✅ **Cerrado para estudio** (`DHNx`, `topotherm`, `tespy`, `oemof-demand`, todos MIT) → **Receta 39**. **Sigue vacío para operación** |

**Nuevos "no proponer", medidos en este pase:**

- **Nada del lado del activo de campo como acelerador reutilizable.** Medido con ocho consultas
  (ver T48): **riesgo de incendio / PSPS = cero repos del sector** en tres ángulos distintos de
  consulta; **salud de transformador (DGA)** = `xDGA` MIT **18 ★ de 2022**; **capacidad de
  alojamiento** = `HostingCapacity_OpenDSS` MIT **7 ★ de 2022**; **inspección de línea por visión** =
  YOLO académicos MIT de 34-37 ★, el de 145 ★ **sin licencia**. Son categorías con presupuesto
  aprobado y **sin base open source mantenida**: presupuestar como **desarrollo a medida** sobre
  `OpenDSS`/`pandapower` y visión estándar. **No prometer acelerador ni estimar como integración.**
- **Detección de fuga de metano en un entregable propietario.** La oferta existe y **no es
  permisiva**: `spaceml-org/STARCOP` es **GPL-3.0** (74 ★) y `MethaneMapper` (85 ★) **no tiene
  licencia**. Gap de permiso, no de oferta — el caso `GEM` otra vez.
- **Control de inversor grid-forming sobre base abierta.** `GridFormingConverters` (140 ★) y los
  modelos WECC de `pnnl` (45 ★) **no tienen licencia**, y son MATLAB/PSCAD. Es la categoría central
  de los recursos basados en inversor en 2026 y su oferta abierta está **bloqueada por permiso**.
- **`sandialabs/OpenCSP` en cualquier alcance.** Única base abierta de solar de concentración que ha
  encontrado esta KB (13 ★, **20 forks**, 91 issues) y **no tiene archivo de licencia en `main`**.
- **`oemof/feedinlib` y `oemof/marketlib`.** Ambos MIT y utilizables en teoría; ambos
  **ARCHIVADOS** (`feedinlib` con 117 ★ y 43 forks). Para generación PV la pieza viva es
  `pvlib-python`. Tercera vez que esta KB tropieza con un archivado que ninguna consulta señala.
- **`EDX`/`OPDM` de ENTSO-E como dependencia de producción sin plan propio.** Son **MIT** y son la
  pieza que hace operable el CGMES europeo, y están mantenidos por **una sola cuenta individual**
  con 2-10 ★ por repo. Proponer como acelerador internalizado con mantenimiento presupuestado.
- **Cualquier compromiso con fecha sobre la hoja de ruta europea o la declaración de APEC.**
  `eur-lex.europa.eu`, `energy.ec.europa.eu` y `apec.org` **no resuelven** desde este entorno
  (T49). `COM(2026) 501`, el acuerdo tripartito del segundo semestre de 2026 y el grupo de trabajo
  de APEC tienen concordancia de fuentes secundarias y **cero** confirmación primaria. Sirven para
  planear; **no para firmar**.
- **Una propuesta argentina que prometa base local.** **Sexta medición consecutiva en cero.** La
  base para Argentina es regional (`PyPSA-CL`, `pypsa-meets-brazil`) o norteamericana permisiva, y
  conviene decirlo antes de que lo pregunten.

## Recetas del undécimo pase (2026-11-20)

### Receta 42 — Dynamic line rating: la norma ya está implementada, lo facturable es el resto

**A quién:** TSO/utility de transmisión en Norteamérica o EMEA que quiera liberar capacidad de línea
sin construir. **Por qué ahora:** FERC nombró *dynamic line ratings* entre sus prioridades críticas
operativas de enero de 2026.

**Piezas:**

1. [`statnett/linerate`](https://github.com/statnett/linerate) (**MIT**, push 2026-11-20) — el núcleo
   de cálculo: una función pura por cada ecuación de **CIGRE TB 601**, más CIGRE TB 207 e **IEEE 738**;
   tipos para conductor/vano/meteorología y solver de bisección vectorizado.
2. [`pvlib/pvlib-python`](https://github.com/pvlib/pvlib-python) (**BSD-3**, ya en la KB) — modelos de
   irradiancia y posición solar para el término de calentamiento solar del balance térmico.
3. Fuente meteorológica: la capa de recurso ya catalogada en `repos/foundations.md` (sección "Recurso
   meteorológico"), más la telemetría de estaciones del cliente.
4. [`GridProtectionAlliance/openHistorian`](https://github.com/GridProtectionAlliance/openHistorian)
   (**MIT**, ya en la KB desde el pase 10) — serie temporal de ampacidad calculada, junto a la medida.
5. [`GMLC-TDC/HELICS`](https://github.com/GMLC-TDC/HELICS) (**BSD-3**, nuevo en este pase) — para
   validar el efecto del *rating* dinámico en el despacho, acoplando el modelo de red con el térmico.

**Cómo se cablea:** la meteorología (medida + pronóstico) y la geometría del conductor entran como
`Weather` y `Conductor` de `linerate` → `model.Cigre601` resuelve temperatura de conductor y ampacidad
por vano → la serie resultante se persiste en `openHistorian` junto a la medida real → el caso de
despacho se valida en `HELICS` acoplando el modelo de red (`pandapower`/`powsybl`) con la serie de
ampacidad → el EMS consume el límite dinámico por línea.

**Qué es el entregable, y qué no.** No es el cálculo: eso está hecho y es citable al estándar, página
a página (el README reproduce el *Example B*, pp. 79-81 de CIGRE TB 601). El entregable es
**(a)** la ingesta y control de calidad de la telemetría meteorológica por vano, **(b)** la
integración con el EMS/SCADA, **(c)** la validación frente a *rating* estático y el expediente que la
acompaña, y **(d)** el régimen de fallback cuando falta el dato. Que las ecuaciones no se escriban es
**argumento de precio y de riesgo**, no una rebaja del alcance.

⚠️ 8 ★ y 7 issues abiertas: hay que leerlas antes de comprometer. El valor está en la trazabilidad al
estándar, no en la comunidad.

### Receta 43 — Consulta en lenguaje natural sobre el modelo CIM, con el plano firmado por un TSO

**A quién:** TSO/DSO europeo con modelo **CGMES/CIM** cuyos ingenieros no escriben SPARQL. **Por qué
es defendible:** el patrón entero está publicado por **Statnett** bajo Apache-2.0; se cita un operador
par, no un vendor.

**Piezas:**

1. [`statnett/cimsparql`](https://github.com/statnett/cimsparql) (**MIT**, push 2026-11-16) — **la
   dependencia**: consulta modelos CIM por SPARQL desde Python.
2. [`statnett/Talk2PowerSystem`](https://github.com/statnett/Talk2PowerSystem) (**Apache-2.0**) — **el
   plano**, no la dependencia. De él se copia: la **N-Shot Tool** (recupera las N preguntas más
   similares del *dataset* de Q&A y las pasa al modelo **con sus plantillas SPARQL**),
   `connector.rq` (conector de recuperación vectorial) y `ontology.trig` (ontología del *dataset* de
   Q&A para **GraphDB**).
3. `pycgmes` + `application-profiles-library` + `CIM-Graph` (ya en la KB, receta de CGMES del pase 10)
   — validación SHACL del modelo antes de cargarlo. **Un modelo que no valida no se consulta.**
4. GraphDB u otro *triple store* — el repo de Statnett trae la configuración (`qa_dataset-config.ttl`).

**Cómo se cablea:** el CGMES del cliente entra por `pycgmes` → se valida con SHACL contra los perfiles
→ se carga en el *triple store* → se construye el *dataset* de Q&A del cliente (pregunta en lenguaje
natural ↔ plantilla SPARQL verificada) con el esquema de `ontology.trig` → en consulta, la N-Shot Tool
recupera los k ejemplos más próximos y los inyecta como *few-shot* → el LLM emite SPARQL →
`cimsparql` la ejecuta → la respuesta se devuelve **con la consulta ejecutada y el subgrafo citado**.

**La propiedad que lo hace vendible en un sector regulado:** no es "un chatbot sobre la red". Es que
la respuesta **es trazable**: lleva adjunta la consulta SPARQL y los nodos CIM de los que sale. El
ingeniero verifica sin confiar.

**Dónde está el trabajo:** el *dataset* de Q&A con plantillas verificadas del cliente — ése es el
activo, y es el 70 % del esfuerzo. El *dataset* de Statnett **no es visible** en el directorio
auditado; asúmase que se construye desde cero.

⚠️ `Talk2PowerSystem` tiene push de mayo de 2026 y su `Roadmap.adoc` dice *"To be addressed"*. **Se
copia la arquitectura; no se depende del repo.**

### Receta 44 — El expediente de impacto de red que Singapur, Malasia y Corea ya exigen

**A quién:** promotor de centro de datos o su asesor en APAC. **Por qué ahora:** esas tres
jurisdicciones exigen **plan de almacenamiento en baterías y de gestión de *curtailment* junto con la
evaluación de impacto de red**. Es un entregable repetible por jurisdicción.

**Piezas:**

1. [`GMLC-TDC/HELICS`](https://github.com/GMLC-TDC/HELICS) (**BSD-3**) — el bus: acopla el simulador
   de transmisión con el de distribución y el del activo en un mismo experimento.
2. `pandapower` (**BSD-3**) o `powsybl` (Apache-2.0) — el estudio de red en régimen permanente.
3. `gridlab-d` (ya en la KB) — el lado de distribución, si el punto de conexión lo requiere.
4. [`sandialabs/snl-quest`](https://github.com/sandialabs/snl-quest) (**BSD-3**) y
   [`epri-dev/DER-VET`](https://github.com/epri-dev/DER-VET) (**BSD-3**) — dimensionado y **valoración**
   del BESS: el plan de almacenamiento que pide el regulador.
5. `epri-dev/OpenDER` (**BSD-3**) — comportamiento normativo del inversor (IEEE 1547-2018) si hay
   generación/almacenamiento propio en el punto de conexión.

**Cómo se cablea:** el perfil de carga del centro de datos (incluida su flexibilidad declarada) y el
modelo de red del punto de conexión se acoplan en `HELICS` → `pandapower`/`powsybl` resuelve los casos
de contingencia y los límites térmicos y de tensión → los escenarios donde se incumple el límite
definen el requisito de flexibilidad → `snl-quest`/`DER-VET` dimensionan y valoran el BESS que lo
cubre → `OpenDER` verifica que el inversor cumple la norma de conexión → el conjunto se redacta como
**evaluación de impacto + plan de BESS + plan de curtailment**.

**Por qué es buen negocio:** el mismo pipeline se reinstancia por jurisdicción cambiando norma de
conexión y mercado. Y en EMEA se reutiliza tal cual contra los **códigos de conexión actualizados**
que ENTSO-E pide legislar.

### Receta 45 — Control y layout de parque eólico: cuatro piezas MIT y una trampa de licencia

**A quién:** promotor u operador de parque eólico. **Lo que aporta de nuevo:** la KB sólo tenía este
frente por `floris` (NatLabRockies); el clúster de **DTU** cubre layout, red de colección y control.

**Piezas:**

1. [`DTUWindEnergy/WindGym`](https://github.com/DTUWindEnergy/WindGym) (**MIT**, push 2026-11-19) —
   entorno de **RL para control de parque**: la pieza viva del clúster.
2. [`DTUWindEnergy/TopFarm2`](https://github.com/DTUWindEnergy/TopFarm2) (**MIT**) — optimización de
   **layout**.
3. [`DTUWindEnergy/OptiWindNet`](https://github.com/DTUWindEnergy/OptiWindNet) (**MIT**) — optimización
   de la **red de colección** interna.
4. [`NatLabRockies/floris`](https://github.com/NatLabRockies/floris) (**BSD-3**, ya en la KB) — el
   modelo de estela **proponible**.
5. `NatLabRockies/OpenOA` (**BSD-3**, ya en la KB) — evaluación operacional contra producción real.

**Cómo se cablea:** `TopFarm2` optimiza posiciones con el modelo de estela → `OptiWindNet` traza la red
de colección sobre ese layout → `floris` evalúa estela y pérdidas del diseño → `WindGym` entrena la
política de control de planta (*wake steering*, *derating*) sobre el entorno → `OpenOA` cierra el
lazo midiendo el resultado contra SCADA real.

⚠️ **La trampa, y es la pieza que uno querría usar:**
[`PyWake`](https://github.com/DTUWindEnergy/PyWake) (85 ★, el modelo de estela más citado del clúster)
**no tiene archivo de licencia en `main`, `master` ni `develop`**. Para el modelo de estela, usar
`floris` (BSD-3). Y antes de descartar `PyWake` definitivamente, **mirar el GitLab de origen**
(`gitlab.windenergy.dtu.dk`): estos repos son espejos y el espejo pierde la licencia (ver T53).

### Receta 30 — Copiloto de estudios N-1 sobre el MCP del propio TSO (EMEA, Francia primero)

**Por qué ahora:** hasta este pase, todo copiloto de red de esta KB se apoyaba en motores envueltos
por terceros. `powsybl/pypowsybl-mcp` lo publica **el operador de la red** (RTE), lo que cambia el
argumento de venta: no se propone una integración inventada, se propone **adoptar la integración que
el TSO ya usa internamente** (arXiv 2607.14158).

**Piezas, todas verificadas en el duodécimo pase:**

| Rol | Pieza | Licencia |
|---|---|---|
| Capa de herramientas de red para el agente | [`powsybl/pypowsybl-mcp`](https://github.com/powsybl/pypowsybl-mcp) | **MPL-2.0** (RTE) |
| Motor de red y modelo | [`powsybl/powsybl-core`](https://github.com/powsybl/powsybl-core) + `pypowsybl` | MPL-2.0 |
| Diagramas unifilares para el expediente | [`powsybl/powsybl-diagram`](https://github.com/powsybl/powsybl-diagram) | MPL-2.0 |
| Entrada del modelo en formato de red europeo | Capa CGMES del séptimo pase (`sogno-platform/cimgen`, `haigutus/triplets`, `soptim/opencgmes`) | MPL-2.0 / permisivas |
| Sala de control / human-in-the-loop | [`opfab/operatorfabric-core`](https://github.com/opfab/operatorfabric-core) (LF Energy / RTE) | **MPL-2.0** |

**Cómo se conecta, y los tres detalles que deciden si funciona:**

1. **El servidor MCP es un servicio, no un subproceso.** El transporte es **streamable HTTP, no
   stdio**: el servidor PyPowsybl **debe estar ya corriendo** antes de que el cliente se conecte. Hay
   que desplegarlo con ciclo de vida propio (contenedor, *health check*, reinicio), no lanzarlo desde
   el cliente.
2. **Las sesiones viven en memoria y se pierden al reiniciar.** El diseño es correcto para privacidad
   —el modelo de red se queda en el servidor y al agente sólo van identificadores de sesión y
   resúmenes filtrados, no el volcado de la red al LLM— pero **obliga a poner persistencia propia
   encima** para cualquier estudio que dure más que el proceso. Esto es trabajo de proyecto, y hay
   que presupuestarlo.
3. **El agente encadena, no decide.** Flujo: cargar modelo CGMES → `load flow` → `security analysis`
   N-1 sobre la lista de contingencias → `sensitivity analysis` sobre las violaciones → generar
   diagrama → redactar el expediente. La aprobación del resultado es humana, en OperatorFabric. Esto
   es **T28** ("la IA asiste, no decide"), que es además el único encuadre que pasa un comité de
   operación.

**Frontera de licencia:** toda la receta es **MPL-2.0** (powsybl, CGMES y OperatorFabric), es decir, un solo régimen de licencia de principio a fin — coincide con la nota del tercer pase de que MPL-2.0 es la licencia por defecto del sector eléctrico europeo. MPL-2.0 es copyleft **por archivo**. Se puede enlazar desde código
propietario sin contaminarlo; lo que se publica son los ficheros **de powsybl** que se modifiquen. En
la práctica: no tocar los fuentes del servidor, construir las herramientas propias como ficheros
nuevos del proyecto.

**Lo que hay que decir en la propuesta y no omitir:** `pypowsybl-mcp` tiene **7 ★ y 2 forks**, y PRs
abiertos de migración al SDK Python de MCP v2. Es un cimiento **institucional pero joven**: la oferta
honesta incluye contribuir aguas arriba, y el riesgo de versión es real.

**Entregable:** servicio MCP desplegado + conjunto de herramientas propias del cliente + expediente
N-1 reproducible con diagramas + integración en sala de control. **Primer hito verificable:** un
estudio N-1 que un ingeniero firme sin rehacerlo a mano.

---

### Receta 31 — Plataforma de analítica del NEM australiano con la frontera de licencia en el diagrama (APAC, Australia)

**Por qué esta receta es distinta de las demás:** no la organiza la función, la organiza **la
licencia**. El stack australiano que apareció en el duodécimo pase es **GPL-3.0 en la capa de datos y
permisivo en la capa de modelo** (T32), y como no hay producto del NEM que esquive `NEMOSIS`, la
frontera de copyleft **es** la arquitectura. Dibujarla al final es rehacer el proyecto.

**Arquitectura en dos lados de una frontera explícita:**

**Lado GPL — servicio de datos aislado** (contenedor propio, sin enlazado con lo propietario, sólo
interfaz de datos: REST/Parquet/tabla):

| Pieza | Licencia | Rol |
|---|---|---|
| [`UNSW-CEEM/NEMOSIS`](https://github.com/UNSW-CEEM/NEMOSIS) (113 ★) | GPL-3.0-or-later | Ingesta de datos históricos publicados por AEMO |
| [`UNSW-CEEM/NEMSEER`](https://github.com/UNSW-CEEM/NEMSEER) | GPL-3.0 | Pronósticos de AEMO (pre-dispatch, PASA) |
| [`Open-ISP/isp-workbook-parser`](https://github.com/Open-ISP/isp-workbook-parser) | GPL-3.0 | Supuestos del **IASR** desde los Excel de AEMO |
| [`Open-ISP/isp-trace-parser`](https://github.com/Open-ISP/isp-trace-parser) | GPL-3.0 | Series de demanda, solar y viento |
| [`Open-ISP/ISPyPSA`](https://github.com/Open-ISP/ISPyPSA) (31 ★) | GPL-3.0 | Expansión de capacidad con metodología **ISP de AEMO** |

**Lado permisivo — motor analítico del cliente** (aquí sí se embebe y se puede cerrar):

| Pieza | Licencia | Rol |
|---|---|---|
| [`UNSW-CEEM/nempy`](https://github.com/UNSW-CEEM/nempy) (71 ★) | **BSD-3** | Simula el **procedimiento de despacho** real del NEM |
| [`UNSW-CEEM/NEMED`](https://github.com/UNSW-CEEM/NEMED) | **BSD-3** | Emisiones del NEM |
| [`UNSW-CEEM/DER_disturbance_analysis`](https://github.com/UNSW-CEEM/DER_disturbance_analysis) | **MIT** | Respuesta de PV y DER a perturbaciones del sistema |
| [`pypsa/pypsa`](https://github.com/PyPSA/PyPSA) | MIT | Motor bajo `ISPyPSA`; usable directo del lado permisivo |

**Cómo se cablea:**

1. El servicio GPL expone **tablas versionadas** (Parquet en objeto + catálogo), no una librería. El
   contrato es el esquema de datos.
2. El motor propietario lee esas tablas y embebe `nempy` para contrafactuales de despacho y `NEMED`
   para la cuenta de emisiones. **Nada del lado propietario importa `NEMOSIS`.**
3. Lo que el cliente compra es el **motor** y el **modelo de decisión**; lo que recibe como open source
   es el servicio de datos, y conviene decirlo así: reduce el *lock-in* percibido y es verdad.
4. Para expansión de capacidad, `ISPyPSA` corre **dentro del lado GPL** como trabajo por lotes que
   emite resultados, o se reconstruye sobre `PyPSA` (MIT) directamente si el entregable tiene que ser
   cerrado. **Es la decisión de diseño más costosa de la receta** y hay que tomarla en la primera
   semana, no en la décima.

**Trampas verificadas en este pase:**

- **`NEMOSIS` aparece como `NOASSERTION` en la API de GitHub y es GPL-3.0-or-later.** Un verificador
  automático lo clasificaría como "sin licencia" y lo descartaría — perdiendo la capa de ingesta de
  toda la región (T31).
- **`TDA_Python`** (diseño y análisis de tarifas, 8 ★) **no tiene licencia**: bloqueado, aunque sea
  justo lo que un proyecto de tarifas querría. No incluirlo.
- **`nem-bidding-dashboard`** (2023) y **`market-control-room`** (2022) son permisivos pero
  **inactivos**: valen como referencia de UI, no como dependencia.
- **AEMO no publica su propio modelo.** `Open-ISP` es una reimplementación de su metodología por un
  tercero. En la propuesta eso se dice: es trazable al ISP, **no es el ISP**.

**Entregable:** servicio de datos del NEM (GPL, aislado) + motor de despacho y emisiones propietario
+ frontera de licencia documentada y revisada por legal **antes** del desarrollo. **Primer hito:** un
contrafactual de despacho reproducible contra datos reales de AEMO, con el diagrama de licencias
firmado.

### Receta 46 — Agente de flexibilidad doméstica de punta a punta, todo permisivo y sin nube (EMEA primero)

**Problema que resuelve.** El cliente —una distribuidora, un *retailer* de energía o un agregador—
quiere un agente que lea el consumo real de una vivienda o un edificio, entienda qué hay conectado y
responda a señales de flexibilidad del operador. Hasta este pase esta KB podía montar la mitad de
arriba (señal, optimización, simulación) pero **no la mitad de abajo**: la lectura del medidor y del
inversor. El pase 13 cierra esa mitad, y la cierra con piezas **permisivas y de origen EMEA**.

**La cadena completa, pieza por pieza, toda verificada el 2026-11-20:**

| Capa | Pieza | Licencia | Qué aporta |
|------|-------|----------|------------|
| **Medidor** | [`pwitab/iec62056-21`](https://github.com/pwitab/iec62056-21) | **BSD-3-Clause** | Lectura local IEC 62056-21 en Python |
| **Medidor (edge/firmware)** | [`lvzon/dsmr-p1-parser`](https://github.com/lvzon/dsmr-p1-parser) | **Apache-2.0** | Parser P1 en C para microcontrolador o gateway |
| **Normalización** | [`Apollon77/smartmeter-obis`](https://github.com/Apollon77/smartmeter-obis) | **MIT** | Traduce OBIS de varios fabricantes a un esquema único |
| **Inversor / DER** | [`volkszaehler/mbmd`](https://github.com/volkszaehler/mbmd) + [`sunspec/pysunspec2`](https://github.com/sunspec/pysunspec2) | **BSD-3** / **Apache-2.0** | Adquisición Modbus como servicio + cliente SunSpec oficial |
| **Modelo de datos** | [`sunspec/models`](https://github.com/sunspec/models) | **Apache-2.0** | Diccionario normativo de DER: semántica, no registros crudos |
| **Semántica del sitio** | [`NeverBlink-OSS/saref-linkml`](https://github.com/NeverBlink-OSS/saref-linkml) | **BSD-3-Clause** | SAREF en LinkML: esquemas generados, no OWL a mano |
| **Gemelo / simulación** | [`JBjoernskov/Twin4Build`](https://github.com/JBjoernskov/Twin4Build) | **MIT** | Simula el edificio sobre el **mismo** modelo semántico |
| **Señal de flexibilidad** | [`OpenLEADR/openleadr-rs`](https://github.com/OpenLEADR/openleadr-rs) (VTN/VEN) + [`ElaadNL/openadr3-client`](https://github.com/ElaadNL/openadr3-client) (Python) | **Apache-2.0 OR MIT** / **Apache-2.0** | **OpenADR 3.0** real — ver la nota de licencia abajo |
| **Actuación EV / carga** | `evcc` (MIT), `EVerest` (Apache-2.0) | — | Ya catalogados en esta KB |
| **Optimización / RL** | `CityLearn` (MIT), `sinergym` (MIT) | — | Ya catalogados: entrenar y evaluar antes de tocar la casa |

**Cómo se cablea, y el orden importa:**

1. **`mbmd` y el lector de medidor publican a un *broker*** (MQTT). Son servicios con ciclo de vida
   propio, no librerías dentro del agente: si el agente cae, la telemetría sigue.
2. **`smartmeter-obis` normaliza** antes de persistir. Normalizar **en la entrada**, no en consulta:
   si el esquema OBIS entra crudo, cada modelo posterior hereda el fabricante.
3. **El esquema generado desde `saref-linkml` es el contrato** entre telemetría y agente. El agente
   razona sobre conceptos SAREF, no sobre `modbus/40072`. Es lo que hace que añadir un fabricante sea
   un conector nuevo y no un cambio en el agente.
4. **`Twin4Build` simula sobre ese mismo modelo semántico.** Es la propiedad que lo hace elegible:
   el gemelo y el agente comparten vocabulario, así que lo aprendido en simulación se transfiere sin
   re-mapeo.
5. **`openleadr-rs` como VEN recibe la señal del operador** (OpenADR 3.0). Si el equipo es Python,
   `ElaadNL/openadr3-client` —mismo origen, misma versión del protocolo.
6. **La actuación va por `evcc`/`EVerest`**, y **detrás de un confirmador humano o de un envolvente
   de seguridad explícito**. Es la regla que el `automotive-kb` dejó probada y que aquí aplica igual:
   el texto del razonamiento del modelo **nunca** llega al actuador; sólo llega un comando validado.

**La nota de licencia, que en este pase es el hallazgo y no una nota al pie:** durante dos pases esta
KB dijo que `openleadr-rs` no tenía licencia y que **OpenADR 3.0 no tenía implementación abierta
licenciada**, y recomendó bajar a 2.0b o reimplementar. **Era falso** (T45 derogada, ver T46):
`Cargo.toml` declara `license = "Apache-2.0 OR MIT"` y `LICENSE-MIT`/`LICENSE-APACHE` devuelven 200.
**Esta receta no existía porque un dato de licencia equivocado la hacía parecer imposible.**

**La trampa que hay que esquivar al dibujar el diagrama, y es específica de esta capa:** si se eligen
las piezas por estrellas, **el entregable se rompe**. `UtilitechAS/amsreader-firmware` (471 ★) es la
opción aparentemente obvia para el firmware del lector y es **Fair Source License 0.9 con tope de
5 usuarios**; `binsentsu/home-assistant-solaredge-modbus` (420 ★) **no tiene licencia**;
`bolagnaise/PowerSync` (96 ★) es **PolyForm Noncommercial**, que prohíbe exactamente el uso que es un
encargo. Los sustitutos limpios tienen **menos** estrellas. **En esta capa el filtro de licencia va
antes del filtro de popularidad**, y se corre abriendo el archivo repo por repo.

**Dimensionado.** 4-6 semanas para una instalación piloto instrumentada de punta a punta con un
fabricante de medidor y uno de inversor (el 70 % del esfuerzo es conectores y normalización, no IA).
10-14 semanas para multi-fabricante con gemelo calibrado y VEN de OpenADR 3.0 certificado contra el
VTN del operador. **Primer hito que conviene fijar:** una semana de telemetría continua normalizada
a esquema SAREF **antes** de proponer cualquier modelo — si la telemetría no es estable, el agente no
es el problema.

**Regiones donde aplica, y por qué en este orden.** **EMEA primero**: 9 de las 13 piezas nuevas son
de origen EMEA y el mandato de medidor inteligente más el acceso local a datos del hogar son políticas
europeas, así que hay base instalada y argumento regulatorio. **North America**: aplica igual, con
`volttron-openadr-ven` (Apache-2.0, PNNL) como VEN si el cliente ya tiene VOLTTRON, y con OpenADR
como protocolo de referencia de la región. **LATAM**: viable en Brasil **si** la consulta del MME
sobre medidor inteligente se convierte en norma — hoy es consulta, no obligación. **APAC**: en Japón
hay que contar con la fragmentación a dos frecuencias; en India el trabajo previo es de
instrumentación y datos, no de modelo.

## Recetas del decimocuarto pase (2026-11-21)

### Receta 47 — Expediente auditable de IA en operación de red, contra la guía de NERC y el plazo CIP de diciembre de 2026

**Para quién:** utility o ISO/RTO de **North America** que ya tiene (o quiere) IA en el lazo de
decisión y necesita **demostrarlo ante el regulador**. Es la receta que la guía de NERC vuelve
vendible: si la IA debe ser **apoyo a la decisión y no controlador autónomo**, entonces el entregable
no es el modelo — **es la prueba de que el humano decidió y de que la máquina sólo recomendó.**

**Restricción de diseño, no negociable y ahora respaldada por la guía:** el texto de razonamiento
del LLM **nunca** llega al actuador. El agente escribe en el **registro de decisiones**; el operador
escribe en el sistema.

| Capa | Pieza | Licencia | Papel concreto |
|------|-------|----------|----------------|
| Política de cumplimiento ejecutable | [`ynotbhatc/rego_policy_libraries`](https://github.com/ynotbhatc/rego_policy_libraries) | **Apache-2.0** | Reglas CIP como **políticas OPA Rego v1** evaluables en CI. Es lo único *ejecutable* del ecosistema CIP abierto |
| Registro de decisiones | **patrón** de [`mizcausevic-dev/grid-decision-record-audit-stream`](https://github.com/mizcausevic-dev/grid-decision-record-audit-stream) | MIT | Eventos de decisión **encadenados por hash**: qué recomendó el agente, con qué datos, quién aprobó. ⚠️ **construir el patrón, no depender del repo** (0 ★, un autor) |
| Cuantificación de confianza | [`gridfm/gridfm-trustlayer`](https://github.com/gridfm/gridfm-trustlayer) | **Apache-2.0** | Incertidumbre de la predicción. **Sin esto no hay apoyo a la decisión**: una recomendación sin intervalo no es decidible por un operador |
| Plantillas de evidencia | [`mizcausevic-dev/nerc-cip-readiness-evidence-bundle`](https://github.com/mizcausevic-dev/nerc-cip-readiness-evidence-bundle) + [`gridsafetechnology-tech/nerc-cip-checklists`](https://github.com/gridsafetechnology-tech/nerc-cip-checklists) | MIT | Estructura CIP-002→CIP-014 y checklists YAML como **punto de partida documental** |
| Modelo de red | `gridfm-graphkit` + `gridfm-datakit` | **Apache-2.0** | ⚠️ **hay que entrenarlo**: no existe checkpoint publicado (verificado dos veces). Presupuestar el entrenamiento, no la descarga |

**Cómo se conecta, en orden:**

1. El modelo de red produce una recomendación **con intervalo de confianza** (`trustlayer`). Una
   recomendación sin intervalo no entra en el flujo.
2. La recomendación se evalúa contra las **políticas Rego**: si viola una regla CIP, **no se muestra
   como accionable**, se muestra como bloqueada y con la regla que la bloquea.
3. Todo lo anterior —entrada, recomendación, intervalo, veredicto de política, identidad del
   aprobador— se escribe en el **registro encadenado por hash**.
4. El operador aprueba o rechaza **en el sistema de control, fuera del agente**.
5. El expediente para el regulador **se genera del registro**, no se redacta a mano.

**Por qué se vende:** el cliente no compra un modelo, compra **la capacidad de aprobar una inversión
en IA ante su regulador tarifario** — que es, literalmente, lo que Morningstar DBRS describe como el
problema nuevo de las autoridades regulatorias (deben evaluar la inversión en IA, no sólo revisar el
capex). El entregable es el expediente.

⚠️ **Lo que NO se promete:** ninguna de estas piezas pasa de 23 ★. Esta receta **no es una
integración de productos maduros**, es **trabajo de ingeniería sobre plantillas**. Cotizar en
consecuencia y decirlo en el SOW.

### Receta 48 — Tubería de distribución LATAM: del dato del regulador al modelo ejecutable, todo permisivo

**Para quién:** distribuidora o regulador de **Brasil** (y, con el conector cambiado, el resto de
LATAM). Es la primera receta de esta KB **enteramente construida con repos de origen LATAM**, y
responde a la pregunta que abre cualquier *engagement* en la región: *"¿de dónde sale el modelo de
red?"*

| Capa | Pieza | Licencia | Papel concreto |
|------|-------|----------|----------------|
| Acceso al dato del regulador | [`Mcp-Brasil/mcp-brasil`](https://github.com/Mcp-Brasil/mcp-brasil) | **MIT** (⚠️ el dato, aparte) | Feature `aneel`: **4 tools** sobre el CKAN de ANEEL (SIGA, generación distribuida, tarifas, banderas). Expone el regulador **como herramientas de agente**, sin escribir el conector |
| Modelo de red ejecutable | [`eniocc/bdgd-tools`](https://github.com/eniocc/bdgd-tools) | **MIT** (byte-read) | **Convierte la BDGD de ANEEL en elementos OpenDSS.** Es la pieza que no hay que escribir: el salto del dato geográfico regulatorio al simulador |
| Simulación de distribución | `dss-extensions/OpenDSSDirect.py` | BSD-3 (ya en la KB) | Estudios de alimentador sobre el modelo convertido |
| Señal operativa | **patrón** de [`nightcrowsgui5-netizen/radar-curtailment-sin`](https://github.com/nightcrowsgui5-netizen/radar-curtailment-sin) | MIT | Cuantifica **curtailment por *constrained-off*** desde datos abiertos del ONS: el indicador que convierte el estudio en un caso de negocio |
| Consulta normativa | [`GuilhermeBarros12/rag_aneel`](https://github.com/GuilhermeBarros12/rag_aneel) | MIT | RAG sobre normativa de ANEEL, para que el agente **cite la regla** en lugar de parafrasearla |

**Cómo se conecta:**

1. `mcp-brasil` da al agente las series y los registros de ANEEL **como tools**, no como scraping.
2. `bdgd-tools` convierte la BDGD del alimentador en cuestión a **OpenDSS**.
3. `OpenDSSDirect.py` corre los escenarios; el agente propone, **no despacha**.
4. El indicador de *curtailment* sobre datos del ONS cuantifica **la pérdida que el proyecto evita**
   — el número que firma el cliente.
5. `rag_aneel` acompaña cada recomendación con **la norma que la respalda**.

**Los tres avisos que hacen esta receta honesta:**

- ⚠️ **`bdgd-tools` no tiene push desde 2024-08-16.** Con 9 forks y 16 issues sobre 10 ★ tiene uso
  real, pero **se adopta como punto de partida de un fork**, con mantenimiento presupuestado, no como
  dependencia viva.
- ⚠️ **`mcp-brasil` separa licencia de código y de dato.** MIT cubre el código; `SOURCES.md` dice que
  `aneel` es *"open data; atribuição"* → **utilizable comercialmente con atribución**, pero hay que
  leer `ACCEPTABLE_USE.md` antes de uso decisorio. **Un conector permisivo no licencia el dato que
  descarga.**
- ⚠️ Las piezas de indicador y RAG tienen **0-3 ★**: se toman como **patrón de referencia**, no como
  componente soportado.

**Por qué importa estratégicamente:** el pase 13 definió el hueco de Globant en LATAM como
*"distribución / capa agéntica / dossier"*. Esta receta muestra que **la capa de abajo ya existe y es
permisiva**, y por tanto **el hueco es exactamente lo que va encima**: optimización, pronóstico
operativo y orquestación agéntica. Un proyecto LATAM **no empieza construyendo conectores**; empieza
donde el valor está sin capturar.

---

## Recetas del decimoquinto pase (2026-11-21)

### Receta 49 — Copiloto de modelo de red con compuerta de validación SHACL (EMEA, y es la forma más limpia de cumplir la restricción de arquitectura)

**El problema del cliente.** Un TSO o DSO europeo quiere automatizar la preparación y revisión de
modelos de red, pero no puede dejar que un LLM escriba en el modelo del sistema. La restricción
—apoyo a la decisión, nunca control— parece incompatible con automatizar de verdad.

**La idea.** No hace falta confiar en el agente si **el esquema del propio sector puede rechazarlo**.
CGMES viene con **SHACL**, que es validación declarativa: el agente propone un modelo candidato y
**SHACL lo acepta o lo rechaza antes de que nada llegue al sistema**. El humano firma sobre un
candidato ya validado por la norma, no sobre texto de un LLM.

**Las piezas, todas permisivas y todas de origen europeo:**

| Capa | Pieza | Licencia |
|------|-------|----------|
| Lectura/escritura del modelo | [`sogno-platform/cimpy`](https://github.com/sogno-platform/cimpy) (Python) o [`cim4j`](https://github.com/sogno-platform/cim4j) (Java) | Apache-2.0 |
| Esquema consultable | [`RWTH-IAEW/cimpyorm`](https://github.com/RWTH-IAEW/cimpyorm) | BSD-3-Clause |
| **Compuerta de validación** | [`SOPTIM/OpenCGMES`](https://github.com/SOPTIM/OpenCGMES) — RDFS + **SHACL** + CIMXML | Apache-2.0 |
| Cálculo eléctrico | [`PyPSA/PyPSA`](https://github.com/PyPSA/PyPSA) o [`powsybl/powsybl-core`](https://github.com/powsybl/powsybl-core) | MIT / MPL-2.0 |
| Caso de prueba | [`entsoe/ReliCapGrid`](https://github.com/entsoe/ReliCapGrid) — modelos de test en CGMES, de ENTSO-E | ver nota de licencia en la KB |

**El cableado, y el orden importa:**

1. `cimpy` carga el CGMES del cliente; `cimpyorm` lo expone como esquema consultable.
2. El agente **sólo lee** y **propone un delta** —nunca escribe en el modelo vivo.
3. **`OpenCGMES` valida el delta con SHACL.** Si falla, el delta vuelve al agente con el error de la
   norma como realimentación. Esto es un bucle **cerrado por el esquema**, no por el LLM.
4. Un delta validado va a `PyPSA`/`powsybl` para el cálculo eléctrico.
5. El humano firma el candidato validado. **El texto de razonamiento del agente nunca llega al
   modelo** — sólo el delta que SHACL aprobó.

**Por qué se vende.** Responde la objeción de fiabilidad con un mecanismo, no con una promesa: *"el
agente no puede introducir un modelo inválido, porque lo valida la norma del sector antes que
usted"*. Y toda la cadena es permisiva y europea, con lo que la pregunta de soberanía queda
respondida en el mismo diagrama.

---

### Receta 50 — Flexibilidad en colocation: el segmento que ENTSO-E describió y nadie atiende (EMEA)

**El hallazgo que la origina.** ENTSO-E (8-may-2026) dice que los centros de datos **hiperescala**
están en posición de prestar servicios de flexibilidad, mientras los de **colocation** están
**limitados por el control del inquilino**. Ese límite **no es físico**: el hierro es el mismo. Es
que el operador del edificio **no controla las cargas** y los inquilinos **no tienen incentivo ni
interfaz** para ceder flexibilidad. Es un problema de **contrato + coordinación + medición**, es
decir, de software.

**La idea.** Construir la capa de coordinación operador ↔ inquilino que convierte un colocation en
un recurso de flexibilidad agregable: medir por inquilino, pedir desplazamiento de carga, liquidar
el incentivo, y exponer el agregado al mercado.

**Las piezas:**

| Capa | Pieza | Licencia |
|------|-------|----------|
| Medición por inquilino | [`volkszaehler/mbmd`](https://github.com/volkszaehler/mbmd) (Modbus) + [`sunspec/models`](https://github.com/sunspec/models) | BSD-3 / Apache-2.0 |
| Señal de demanda | [`openadr3-client`](https://github.com/ElaadNL/openadr3-client) u [`openleadr-rs`](https://github.com/OpenLEADR/openleadr-rs) (OpenADR 3.0) | Apache-2.0 / MIT-o-Apache |
| Esquema del dato | SAREF vía [`Twin4Build`](https://github.com/JBjoernskov/Twin4Build) / `saref-linkml` | MIT / BSD-3 |
| Mecanismo de incentivo | [`TU-Delft-AI-Energy-Lab/MARL-iDR`](https://github.com/TU-Delft-AI-Energy-Lab/MARL-iDR-Multi-Agent-Reinforcement-Learning-for-Incentive-based-Residential-Demand-Response) — RL multiagente de DR **basada en incentivos**: el esquema, no el código | MIT |
| Desplazamiento de carga batch | patrón de [arXiv 2609.38020](https://arxiv.org/pdf/2609.38020) (*batch workload temporal shifting*) ⚠️ **id sin verificar** (arxiv.org rechazado por el proxy) |
| Oferta al mercado | [`phasenexa/nexa-bidkit`](https://github.com/phasenexa/nexa-bidkit) (day-ahead / intradiario europeo) | MIT |
| Simulación previa | [`dos-group/vessim`](https://github.com/dos-group/vessim) — simula sistemas energéticos de centro de datos | MIT |

**El cableado.** `mbmd` da consumo por inquilino sobre SAREF → `vessim` simula cuánta flexibilidad
existe realmente antes de prometer nada → OpenADR 3.0 transporta la señal al inquilino → el esquema
de incentivos de `MARL-iDR` fija el pago → `nexa-bidkit` oferta el agregado. **El agente propone el
plan de desplazamiento; el despacho real lo ejecuta el sistema del inquilino.** La frontera se
dibuja en el contrato antes que en el código.

**Por qué este encargo existe.** El propio operador de transmisión europeo publicó que este segmento
**no puede** prestar flexibilidad por una causa nombrada. Llegar con la causa resuelta es la
propuesta.

---

### Receta 51 — Expediente NERC CIP con herramientas de un laboratorio nacional (NA) — extiende la receta 47

**Lo que cambia respecto a la 47.** La receta 47 (pase 14) definió el expediente auditable pero **no
tenía ninguna pieza permisiva de origen norteamericano**. Este pase la encuentra: el **Idaho National
Laboratory** publica en **MIT** sus herramientas de *Cyber-Informed Engineering*, que es precisamente
el marco con el que se argumenta ciberseguridad de OT ante el regulador.

| Capa | Pieza | Licencia |
|------|-------|----------|
| Análisis CIE de microrred | [`idaholab/CIEMAT`](https://github.com/idaholab/CIEMAT) | MIT |
| Análisis CIE de baterías | [`idaholab/CIEBAT`](https://github.com/idaholab/CIEBAT) | MIT |
| Dato público federal, para agente | [`maxoliverbr/eia-api-ts`](https://github.com/maxoliverbr/eia-api-ts) — wrapper de EIA API v2 **para uso agéntico** | MIT |
| Automatización de estudio | [`mzy2240/ESA`](https://github.com/mzy2240/ESA) (PowerWorld desde Python) | Apache-2.0 |
| Registro de decisiones | patrón de cadena por hash (receta 47) |

**El gancho normativo, con su advertencia.** Dos afirmaciones concurrentes de fuente secundaria,
⚠️ **sin verificar contra documento primario de NERC** (open item 15-R1): (1) **NERC CIP asume un
sistema de control operado por humanos y no aborda agentes autónomos**; (2) **una herramienta de IA
que toca un BES Cyber System categorizado hereda las obligaciones de ese sistema**.

Si (2) se sostiene, el encargo se formula solo: la pregunta del cliente deja de ser *"¿puedo usar
IA?"* y pasa a ser *"¿qué obligaciones hereda lo que acabo de conectar?"* — una pregunta de **alcance
y evidencia**, que es exactamente el entregable. **Verificar (1) y (2) antes de ponerlas en una
propuesta.**

**La frontera, no negociable y ahora triplemente respaldada:** los agentes **no entran en la zona de
control** —SCADA, EMS, control de ADMS, despacho DERMS, automatización de subestación, PLC—: sin
herramienta, sin credencial, **sin ruta de red**; sólo lectura por defecto y rutas de revocación.

---

### Receta 52 — Agente de planificación de red para APAC, deliberadamente sin tiempo real

**El dato que la dicta.** **23% de los operadores de red de Asia Oriental usa IA en operación en
tiempo real; 54% en planificación del desarrollo de red**, y la IEA atribuye la diferencia a
**fiabilidad** (abril 2026; ⚠️ por snippet). El 23% no es inmadurez del cliente: **es su política de
riesgo**. La receta renuncia al tiempo real **a propósito** y lo dice en la primera página de la
propuesta.

**Y la segunda restricción, también de la IEA:** la **falta de interconexiones transfronterizas** en
Asia Oriental hace que el valor sea **intra-país**, y los modelos **no transfieren entre países**
(generaliza el hallazgo de las dos frecuencias de Japón de los pases 13–14). Por tanto: **un
despliegue por país, nunca una plataforma regional**. Quien ofrezca "una plataforma para APAC" está
ofreciendo algo que no funciona.

**Las piezas:**

| Capa | Pieza | Licencia |
|------|-------|----------|
| Modelado del sistema | [`PyPSA/PyPSA`](https://github.com/PyPSA/PyPSA) | MIT |
| Red de distribución | [`dss-extensions/OpenDSSDirect.py`](https://github.com/dss-extensions/OpenDSSDirect.py) / [`.jl`](https://github.com/dss-extensions/OpenDSSDirect.jl) | MIT |
| Agente de estudios | [`Power-Agent/PowerMCP`](https://github.com/Power-Agent/PowerMCP) + [`PowerSkills`](https://github.com/Power-Agent/PowerSkills) | MIT |
| Marco de madurez | [arXiv 2607.28822](https://arxiv.org/pdf/2607.28822) — brechas de capacidad de IA agéntica en sistemas de potencia. ⚠️ **id sin verificar** (arxiv.org rechazado por el proxy) |
| VPP (origen APAC) | [`ruikelyu/Real-time-operation-strategy-of-virtual-power-plants`](https://github.com/ruikelyu/Real-time-operation-strategy-of-virtual-power-plants) | MIT |
| Precio spot de China | [`ronaldowzy/price_forecast`](https://github.com/ronaldowzy/price_forecast) | MIT |
| Solar | [`renewables-ninja/gsee`](https://github.com/renewables-ninja/gsee) + [`pvlib/pvlib-python`](https://github.com/pvlib/pvlib-python) | BSD-3 |

**El cableado.** El agente opera **sobre el modelo, no sobre la red**: toma el caso de planificación,
ejecuta estudios con `PowerMCP` sobre `PyPSA`/OpenDSS, y entrega **escenarios comparados con su
trazabilidad**. Ninguna credencial del agente alcanza un sistema de operación — lo que además
encaja con la *AI Basic Act* coreana (en vigor **22-ene-2026**), que obliga a **notificar uso de IA
de alto impacto y etiquetar salidas generativas**: un entregable de planificación con trazabilidad
y etiquetado es **más fácil de declarar** que un sistema que toca el despacho.

**La frase de apertura de la propuesta:** *"no le vamos a proponer IA en tiempo real, por la misma
razón por la que el 77% de los operadores de su región no la usa."*

## Recetas del pase 16 (2026-11-24)

Contexto que cambia estas cuatro recetas respecto de las anteriores: la **restricción de arquitectura
de esta KB dejó de ser una tesis propia**. Está en un **borrador de norma del NIST** (comportamiento
determinista, explicabilidad, degradación elegante, *fail-safe*) y está **embarcada en el producto de
un operador de sistema nacional** (el servidor MCP del ONS brasileño). Eso permite, por primera vez,
proponer la compuerta **citando a quien ya la construyó** en vez de argumentándola.

### Receta 53 — Compuerta de contratos de datos sobre el portal de un regulador u operador (replica lo que el ONS ya publicó)

**Es la receta 49 (compuerta de validación) con el precedente dentro.** En el pase 15 esta KB la
propuso como diseño propio con SHACL. El ONS la embarcó con **ODCS + DuckDB** y la publicó
**Apache-2.0**. Ahora se vende mostrando el repo.

**Piezas (todas verificadas vivas el 2026-11-24, licencias leídas byte a byte):**

| Pieza | Licencia | Rol |
|-------|----------|-----|
| [ONSBR/TIAGO-Dados-Abertos](https://github.com/ONSBR/TIAGO-Dados-Abertos) | **Apache-2.0** (11.357 B) | **El servidor, reutilizable tal cual.** MCP + enrutado + validación + ejecución |
| [bitol-io/open-data-contract-standard](https://github.com/bitol-io/open-data-contract-standard) | **Apache-2.0** (11.356 B) | **ODCS**: el formato del contrato. Declara schema, unidades, **aditividad por columna** y agregaciones válidas |
| DuckDB | MIT | Motor de ejecución analítica embebido |
| Cliente MCP (Claude, o cualquier host MCP) | — | Donde corre el modelo. **Nunca en el servidor** |

**Cómo se cablea, y por qué cada paso existe.** El modelo del cliente recibe **el catálogo y los
contratos**, no los datos. Escribe SQL contra un schema **declarado**, no imaginado. El servidor
valida ese SQL contra el contrato antes de ejecutarlo, ejecuta en DuckDB, y devuelve el dato **con su
unidad y su fuente probadas por el contrato**. Si el contrato no sostiene una afirmación, el servidor
**marca el campo como desconocido en vez de deducirlo**.

**Los cinco modos de fallo que el contrato elimina** (del README del ONS, citables ante cliente):
elegir el dataset equivocado entre recortes de distinta granularidad —«la consulta corre, devuelve un
número plausible, y responde otra pregunta»—; escribir SQL contra un schema inventado; **errar la
unidad (`MWmed` no es `MWh`, y la diferencia no aparece en el resultado)**; **agregar lo que no se
agrega** (sumar una columna que ya es promedio duplica el valor sin arrojar ningún error); y perder
la procedencia.

**Qué es lo facturable.** El servidor es Apache-2.0: **no se factura construirlo**. Se factura
**escribir los contratos ODCS del dominio del cliente**, que es modelado semántico y consultoría de
dominio, y es exactamente el trabajo que no se puede copiar de un repo. Portales objetivo
inmediatos: **ANEEL** (sobre `tarifas-energia-api`, receta 48), **CAMMESA**, **CEN de Chile**,
**EIA** (donde ya hay `eia-api-ts` MIT y `cyanheads/eia-energy-mcp-server` Apache-2.0), **ENTSO-E**
(donde ya existe la capa CIM/CGMES de los pases 13-15).

**Por qué pasa el filtro de arquitectura.** Es la forma más limpia que esta KB conoce de cumplirlo:
el agente **no toca nada operativo**, consulta datos publicados; la determinación la da el contrato,
no el modelo; y **ningún LLM corre en el servidor**, así que el despliegue no arrastra una decisión
de soberanía de modelo — argumento directo en EMEA y en APAC.

⚠️ **Límite declarado.** TIAGO es un servidor de **consulta de datos abiertos**, no de operación: su
alcance es el portal público, no el SIN ni el despacho. Proponer el **patrón** y la **autoría
institucional**, no un alcance operativo que el repo no tiene.

### Receta 54 — Expediente de calificación de centro de datos ≥ 500 kW para el esquema delegado de la UE

**Tiene umbral, criterios y un reglamento delegado en curso: hay contraparte que paga y hay fecha.**
El **21-sep-2026** la Comisión propuso, dentro del *Data Centre Energy Efficiency Package*, un
**reglamento delegado** con un **esquema común de calificación** para centros de datos de **potencia
TI instalada ≥ 500 kW**, más consulta sobre **estándares mínimos de rendimiento**. Califica
eficiencia energética, **eficiencia hídrica**, uso de renovables, **reutilización de calor residual**
y **flexibilidad**.

**Dónde está la ventaja de esta KB: dos de los cinco criterios son stack que ya tiene inventariado.**

| Criterio del esquema | Piezas proponibles | Licencia |
|----------------------|--------------------|----------|
| **Flexibilidad** | Stack de flexibilidad y DER de las recetas 46 y 50; [`eclipse-volttron/volttron-core`](https://github.com/eclipse-volttron/volttron-core) + [`volttron-openadr-ven`](https://github.com/eclipse-volttron/volttron-openadr-ven) | Apache-2.0 |
| **Reutilización de calor residual** | Stack de calor de distrito del décimo pase: `DHNx`, `topotherm`, `tespy` | MIT |
| Eficiencia energética (medición y verificación) | Capa M&V y de medición de los pases 4 y 13 | MIT / permisivas |
| Modelado del edificio/instalación | [`LBNL-ETA/EnergyPlus-MCP`](https://github.com/LBNL-ETA/EnergyPlus-MCP) + [`NatLabRockies/OpenStudio`](https://github.com/NatLabRockies/OpenStudio) | ⚠️ ver nota |
| Compuerta de evidencia | Receta 53 (contratos ODCS sobre los datos de medición) | Apache-2.0 |

**El gancho comercial preciso:** el esquema convierte **flexibilidad y calor residual en atributos
calificados y declarables**, no en buenas intenciones. Eso los vuelve **trabajo de evidencia
auditable**, que es un entregable con fecha. Y conecta con el **acuerdo tripartito modelo** de la
hoja de ruta (COM(2026) 501): la UE reconoce que integrar un centro de datos en la red es un problema
**contractual y de coordinación** — el mismo diagnóstico que ENTSO-E hizo del *colocation* en la
receta 50, ahora con respaldo de la Comisión. **La receta 50 y esta se venden juntas.**

⚠️ `NatLabRockies/OpenStudio` devuelve `NOASSERTION` y **no se le leyó la licencia byte a byte en
este pase**: resolver antes de incluirlo en una propuesta (ítem 16-R4).
⚠️ Toda la base regulatoria de esta receta es **secundaria convergente** (seis fuentes), porque los
hosts primarios de la UE no resuelven DNS desde esta sesión. Verificar el reglamento delegado contra
EUR-Lex antes de comprometer alcance con un cliente.

### Receta 55 — Arnés de conformidad contra el perfil de infraestructura crítica del NIST (NA) — extiende las recetas 47 y 51

**Se vende antes de que el perfil se publique, porque el borrador ya dice qué va a pedir.** El NIST
desarrolla un **Trustworthy AI in Critical Infrastructure Profile** del AI RMF cuyas necesidades
declaradas son **comportamiento determinista, explicabilidad, degradación elegante y operación
*fail-safe***. Hay **community of interest abierta a comentarios** — vía de entrada barata y de alta
credibilidad: participar en el comentario público es posicionamiento.

**Los cuatro requisitos, y con qué se demuestra cada uno:**

| Requisito del perfil | Cómo se evidencia | Piezas |
|----------------------|-------------------|--------|
| **Comportamiento determinista** | La compuerta de la receta 53: la respuesta la determina el contrato, no el muestreo del modelo. Registro de contrato aplicado por consulta | ODCS + servidor Apache-2.0 |
| **Explicabilidad** | Traza de procedencia: cada número con su dataset y su URL de origen | Receta 53 |
| **Degradación elegante** | El caso «no puedo probarlo» devuelve **desconocido** en vez de un número plausible. Es un requisito de diseño, y ya hay implementación de referencia | TIAGO como precedente |
| **Operación *fail-safe*** | El agente **no tiene ruta de escritura** al sistema de control. Es arquitectura, no política | Recetas 47 y 51 |
| Ingeniería informada por ciber | `idaholab/CIEMAT` + `CIEBAT` (**MIT**, *Cyber-Informed Engineering*, laboratorio nacional) | MIT |

**Encuadre comercial.** Apilar con la **receta 47** (expediente auditable contra la guía NERC, plazo
CIP de diciembre de 2026) y la **51** (herramientas de laboratorio nacional). El argumento de venta
es que **los cuatro requisitos son auditables y el cliente no tiene hoy cómo demostrarlos**, y que
**Deloitte y la NERC coinciden** en que la IA es apoyo a la decisión y no controlador autónomo: el
expediente no es una concesión, es la forma del producto. Canal adicional: el **MOU NIST–DOE** de
agosto de 2026 y los **Centers for AI in Manufacturing and Critical Infrastructure** (con MITRE).

⚠️ **Estado del borrador no verificado**, cobertura secundaria, y **ninguna fuente lo vincula a la
Genesis Mission** (ítem 16-R1). Proponer como **tendencia de normalización bien fundada**, nunca como
requisito vigente. ⛔ **No citar `micro-ark.com`** ni su afirmación de que la FERC exige trazas
«100 % transparentes».

### Receta 56 — Operacionalizar los modelos que el operador ya publica (LATAM, Brasil primero)

**La inversión del punto de partida.** Hasta este pase, una propuesta de pronóstico en Brasil
empezaba por construir un modelo. Ya no: **el ONS publica los suyos con licencia permisiva**, así que
lo que se propone es **operacionalizarlos, validarlos y ponerles interfaz** — y eso es defendible
ante el regulador precisamente porque es el modelo del operador.

| Pieza | Licencia (byte-read) | Rol |
|-------|----------------------|-----|
| [ONSBR/smapOnsR](https://github.com/ONSBR/smapOnsR) | **MIT** (vía `DESCRIPTION`) | **SMAP/ONS** de afluencias en R. En un sistema hidrotérmico, la variable de la que cuelga el resto |
| [ONSBR/prevcarga](https://github.com/ONSBR/prevcarga) | **Apache-2.0** | PrevCarga-DESSEM, reescritura activa (push 2026-11-23) |
| [ONSBR/PrevCargaDESSEM](https://github.com/ONSBR/PrevCargaDESSEM) | **MIT** (vía `DESCRIPTION`) | Previsión de carga, copyright **CEPEL + ONS** |
| [ONSBR/TIAGO-Dados-Abertos](https://github.com/ONSBR/TIAGO-Dados-Abertos) | **Apache-2.0** | Capa de acceso con compuerta (receta 53) |
| [`bdgd-tools`](https://github.com/eniocc/bdgd-tools) + [`bdgd2opendss`](https://github.com/PauloRadatz/bdgd2opendss) | MIT | Cadena de distribución de la receta 48, para bajar del sistema a la red |
| [`TimeCopilot/timecopilot`](https://github.com/TimeCopilot/timecopilot) | MIT | *Challenger* agéntico: compara el modelo del operador contra TSFM y **explica** la diferencia |

**El caso de negocio, con el número.** Brasil **curtailed el 20,6 % de su solar+eólica en 2025**
(análisis sectorial; ⚠️ verificar contra ONS). Ese desperdicio es un problema de **pronóstico,
despacho y flexibilidad** — y ahora los modelos de pronóstico del operador están disponibles en MIT.
**La combinación de esos dos hechos es la propuesta LATAM más fuerte que esta KB ha podido formular.**

**Cómo se cablea.** `smapOnsR` produce afluencias; `prevcarga` produce carga; `timecopilot` corre como
*challenger* y explica divergencias; la receta 53 expone todo por MCP con contratos ODCS de modo que
cada número salga con unidad y procedencia; `bdgd2opendss` baja a modelo de distribución ejecutable
donde el caso sea de red y no de sistema. **Ningún componente escribe en un sistema de control.**

⚠️ `smapOnsR` y `PrevCargaDESSEM` resuelven **MIT en `DESCRIPTION`** (convención de R, `LICENSE` de
45 y 95 B); documentar ese hallazgo en la propuesta, porque una revisión legal superficial los leerá
como «sin licencia» (T61). ⛔ **`ONSBR/DadosAbertos` (43 ★) no tiene licencia**: es el repo más
visible de la organización y el único inutilizable.

### Receta 57

**Nombre:** *Engagement* de mercado eléctrico australiano (NEM) con stack permisivo de extremo a extremo
**Región:** APAC · **Licencia resultante:** MIT + BSD-3-Clause + CC-BY-4.0 (sin copyleft, sin indemnidad)

**Por qué esta receta existe.** Hasta este pase, la respuesta de esta KB a un cliente australiano
era —sin saberlo— «hay stack abierto pero es **GPL-3.0**», porque el inventario australiano era
académico (`UNSW-CEEM`, `Open-ISP`). Las capas añadidas en el pase 17 son **permisivas** y cubren los
dos extremos útiles: datos operativos y modelos de la agencia nacional.

**Piezas, todas con licencia leída byte a byte:**

| Capa | Pieza | Licencia |
|------|-------|----------|
| Ingesta primaria | [opennem/nemweb](https://github.com/opennem/nemweb) — ficheros **NEMWEB de AEMO** | MIT |
| Plataforma + API | [opennem/opennem](https://github.com/opennem/opennem) + [openelectricity-python](https://github.com/opennem/openelectricity-python) (cliente **oficial**) | MIT |
| Supuestos de planificación | [opennem/IspParser](https://github.com/opennem/IspParser) — *workbooks* del ISP de AEMO → JSON | MIT |
| Red física | [csiro-energy-systems/Synthetic-NEM-2000bus-Data](https://github.com/csiro-energy-systems/Synthetic-NEM-2000bus-Data) — 2.000 nodos, Matpower | CC-BY-4.0 (**dato**: exige atribución) |
| Despacho y precios | [csiro/ensys-NEMX.jl](https://github.com/csiro/ensys-NEMX.jl) — reconstruye el despacho de **5 min** y lo re-resuelve como OPF | BSD-3 |
| Adecuación | [csiro/ensys-iPASA.jl](https://github.com/csiro/ensys-iPASA.jl) — LOLE/EUE/NEUE | BSD-3 |
| Motores | [Sienna-Platform/PowerSimulations.jl](https://github.com/Sienna-Platform/PowerSimulations.jl) + [NatLabRockies/PRAS](https://github.com/NatLabRockies/PRAS) | BSD-3 + MIT modificado |
| Restricciones de mercado | [ampere-ventures/NEM_constraints](https://github.com/ampere-ventures/NEM_constraints) — ecuaciones de **NEMDE** | MIT |

**Cómo se cablea.** `nemweb` descarga los ficheros de AEMO → `opennem` normaliza y expone API →
`IspParser` aporta los supuestos del ISP → `iPASA.jl` monta el caso acoplando la **red sintética**,
los **datos del ISP** y **PRAS** sobre el ecosistema **Sienna**, y `NEMX.jl` resuelve el despacho y
los precios nodales. La capa agéntica se sitúa **sólo en consulta y preparación de casos**, nunca en
despacho.

**Lo que hace esta receta distinta de las demás de este archivo: no hay que diseñarla.** `iPASA.jl`
**ya es** ese acoplamiento, publicado por la **agencia científica nacional** australiana, con **DOI
(`10.25919/7j2y-c896`)** y documentación. Se reutiliza la arquitectura, no se inventa; el trabajo
del estudio es el caso del cliente, no la integración.

⚠️ **Cláusulas que hay que respetar:** `Synthetic-NEM-2000bus-Data` es **CC-BY-4.0**, es decir
**dato con obligación de atribución** —no código permisivo— y la atribución debe aparecer en el
entregable. ⚠️ **No transfiere a otro mercado**: el valor está en que los *parsers* hablan el idioma
de AEMO. Para otro país, se reescribe la capa de ingesta (restricción APAC del pase 15: **país por
país, nunca plataforma regional**).

### Receta 58

**Nombre:** La compuerta dentro de la formulación — el modelo aprendido como restricción, no como actuador
**Región:** Global · **Licencia resultante:** BSD-3 + *rider* de reserva de derechos del Gobierno de EE. UU. (**sin indemnidad si se respeta el límite de dependencias**)

**El problema que resuelve.** Las recetas 49 y 53 de esta KB construyen la compuerta como **dos
sistemas y un contrato**: el agente propone un delta, y una validación externa (**SHACL**, **ODCS**)
lo acepta o lo rechaza antes de que toque el modelo vivo. Funciona, pero tiene una costura: el
agente **puede** proponer un punto infactible, y la seguridad depende de que la compuerta esté bien
construida y nadie la rodee.

**La receta.** [lanl-ansi/MathOptAI.jl](https://github.com/lanl-ansi/MathOptAI.jl) **empotra el
predictor entrenado dentro del problema de optimización** de JuMP. El modelo de ML deja de ser un
sistema que propone y pasa a ser **una restricción más**, junto a las de red y de mercado. El
*solver* devuelve un punto **factible por construcción** o declara **infactible**: no hay un estado
intermedio en el que una propuesta inválida exista y haya que interceptarla.

**Cableado concreto:**

1. Entrenar el predictor donde ya se entrena (p. ej. pronóstico de demanda o de renovable con
   [openSTEF](https://github.com/OpenSTEF/openstef), MPL-2.0 — **dependencia, no base a forkear**).
2. Exportar el predictor e importarlo con `MathOptAI.jl` **dentro** del modelo JuMP.
3. Añadir las restricciones del sistema en el **mismo** modelo: límites de rampa, reserva,
   capacidad, y la formulación de red.
4. Resolver con un solver MINLP ([lanl-ansi/Juniper.jl](https://github.com/lanl-ansi/Juniper.jl),
   **MIT**) o el que corresponda a la formulación.
5. **La capa agéntica se queda fuera del lazo**: compone el caso, explica el resultado y redacta el
   expediente. **El texto de razonamiento del LLM nunca llega a un actuador** — restricción
   invariante de esta KB desde la receta 46.

**Por qué es el mejor argumento comercial que tiene esta KB.** Dieciséis pases de confirmaciones
externas dicen **qué no vender** (NERC: *decision-support*; IEA: 23 % en tiempo real frente a 54 %
en planificación; NIST: comportamiento determinista, degradación elegante, operación a prueba de
fallos). Esta receta dice **cómo construir lo que sí se vende**, en el lenguaje que el sector ya
audita: **restricciones en un problema de optimización**. Frente a un comité de operación, el
enunciado pasa de «pondremos una validación delante del modelo» a **«el modelo no puede proponer un
punto infactible, porque vive dentro del despacho»**. Y encaja con el *sandbox* de **Ofgem**
(pase 17, EMEA), donde la compuerta deja de ser argumento de venta y pasa a ser **el entregable que
el regulador examina**.

🚨 **Límite de licencia que forma parte de la receta, no es una nota al pie.** `MathOptAI.jl` es la
variante **más limpia** de `lanl-ansi` (BSD-3 + reserva federal, **sin** indemnidad y **sin** deber
de marcado). Úsese **con JuMP directamente**. Si se acopla a la familia `PowerModels.jl`, arrastra
`InfrastructureModels.jl`, que **impone indemnidad al licenciatario** frente al Gobierno de EE. UU.
(T73/T74): en ese caso, **revisión legal antes de la propuesta**. Donde el diseño admita las dos
opciones, preferir **Sienna** (`PowerSimulations.jl`, BSD-3 limpio) como base de modelado.

### Receta 59

**Nombre:** Diligencia de licencia sobre el **árbol de dependencias**, no sobre el repo de entrada
**Región:** Global · **Entregable:** anexo de licencias de la propuesta

**Por qué es una receta y no una advertencia.** El pase 17 encontró el primer caso de esta KB en que
**el riesgo de licencia no está donde se mira**: `PowerModels.jl` no impone indemnidad, pero su
dependencia común `InfrastructureModels.jl` **sí**. Revisar el repo de entrada, aprobarlo y heredar
la obligación por transitividad es el modo de fallo **por defecto**, y ninguna herramienta SPDX lo
señala porque **ningún campo SPDX expresa una indemnidad**.

**Procedimiento, en el orden que funciona:**

1. **Manifiesto primero** (T46): `Project.toml`, `pyproject.toml`, `Cargo.toml`, `package.json`,
   `DESCRIPTION`, `pom.xml`. Una expresión SPDX en el manifiesto gana a la adivinanza.
2. **Enumerar el árbol**, no el repo. Para cada dependencia directa e indirecta, repetir el paso 1.
3. **Leer el texto completo de toda licencia que devuelva `NOASSERTION`**, y leerlo **hasta el
   final**: la clase ortográfica se resuelve en la **primera línea** (`BSD 3 Clause Licence` de
   CSIRO), pero la indemnidad de `InfrastructureModels.jl` está en el **último párrafo** (T75).
4. **Buscar cuatro términos** que ningún SPDX expresa y que cambian la propuesta:
   *indemnify* / *hold harmless*; prohibición de **entrenar modelos** con el código (T57);
   **deber de marcar** las modificaciones; y **conversión diferida** (BSL 1.1 — «hoy» y «en cuatro
   años» son respuestas distintas).
5. **Antes de excluir** un repo insignia por licencia, buscar su **fork de fundación** (T64:
   VOLTTRON `NOASSERTION` en el repo histórico, **Apache-2.0** en `eclipse-volttron/volttron-core`).
6. **Clasificar** cada pieza en: base a forkear / dependencia / dependencia con revisión legal /
   excluida. La frontera **MPL-2.0** (copyleft **por archivo**: `openSTEF`, familia `powsybl`) es
   «dependencia», nunca «base a forkear en silencio».

**Entregable.** Una tabla por *engagement* con: pieza · licencia **leída** (con tamaño en bytes y
primera línea) · obligaciones no-SPDX · clasificación. Es el anexo que evita que una obligación
contractual entre en un contrato de cliente sin que nadie la haya visto, y se construye **una vez
por stack**, no una vez por propuesta.
