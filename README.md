---
industry: energy
region: Global
updated: 2026-11-24
---

# ⚡ Energy KB

> Knowledge base de la industria **Energy** para Globant AI Studios.
> Smart grid, renewable optimization, demand forecasting, ESG reporting agents

## Estructura

```
energy-kb/
├── agents/        # Agentes AI open source de la industria
├── repos/         # Repos MIT/Apache como punto de partida
├── verticals/     # Plataformas verticales customizables con AI
├── intel/         # Mercado, players, tendencias
├── compose/       # Recetas: cómo componer soluciones
└── ingest/        # Scripts de actualización automática
```

## Uso

1. **Nuevo engagement**: leer `intel/market.md` + `repos/foundations.md`
2. **Proponer solución AI**: `agents/top.md` + `compose/patterns.md`
3. **Mantenerse al día**: correr `ingest/update.sh` semanalmente

## Estado (pase 19 — 2026-11-24)

- **636 direcciones** inventariadas, licencia leída byte a byte, estrellas/forks/push medidos.
  **Cobertura por forja, medida por primera vez en el pase 19:** 625 `github.com`, 9 `gitlab.com`,
  1 `sourceforge.net`, 1 PyPI.
- Último pase: **el plano de forja**. El inventario estaba sesgado por **forja**, no por
  vocabulario: `grep -o "gitlab.com/..."` sobre 618 direcciones devolvía **0**. Detrás había 9
  proyectos verificados —7 permisivos— de **DLR**, **DIW Berlin** y **OFFIS**: `AMIRIS`, `REMix`,
  la familia `FAME`, `DIETERpy`, y `mosaik`, el par europeo de `HELICS` que llevaba 18 pases
  ausente.
- **Lectura obligatoria antes de aceptar un veredicto de licencia:** `intel/trends.md` **T84** — un
  `other` / `NOASSERTION` de una API **no informa en ninguna de las dos direcciones**. En un mismo
  barrido, uno resolvió a Apache-2.0 y otro a LGPL-3.0-only.
- **Antes de declarar que algo no existe:** `compose/patterns.md` **Receta 66** (auditoría de forja)
  y `intel/trends.md` **T88** — cuatro sondas de hueco en inglés contra esta KB en español
  produjeron **cuatro falsos huecos**.
- **Trampa de categoría:** `AMIRIS` y `FAME` son modelos **basados en agentes** (agentes económicos),
  **no agentes LLM**. Ver `agents/top.md`.

---
*Red de KBs Globant AI Studios → [globant-kb](../globant-kb/)*
