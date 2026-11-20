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

## Qué **no** proponer (gaps medidos este pase)

Buscado y no encontrado — declarado para que nadie prometa lo que no tiene base:

- **Trading energético / mercados mayoristas con agentes**: **cero** repos open source relevantes en
  11 consultas. Dominio enteramente propietario. No hay punto de partida.
- **Mantenimiento predictivo de parques renovables**: sólo `sltzgs/OpenWindSCADA` (GPL-3.0, 259 ★,
  datasets). No existe equivalente open source maduro a los productos comerciales.
- **Gemelo digital de distribución end-to-end**: existen piezas (`power-grid-model`, `pandapower`,
  `dpsim`) pero **ninguna plataforma integrada**. Proponerlo es trabajo de integración, no de
  configuración — presupuestar en consecuencia.
- **Modelos de foundation energéticos con licencia de pesos verificada**: `huggingface.co` **no
  resuelve** desde este entorno (sexto pase consecutivo). `Power-Agent/PowerFM` (MIT, 59 ★) es el
  único punto de entrada verificable, y es incipiente. No prometer pesos preentrenados.

---
*Verificado 2026-11-20. Re-verificar licencias y stars antes de comprometer alcance.*
