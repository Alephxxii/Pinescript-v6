# PineScript v6 — Indicadores y Estrategias ICT

Repositorio de indicadores y estrategias programados en **PineScript v6** para TradingView, centrado en los conceptos de **ICT (Inner Circle Trader)** de Michael Huddleston.

---

## 📁 Estructura del repositorio

```
📦 Pinescript-v6
 ┣ 📂 indicators/
 ┃ ┗ 📂 ict/
 ┃   ┣ 📄 fair_value_gap.pine        — Detector de Fair Value Gaps (FVG)
 ┃   ┣ 📄 order_blocks.pine          — Detector de Order Blocks (OB)
 ┃   ┣ 📄 market_structure.pine      — BOS / CHoCH (Market Structure)
 ┃   ┗ 📄 liquidity_levels.pine      — Niveles de liquidez BSL / SSL
 ┣ 📂 strategies/
 ┃ ┗ 📂 ict/
 ┃   ┣ 📄 silver_bullet.pine         — Estrategia Silver Bullet
 ┃   ┗ 📄 ote_strategy.pine          — Estrategia OTE (Optimal Trade Entry)
 ┗ 📂 docs/
   ┣ 📄 ict_concepts.md              — Guía de referencia de conceptos ICT
   ┗ 📄 pinescript_v6_notes.md       — Notas y cambios de PineScript v6
```

---

## 🧠 Conceptos ICT cubiertos

| Concepto | Descripción |
|---|---|
| **Fair Value Gap (FVG)** | Desequilibrio de precio entre 3 velas consecutivas |
| **Order Block (OB)** | Última vela bajista/alcista antes de un movimiento impulsivo |
| **BOS** | Break of Structure — ruptura de estructura de mercado |
| **CHoCH** | Change of Character — cambio de carácter / reversión |
| **BSL / SSL** | Buy Side / Sell Side Liquidity — máximos y mínimos previos |
| **OTE** | Optimal Trade Entry — zona de retracement 61.8–79% de Fibonacci |
| **Silver Bullet** | Setup de 1 hora entre las 10:00–11:00 / 14:00–15:00 NY |
| **Power of 3 (PO3)** | Accumulation → Manipulation → Distribution |

---

## ⚙️ Requisitos

- Cuenta de **TradingView** (Free, Pro o superior)
- Acceso al editor de **Pine Script** en TradingView
- Los scripts usan `//@version=6`

---

## 🚀 Cómo usar

1. Abre TradingView → Pine Editor (botón inferior)
2. Copia el contenido del archivo `.pine` que quieras usar
3. Pégalo en el editor y haz clic en **"Add to chart"**
4. Ajusta los parámetros en el panel de configuración del indicador

---

## 📚 Documentación

- [`docs/ict_concepts.md`](docs/ict_concepts.md) — Explicación detallada de cada concepto ICT
- [`docs/pinescript_v6_notes.md`](docs/pinescript_v6_notes.md) — Cambios y mejoras de PineScript v6 vs v5

---

## ⚠️ Disclaimer

Este repositorio es únicamente con fines **educativos**. Los indicadores y estrategias aquí presentes **no constituyen asesoramiento financiero**. Opera siempre con gestión de riesgo adecuada.
