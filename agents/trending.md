---
industry: energy
region: Global
updated: 2026-11-24
---

# 📈 Agentes trending — energy

> **Archivo APPEND-ONLY.** Cada pase añade una sección fechada arriba y conserva el historial
> debajo. No reescribir: el valor de este archivo es la serie temporal.

## 2026-11-24 — pase 19 (el inventario estaba sesgado por *forja*, no por vocabulario: 0 de 618 direcciones en GitLab; y un veredicto `other` de la API no es un hallazgo de licencia en ninguna de las dos direcciones)

**Cuarto pase del día sobre `energy`** (los pases 16, 17 y 18 empujaron contenido hoy a las 03:56Z,
04:59Z y 06:01Z). El control remoto-contra-rotación se ejecutó primero, por **octava vez con
rédito**: `rotation.json` leía `next: 10` mientras `energy-kb` ya tenía **tres** *commits* del
2026-11-24, así que los tres pases anteriores empujaron contenido y **ninguno avanzó la rotación**.
Este pase avanza la rotación en el mismo turno que el *push* de contenido.

### Lo agéntico nuevo de la semana en esta capa

| Pieza | Licencia | ★ | Push | Novedad |
|-------|----------|---|------|---------|
| [AI4REALNET/grid2evaluate](https://github.com/AI4REALNET/grid2evaluate) | **MPL-2.0** | 0 | **2026-11-03** | Arnés de **evaluación** de agentes sobre `Grid2Op`. Lo que faltaba entre «tenemos un agente de red» y «podemos medirlo antes de proponerlo» |
| [AI4REALNET/distributed-rl-gnn](https://github.com/AI4REALNET/distributed-rl-gnn) | **MIT** | 0 | 2026-10-30 | RL distribuido con GNN sobre la topología. La licencia más permisiva de la organización |
| [AI4REALNET/XLLM](https://github.com/AI4REALNET/XLLM) | **MPL-2.0** | 1 | 2026-05-24 | La única pieza **LLM** de la familia AINETUS: acopla optimización con criterio del operador |
| [AI4REALNET/T2.3_explaining_action_alternatives](https://github.com/AI4REALNET/T2.3_explaining_action_alternatives) | **MPL-2.0** | 0 | 2026-02-20 | Explicabilidad de la maniobra propuesta: la mitad exigible por el regulador |
| [AI4REALNET/distributed_rl](https://github.com/AI4REALNET/distributed_rl) | **MPL-2.0** | 0 | 2026-04-14 | Entregable D2.2, Politecnico di Milano |

**El hallazgo agéntico del pase no es una pieza, es una proporción.** La organización `AI4REALNET`
tiene **16 repositorios y sólo 5 con licencia utilizable**: once no llevan fichero de licencia o
declaran `NOASSERTION`. En un consorcio financiado por la UE la licencia se aplica **por
repositorio-entregable, no por organización**, y «está en LF Energy» no convierte un repo de paquete
de trabajo en dependencia (**T87**). Ninguna de las cinco pasa de 1 estrella: son el **arnés y la
explicabilidad** de la pila `Grid2Op` + `ExpertOp4Grid` + `OperatorFabric` que esta KB ya tiene, no
su punto de partida.

### El cero agéntico de LATAM: era de forja, y sigue bloqueado por licencia

El pase 16 encontró que *«el cero agéntico de LATAM era del idioma»*. Este pase midió la otra
hipótesis —**que era de forja**— y la respuesta es **sí, y no sirve**. Fuera de GitHub hay
suministro de origen LATAM:

| Pieza | Forja | Veredicto de licencia | Estado |
|-------|-------|-----------------------|--------|
| [OpenREiD](https://sourceforge.net/projects/openreid/) | **SourceForge** | **Ninguna declarada** (`licenses: []` en la REST de SourceForge) | Activo: creado 2025-10-21, ficheros al 2026-10-05. Instituto de Energía Eléctrica, **UNSJ-CONICET, San Juan, Argentina**. *Plugin* QGIS para modelar y analizar redes de distribución sobre OpenDSS. **No proponible** |
| [openpy-dsse](https://pypi.org/project/openpy-dsse/) | **PyPI** | `License :: Other/Proprietary License`; el campo `license` contiene literalmente la cadena `"LICENSE"` | v0.1.4. Estimación de estado de red de distribución modelada en OpenDSS. **No proponible** |
| [jlara6/OpenPy-DSSE](https://github.com/jlara6/OpenPy-DSSE) | GitHub | `NOASSERTION` | 14 ★, *push* **2023-04-27**. Tres años y medio sin movimiento |

**La conclusión comercial no cambia; cambia la razón.** Durante varios pases esta KB registró
«cero repos agénticos de origen LATAM» como una medida de **ausencia de suministro**. Es más preciso
decir: hay suministro, está en SourceForge y PyPI, y está **bloqueado por licencia** — igual que
`idiap/pydhn`, bloqueado por licencia y no por calidad. Para un *engagement* LATAM el efecto
práctico es idéntico (no hay base sobre la que presupuestar), pero el camino de salida es otro: **es
una conversación con un instituto identificable —el IEE de la UNSJ-CONICET— sobre relicenciar, no un
desarrollo desde cero.** Eso es accionable; «no existe» no lo era.

### Advertencia de método que este pase se aplicó a sí mismo

Este pase empezó buscando huecos con vocabulario **inglés** (`district heating`, `carbon
accounting`, `subsurface`, `nuclear`) y produjo **cuatro falsos huecos**: los cuatro están cubiertos
en esta KB, que está escrita **en español** (`redes de calor de distrito`, `intensidad de carbono`,
`subsuelo`, `nuclear`). La KB ya clasificaba `idiap/pydhn` con más precisión que el buscador. El
pase 16 descubrió que los hallazgos tienen un sesgo de idioma; este pase descubre que **las
auditorías también lo tienen**, y es más peligroso, porque un falso hueco se publica como novedad.
Ver **T88**.

## 2026-11-24 — pase 18 (el cero agéntico de la capa meteorológica, medido con cuatro consultas; y el envoltorio MCP permisivo que no sanea una fuente restringida)

**Tercer pase del día.** El pase abrió la capa de modelo meteorológico completa
(`repos/foundations.md` §1–§5, **63 direcciones nuevas**) y la pregunta agéntica tiene una respuesta
clara y nueva: **en esta capa el componente físico está terminado y la orquestación no existe.**

### Novedades agénticas de la semana en esta capa

| Pieza | Licencia | ★ | Push | Novedad |
|-------|----------|---|------|---------|
| [weather-mcp/weather-mcp](https://github.com/weather-mcp/weather-mcp) | **MIT** | 58 | **2026-11-24** | *Push* del propio día del pase. 17 *tools*; el servidor MCP meteorológico más traccionado de 276 medidos |
| [cyanheads/open-meteo-mcp-server](https://github.com/cyanheads/open-meteo-mcp-server) | **Apache-2.0** | 14 | 2026-11-18 | Geocodificación, pronóstico global, clima histórico, marino y calidad de aire sobre `open-meteo` |
| [PredictionMarketTrader/openthomas](https://github.com/PredictionMarketTrader/openthomas) | **MIT** | 25 | 2026-09-12 | Agente de pronóstico **auto-mejorable** con P&L real en mercados de predicción |

### El cero, con forma

| Consulta | Total | Techo | Distribución tras el primero |
|----------|-------|-------|------------------------------|
| `agent weather forecasting llm` | 69 | **25 ★** | 5 · 4 · 4 · 2 · 2 · 0 · 0 |
| `agentic climate data analysis` | 21 | **2 ★** | 0 · 0 · 0 (uno ya archivado, AGPL-3.0) |
| `mcp server weather forecast` | 276 | **58 ★** | 39 · 34 · 14 · 10 · 7 · 7 · 6 |
| `mcp server energy grid` | 12 | **7 ★** | 3 · 1 · 1 · 0 |

Cuatro consultas, cuatro techos de dos cifras bajas. **No hay un solo agente de procedencia
institucional sobre pronóstico numérico del tiempo**, mientras los modelos que habría que orquestar
suman miles de estrellas y están mantenidos por ECMWF, NVIDIA, Google Research y DeepMind. Es la
asimetría inversa a la que esta KB mide en operación de red (donde sobran agentes y falta el
componente físico auditable).

### El hallazgo de licencia del pase, en su versión agéntica

**Un envoltorio MCP permisivo no sanea una fuente restringida.**
`cyanheads/open-meteo-mcp-server` es **Apache-2.0** de verdad: su código es libre. Llama a
`api.open-meteo.com`, cuyo servicio público es *free for non-commercial use* y cuyo servidor es
**AGPL-3.0**. El inventario de dependencias de un piloto mostrará `Apache-2.0` y **no mostrará la
restricción que de hecho aplica al producto**. Esta KB ya tenía el aviso sobre `open-meteo` desde el
pase 5; lo nuevo es que **la capa MCP lo vuelve invisible**, porque desplaza la licencia que se
inspecciona de la fuente al envoltorio.

Sustitutos permisivos, ya inventariados en este pase y con región asignada:
[ecmwf/ecmwf-opendata](https://github.com/ecmwf/ecmwf-opendata) (Apache-2.0, 342 ★, EMEA) y
[blaylockbk/Herbie](https://github.com/blaylockbk/Herbie) (MIT, 801 ★, North America).
**Y el hueco construible queda nombrado: no existe ningún servidor MCP sobre los datos abiertos de
ECMWF.**

### Dos exclusiones duras que afectan a cualquier arquitectura agéntica de esta capa

1. **`198808xc/Pangu-Weather`** (1.402 ★, el modelo de IA meteorológica más traccionado de origen
   APAC): **sin fichero de licencia** en `main` ni `master`; el README declara los pesos **CC
   BY-NC-SA 4.0** y escribe en negrita *«The commercial use of these models is forbidden.»*
   🚫 **No es un *tool* invocable en un producto de cliente.**
2. **`microsoft/aurora`** (1.049 ★, código **MIT** verificado byte a byte): el fabricante declara en
   el README que el código *«has not been developed nor tested for non-academic purposes»* y nombra
   *«critical infrastructure operations»* entre los riesgos de uso consecuente. ⚠️ **Permitido por
   licencia, desaconsejado por el autor para el uso exacto que propondríamos.** Se inventaría como
   *benchmark*, no como componente.

**La regla general que sale de aquí, y vale para toda la KB: cuando el artefacto que se despliega es
un modelo entrenado, hay que leer la licencia de los PESOS, y está en el README** (T78). Para los
*tools* que un agente invoca, el campo SPDX del repo es el dato equivocado.

## 2026-11-24 — pase 17 (el puente ML→optimización que *es* la compuerta de esta KB, escrito en código; y el agente energético de una agencia científica nacional)

**Titular del pase: la restricción de arquitectura de esta KB —«no se vende control autónomo, se
vende la compuerta»— tiene desde este pase una *implementación de referencia* y no sólo recetas
propias.** `MathOptAI.jl` del Los Alamos National Laboratory **empotra un predictor de ML ya
entrenado dentro de un problema de optimización** de JuMP/ExaModels. El modelo aprendido deja de
ser un actuador que propone acciones y pasa a ser **una restricción más dentro del modelo físico y
de mercado**, que el *solver* satisface o declara infactible. Es la receta 49 de esta KB
(«el agente propone un delta, la compuerta lo acepta o lo rechaza contra el esquema del sector»)
pero resuelta **en la misma formulación matemática**, no con dos sistemas y un contrato entre ellos.

| Agente / puente | Licencia | ★ | Push | Región de origen | Qué hace |
|-----------------|----------|---|------|------------------|----------|
| [lanl-ansi/MathOptAI.jl](https://github.com/lanl-ansi/MathOptAI.jl) | ⚠️ BSD-3 + *riders* de contrato federal (byte-read, 2.293 B — ver taxonomía abajo) | 90 | 2026-08-27 | North America | Empotra predictores de ML entrenados **dentro** de JuMP/ExaModels: la salida del modelo queda sujeta a las restricciones del sistema |
| [csiro-energy-systems/gen_agents_localLLM_on_Setonix](https://github.com/csiro-energy-systems/gen_agents_localLLM_on_Setonix) | **Apache-2.0** (byte-read, 11.334 B) | 2 | 2025-04-24 | APAC | Agentes generativos con **LLM local** sobre **Setonix**, el supercomputador del Pawsey Centre. Primer repo agéntico de una **agencia científica nacional** en esta KB |

**Por qué `MathOptAI.jl` importa más que sus 90 ★.** Esta KB lleva dieciséis pases acumulando
confirmaciones *externas* de que el sector no comprará control autónomo (criterio propio → NERC →
IEA con número, 23 % vs 54 % → NIST, borrador de norma → ONS, producto embarcado → PSR). Todas esas
confirmaciones dicen **qué no vender**. `MathOptAI.jl` es la primera pieza inventariada que dice
**cómo construir lo que sí se vende**, y lo dice en la forma que el sector ya sabe auditar: un
problema de optimización con restricciones. Para un *engagement*, el argumento cambia de
«pondremos una validación delante del modelo» a «el modelo **no puede** proponer un punto
infactible, porque vive dentro del despacho».

⚠️ **Y aquí está la trampa del pase, que es de licencia y no de ingeniería.** `MathOptAI.jl` es de
`lanl-ansi`, y la familia de licencias de ese laboratorio **no es BSD-3 limpio**: ver la sección de
`repos/trending.md` de este mismo pase. `MathOptAI.jl` es la variante **más limpia** de la familia
(BSD-3 + reserva de derechos del Gobierno de EE. UU., **sin** obligación de indemnidad y **sin**
deber de marcado), de modo que es la pieza del ecosistema LANL **que mejor se propone**. Pero su
dependencia natural dentro de la familia PowerModels, `InfrastructureModels.jl`, **sí** lleva
indemnidad. Proponer `MathOptAI.jl` con JuMP directamente: sí. Proponerlo acoplado a PowerModels
sin revisión legal: no.

### El cero que este pase NO rompe, y conviene decirlo

No aparecieron **agentes de operación de red** nuevos y proponibles. El sexto cero consecutivo en
esa categoría se mantiene, y por primera vez con una explicación que no es del instrumento sino
**del mercado**: el 23 % de operadores de Asia Oriental que usan IA en tiempo real (IEA, pase 15),
la guía de la NERC que la fija como *decision-support* (pase 14) y el borrador del NIST (pase 16)
describen un sector que **no está comprando ese agente**. El cero es coherente con la demanda.

## 2026-11-24 — pase 16 (el servidor MCP oficial de un operador nacional, y es Apache-2.0; el cero agéntico de LATAM era del idioma)

**Titular del pase: el ONS brasileño publica el servidor MCP de su portal de datos abiertos, con
licencia Apache-2.0, y la arquitectura es exactamente la que esta KB propuso como receta 49.**

[`ONSBR/TIAGO-Dados-Abertos`](https://github.com/ONSBR/TIAGO-Dados-Abertos) — **Apache-2.0**
(`LICENSE` leído byte a byte: **11.357 B**, el tamaño canónico exacto del texto completo de Apache
2.0), **29 ★**, último push **2026-11-20**, publicado en PyPI como `mcp-tiago-dados-abertos`, con
workflow de tests en CI. Es el **servidor MCP oficial de `dados.ons.org.br`**, el portal de datos
abiertos del Operador Nacional do Sistema Elétrico.

Lo que importa no es que exista: es **cómo está construido**. Del propio README:

- Una **capa semántica en YAML** declara, por dataset, el schema, las unidades y las agregaciones
  válidas. El estándar es **ODCS v3.1.0** (Open Data Contract Standard, de `bitol-io`).
- **El servidor rutea, valida y ejecuta; el modelo del cliente escribe el SQL.**
- **«Nenhum modelo de linguagem roda no servidor»** — ningún LLM corre en el servidor. Entrega
  catálogo y contratos, valida, ejecuta, y *«tudo o que devolve é determinístico e rastreável ao
  contrato»*.
- Cuando no puede probar un dato, **declara desconocido en vez de deducir**.
- Motor de ejecución: **DuckDB**.

> **ESTO ES LA RECETA 49 DE ESTA KB, EN PRODUCCIÓN, ESCRITA POR UN TSO.** En el pase 15 esta KB
> propuso —como diseño propio, sin precedente— un copiloto de modelo de red con una **compuerta de
> validación** que acepta o rechaza la propuesta del agente contra el esquema del propio sector
> antes de que toque nada vivo, para que «automatización» y «no control» dejaran de estar en
> conflicto. Tres pases después aparece el mismo patrón implementado, con otro estándar
> (**ODCS en vez de SHACL**) y otro motor (**DuckDB**), por el operador del sistema brasileño.
> **Es la séptima confirmación independiente de la restricción de arquitectura de esta KB y la
> primera que está EMBARCADA en un producto, no en un análisis, una norma o un paper.**

Los cinco modos de fallo que el README nombra son el argumento de venta de la compuerta, y son
citables tal cual ante un cliente: elegir el dataset equivocado (el portal publica recortes
parecidos con granularidades distintas, «la consulta corre, devuelve un número plausible, y responde
otra pregunta»), escribir SQL contra un schema imaginado, **errar la unidad (`MWmed` no es `MWh`, y
la diferencia no aparece en el resultado)**, agregar lo que no se agrega (sumar una columna que ya es
promedio duplica el valor «sin error ninguno»), y perder la procedencia.

### Cierra el ítem abierto 15-R2, y lo cierra el vocabulario, no el esfuerzo

El pase 15 dejó anotado: *«sigue habiendo CERO repos agénticos/LLM de origen LATAM, y el vocabulario
agéntico es/pt NO se re-corrió en corto»*, marcándolo como **el cero falso más probable de la KB**.
Lo era. La consulta que lo rompió tiene **cuatro palabras en portugués sobre nombres propios**:

```
gh api -X GET search/repositories -f q="ons dados abertos mcp"
→ total_count: 1
```

Un resultado. El correcto. **El cero anterior era del instrumento, no del mundo** — tercera vez que
T58 se confirma en esta KB y la primera en que el idioma, no la longitud, era la variable.

> **T63 — PARA LATAM, LA CONSULTA CORTA TIENE QUE SER EN EL IDIOMA DE LA INSTITUCIÓN.** Los barridos
> agénticos anteriores de esta KB se corrieron en inglés sobre términos descriptivos. El activo
> estaba publicado por una institución que nombra sus cosas en portugués (`dados abertos`). Antes de
> declarar un cero regional: **probar el nombre propio del artefacto en el idioma del regulador o
> del operador.**

### Y detrás del MCP había una organización entera de 13 repos, ninguno inventariado

Repetición literal de la lección del pase 8 («había una organización entera de ~30 repos permisivos
catalogada en uno solo»), ahora en LATAM y en el operador del sistema. **Las 13 direcciones de
`ONSBR` estaban ausentes de un inventario de 500.** Licencias leídas byte a byte:

| Repo | Licencia (byte-read) | ★ | Último push | Qué es |
|------|----------------------|---|-------------|--------|
| [ONSBR/TIAGO-Dados-Abertos](https://github.com/ONSBR/TIAGO-Dados-Abertos) | **Apache-2.0** (11.357 B) | 29 | 2026-11-20 | Servidor MCP oficial del portal de datos abiertos |
| [ONSBR/smapOnsR](https://github.com/ONSBR/smapOnsR) | **MIT** (vía `DESCRIPTION`) | 13 | 2026-07-22 | Implementación en R del modelo hidrológico **SMAP/ONS** |
| [ONSBR/PrevCargaDESSEM](https://github.com/ONSBR/PrevCargaDESSEM) | **MIT** (vía `DESCRIPTION`) | 7 | 2025-03-27 | Modelo de **previsión de carga**; copyright **CEPEL + ONS** |
| [ONSBR/HidrViewer](https://github.com/ONSBR/HidrViewer) | **MIT** (1.069 B) | 7 | 2026-07-16 | Visualización y detección de formas en series hidrológicas |
| [ONSBR/prevcarga](https://github.com/ONSBR/prevcarga) | **Apache-2.0** (11.374 B) | 3 | **2026-11-23** | PrevCarga-DESSEM, reescritura activa (push de anteayer) |
| [ONSBR/TIAGO-Transcricao](https://github.com/ONSBR/TIAGO-Transcricao) | **Apache-2.0** (11.373 B) | 3 | 2026-09-09 | Rama de transcripción de la familia TIAGO |
| [ONSBR/ONS.Hidrologia.Dadosabertos.API](https://github.com/ONSBR/ONS.Hidrologia.Dadosabertos.API) | MIT | 3 | 2024-08-20 | API de hidrología sobre datos abiertos |
| [ONSBR/deck-api](https://github.com/ONSBR/deck-api) | **MIT** (1.069 B) | 1 | 2023-10-05 | API REST sobre los *decks* de los modelos de planificación |
| [ONSBR/DadosAbertos](https://github.com/ONSBR/DadosAbertos) | ⛔ **sin licencia** | 43 | 2026-08-06 | El repo con **más estrellas de la organización, y el único inutilizable** |

Las 13 direcciones están verificadas vivas con `git ls-remote`.

> **T61 — UN `LICENSE` DE 45 BYTES NO ES UNA LICENCIA AUSENTE: ES LA CONVENCIÓN DE R.** `smapOnsR`
> (45 B) y `PrevCargaDESSEM` (95 B) devuelven `NOASSERTION` por API y su `LICENSE` contiene
> **únicamente** `YEAR:` y `COPYRIGHT HOLDER:`. No falta nada: es el idioma `License: MIT + file
> LICENSE` de los paquetes de R, que **exige** que ese archivo contenga sólo eso. La licencia real
> está en `DESCRIPTION`, y en los dos casos es **MIT**. Un archivo de licencia sospechosamente
> diminuto hay que resolverlo en `DESCRIPTION` (R) o en el manifiesto del lenguaje, no descartarlo.
> Sexta vez que `NOASSERTION` resulta falso negativo en esta KB, y la primera por este mecanismo.

### La confirmación LATAM que no es un repo: PSR describe la misma arquitectura

Un artículo de **PSR** (`psr-inc.com`, julio de 2026) propone un agente que interactúa con un modelo
hidrotérmico **únicamente a través de capacidades de dominio controladas y tipadas**, y deja escrito
que **el agente no reemplaza al solver de optimización**. Es la misma frontera que TIAGO implementa y
que esta KB sostiene desde el pase 1, formulada por una consultora brasileña del sector. Nota de
procedencia: es un **artículo de opinión técnica**, no una norma ni un despliegue — vale como
precedente citable de que el patrón es el consenso regional, no como referencia normativa.

### Exclusiones duras de este pase (ambas con tracción)

- ⛔ [`lhg96/smartEMS-MultiAgent-Demo`](https://github.com/lhg96/smartEMS-MultiAgent-Demo)
  (`NOASSERTION` por API, 6 ★, origen **Corea**). `LICENSE` de **2.699 B** cuya primera línea no
  vacía es **`Custom License Agreement`**: uso personal, educativo y de investigación permitido,
  **uso comercial prohibido sin licencia comercial separada** (contacto por email), explícitamente
  incluyendo *«integración en productos o servicios comerciales»*, *«uso en producción para
  operaciones de negocio»* y *«despliegue como parte de actividades generadoras de ingresos»*.
  **Inutilizable para Globant.**
- ⛔ [`d2rojas/LLMs-Agents-For-SmartGrids-Code`](https://github.com/d2rojas/LLMs-Agents-For-SmartGrids-Code)
  (5 ★): código del caso de estudio *«LLMs and Agentic AI Systems for Smart Grids»*. **Sin ningún
  artefacto de licencia** en `main`/`master`/`develop` × 4 nombres de archivo. Citable como paper,
  no incorporable.

> **T62 — LA FRASE DE CONCESIÓN DE MIT NO SÓLO SE PREFIJA: SE MUTA POR DENTRO.** El pase 15 (T56)
> encontró una licencia propietaria que **precedía** la frase de MIT con su propio título. Esta
> **la reescribe**: *«Permission is hereby granted, free of charge, to any person obtaining a copy of
> this software and associated documentation files (the "Software"), to use, copy, modify, and
> distribute the Software **for personal, educational, and non-commercial purposes**»*. Es la frase
> de MIT con la cláusula comercial insertada en el medio, de modo que **un detector por similitud de
> frase la puntúa aún más alto que el impostor del pase 15**. Los dos discriminadores de T56
> siguieron funcionando sin cambios: primera línea no vacía (`Custom License Agreement`) y tamaño
> (**2.699 B** frente a ~1,07 kB de MIT; el impostor del pase 15 medía 2.646 B, **53 bytes de
> diferencia** — la familia tiene un tamaño característico).

### El techo agéntico de esta KB es real, y esta vez se midió con el instrumento correcto

El pase 15 dejó la regla de que **cualquier KB de esta flota que reporte un techo de descubrimiento
debe re-probar primero con UNA PALABRA sobre un nombre propio**. Se hizo: seis barridos sobre nombres
propios de artefactos y protocolos (`2030.5 der`, `sunspec`, `gridlab-d`, `openfast wind`,
`energyplus openstudio`, `iec 62325`, `powsybl`, `volttron`) más cuatro con filtro de recencia
(`pushed:>2026-06-01`/`>2026-08-01`/`>2026-09-01`) sobre la capa agéntica.

**Resultado: los cinco ancla agénticos que devolvieron los barridos ya estaban todos inventariados**
— `Power-Agent/PowerMCP` (242 ★), `Power-Agent/PowerFM`, `LBNL-ETA/EnergyPlus-MCP` (132 ★),
`TimeCopilot/timecopilot` (643 ★), `idfkit/idfkit-mcp`. En la capa de protocolo, **16 de 28
candidatos ya estaban held**. Lo nuevo en agéntico es cola larga de 0–6 ★, consistente con la
medición del pase 10 (33 repos en siete semanas, el mejor con 7 ★).

> **El techo agéntico global de esta KB está confirmado; el que era falso era el regional.** La
> conclusión operativa no es «buscar más», es **buscar en otro idioma y por institución**: el único
> hallazgo de primer orden del pase salió de una consulta de cuatro palabras en portugués.

### Cola larga agéntica nueva, con licencia leída byte a byte

| Repo | Licencia (byte-read) | ★ | Push | Nota |
|------|----------------------|---|------|------|
| [cyanheads/eia-energy-mcp-server](https://github.com/cyanheads/eia-energy-mcp-server) | **Apache-2.0** (10.846 B) | 3 | 2026-11-15 | MCP sobre la **EIA API v2**. `NOASSERTION` por API, Apache por byte-read |
| [HPML6998-S26-Team13/hpml-assetopsbench-smart-grid-mcp](https://github.com/HPML6998-S26-Team13/hpml-assetopsbench-smart-grid-mcp) | **MIT** (1.111 B) | 1 | 2026-07-01 | **SmartGridBench**: benchmark de mantenimiento de transformadores con *tool-calling*. Categoría nueva: **banco de pruebas agéntico sectorial** |
| [alanmossinger/ai-enablement-proof](https://github.com/alanmossinger/ai-enablement-proof) | **MIT** (1.071 B) | 1 | 2026-11-11 | Agente autónomo **«gobernado»** para fiabilidad de red en EE. UU. El encuadre de gobernanza es el dato, no el código |
| [lubosstrejcek/victron-vrm-mcp](https://github.com/lubosstrejcek/victron-vrm-mcp) | **MIT** | 5 | 2026-11-13 | MCP sobre la API cloud **Victron VRM** (solar, batería, red) |
| [lubosstrejcek/victron-tcp](https://github.com/lubosstrejcek/victron-tcp) | **MIT** (1.070 B) | 7 | 2026-11-02 | MCP sobre dispositivos **Victron GX** en tiempo real |
| [KoshiirRa/midgley](https://github.com/KoshiirRa/midgley) | **Apache-2.0** (10.172 B) | 2 | 2026-11-23 | Multi-agente LLM de pronóstico de precio de combustible (RBOB mayorista y retail) |

Patrón nuevo y útil: **el MCP de dispositivo de fabricante** (Victron ×2, `emporiaenergy/emporia-mcp`
sin licencia). Es la vía de entrada agéntica al activo doméstico que no pasa por la nube del
fabricante, y complementa la receta 46.

> **T60 — `OR` EN UNA CONSULTA DE `search/repositories` LA DETONA.** `substation OR scada llm
> pushed:>2026-06-01` devolvió **422.652 resultados** encabezados por `ollama`, `firecrawl`,
> `langchain` y `transformers`: el `OR` disuelve el anclaje de dominio y la consulta cae en el corpus
> agéntico global. La misma intención en dos consultas separadas devuelve 9 y 59 resultados, todos
> del dominio. **`OR` no es un ensanchador, es un destructor de precisión** — mismo fallo de clase
> que el término `agentic grid` del pase 15, por otra causa.

---

## 2026-11-21 — pase 15 (una licencia propietaria que empieza con la frase literal de MIT, y el número que la KB llevaba ocho pases pidiendo: 23% vs 54%)

**Titular del pase: el incipit de MIT no identifica una licencia.**
[`Zara-Toorox/Solar-Forecast-ML`](https://github.com/Zara-Toorox/Solar-Forecast-ML) (**318 ★**, el
repo de pronóstico solar con más tracción aparecido en el barrido) devuelve `NOASSERTION` por API.
Su archivo `LICENSE` arranca con **`PROPRIETARY AND NON-COMMERCIAL LICENSE`** y, dos líneas después,
contiene **palabra por palabra** la frase con la que abre MIT: *"Permission is hereby granted, free
of charge, to any person obtaining a copy of this software and associated documentation files (the
'Software')"*. El detector de esta KB —que busca esa frase— **lo clasificó como MIT**. Lo era todo
menos MIT: uso comercial prohibido, y una **cláusula 4 de restricción de entrenamiento de IA** que
prohíbe usar el código para entrenar o afinar modelos sin permiso escrito.

> **T56 — EL INCIPIT DE MIT NO ES UN IDENTIFICADOR DE LICENCIA.** Una licencia propietaria puede
> abrir su cláusula de concesión con la frase exacta de MIT y restringir todo después. Los dos
> discriminadores de coste cero, **en este orden**: (1) **la primera línea no vacía** del archivo;
> (2) **el tamaño** —MIT real mide ~1,05–1,09 kB; este medía **2.646 B**. Buscar la frase de
> concesión *en cualquier parte* del archivo es el error; hay que leer **el título**.
>
> **T57 — CLÁUSULA DE PROHIBICIÓN DE ENTRENAMIENTO DE IA: clase nueva.** Aparece una licencia que
> prohíbe explícitamente usar el código para entrenar o afinar LLM o sistemas de generación de
> código. No es un problema de redistribución sino **de uso interno de un estudio de IA**, y ningún
> campo SPDX la expresa. Hay que leerla.

### Lo que sí entra: cuatro agentes nuevos, los cuatro con licencia leída byte a byte

| Nombre | Licencia | Descripción | Stars | Forks | Último push | Región origen |
|--------|----------|-------------|-------|-------|-------------|---------------|
| [RedaElMakroum/agentic-ai-hems](https://github.com/RedaElMakroum/agentic-ai-hems) | MIT (leída, 1.071 B) | *Agentic AI Home Energy Management System*: framework de LLM para gestión energética residencial. El primer agente **doméstico** explícito de la KB | 18 | 4 | 2025-11-05 | EMEA |
| [IBM/OpenDsStar](https://github.com/IBM/OpenDsStar) | Apache-2.0 (leída, 11.356 B) | Implementación abierta del agente **DS-Star**: sustituye el paso por archivos del agente de ciencia de datos. Útil como capa de análisis sobre datos de red | 25 | 3 | 2026-05-10 | North America |
| [maxoliverbr/eia-api-ts](https://github.com/maxoliverbr/eia-api-ts) | MIT (leída, 1.066 B) | Wrapper tipado de la **EIA API v2** construido **explícitamente para uso agéntico**. Es la pieza de acceso al dato público de energía de EE. UU. que faltaba | 11 | 2 | 2026-11-19 | North America |
| [TU-Delft-AI-Energy-Lab/MARL-iDR](https://github.com/TU-Delft-AI-Energy-Lab/MARL-iDR-Multi-Agent-Reinforcement-Learning-for-Incentive-based-Residential-Demand-Response) | MIT (leída, 1.078 B) | RL multiagente para respuesta a la demanda residencial **basada en incentivos**. Paper + código; no mantenido desde 2023 pero es la referencia del esquema | 50 | 9 | 2023-08-02 | EMEA |

### El dato de adopción que esta KB llevaba ocho pases pidiendo

El *open item* de la IEA **"Energy and AI in East Asia"** —abierto desde el pase 13— queda
**parcialmente cerrado, por snippet y no por lectura directa** (`iea.blob.core.windows.net` **no
resuelve** desde este entorno; ver "Instrumento"). El número:

> **Sólo el 23% de los operadores de red de Asia Oriental usa IA en operación en tiempo real,
> frente al 54% en planificación del desarrollo de la red** — y la IEA atribuye la diferencia
> explícitamente a **preocupaciones de fiabilidad**.

Por qué es el dato más útil de la serie para la capa agéntica: la KB venía **imponiendo** la
restricción de arquitectura (agente como apoyo a la decisión, nunca controlador) y el pase 14 la
encontró **publicada por NERC**. Esto la **cuantifica desde el lado de la demanda**: el mercado ya
eligió, y eligió planificación. La consecuencia comercial es direccional y se puede decir en una
reunión: **en APAC se vende agente de planificación, no de control en tiempo real**, y el 23% no es
un techo de madurez del cliente sino **su política de riesgo**.

### Confirmación de tercer canal de la restricción de arquitectura

Guía de práctica para utilities (NA, secundaria): los agentes **no entran en la zona de control**
—SCADA, EMS, funciones de control de ADMS, despacho DERMS, automatización de subestación, PLC y
sistemas de seguridad—, y ahí **no tienen herramienta, ni credencial, ni ruta de red**;
credenciales de **sólo lectura** por defecto y rutas de revocación. Es la tercera vía independiente
que llega a la misma frontera: receta de la KB (propia) → NERC (regulador, pase 14) → guía de
práctica + 23% de la IEA (mercado, este pase). **Deja de ser una opinión de arquitectura.**

### Exclusiones de este pase (las tres llegaron como `NOASSERTION` y las tres tienen tracción)

| Repo | ★ | La API dice | El archivo dice | Veredicto |
|------|---|-------------|-----------------|-----------|
| [u9n/dlms-cosem](https://github.com/u9n/dlms-cosem) | 124 | `NOASSERTION` | **Business Source License 1.1** en `pyproject.toml` + clasificador `License :: Other/Proprietary`. El *Additional Use Grant* prohíbe el "Competing Use", que incluye **"exponer las API del Licensed Work"** | ❌ **No es open source.** Y era el candidato DLMS/COSEM con más tracción: para una consultoría que construya producto de medición para una utility, "competing use" es exactamente el riesgo |
| [Zara-Toorox/Solar-Forecast-ML](https://github.com/Zara-Toorox/Solar-Forecast-ML) | 318 | `NOASSERTION` | `PROPRIETARY AND NON-COMMERCIAL LICENSE` (2.646 B) + prohibición de entrenamiento de IA | ❌ **Exclusión dura** (ver T56/T57) |
| [GreatTM/PowerBiMIP](https://github.com/GreatTM/PowerBiMIP) | 42 | `NOASSERTION` | Aviso corto de 1.067 B: "academic and non-commercial research purposes only", Southeast University. Push **de hoy** | ❌ Misma forma que OpenCDA en la KB de automotive: activo, reciente, **no utilizable** |
| [ValentinRigoni/Open-DSOPF](https://github.com/ValentinRigoni/Open-DSOPF) | 80 | `NOASSERTION` | **Ningún artefacto de licencia** (6 nombres × 3 ramas, todos 404) | ❌ Sin concesión expresa: no se puede construir sobre él |

**Nota sobre T46 (manifest-first), que paga por tercera vez:** `dlms-cosem` sólo se delata leyendo
`pyproject.toml`. La BSL 1.1 es la **quinta** clase no-OSI que esta KB encuentra en la capa
prosumer/medición, después de fair-source, PolyForm no comercial, revocable y permisiva-bespoke
(T47). Es la más peligrosa de las cinco porque **se confunde con open source** y porque su
conversión diferida hace que "hoy" y "en cuatro años" tengan respuestas distintas.

### Instrumento

- `iea.blob.core.windows.net` **no resuelve** desde este entorno: el informe de la IEA sigue **sin
  leerse byte a byte** y todo número suyo es **de snippet por construcción**. El *open item* se
  degrada de "sin leer" a "resumido por fuente secundaria", no a "cerrado".
- **`gh api repos/<owner>/<repo>` está denegado por el alcance de la sesión**, mientras
  `gh api search/repositories` y `raw.githubusercontent.com` **sí funcionan**. Consecuencia
  práctica: **la rama por defecto no se puede consultar**, así que el sondeo de licencia debe
  iterar `main`/`master`/`develop` a ciegas. Un `NO ARTEFACT` obtenido por la vía de `gh api repos`
  es un fallo de permiso disfrazado de hallazgo — así se perdió un barrido entero este pase.
- **Término de búsqueda inutilizable, clase ya conocida:** `agentic grid` → **3.425 resultados** de
  sensores de Unity, tarjetas "bento grid" y bots de *grid trading*. "grid" sin contexto de dominio
  no discrimina. Confirma T47: **el discriminador que funciona es el nombre propio de un artefacto
  técnico** (`entso-e`, `cim cgmes`, `opendss`, `aneel`, `iec61850`), no el adjetivo "agentic".

## 2026-11-21 — pase 14 (el regulador publica la restricción de arquitectura; y el "cero de cumplimiento NERC CIP" resulta ser del instrumento)

**Titular del pase: por primera vez el hallazgo de agentes viene del regulador, no de GitHub.** La
guía de **NERC** establece que la IA en el sistema eléctrico debe ser **apoyo a la decisión, no
controlador autónomo**. Es palabra por palabra la restricción que las recetas de esta KB ya
imponían; lo que cambia es que deja de ser una buena práctica del proveedor y pasa a ser **la
lectura publicada del regulador de referencia de NA**.

**Confirmación cruzada del cero más persistente de esta KB.** La IEA, citada por el ADB (jun-2026),
afirma que *la adopción de IA sigue siendo limitada en la operación de red crítica para el sistema*
aun donde el valor es claro. Esta KB midió ese cero **siete u ocho pases seguidos contando repos en
GitHub**. Ahora hay **dos mediciones independientes por canales distintos** —oferta y demanda— que
apuntan al mismo sitio. Eso convierte el cero en un hecho del sector y no en un límite del método.

**El cero que sí era del instrumento.** Aplicada la lección de la KB hermana de automotive (*las
consultas largas de `search/repositories` devuelven un cero literal porque hacen AND de todos los
términos sobre nombre/descripción/topics*), el registro *"cero herramientas de cumplimiento NERC CIP
frente al plazo de diciembre de 2026"* se re-midió con `topic:nerc-cip` → **21 repos**. La
conclusión comercial, sin embargo, apenas se mueve: **son plantillas y checklists, no herramientas**,
y ninguno pasa de 23 ★.

| Pieza | Repo | Licencia | ★ / forks / issues | Push | Qué es |
|-------|------|----------|--------------------|------|--------|
| Política de cumplimiento ejecutable | [ynotbhatc/rego_policy_libraries](https://github.com/ynotbhatc/rego_policy_libraries) | **Apache-2.0** (byte-read 11.357 B) | 23 / 2 / **17** | 2026-11-20 | OPA Rego v1: CIS, DISA STIG, NIST, **incluye NERC**. No específico de energía |
| Registro de decisiones auditable | [mizcausevic-dev/grid-decision-record-audit-stream](https://github.com/mizcausevic-dev/grid-decision-record-audit-stream) | **MIT** | 0 / — / — | 2026-10-31 | **Eventos de decisión de IA encadenados por hash** para auditoría NERC. Se recomienda **el patrón**, no el repo |
| *Evidence bundle* CIP | [mizcausevic-dev/nerc-cip-readiness-evidence-bundle](https://github.com/mizcausevic-dev/nerc-cip-readiness-evidence-bundle) | **MIT** | 1 / — / — | 2026-05-31 | Perfil CIP-002 → CIP-014 + TSA SD-2021-02C |
| Checklists CIP | [gridsafetechnology-tech/nerc-cip-checklists](https://github.com/gridsafetechnology-tech/nerc-cip-checklists) | **MIT** | 0 / — / — | 2026-11-07 | CIP-002, CIP-003-9 *low impact*, CIP-010 en YAML |
| *Crosswalk* regulatorio APAC | [Johnbjoseph-cybersec/india-ot-regulation-crosswalk](https://github.com/Johnbjoseph-cybersec/india-ot-regulation-crosswalk) | **MIT** | 0 / — / — | 2026-11-12 | **CEA India, *Cyber Security in Power Sector Regulations 2026*** ↔ NIST CSF 2.0 |

**El último es un hallazgo de canal, no de producto, y es reutilizable:** es la primera vez que
**texto regulatorio de APAC entra en esta KB a través de GitHub**. Con el lado demanda de la web sin
resolver desde este entorno, **buscar la norma como artefacto de cumplimiento** (`crosswalk`,
`mapping`, `checklist`) es una vía que funciona donde el documento no se alcanza.

**Precisión de licencia con efecto en composición:** `OpenEMS` no es AGPL-3.0 a secas — **Edge y
Backend son EPL-2.0**, sólo la UI es AGPL-3.0. Un agente MIT **puede** integrarse con el Backend sin
activar la cláusula de red, algo que esta KB venía descartando. Ver T55.

**Nada nuevo proponible en agentes de operación de red este pase.** Se mantiene el estado del pase
12: el cero lo rompió un TSO, y sigue siendo el único.

## 2026-11-20 — pase 13 (el hallazgo es un error propio: la KB había resuelto bien una licencia y un pase posterior la "des-resolvió"; y OpenADR 3.0 deja de ser un gap)

**Titular del pase: por primera vez el hallazgo principal no viene de fuera sino de dentro.**
Durante dos pases esta KB afirmó que [`OpenLEADR/openleadr-rs`](https://github.com/OpenLEADR/openleadr-rs)
no tenía archivo de licencia y que por tanto **"OpenADR 3.0 no tiene implementación abierta
licenciada"** (T45, ahora derogada). Es falso: `Cargo.toml` declara `license = "Apache-2.0 OR MIT"`
y `LICENSE-MIT` + `LICENSE-APACHE` devuelven **200** en `main` y en `master`.

Lo que lo hace grave no es el error, es **que la KB ya tenía la respuesta correcta escrita**. En
`agents/top.md`, en una tabla titulada *"Licencias rescatadas leyendo el archivo crudo"*, consta de
un pase anterior: `openleadr-rs | NOASSERTION | doble MIT / Apache-2.0 | LICENSE-MIT + LICENSE-APACHE`.
Un pase posterior volvió a medir con una lista de sondas más corta, obtuvo 404 (correctamente: esos
archivos no existen con esos nombres) y **escribió la conclusión contraria sin mirar el registro
propio**. El dato falso se propagó a tres archivos y sostuvo una receta entera.

**Lo que costaba:** la KB recomendaba entregar respuesta a la demanda sobre **OpenADR 2.0b**,
negociar licencia durante semanas, o **reimplementar 3.0 desde la especificación "como trabajo
facturable"**. Las tres innecesarias. No es un repo mal clasificado: es **una decisión de
arquitectura regional tomada sobre un hecho falso**.

**La regla, que es la más barata de aplicar de toda esta KB:** antes de escribir un negativo —"sin
licencia", "cero repos", "no existe"— **buscar la entidad en la propia KB**. Si hay registro
positivo previo, el negativo nuevo tiene que **explicar la discrepancia**, no sobrescribirla. Un
negativo reciente no gana a un positivo verificado por ser más reciente. El coste es asimétrico: un
falso positivo mete un repo malo en una tabla, un falso negativo **borra una capacidad del catálogo
y nadie la vuelve a buscar porque ya está "medida"**.

### La capa OpenADR 3.0 que el gap falso ocultaba, con dos piezas más

| Agente / pieza | Repo | Licencia | ★ / forks | Push | Qué hace |
|---|---|---|---|---|---|
| **openleadr-rs** | [OpenLEADR/openleadr-rs](https://github.com/OpenLEADR/openleadr-rs) | **Apache-2.0 OR MIT** | 107 / 30 | 2026-11-20 | VTN + VEN de OpenADR 3.0 en Rust (Stichting ElaadNL). **Licencia rectificada este pase** |
| **openadr3-client** | [ElaadNL/openadr3-client](https://github.com/ElaadNL/openadr3-client) | Apache-2.0 | 6 / 3 | 2026-11-19 | Cliente BL + VEN de OpenADR 3.0 en **Python**, mismo origen: un equipo Python ya no tiene que bajar a 2.0b |
| **volttron-openadr-ven** | [eclipse-volttron/volttron-openadr-ven](https://github.com/eclipse-volttron/volttron-openadr-ven) | Apache-2.0 | 6 / 6 | 2026-07-21 | VEN como agente **VOLTTRON**: empalma la respuesta a la demanda con el framework de agentes de edificio del PNNL que esta KB ya cataloga |
| **oadr30** | [universaldevices/oadr30](https://github.com/universaldevices/oadr30) | ⚠️ *"Universal Devices Free/MIT"* (redacción propia) | 10 / 1 | 2026-05-07 | Paquete Python OpenADR 3.0. **Permisiva en sustancia, no identificador OSI**: requiere lectura legal, no descarte |

### Capa nueva: medición y modelo de datos de DER — 12 repos permisivos nuevos

Barrido por **protocolo** (regla del pase 8), con tres términos: `SunSpec`, `IEC 62056`, `SAREF`.
Hasta aquí la KB tenía el motor de red, los entornos RL, los protocolos de carga y la capa MCP.
Faltaba **cómo se lee el medidor y el inversor, y con qué modelo de datos** — la capa que decide si
un piloto agéntico llega a tocar hardware del cliente.

Lo relevante para la caza de agentes: **`sunspec/models` (Apache-2.0, 135 ★) es el diccionario de
datos normativo de la propia alianza SunSpec**, no una implementación de terceros. Un agente que
tenga que razonar sobre inversores necesita ese vocabulario; es la pieza que convierte "leer un
registro Modbus" en "leer un campo con semántica". Lo mismo hace `saref-linkml` (BSD-3-Clause) del
lado europeo, y `Twin4Build` (MIT) es la única pieza encontrada que **une ontología con simulación
dinámica**. Las 16 filas verificadas están en `agents/top.md` y `repos/foundations.md`.

### El riesgo del pase: la capa de medición concentra las licencias no-OSI

El pase 12 encontró la licencia **revocable** (Energinet `MTB`). Este pase demuestra que **no era un
caso aislado sino una familia**, y que se concentra en la capa de consumidor/*prosumer*. Cuatro de
los repos con más tracción del barrido **no se pueden usar**, y la API informa `NOASSERTION` en todos:

- [`UtilitechAS/amsreader-firmware`](https://github.com/UtilitechAS/amsreader-firmware) — **471 ★**,
  **Fair Source License 0.9** con **`Use Limitation: 5 users`**. Un tope de cinco usuarios.
- [`bolagnaise/PowerSync`](https://github.com/bolagnaise/PowerSync) — 96 ★, **PolyForm
  Noncommercial 1.0.0**: prohíbe el uso comercial, que es exactamente lo que es un encargo.
- [`binsentsu/home-assistant-solaredge-modbus`](https://github.com/binsentsu/home-assistant-solaredge-modbus)
  — **420 ★ y ningún archivo de licencia** en ninguna rama.
- [`matthijskooijman/arduino-dsmr`](https://github.com/matthijskooijman/arduino-dsmr) — 145 ★ /
  **123 forks**, sin licencia y parado desde 2023. La proporción fork/★ de 0,85 dice que se usa
  **copiando código**, que es la peor forma de depender de un repo sin licencia.

Las cuatro tienen más estrellas que varias de las piezas limpias que sí se pueden proponer. **En
esta capa la tracción y la usabilidad legal están descorreladas**, y es la única capa de esta KB
donde eso pasa de forma sistemática.

### Términos inutilizables nuevos

- **`IEEE 1547`** (460 resultados): devuelve `PENTESTING-BIBLE` (14.028 ★), GNN para
  recomendación, *optical flow*. **Un número de norma a secas no es término de búsqueda**: "1547"
  coincide con cualquier cita o identificador. Usar el protocolo que la implementa (**IEEE 2030.5**).
- **`virtual power plant DER aggregation`** (96 resultados): diseño de proteínas, *conformal
  prediction*, Segment Anything. **Una frase genérica larga coincide con `awesome-*`**, y las listas
  curadas contienen todo el vocabulario técnico del mundo.

Misma causa en los dos: el término no es *específico del dominio* sino *frecuente en todo el corpus*.
El discriminador que funciona es el **nombre propio de un artefacto**: protocolo, ontología, formato
u organización.

---

## 2026-11-20 — pase 12 (se rompe el cero de agentes de operación de red, y lo rompe RTE; y la cola larga de MCP se midió entera: 0–4 ★)

**Titular del pase: el cero más persistente de esta KB —"ningún agente de operación de red"—
cae, y no por un repo de laboratorio: lo publica un TSO.
[`powsybl/pypowsybl-mcp`](https://github.com/powsybl/pypowsybl-mcp) (MPL-2.0, 7 ★, 2 forks, push
2026-11-18, `Copyright (c) 2026, RTE`) expone load flow, seguridad N-1 y sensibilidad como
herramientas MCP sobre pypowsybl. Es la confirmación ejecutable de T2.**

Lo que cambia respecto de los siete pases anteriores no es que apareciera "un agente más": es **de
quién viene**. Los pases 4 a 11 midieron el cero con consultas genéricas y lo atribuyeron a
inmadurez del sector. La lectura correcta, visible ahora, es que **la capa agéntica de red no se
publica en el vocabulario que la búsqueda genérica usa**: se publica dentro de la organización del
motor de red (`powsybl`, no "grid agent"), por el equipo del operador, y con un paper de posición
(arXiv 2607.14158) en vez de un anuncio. Es el mismo fallo de vocabulario que el pase 10 describió
para `StorageVET` y el 11 para `HELICS`, aplicado por fin a la categoría agéntica.

### La medición que acompaña, y es menos halagüeña

Ocho servidores MCP energéticos de la cola larga, todos verificados por API este pase:
`MCP-Energy-Hub` (MIT, 2 ★), `energyatit-mcp-server` (MIT, 1 ★), `octopus-mcp` (MIT, 1 ★),
`homewizard-mcp-server` (MIT, 1 ★), `UBEM-MCP` (BSD-3, 1 ★), `gridhub-mcp` (MIT, 0 ★),
`szl-energy-mcp` (Apache-2.0, 0 ★), `opendss-mcp-server` (MIT, 4 ★).

**Rango completo 0–4 ★; sólo uno tiene forks > 0.** Licencia y actividad son buenas (casi todo MIT o
Apache-2.0, cinco con push en 2026). Lo que falta es comunidad. El quinto pase ya lo había dicho;
este pase lo deja medido y cerrado: **en MCP energético, la procedencia institucional pesa más que
las estrellas.** `pypowsybl-mcp` con 7 ★ es proponible porque detrás está RTE; `energyatit-mcp-server`
con 1 ★ se autodescribe "first and only energy MCP server" y no es ni lo uno ni lo otro.

### El repo LATAM que parecía el hallazgo del año, y hay que decir que no lo es

[`saptiva-ai/octavius-energy-lab`](https://github.com/saptiva-ai/octavius-energy-lab) (Apache-2.0,
Saptiva, México, push 2026-11-10) se presenta como banco de evaluación de *agent harnesses* sobre
datos de **CENACE** y Low Carbon London, con Qwen3-8B local y TimesFM. Sería exactamente el repo
agéntico de origen LATAM que esta KB lleva pases pidiendo.

Se leyó el README antes de ficharlo. **El propio README dice que el dominio energético "no está
todavía en este árbol"**: los datasets y los modelos son fases futuras. Lo que existe es la
plataforma (Next.js 15, FastAPI con orquestador de tool-calling, Mongo/Redis/MinIO/Weaviate,
OpenTelemetry/Prometheus/Grafana/Loki) y una regla de método que merece citarse —**"no optimizar el
benchmark para que el harness parezca bueno"**—. 0 ★, 0 forks. Se autodescribe como "el punto de
partida".

Además anota que **los pesos de TimesFM 3.0 son de uso no comercial**, lo que cerraría la vía de
producción aunque el repo sea Apache-2.0.

**Ficha honesta: señal de mercado, no cimiento.** Hay una empresa mexicana de IA construyendo esto
con licencia permisiva y criterio de evaluación explícito; todavía no hay nada energético dentro.
**Acción para el pase 13: volver a medirlo.** Si el dominio aterriza, es el primer banco de
evaluación agéntico energético de origen LATAM y cambia el mapa de la región.

### Método: casi catalogamos un fork de 0 ★ en lugar del upstream de 238 ★

La búsqueda ofreció `CorradoMariaCaminiti/PowerMCP` con descripción completa. El verificador
(`search/repositories`) dijo `NOTFOUND`; `raw.githubusercontent.com` devolvió `200`. Las dos cosas
son ciertas: **la API de búsqueda de GitHub no indexa forks**, y eso es un fork de
[`Power-Agent/PowerMCP`](https://github.com/Power-Agent/PowerMCP) (MIT, **238 ★**, 67 forks), que
esta KB ya tenía.

**La firma `NOTFOUND` en búsqueda + `200` en raw identifica un fork.** Importa en los dos sentidos:
un `NOTFOUND` no prueba inexistencia, y —más peligroso— la verificación por `curl raw` que esta KB
adoptó tras el sexto pase **habría aceptado el fork como hallazgo**. Ver agents/top.md §1 del
duodécimo pase.

## 2026-11-20 — pase 11 (el agente de red que la KB tenía fichado como "precedente" tenía dentro una arquitectura, y el README `.adoc` es la razón de que nadie lo supiera)

**Titular del pase: el séptimo cero consecutivo en agentes de operación de red se mantiene por
consulta genérica — pero el inventario agéntico de esta KB sube de calidad sin una sola fila nueva,
porque la pieza que ya tenía estaba mal clasificada. `statnett/Talk2PowerSystem` (Apache-2.0, TSO
noruego) no es sólo un precedente: contiene una N-Shot Tool de texto-a-SPARQL sobre CIM, una
ontología para GraphDB y un conector de recuperación vectorial. Y su mitad ejecutable,
`statnett/cimsparql` (MIT), estaba sin catalogar.**

### Por qué ningún pase lo vio, y es un hallazgo de método reutilizable

El README de ese repo **no se llama `README.md`: se llama `ReadMe.adoc`** (AsciiDoc). La sonda
estándar de esta KB —`curl raw.githubusercontent.com/{repo}/main/README.md`— devuelve **404**, y un
404 de README se interpreta como "repo vacío o sin documentar". Se probaron cinco variantes
(`main/README.md`, `master/README.md`, `main/readme.md`, `main/README.rst`, `main/docs/index.md`):
las cinco, 404. El repo tiene documentación extensa, roadmap y changelog, todo en `.adoc`.

**AsciiDoc es el formato de documentación habitual en ingeniería industrial europea** (Eclipse,
consorcios IEC, TSOs). La regla operativa que se desprende, y que debería aplicarse a cualquier
medición futura de esta KB: **antes de concluir que un repo institucional europeo está vacío, probar
`ReadMe.adoc`, `README.adoc` y `README.asciidoc`**. Ver T52.

### Lo que hay dentro, verificado archivo por archivo

| Pieza | Qué es | Por qué importa |
|-------|--------|-----------------|
| `qa-dataset-ontology-schema/README.md` | **N-Shot Tool**: recupera las N preguntas más similares del *dataset* de Q&A y las pasa al chatbot **con sus plantillas SPARQL** | Es *few-shot retrieval* texto-a-SPARQL **descrito por el operador de la red**, no por un laboratorio |
| `connector.rq` | Definición de *retrieval connector* para indexar entidades de la base en una base vectorial | La capa de recuperación, explícita |
| `ontology.trig` | Ontología para almacenar el *dataset* de Q&A en **GraphDB** | El esquema de evaluación, reutilizable |
| `qa_dataset-config.ttl` | Configuración del repositorio GraphDB | Reproducible |
| `demo1/`, `data/`, `diagram/`, `docs/` | Demo, datos, diagramas | No auditados en este pase |

El *dataset* de Q&A en sí **no aparece** en ese directorio (no hay JSON/YAML/CSV de pares
pregunta-consulta visibles); la página indica "View all files", así que puede estar en otra ruta. **Se
registra como no verificado**, no como ausente.

### La fila que se añade a la cadena agéntica

| Agente / pieza | Repo | Licencia | ★ | Forks | Push | Región |
|----------------|------|----------|---|-------|------|--------|
| Consulta CIM por SPARQL desde Python | [statnett/cimsparql](https://github.com/statnett/cimsparql) | **MIT** | 10 | 7 | 2026-11-16 | EMEA |

Es la mitad ejecutable de `Talk2PowerSystem`: el mismo TSO, licencia más permisiva, **push de hace
cuatro días** (frente a mayo de 2026 del repo "vitrina"). ⚠️ 9 issues abiertas. Quien quiera montar
el patrón NL→CIM, **la dependencia es `cimsparql`; `Talk2PowerSystem` es el plano**.

### Reclasificación, con el juicio anterior intacto donde sigue siendo válido

Lo que **cambia**: `Talk2PowerSystem` pasa de *"precedente citable, no dependencia"* a
**"arquitectura de referencia copiable, publicada por un TSO bajo Apache-2.0"**.

Lo que **no cambia, y hay que seguir diciéndolo en una propuesta**: 17 ★, último push 2026-05-15,
`Roadmap.adoc` dice *"To be addressed"* y `Contributing` dice *"To Be addressed"*. **No es una base de
producto.** La única pieza agéntica/predictiva de esta KB con operación real en una *utility* sigue
siendo [`OpenSTEF/openstef`](https://github.com/OpenSTEF/openstef) (MPL-2.0, Alliander + RTE).

### El cero que se mantiene, medido por séptima vez y ahora también desde fuera de GitHub

La consulta mandada por el ciclo —`top open source AI agents energy 2026 github MIT`, en buscador
web, no en la API— devuelve **exclusivamente *frameworks* de propósito general**: OpenHands, OpenCode,
CrewAI, Hermes Agent, OpenClaw, LangGraph, AutoGen, OpenAI Agents SDK, Pydantic AI, LlamaIndex.
**Ninguno de dominio energético.** Siete pases midiendo el mismo cero por la API de GitHub, y el
buscador web —otra fuente, otro índice— devuelve el mismo resultado.

Para una conversación con cliente, esto ya se puede decir sin hedging: **no existe hoy un agente
abierto de operación de red con tracción de mercado.** Lo que existe es (a) la capa institucional
(`Power-Agent/*`, `PowerMCP`, `EnergyPlus-MCP`, `Talk2PowerSystem` + `cimsparql`), (b) la capa de
forecasting de propósito general (`timecopilot`, `chronos`), y (c) *frameworks* genéricos sobre los
que se construye. **El agente se construye; el plano, desde este pase, se puede copiar de un TSO.**

## 2026-11-20 — pase 10 (la cola larga agéntica tiene número: 33 repos en siete semanas, el mejor con 7 estrellas y sin licencia)

**Titular del pase: este pase no encontró ningún agente energético nuevo proponible, y por primera
vez puede decir cuántos hay y de qué tamaño.** La consulta `agent energy grid in:name,description
created:>2026-10-01` devuelve **33 repos creados en las últimas siete semanas**. El mejor tiene
**7 ★ y licencia `NOASSERTION`**; los cinco siguientes tienen **1, 0, 0, 0 y 0 estrellas** y
**ninguno tiene licencia**:

| Repo | Licencia | ★ | Push | Qué dice ser |
|------|----------|---|------|--------------|
| `arhamshah08/energy-hack` | ⚠️ NOASSERTION | 7 | 2026-11-16 | Pack de recursos "agent-ready" para un hack day de energía |
| `xvbohan92-ai/gridnote-energy-agent` | ⚠️ **sin licencia** | 0 | 2026-10-26 | Agente de análisis energético "evidence-backed" con **LangGraph**, sólo lectura |
| `tarrini/renewable-grid-agent` | ⚠️ **sin licencia** | 0 | 2026-10-11 | Despacho simulado de corredor renovable |
| `Likhitha-B-Y/smart-grid-energy-arbitrage-agent` | ⚠️ **sin licencia** | 0 | 2026-10-09 | Arbitraje de energía |
| `ssblip/gridmind` | ⚠️ **sin licencia** | 0 | 2026-10-11 | Multi-agente para gestión autónoma de red renovable |

Y en MCP, `mcp energy grid in:name,description created:>2026-09-01` devuelve **4 repos, los cuatro
con 0 estrellas** (`pipeworx-io/mcp-georgia-energy` y `azmartone67/dchub-claude-plugin` ya estaban
catalogados; `sohamshindework/gridpulse` se creó **hoy**).

**Lo que esto cambia, que no es poco:** hasta este pase, "no hay agente de operación de red
proponible" era una ausencia. Ahora es una **distribución medida**: hay actividad —33 repos en siete
semanas, nombres que prometen despacho autónomo y arbitraje— y **toda ella está por debajo del umbral
de proponible, y mayoritariamente sin licencia**. Es el **sexto cero consecutivo** en operación de
red, y el primero con la forma del cero descrita. Un cliente que pregunte "¿no hay ya agentes de red
open source?" tiene ahora una respuesta con número: los hay, son de una semana, de una persona y de
cero estrellas.

`gridnote-energy-agent` merece una nota aparte porque **acierta en el diseño**: LangGraph,
*evidence-backed*, y explícitamente **sólo lectura**. Es la regla de arquitectura de esta KB y la
postura de `OpenVigil` (pase 9), en un repo de cero estrellas sin licencia. **La idea correcta está
circulando; la base utilizable no.**

### Lo que sí aportó este pase a la capa agéntica: el banco de pruebas que un agente de red necesitaría

El hallazgo principal del pase 10 son dos organizaciones institucionales norteamericanas (EPRI y
Grid Protection Alliance, ~125 repos — ver `repos/trending.md`). **Ninguno de esos repos es un
agente, y conviene decirlo sin adornos.** Pero dos piezas son precondición directa de la capa
agéntica, y esta KB no las tenía:

| Repo | Licencia | ★ | Forks | Push | Por qué importa para un agente |
|------|----------|---|-------|------|-------------------------------|
| [epri-dev/Universal-Semantic-Standard-Test-Harness](https://github.com/epri-dev/Universal-Semantic-Standard-Test-Harness) | **BSD-3-Clause** | **0** | 1 | 2026-08-18 | Banco de pruebas de **interoperabilidad semántica**. Un agente que actúa sobre la red necesita exactamente esto: un arnés que compruebe que lo que entendió es lo que el modelo dice |
| [Haigutus/cim-bench](https://github.com/Haigutus/cim-bench) | **MIT** | 10 | 5 | 2026-07-16 | **Benchmarking de herramientas CIM**. Comparar implementaciones es el paso previo a dejar que un modelo elija entre ellas |
| [GridProtectionAlliance/openECA](https://github.com/GridProtectionAlliance/openECA) | **MIT** | 16 | 8 | 2026-11-15 | *Extensible Control & Analytics*: el punto de inserción de analítica en el lazo operativo. ⚠️ **20 issues abiertas** |

El patrón que esta KB viene registrando desde el pase 4 se repite con otro signo: **la capa de
evaluación llega antes que la capa de agente, y llega de las instituciones.** `PowerAgentBench` y
`PowerFM` (pase 4-5) venían de la academia; el arnés semántico de EPRI tiene **cero estrellas y tres
meses**. Cuando exista un agente de operación de red proponible, el arnés para auditarlo ya estará
escrito, en BSD-3, y nadie lo habrá mirado.

### Nota de método que afecta al descubrimiento de agentes

El pase 9 estableció "buscar la norma, no el buzzword". Este pase encontró el límite de esa regla, y
es el motivo por el que nueve pases no vieron 125 repos institucionales: **las instituciones no
nombran sus herramientas por la categoría ni por la norma, sino por el acrónimo interno del método**.
`StorageVET`, `DER-VET`, `QuESt`, `openMIC`, `openXDA`, `ProGRESS`, `SPI-Tool`. Ninguno contiene el
término de su categoría. La consulta que los encuentra es `org:epri-dev` y
`org:GridProtectionAlliance` — es decir: **cuando la oferta esperable es de investigación aplicada,
buscar la institución, no la cosa.** Ver **T47**.

Para la caza de agentes esto tiene una consecuencia directa y comprobable en el próximo pase:
conviene barrer por organización los laboratorios e institutos que ya aparecen en esta KB
(`pnnl`, `argonne-*`, `lbl-srg`, `NatLabRockies`, `equinor`, `statnett`, `alliander-opensource`,
`entsoe`) antes de volver a barrer por buzzword agéntico.

## 2026-11-20 — pase 9 (el agente que opera un activo real: 22 agentes, capa de autorización humana, y publica que no está verificado)

**Titular del pase: apareció el primer repo de esta KB que implementa T28 ("la IA asiste, no decide")
como código y no como frase de README — y que publica su propio estado como NO VERIFICADO.**
[`Ninemilo/OpenVigil`](https://github.com/Ninemilo/OpenVigil) (**Apache-2.0** confirmada en `LICENSE`
crudo, 180 ★, 37 forks, creado 2026-09-04, push 2026-11-17, **0 issues abiertas**) es una plataforma
de O&M de parque eólico que encadena monitoreo → alarma → diagnóstico → **aprobación humana** →
orden de trabajo → evidencia de campo → actualización de conocimiento en un flujo auditable.

### Qué tiene dentro, verificado leyendo el repo

| Capa | Implementación |
|------|----------------|
| Agentes | **22 agentes** en tres capas: decisión, revisión, ejecución. Runtime de agentes con **16 tools** |
| Orquestación | **LangGraph** en backend Python + catálogo SQL gobernado con **18 tools** |
| Modelos | **LiteLLM**; proveedores nombrados: SiliconFlow, Alibaba Bailian, DeepSeek (**origen APAC**) |
| Datos | SCADA, CMS, meteorología, alarmas manuales; conectores SCADA / MQTT / HTTPS / **EAM** |
| Backend | FastAPI, PostgreSQL + **TimescaleDB** + **pgvector**, Redis, Dramatiq, MinIO, **Neo4j** |
| Workers | `pyOMA2` (análisis modal estructural) y parser PDF/OCR basado en **Docling** |
| Benchmark | **CARE v6** offline (Fraunhofer IEE): 95 eventos, 36 activos, **CC BY-SA 4.0 y NO incluido** en el repo — lo aporta el operador |
| Frontend | React 19, vinext, Cloudflare Worker + D1 (sólo demo) |

### Por qué es el hallazgo del pase, y qué NO se puede decir de él

Lo valioso es la **postura**, no la precisión: el propio README declara que es una *"production
candidate implementation, not a system already deployed in production"*, y marca **UNVERIFIED** la
exactitud de campo, la calibración real, la operación en sombra y la calificación formal de release.
La salida de la demo proviene de **fixtures deterministas, no de modelos en vivo**, y no hay
releases publicados. Documentación en **ocho idiomas**.

- **Usar como plantilla** del patrón de autorización: la IA propone alternativas, **la persona
  autoriza las acciones de alto riesgo**. Es exactamente la regla de arquitectura de esta KB, ya
  escrita en código y con capa de revisión separada de la de ejecución.
- **No citar ninguna cifra de desempeño**: no publica ninguna. Es un hallazgo de *viabilidad y
  diseño*, no de *ranking*. (Misma disciplina que el pase de automotive aplicó a `drivingbench`.)
- **Riesgos medidos**: 180 ★ y **0 issues abiertas** en 2,5 meses con 63 commits sugieren velocidad
  de autor único; **no nombra ningún protocolo industrial** (ni OPC UA ni IEC 61400-25), y los
  contratos reales de SCADA/CMS/EAM siguen pendientes de pruebas de aceptación conjuntas. El gemelo
  digital es una **vista operativa 2D, no una simulación física**.

**Lectura de patrón, tercera confirmación en esta rotación:** automotive encontró `LionDriver`
publicando 42 defeaters abiertos; automotive encontró `wtfault-scanner` con "never makes anything
up"; energy encuentra `OpenVigil` marcando UNVERIFIED lo que no probó. **Publicar el propio límite
se consolidó como movimiento de credibilidad en industrias reguladas.**

### La capa ISO 15118 / Plug&Charge: esta KB tenía el lado del CSMS y le faltaba el del vehículo

El séptimo pase catalogó la carga de EV como la categoría más grande del open source energético
(T31) con `evcc`, `EVerest`, `steve` y `mobilityhouse/ocpp`. Faltaba el **protocolo
vehículo↔cargador**. Buscando `"ISO 15118"` como término único:

| Repo | Licencia | ★ | Forks | Push | Qué aporta |
|------|----------|---|-------|------|-----------|
| [ecog-io/iso15118](https://github.com/ecog-io/iso15118) | **Apache-2.0** | 250 | 142 | 2026-11-17 | Implementación de ISO 15118 **-2, -20 y -8**. Ratio fork:★ = **0,57**, señal de construcción, no de estrella |
| [SwitchEV/RISE-V2G](https://github.com/SwitchEV/RISE-V2G) | **MIT** | 261 | 95 | ⚠️ 2025-12-19 | La implementación de referencia histórica de la interfaz V2G. **11 meses sin push** |
| [ecog-io/josev](https://github.com/ecog-io/josev) | **Apache-2.0** | 164 | 23 | 2026-11-16 | Versión comunitaria de Josev: "sistema operativo" para estaciones de carga V2G |
| [matth-x/MicroOcpp](https://github.com/matth-x/MicroOcpp) | **MIT** | 547 | 220 | ⚠️ 2025-12-04 | Cliente OCPP 1.6 / 2.0.1 **para microcontroladores**. 135 issues abiertas y casi un año sin push |

**Lectura honesta: la capa de protocolo existe, es permisiva, y la mitad se está quedando vieja.**
`ecog-io/*` es lo vivo (push de noviembre de 2026); `RISE-V2G` y `MicroOcpp` son las piezas más
citadas de la categoría y llevan ~11 meses sin movimiento. Para un SoW: partir de `ecog-io`, usar
`RISE-V2G` como referencia de lectura, y **no** comprometer `MicroOcpp` en firmware sin antes
auditar sus 135 issues.

### EEBus/SPINE: el protocolo de flexibilidad doméstica de EMEA, y un fabricante publicando el stack

| Repo | Licencia | ★ | Forks | Push | Nota |
|------|----------|---|-------|------|------|
| [enbility/eebus-go](https://github.com/enbility/eebus-go) | **MIT** | 123 | 53 | 2026-11-06 | Implementación de EEBUS en Go; la base viva de la categoría |
| [NIBEGroup/openeebus](https://github.com/NIBEGroup/openeebus) | **Apache-2.0** | 68 | 18 | 2026-11-12 | EEBUS (**SHIP y SPINE**) en C, publicado por **NIBE Group**, fabricante sueco de bombas de calor |
| [volschin/eebus-ha-bridge](https://github.com/volschin/eebus-ha-bridge) | **MIT** | 41 | 9 | 2026-11-19 | Puente EEBUS→Home Assistant sobre `eebus-go`, con API gRPC |
| [FlexMeasures/flexmeasures-s2](https://github.com/FlexMeasures/flexmeasures-s2) | **Apache-2.0** | 2 | 0 | 2026-09-21 | Tooling para mensajes **S2** (EN 50491-12-2) dentro de FlexMeasures |

**`NIBEGroup/openeebus` extiende T2 un escalón.** T2 decía que *los operadores de red* se volvieron
proveedores de open source (RTE, Alliander). Aquí el que publica el stack de protocolo es un
**fabricante de equipo**. La consecuencia comercial: en EMEA el integrador ya no necesita licenciar
una pila EEBus propietaria para hablar con una bomba de calor.

Y el dato incómodo del mismo cuadro: **el estándar S2 de flexibilidad tiene tooling, y tiene 2
estrellas.** La norma existe, la comunidad todavía no.

### Dos "resultados de búsqueda" que no eran hallazgos

La búsqueda web de este pase volvió a presentar `DatariusAI/AI-in-Energy` como *"daily-refreshed hub
of the latest AI, ML and data science research and code for energy and utilities"*. La API dice:
**0 ★, 0 forks, sin licencia, creado 2026-10-08** — y el octavo pase **ya lo había catalogado con
esa misma advertencia** en `repos/foundations.md`. Se registra aquí sólo como confirmación
independiente de que el buscador describe el README y no la tracción.

Lo nuevo de este pase en la misma categoría: `ishandutta2007/Awesome-Energy-Utilities-CRM` (**MIT,
0 ★**, creado 2026-10-12), única pista hacia la capa meter-to-cash y sin tracción; y
`AI4Electricity/Awesome-AI-for-Electricity` (**MIT**, 153 ★), que **no tuvo push desde 2025-03-30:
20 meses**.

Los índices vivos siguen siendo los dos que esta KB ya tenía:
[`protontypes/open-sustainable-technology`](https://github.com/protontypes/open-sustainable-technology)
(CC-BY-4.0, 2.586 ★ — aparece en **todas** las consultas de protocolo de este pase, lo que confirma
que es el mapa del espacio) y [`ps-wiki/best-of-ps`](https://github.com/ps-wiki/best-of-ps)
(CC-BY-SA-4.0, 297 ★, push 2026-11-20, ranking semanal).

### Anomalías ★/fork que confirman T19 en esta muestra

- [`Ali-Marandi/grid-resilience`](https://github.com/Ali-Marandi/grid-resilience) — MIT, **108 ★ y 0 forks**.
- `KEV0143/Comparative-analysis-of-hourly-load-forecasting-using-PatchTST-TFT-NHiTS-and-CatBoost` — Apache-2.0, **1.764 ★ y 0 forks**.

Ninguno de los dos se cita como validado por comunidad. Un repo con mil setecientas estrellas y
cero forks no lo usó nadie.

## 2026-11-20 — pase 8 (el método de "buscar la norma local" no generaliza, y la razón es utilizable)

**Titular del pase: la lección que abrió APAC en el pase 7 no se exporta a EMEA ni a LATAM, y el
por qué es una regla de búsqueda, no una conclusión sobre el sector.** El pase 7 dejó cinco
candidatos —`CEI 0-21` (Italia), `VDE-AR-N 4105` (Alemania), `G99` (Reino Unido), `PRODIST`
(Brasil), `NOM-001-SEDE` (México)— con la hipótesis de que nombrar la norma de conexión local
abriría cada región como `CSIP-AUS` e `IEEE 2030.5` abrieron Australia. Las cinco consultas se
corrieron contra `search/repositories`. **Ninguna devolvió un repo institucional con tracción.**

| Término buscado | Resultados | Lo mejor que apareció | Licencia | ★ |
|-----------------|-----------|----------------------|----------|---|
| `VDE-AR-N` (Alemania) | 188 | [KIT-IAI/PIDE](https://github.com/KIT-IAI/PIDE) — simulación de integración de DER y control autónomo de reactiva en redes de distribución | **MIT** (verificada en `LICENSE` crudo: Karlsruhe Institute of Technology, IAI) | 5 |
| `NOM-001-SEDE` (México) | 74 | [jacometoss/PyEWS](https://github.com/jacometoss/PyEWS) — dimensionado de conductores eléctricos | GPL-3.0 | 4 |
| `G99` (Reino Unido) | 24 | [Nero-Engine/spark-pack-mcp](https://github.com/Nero-Engine/spark-pack-mcp) — servidor MCP de cálculo eléctrico con G98/G99 | **sin licencia** | 0 |
| `CEI 0-21` (Italia) | 10 | calculadoras fotovoltaicas italianas de autor individual | MIT / varias | 0 |
| `PRODIST` (Brasil) | 142 | **nada**: colisión de nombres completa | — | — |

**La regla que sale de esto, y vale para cualquier industria de esta KB: buscar el *protocolo*, no
la *norma*.** `IEEE 2030.5` y `CSIP-AUS` son protocolos máquina-a-máquina con implementación
obligatoria: producen librerías, clientes y servidores. `VDE-AR-N 4105`, `CEI 0-21`, `G99` y
`NOM-001-SEDE` son normas documentales de cumplimiento: producen hojas de cálculo y calculadoras de
0 ★. La diferencia no es la madurez eléctrica del país —Alemania e Italia no están detrás de
Australia— sino **si la norma obliga a que dos máquinas se hablen**. Donde obliga, hay código
abierto; donde sólo obliga a entregar un expediente, hay PDF.

⚠️ **`PRODIST` se suma a la lista de términos inutilizables** (`hydrogen`, `AMI`, `utility billing`,
`reservoir`, registrados en pases anteriores): 142 resultados y **ninguno** es el PRODIST de ANEEL.
"ProDist" es, en GitHub, cálculo de distribuciones de probabilidad, un sistema de gestión de
distribuidores y un curso de programación distribuida. Para Brasil hay que volver al vocabulario que
sí funcionó en el pase 6: **el nombre del framework más el país** (`pypsa-meets-brazil`).

**Único rescate institucional del barrido: `KIT-IAI/PIDE` (MIT, 5 ★, push 2026-08-05).** Es del
Institute for Automation and Applied Informatics del KIT, y simula integración de generación
distribuida con control autónomo de potencia reactiva. 5 ★ no es tracción: vale como **referencia de
método verificable** para una propuesta en Alemania, no como dependencia.

### Quinto pase consecutivo sin agente de operación de red — ahora medido también desde fuera de GitHub

La consulta global prescrita (`top open source AI agents energy 2026 github MIT`) devuelve listicles
de agentes de propósito general —OpenClaw, Hermes, OpenCode, OpenHands, CrewAI, Browser Use— **sin
una sola entrada energética**. Las fuentes además se contradicen en estrellas y licencias entre sí.
Eso confirma, desde un canal distinto al conteo de repos, lo que los pases 4-7 midieron: la capa
agéntica energética **es institucional o es de forecasting**, y no de mercado. Lo proponible sigue
siendo `Power-Agent/*` (MIT), `pypsa-mcp` (MIT), `EnergyPlus-MCP` (BSD) y la cadena de forecasting
del pase 7.

### Novedad agéntica real del pase, pequeña y honesta

[`open-energy-transition/gridlens`](https://github.com/open-energy-transition/gridlens) — **MIT**,
1 ★, push **2026-11-19**. Se describe como *"AI-native app to see who's using which energy models,
where, and for what grid decisions"*. Es el primer repo que esta KB registra cuyo objeto es
**observabilidad del propio ecosistema de modelos**: qué modelo usa quién y para qué decisión de red.

⚠️ **Cómo proponerlo:** 1 ★ y un día de vida. **No es una dependencia.** Vale por dos cosas
concretas: (a) confirma que Open Energy Transition —el autor de `pypsa-mcp`— está construyendo la
capa agéntica alrededor de PyPSA, y (b) el problema que nombra (*trazabilidad de qué modelo sostiene
qué decisión*) es exactamente el entregable que un cliente regulado pide y que ningún repo cubría.
Si se vuelve real, es la pieza de governance del stack.

### Correcciones de este pase a afirmaciones de pases anteriores

1. **`CommonGrid` sí tiene repo de código localizable.** `compose/patterns.md` e `intel/trends.md`
   registraron *"buscados en GitHub: sin repo de código localizable"*. Es
   [`TextureHQ/commongrid`](https://github.com/TextureHQ/commongrid) — 14 ★, push 2026-11-19. El
   fallo fue de vocabulario de organización: `user:texture-hq` devuelve HTTP 422 y la organización
   real es `TextureHQ`. **La advertencia de licencia que la KB había hecho se confirma y se
   endurece**: el `LICENSE` crudo dice literalmente *"Open Data Commons Open Database License (ODbL)
   v1.0 — Copyright (c) 2025-2026 Texture, Inc."* Es licencia de **base de datos**, con obligación de
   compartir derivados de la base: utilizable como fuente, **no empotrable** como dataset en un
   entregable cerrado.
2. **El "gap de geotermia" era, en efecto, artefacto de sintaxis** (como el pase 7 sospechó): existe
   [`open-energy-transition/geothermal-modelling`](https://github.com/open-energy-transition/geothermal-modelling)
   — **AGPL-3.0**, 6 ★, push 2026-11-16. Gap cerrado en oferta; abierto en licencia proponible.

## 2026-11-20 — pase 7 (aparece el agente que faltaba, y no es un agente de red: es de forecasting)

**Titular del pase: por primera vez en cuatro pases la capa agéntica energética tiene una novedad
proponible, y llega por el lado del forecasting, no por el de la operación de red.**
[`TimeCopilot/timecopilot`](https://github.com/TimeCopilot/timecopilot) (MIT, 643 ★, 89 forks,
push 2026-11-18) se describe como *"the Agentic Forecasting Framework. Built on LLMs and Time Series
Foundation Models"*. Es la primera pieza que combina las dos capas que esta KB tenía separadas —
razonamiento LLM (pases 1-3) y foundation models (pase 4) — en un solo framework permisivo con
tracción real. No es energético por diseño, pero el forecasting de carga y precio es su caso de uso
canónico, y es la respuesta concreta al gap que los pases 4, 5 y 6 declararon.

**La cadena de forecasting agéntico, toda verificada este pase y toda permisiva:**

| Capa | Repo | Licencia | ★ | Rol |
|------|------|----------|---|-----|
| Orquestación agéntica | [TimeCopilot/timecopilot](https://github.com/TimeCopilot/timecopilot) | MIT | 643 | LLM elige modelo, explica el pronóstico |
| Modelo fundacional de series | [amazon-science/chronos-forecasting](https://github.com/amazon-science/chronos-forecasting) | Apache-2.0 | 6328 | Pre-entrenado, zero-shot |
| Forecasting energético con TSFM | [arnaud-vs/open-predico](https://github.com/arnaud-vs/open-predico) | Apache-2.0 | 54 | Aplica TSFM a energía |
| Línea base corta solar/viento/carga | [williamhobbs/hefty](https://github.com/williamhobbs/hefty) | BSD-3-Clause | 85 | El baseline honesto a batir |
| Pipeline de producción de utility | [OpenSTEF/openstef](https://github.com/OpenSTEF/openstef) | MPL-2.0 | 184 | Ya catalogado; sigue siendo el de operación |

⚠️ **Cómo proponerlo sin exagerar:** `timecopilot` y `chronos` son de propósito general. Lo que esta
KB puede afirmar es que **existe la cadena**, no que esté validada en despacho. `openstef` sigue
siendo la única pieza con operación real en una utility (Alliander, RTE). La receta nueva —
*Receta 25* en `compose/patterns.md` — pone `timecopilot` en la vía de **evaluación**, con `openstef`
como control, y no en la vía de producción.

**Segunda novedad, institucional y pequeña: un TSO escribió un agente sobre su propio modelo de red.**
[`statnett/Talk2PowerSystem`](https://github.com/statnett/Talk2PowerSystem) (Apache-2.0, 17 ★, push
2026-05-15) es de Statnett, el operador de transmisión noruego: *"Talk to the Power System"*, LLM
sobre grafo de conocimiento CIM. Es la primera vez que esta KB registra un **agente de red escrito por
el operador**, no por un laboratorio ni por un consorcio. Son 17 ★ y el último push es de mayo: no es
una base de producto, **es la prueba de que el patrón es el que los TSO quieren**. Para una propuesta
vale más como precedente citable que como dependencia.

**Lo que sigue sin existir, y ahora con medición de industria, no sólo de repos.** Las búsquedas de
agentes energéticos creados después de 2026-08-01 (`energy agent LLM`, `grid OR substation OR utility
agentic`, ambas con `created:>`) devuelven **ruido puro**: extensiones de Chrome, bots de pentest,
asistentes de voz domésticos. Cuarto pase consecutivo sin un agente de operación de red proponible.
La novedad es que ahora hay un número externo que dice lo mismo: una **encuesta de la IEA a operadores
de red de 13 países** encuentra que sólo el **23 % usa IA para operación en tiempo real**, frente a
**~70 % que la usa para mantenimiento de activos y planificación**. El hueco que esta KB medía
contando repos es el mismo que la IEA mide contando operadores. Eso convierte el gap en **argumento de
venta**: el trabajo proponible hoy está en el 70 %, no en el 23 %.

**Confirmación regulatoria que refuerza la tesis human-in-the-loop del pase 3 y 6:** la encuesta de
Grant Thornton 2026 del sector energético reporta que para el **54 %** la incertidumbre regulatoria y
de cumplimiento es la principal preocupación al desplegar IA agéntica, con **38 % en piloto o prueba
de valor** y **32 % que se estanca después de haber sido declarado listo para escalar**. Ese 32 % es
el mercado de Globant: no es un problema de modelo, es de operacionalización y gobernanza.
Guía **CISA/NSA de mayo de 2026** para infraestructura crítica: zero trust, defensa en profundidad y
**mínimo privilegio** — es decir, la arquitectura donde el agente propone y
[`opfab/operatorfabric-core`](https://github.com/opfab/operatorfabric-core) acepta.

## 2026-11-20 — pase 6 (ninguna novedad agéntica pasa la barra, y una confirmación regulatoria que vale más)

**Titular del pase, dicho como corresponde: en la capa de agentes energéticos no hay novedad
proponible esta semana.** La búsqueda global de "mejores agentes AI open source 2026" devuelve
`OpenClaw`, `Hermes`, `OpenHands`, `Browser Use`, `CrewAI` y `LangGraph` — agentes y frameworks de
propósito general, **ninguno energético**. Esto confirma por tercer pase consecutivo el hallazgo del
pase 5: **no existe un "agente energético" open source de propósito general con tracción**, y lo
creíble sigue siendo lo institucional ya catalogado (`PowerMCP`, `PowerSkills`, `EnergyPlus-MCP`,
`idfkit-mcp`, `pypsa-mcp`, la familia `energnn`). Se registra como hueco medido, no como silencio.

**Lo que sí es nuevo y cambia el argumento de venta de la capa agéntica: la NERC dice por escrito que
la IA debe asistir la decisión, no actuar de forma autónoma.** Hasta ahora la tesis
*human-in-the-loop* de esta KB —que `operatorfabric-core` es la pieza sin la cual una demo de red no
es desplegable, establecida en el pase 3— se sostenía en razonamiento de ingeniería. Ahora tiene
respaldo del organismo que fija los estándares de fiabilidad de la red norteamericana. Deja de ser
una opinión de arquitectura y pasa a ser **cumplimiento**: en un encargo con una utility de EE. UU.,
la capa de aceptación humana no es un extra que se negocia, es el requisito.

**Dónde encaja cada pieza, ahora que la obligación es explícita:**

| Capa | Repo | Licencia | Rol bajo la guía de la NERC |
|------|------|----------|------------------------------|
| Razonamiento sobre herramientas | [Power-Agent/PowerMCP](https://github.com/Power-Agent/PowerMCP) | MIT | Propone; **no ejecuta** |
| Recomendación de maniobra | [ainetus/ExpertOp4Grid](https://github.com/ainetus/ExpertOp4Grid) | MPL-2.0 | Propone topología |
| **Aceptación humana trazable** | [opfab/operatorfabric-core](https://github.com/opfab/operatorfabric-core) | MPL-2.0 | **La pieza que satisface el requisito** |
| Ejecución en campo | [VOLTTRON/volttron](https://github.com/VOLTTRON/volttron) | Apache-2.0 | Actúa sólo tras aceptación |

**Novedad regional de contexto, no de repo (ver `intel/market.md` para el detalle):** la Comisión
Europea publicó el **3 de junio de 2026** una *Strategic Roadmap for Digitalisation and AI in the
Energy Sector* con tres pilares, y el **17 de julio de 2026** una propuesta de modificación del
Reglamento del Mercado Eléctrico. Para la capa agéntica importa una línea concreta: la Comisión
**redactó guías de clasificación de sistemas de IA de alto riesgo según el artículo 6 del AI Act**. Si
un copiloto de operación de red cae en esa clasificación, el *human-in-the-loop* de arriba es
obligatorio también en EMEA, por la misma razón que en North America pero con otra base legal.
⚠️ Todo esto proviene de **fuentes secundarias**: el registro primario de la UE
(`data.consilium.europa.eu`) **no resuelve desde este entorno**, sexto pase consecutivo con esa
limitación. No citar fechas de artículo en una propuesta sin abrir el documento oficial.

## 2026-11-20 — pase 5 (la cohorte LF Energy de septiembre, y una trampa de verificación propia)

**Titular del pase: los cuatro proyectos que LF Energy anunció el 15 de septiembre de 2026 existen,
son localizables y tres de los cuatro son permisivos o MPL — pero ninguno pasa de 34 ★.** El pase 4
cerró diciendo que faltaba el modelo y lo encontró (`gridfm`, `GridSFM`). Este pase cierra el circuito
institucional: el consorcio que publica esos modelos tiene además una **familia agéntica de red**
recién nacida, con gobernanza de la Linux Foundation y convertidores hacia los dos motores que esta
KB ya tenía (`powsybl` y `pandapower`).

**Nuevo esta semana — cohorte LF Energy (anuncio 2026-09-15), verificada repo por repo:**

| Repo | Licencia | ★ | Forks | Issues | Push | Señal |
|------|----------|---|-------|--------|------|-------|
| [energnn/energnn](https://github.com/energnn/energnn) | **MPL-2.0** | 34 | 4 | 15 | 2026-11-16 | GNN para redes de energía **reales**, no sintéticas. Creado 2025-10-16 |
| [assetlife-project/assetlife](https://github.com/assetlife-project/assetlife) | **Apache-2.0** | 7 | 3 | **32** | 2026-11-19 | Modelado estocástico de vida de activo. Creado 2026-09-03: **32 issues sobre 7 ★** |
| [SMART-HEMS-Benchmark/smart-hems-benchmark](https://github.com/SMART-HEMS-Benchmark/smart-hems-benchmark) | **MIT** | 7 | 2 | 0 | 2026-07-09 | Banco de pruebas HEMS; el par de evaluación de `agentic-ai-hems` |
| [energnn/tensio](https://github.com/energnn/tensio) | **MPL-2.0** | 1 | 0 | 0 | 2026-10-19 | Aplicación de EnerGNN a mejora de tensiones |
| [energnn/pypowsybl-to-energnn](https://github.com/energnn/pypowsybl-to-energnn) | **MPL-2.0** | 3 | 2 | 2 | 2026-10-15 | Conversor `pypowsybl` → grafo EnerGNN |
| [energnn/pandapower-to-energnn](https://github.com/energnn/pandapower-to-energnn) | **MPL-2.0** | 0 | 0 | 0 | 2026-09-08 | Conversor `pandapower` → grafo EnerGNN |

**Por qué los conversores importan más que la librería.** `energnn` sola es una librería de GNN con 34 ★:
nada que justifique una propuesta. Los dos conversores la convierten en otra cosa — una capa que lee
el modelo de red que el cliente **ya tiene** en PowSyBl o pandapower y lo entrega como grafo
entrenable. El valor no está en el modelo, está en que no hay que rehacer el modelo de red.

**La señal de `assetlife` es la relación issues/estrellas, no las estrellas.** 32 issues abiertas
sobre 7 ★ y dos meses y medio de vida es desarrollo activo de un equipo, no abandono. El pase 4 de
esta KB estableció la regla de comprobar `forks_count` antes de comprometer alcance; este pase añade
el corolario: **en un repo recién nacido, `open_issues_count` alto es señal positiva**, al revés que
en uno maduro.

### Corrección de método: mi propio verificador se equivocó, y el error era en la dirección peligrosa

Al resolver licencias leyendo el archivo crudo, el detector marcó `energnn/energnn` como **AGPL-3.0**.
La API de GitHub decía **MPL-2.0**. Ganó la API: el texto de la MPL-2.0 **nombra la AGPL en su propia
cláusula 1.12** ("Secondary Licenses" = GPL-2.0, LGPL-2.1, AGPL-3.0), de modo que cualquier detección
por `grep` de la cadena *"GNU Affero"* convierte toda MPL-2.0 en AGPL.

**Consecuencia para esta KB:** la familia europea de LF Energy es MPL-2.0 de forma consistente
(ver nota del tercer pase) — es decir, **toda ella** es vulnerable a este falso positivo. Un pase
futuro que "rescate licencias leyendo el crudo" sin esta precaución reclasificaría media KB a AGPL e
inventaría una obligación de liberar el servicio que no existe. Regla: **ante conflicto entre la API
y un detector de texto sobre una licencia de la familia MPL, gana la API**; el archivo crudo sólo
decide cuando la API dice `null` o `NOASSERTION`.

### La cola larga de agentes LLM energéticos sigue sin ser proponible

Consulta `energy agent LLM in:name,description created:>2026-06-01`, 15 resultados. **Ninguno pasa de
7 ★**; la mayoría son 0 ★ de autor individual (`langgraph-energy-agent` MIT 0 ★,
`energyplus-llm-hvac-agent` MIT 0 ★, `renewable-energy-LLM-agent` sin licencia,
`Knowledge-Orchestrated-LLM-Agent-Workflow` 1 ★ sin licencia). Es el mismo patrón que el pase 3 midió
en LATAM: la demanda se ve, la oferta es personal y sin licencia.

**Lectura:** lo creíble en esta categoría sigue siendo lo institucional que esta KB ya tiene
(`Power-Agent/PowerMCP`, `LBNL-ETA/EnergyPlus-MCP`, `idfkit/idfkit-mcp`,
`open-energy-transition/pypsa-mcp`). **No** hay un "agente energético" open source de propósito
general con tracción. Sigue siendo integración, no instalación.

---

## 2026-11-20 — pase 4 (los foundation models de red, y una trampa de estrellas)

**Titular del pase: apareció la capa que faltaba entre el servidor MCP y el entorno RL — modelos
preentrenados específicos de red, permisivos y con respaldo corporativo.** Los pases 1-3 de hoy
describieron el razonamiento sobre herramientas (`PowerMCP`), el lugar de ejecución (`VOLTTRON`) y la
sala de control (`operatorfabric-core`). Faltaba el modelo.

**Nuevo esta semana — foundation models de red:**

| Repo | Licencia | ★ | Forks | Push | Señal |
|------|----------|---|-------|------|-------|
| [microsoft/GridSFM](https://github.com/microsoft/GridSFM) | MIT | 177 | 41 | 2026-07-15 | Microsoft publica *Small Foundation Models* de red. Creado 2026-04-23; **sin push en 4 meses** |
| [gridfm/gridfm-datakit](https://github.com/gridfm/gridfm-datakit) | Apache-2.0 | 170 | 40 | 2026-11-14 | genera datos de flujo de potencia para entrenar |
| [gridfm/gridfm-graphkit](https://github.com/gridfm/gridfm-graphkit) | Apache-2.0 | 113 | 41 | 2026-11-19 | entrena/fine-tunea el GNN fundacional; par del anterior |
| [emarche/RL2Grid](https://github.com/emarche/RL2Grid) | MIT | 58 | 11 | 2026-09-16 | benchmark estandarizado de agentes RL en red realista |

Relación fork/star de `gridfm-graphkit`: **0.36** — la más alta de la categoría agéntica de esta KB.
Gente lo está bifurcando para entrenar, no sólo marcándolo. Es la señal que distingue una categoría
naciente real de una moda.

**Nuevo esta semana — MCP sobre datos de red en vivo (categoría embrionaria, 0–3 ★):**

`azmartone67/dchub-mcp-server` (MIT, *Data Center Power Index*, 300+ mercados),
`pipeworx-io/mcp-neso` (MIT, operador británico NESO), `pipeworx-io/mcp-georgia-energy` (MIT),
`sohamshindework/gridpulse` (MIT, red DE+US, scheduling carbon-aware, **creado hace dos días**).

Se registran como *prueba de viabilidad del patrón*, no como dependencias. Lo relevante para una
propuesta: conectar el API de un TSO a un agente vía MCP es ya trabajo de días.

**Hallazgo negativo que ahorra un error:** dos repos de forecasting de carga con **1764 ★ / 0 forks** y
**1627 ★ / 0 forks** (misma cuenta, `KEV0143`, cero issues en ambos). Habrían encabezado la tabla de
forecasting de esta KB. Descartados: estrellas de cuatro cifras con relación fork/star de 0.00 no son
adopción. **Regla nueva: ante >1000 ★, verificar `forks_count` e `open_issues_count` antes de escribir
la fila.**

**Categoría confirmada vacía otra vez:** agente de *ejecución* de trading mayorista. Cuarto pase
consecutivo sin encontrarlo. `assume` y `elecsim` siguen siendo simuladores.

**Deuda de verificación del pase 1, cerrada.** El primer pase dejó cinco filas con licencia `?`.
Resueltas todas hoy, y **las cinco son inutilizables** — vale la pena que quede escrito, porque una
licencia desconocida se parece demasiado a una licencia permisiva cuando hay prisa:

| Repo | Veredicto | Evidencia |
|------|-----------|-----------|
| `Basil-Saad/smart-water-grid-ai` | ❌ **"All rights reserved"** | el `LICENSE` dice literalmente *"No permission is granted to copy, modify, redistribute, or use this project"*; publicado *"for academic and portfolio purposes only"* |
| `sariekiriyuu/smartEMS-MultiAgent-Demo` | ❌ **no comercial** | *"Custom License Agreement"*: permiso sólo para uso *personal, educational, and non-commercial* |
| `Marinalizm/BESS-energy-management-system` | ❌ sin licencia | sin archivo en ninguna rama |
| `ArsamAryandoust/awesome-ml-power-systems` | ❌ sin licencia | sin archivo en ninguna rama |
| `Legalagecolouring820/Random-Forest-Model-EMS-...` | ❌ sin licencia | sin archivo en ninguna rama |

**La lección**: `?` en una columna de licencia no es neutral, es **deuda**. De cinco casos, cero
resultaron usables — dos de ellos con prohibición expresa. Ninguna fila con licencia sin resolver
debería sobrevivir a un pase.

⚠️ **Nota de homónimos**: existen **dos** repos `smartEMS-MultiAgent-Demo` distintos
(`sariekiriyuu/`, 3 ★ y `lhg96/`, 6 ★), con la misma descripción. No son el mismo proyecto ni un
renombre: resuelven por separado en la API con contadores distintos. Al citar uno, incluir el owner.

---

## 2026-11-20 — pase 3 (la capa agéntica europea y su licencia)

**Titular del pase: existen DOS stacks agénticos energéticos, no uno, y se distinguen por licencia.
El norteamericano (`Power-Agent`, Harvard SEAS) es MIT. El europeo, que esta KB no tenía registrado,
se está consolidando bajo LF Energy y es MPL-2.0 — copyleft de archivo, no permisivo.**

Los dos pases anteriores de hoy registraron el stack MIT y lo declararon "el punto de partida más
fuerte que existe". Sigue siendo cierto para North America. Pero para un encargo con un TSO europeo
la respuesta es otra, y es la que faltaba.

### El hallazgo que cierra una pregunta abierta: la organización `ainetus` existe

El pase anterior registró AINETUS a partir de prensa (Enlit, LF Energy) **sin localizar el código**.
Está en GitHub, bajo la organización `ainetus`, activa esta semana:

| Nombre | Licencia | Descripción | Stars | Forks | Último push | Región origen |
|--------|----------|-------------|-------|-------|-------------|---------------|
| [ainetus/ExpertOp4Grid](https://github.com/ainetus/ExpertOp4Grid) | **MPL-2.0** | Sistema experto que **opera** una red eléctrica: motor de recomendación de maniobras topológicas. Núcleo del asistente de operación AINETUS (proyecto AI4REALNET, gobernanza LF Energy) | 12 | 4 | 2026-11-18 | EMEA |
| [ainetus/Expert_op4grid_recommender](https://github.com/ainetus/Expert_op4grid_recommender) | **MPL-2.0** | Recomendador basado en los principios de ExpertOp4Grid: analiza y propone acciones al operador | 1 | 3 | 2026-11-18 | EMEA |
| [ainetus/soft_label_gnn](https://github.com/ainetus/soft_label_gnn) | **MPL-2.0** | GNN con etiquetas blandas para el mismo programa de investigación | 4 | 3 | 2026-03-05 | EMEA |
| [ainetus/Grid2Op_MORL](https://github.com/ainetus/Grid2Op_MORL) | **MPL-2.0** | RL multi-objetivo sobre Grid2Op | 0 | 2 | 2026-06-11 | EMEA |

**Lectura honesta de las cifras**: 12 ★ es *muy* poco. No es un proyecto con comunidad; es código de
investigación con respaldo institucional (RTE, AI4REALNET, LF Energy) publicado hace ~6 meses. Su
valor no está en la tracción sino en **de quién viene y con qué se integra**.

### La pieza que faltaba entre el agente y la sala de control

| Nombre | Licencia | Descripción | Stars | Forks | Último push | Región origen |
|--------|----------|-------------|-------|-------|-------------|---------------|
| [opfab/operatorfabric-core](https://github.com/opfab/operatorfabric-core) | **MPL-2.0** | Plataforma LF Energy de **sala de control**: agrega, prioriza y encamina notificaciones y tarjetas de acción a los operadores. Es el sitio donde un agente deposita una recomendación para que un humano la vea y la acepte | 42 | 29 | 2026-11-19 | EMEA |
| [PowerGridModel/power-grid-model-ai](https://github.com/PowerGridModel/power-grid-model-ai) | **MPL-2.0** | **Agent Skills** para `power-grid-model` (LF Energy / Alliander): da al LLM acceso al motor de cálculo de red de grado producción | 5 | 2 | 2026-11-17 | EMEA |

`operatorfabric-core` es el hallazgo de arquitectura del pase. Esta KB ya registraba motores de
cálculo, entornos RL y servidores MCP, pero **ninguna pieza de "human-in-the-loop"**. En operación de
red eso no es un detalle: ningún TSO deja que un agente ejecute una maniobra. La recomendación tiene
que llegar a una sala de control, con trazabilidad y aceptación explícita. Ese es el componente.

### Lo que esto cambia en una decisión concreta

- **Un encargo europeo de operación de red no se arma con `Power-Agent`.** Se arma con
  `Grid2Op` (MPL-2.0) + `ExpertOp4Grid` (MPL-2.0) + `operatorfabric-core` (MPL-2.0), que ya están
  diseñados para integrarse entre sí y comparten gobernanza.
- **MPL-2.0 no es un bloqueo, pero no es MIT.** El copyleft es **por archivo**: se puede enlazar
  desde código propietario y distribuir el conjunto, pero las modificaciones *a los archivos MPL*
  deben publicarse. Para un entregable de cliente eso es manejable; para uno de marca blanca donde
  el cliente quiere el motor modificado y cerrado, no lo es. Hay que decidirlo al inicio, no al final.
- **El patrón de licencia tiene geografía.** No es casualidad: la capa americana nace en universidad
  (Harvard → MIT) y la europea en operadores de red (RTE/Alliander → MPL, la licencia de PowSyBl y
  Grid2Op). Conviene anticiparlo al estimar cualquier encargo transatlántico.

## 2026-11-20 — pase 2 (barrido de huecos declarados)

**Titular del pase: la categoría agéntica energética no se agota en `Power-Agent`. Apareció una
plataforma de control distribuido con 504 ★ cuya licencia esta KB nunca había resuelto, y un
segundo servidor MCP de EnergyPlus que sí es MIT.**

Este pase no buscó novedades por buzzword: atacó uno por uno los **gaps declarados** del pase
anterior de hoy. Tres de ellos ya no son gaps.

| Nombre | Licencia | Descripción | Stars | Forks | Último push | Región origen |
|--------|----------|-------------|-------|-------|-------------|---------------|
| [VOLTTRON/volttron](https://github.com/VOLTTRON/volttron) | **Apache-2.0** (resuelta; la API dice `NOASSERTION`) | Plataforma de control distribuido de PNNL/Battelle: bus de mensajes + agentes desplegables en edificios y equipos de red. Es **infraestructura de agentes**, anterior a los LLM y ya desplegada en campo | 504 | 284 | 2026-11-03 | North America |
| [eclipse-volttron/volttron](https://github.com/eclipse-volttron/volttron) | Apache-2.0 | **Nuevo hogar en la Eclipse Foundation.** Hoy tiene 0 ★ y un último push del 2026-07-21: la migración está empezada, no terminada | 0 | 1 | 2026-07-21 | North America |
| [idfkit/idfkit-mcp](https://github.com/idfkit/idfkit-mcp) | **MIT** (verificada en `LICENSE` crudo) | Segundo servidor MCP para EnergyPlus. **Licencia limpia**, al contrario que el de LBNL | 14 | 2 | 2026-11-16 | North America |
| [assume-framework/assume](https://github.com/assume-framework/assume) | MIT | Simulación **basada en agentes de mercados eléctricos** (Fraunhofer IEE / INATECH / TU Dresden). Rompe el gap "cero repos de mercados" | 128 | 53 | 2026-11-19 | EMEA |

### Lo que esto cambia en una decisión concreta

- **`EnergyPlus-MCP` (LBNL, 130 ★) ya no es la única puerta a EnergyPlus por MCP.** El pase anterior
  advirtió —con razón— que su licencia es una BSD modificada sin archivo `LICENSE`, con derechos del
  gobierno de EE. UU. y contacto de IP en LBNL. `idfkit-mcp` es **MIT verificada**, con el coste de
  ser mucho más joven (14 ★, v. inicial). Para un entregable de marca blanca con revisión legal
  corta, `idfkit-mcp` es el camino; para cobertura funcional (35 tools), el de LBNL.
- **`VOLTTRON` es Apache-2.0 y lleva años en edificios reales.** Es la pieza que faltaba entre "la
  plataforma copyleft de registro" y "la capa agéntica MIT": permite ejecutar agentes **en el borde**,
  junto al equipo, sin AGPL. Que esté migrando a Eclipse es una señal de gobernanza, pero
  **la org nueva todavía no es la fuente de verdad** — hoy el código vivo está en `VOLTTRON/volttron`.

### Advertencia de método que cambió este pase

El pase anterior fijó la regla "`NOASSERTION` ≠ sin licencia: leer el `LICENSE` crudo". Esa regla es
necesaria pero **insuficiente**: `oemof/oemof-solph` (430 ★) y `pypsa-meets-earth/pypsa-earth`
(384 ★) **no tienen archivo `LICENSE` en ninguna rama** y sin embargo sí declaran licencia, en un
identificador **SPDX dentro de `pyproject.toml` / `README`** (estándar REUSE):

- `oemof-solph` → `SPDX-License-Identifier: MIT` en `pyproject.toml` (+ `LICENSES/MIT.txt`).
- `pypsa-earth` → `SPDX-License-Identifier: AGPL-3.0-or-later` en el `README`.

Regla nueva, en orden: **(1) `LICENSE` crudo → (2) SPDX en `pyproject.toml`/`README` → (3) sólo
entonces declararlo irresuelto.** Saltarse el paso 2 habría costado descartar un repo MIT de 430 ★ y,
peor, **haber tratado como permisivo un AGPL de 384 ★**.

### Canales de verificación de este pase (cambiaron respecto del anterior)

| Canal | Pase anterior | Hoy |
|-------|---------------|-----|
| `api.github.com` / `github.com` vía curl | HTTP 403 (política de host) | **HTTP 200** |
| `gh api search/repositories` con `q=repo:owner/name` | funciona | funciona (único camino fiable) |
| `gh api repos/{owner}/{repo}` | no registrado | **403**: la sesión sólo alcanza sus repos configurados |
| `raw.githubusercontent.com` | 200 | 200 |
| `huggingface.co` | "no resuelve" | **403 del proxy** — es política de red, no DNS |
| `gitee.com` | no probado | **403 del proxy** → la hipótesis "los repos chinos están en Gitee" **no se puede testear desde aquí** |
| `eur-lex.europa.eu` | no probado | **403 del proxy** → la verificación del AI Act contra el Diario Oficial que pidió el pase anterior **es imposible en este entorno** |
| Fetch directo de páginas (arxiv.org, oati.com, twobirds.com) | no registrado | **falla DNS/allowlist** → todo dato de prensa de este pase es de **snippet de búsqueda, no de fuente primaria** |

**Consecuencia honesta**: en esta KB, sólo lo verificado contra GitHub es dato de primera mano.
Todo lo regulatorio y de mercado es secundario, y está marcado como tal.

---

## 2026-11-20 — pase 1 (verificación del stack agéntico)

**Titular del pase: apareció un stack agéntico energético completo, todo MIT, y un servidor MCP de
laboratorio nacional.** Verificado contra la GitHub REST API.

| Nombre | Licencia | Descripción | Stars | Último push |
|--------|----------|-------------|-------|-------------|
| [Power-Agent/PowerMCP](https://github.com/Power-Agent/PowerMCP) | MIT | Servidores MCP para software de sistemas de potencia (PowerWorld y otros) | 238 | 2026-11-17 |
| [LBNL-ETA/EnergyPlus-MCP](https://github.com/LBNL-ETA/EnergyPlus-MCP) | BSD modificada | Primer servidor MCP open source para EnergyPlus: 35 tools sobre modelos IDF (LBNL) | 130 | 2026-11-20 |
| [Power-Agent/PowerSkills](https://github.com/Power-Agent/PowerSkills) | MIT | Agent Skills para análisis de sistemas de potencia | 81 | 2026-10-24 |
| [open-energy-transition/pypsa-mcp](https://github.com/open-energy-transition/pypsa-mcp) | MIT | PyPSA expuesto a LLMs vía MCP | 74 | 2026-03-20 |
| [Power-Agent/PowerFM](https://github.com/Power-Agent/PowerFM) | MIT | Foundation models para potencia y energía | 59 | 2026-10-24 |
| [Power-Agent/PowerAgentBench](https://github.com/Power-Agent/PowerAgentBench) | MIT | Benchmark de agentes de sistemas de potencia | 50 | 2026-11-02 |
| [Power-Agent/PowerWF](https://github.com/Power-Agent/PowerWF) | MIT | Workflows agénticos para sistemas de potencia | 44 | 2026-11-12 |

**Qué cambió respecto del pase de 2026-08-01**: ese pase registró `X-GridAgent`, `GridMind` y
`PowerAgent` como *papers* (arXiv, Argonne, Harvard). Hoy `Power-Agent` es **código MIT publicado y
versionado** en cinco repos, con benchmark propio. La categoría pasó de literatura a software
instalable en ~3 meses.

**Señal de madurez a vigilar**: que `PowerAgentBench` exista antes que la adopción masiva. Igual que
en automotive, publicar el propio benchmark/defeater count se volvió movida de credibilidad.

**Advertencia sobre `EnergyPlus-MCP`**: no tiene archivo `LICENSE`; el README declara BSD modificada
con texto en `License.txt`. Versión **0.1.0**. No asumir licencia desde la API (devuelve
`NOASSERTION`).

---

## Historial

### 2026-07-02 — pase automático (datos NO verificados)

⚠️ **Advertencia añadida 2026-11-20**: las filas de abajo provienen de un pipeline de keyword-match
sin verificación. Al menos una (`mtd`, conversor de Markdown a DOCX) **no pertenece al dominio
energético**, y varias tienen 0–2 stars. Se conservan por la regla append-only, **no** como
hallazgos curados. No usar en una propuesta.
Re-verificadas el 2026-11-20 contra la API: **3 de 10 URLs ya no resuelven** (`Hartblack356/mtd` y `Legalagecolouring820/Random-Forest-Model-...` fueron borradas; `openremote/openremote` fue renombrada a `openremote/core`). Ese 30 % de link-rot en 4 meses es la razón por la que cada pase debe re-verificar y no arrastrar filas.


> Última actualización: 2026-07-02

| Nombre | Licencia | Descripción | Stars |
|--------|----------|-------------|-------|
| [smart-water-grid-ai](https://github.com/Basil-Saad/smart-water-grid-ai) | ? | AI-powered IoT smart water grid management system, Firebase, XGBoost, and Digita | 1 |
| [oscp-go](https://github.com/ChargePi/oscp-go) | MIT | Open Smart Charging Protocol SDK for Go | 3 |
| [BESS-energy-management-system](https://github.com/Marinalizm/BESS-energy-management-system) | ? | ⚡ Monitor and control your 300MW Battery Energy Storage System (BESS) in real-ti | 2 |
| [smartEMS-MultiAgent-Demo](https://github.com/sariekiriyuu/smartEMS-MultiAgent-Demo) | NOASSERTION | ⚡ Simulate and visualize energy management with a multi-agent AI framework for r | 2 |
| [mtd](https://github.com/Hartblack356/mtd) | MIT | Convert Markdown to DOCX and ODT with themes, YAML frontmatter, and CLI, SDK, or | 0 |
| [pyiec61850-ng](https://github.com/f0rw4rd/pyiec61850-ng) | GPL-3.0 | Python bindings for libiec61850, packaged as a Python wheel based on libiec61850 | 6 |
| [grid-gym](https://github.com/pt9912/grid-gym) | NOASSERTION | grid-gym is an open-source platform for deterministic simulation and validation  | 2 |
| [awesome-ml-power-systems](https://github.com/ArsamAryandoust/awesome-ml-power-systems) | ? | A curated collection of papers, datasets, software, benchmarks, and resources at | 1 |
| [openremote](https://github.com/openremote/openremote) | NOASSERTION | 100% open-source IoT Platform - Integrate your devices, add intelligence, build  | 1.8k |
| [Random-Forest-Model-EMS-system-data-machine-learning-early-warning](https://github.com/Legalagecolouring820/Random-Forest-Model-EMS-system-data-machine-learning-early-warning) | ? | Predict EMS data with random forest to flag machine issues early and improve ene | 0 |

---
*Pipeline automático — se actualiza cada hora.*
---
