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

## Estado (pase 18 — 2026-11-24)

- **618 direcciones** inventariadas, licencia leída byte a byte, estrellas/forks/push medidos.
- Último pase: **la capa meteorológica** que alimenta todo pronóstico renovable (ECMWF `anemoi` +
  `earthkit`, `graphcast`, `neuralgcm`, NVIDIA `earth2studio`/`physicsnemo`, `Herbie`, Open Climate
  Fix, sustrato Zarr/Icechunk).
- **Lectura obligatoria antes de proponer un modelo entrenado:** `intel/trends.md` **T78** — la
  licencia que obliga cubre los **pesos** y está en el README, no en el fichero de licencia.
- **Señal de aptitud para producción**: `intel/trends.md` **T82** — ECMWF publica el nivel de
  madurez por repo (`graduated` / `incubating` / `emerging` / `sandbox` / `archived`).

---
*Red de KBs Globant AI Studios → [globant-kb](../globant-kb/)*
