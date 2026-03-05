# Conceptos ICT — Guía de Referencia

> **ICT** = Inner Circle Trader | Metodología de trading desarrollada por **Michael J. Huddleston**.
> Basada en el comportamiento del "Smart Money" (bancos e instituciones) y en los conceptos de mercado de Forex, Futuros e Índices.

---

## 📐 Estructura de Mercado

### Break of Structure (BOS)
- Ocurre cuando el precio rompe un **swing high anterior** (en tendencia alcista) o un **swing low anterior** (en tendencia bajista).
- Confirma la **continuación** de la tendencia en curso.
- Es el tipo de ruptura más común.

### Change of Character (CHoCH)
- Ocurre cuando el precio rompe un swing **en contra de la tendencia** vigente.
  - En tendencia alcista: rompe un swing low → CHoCH bajista.
  - En tendencia bajista: rompe un swing high → CHoCH alcista.
- Señala una **posible reversión** del mercado.
- También conocido como "Market Structure Shift (MSS)".

```
Alcista:     HL — HH — HL — HH     (Higher Lows + Higher Highs)
Bajista:     LH — LL — LH — LL     (Lower Highs + Lower Lows)
BOS:         HH roto en tendencia alcista
CHoCH:       HL roto en tendencia alcista (primeras señales de reversión)
```

---

## 🧱 Order Blocks (OB)

- Un **Order Block** es la última vela de impulso opuesto antes de un movimiento agresivo.
  - **Bullish OB**: última vela bajista antes de un impulso alcista.
  - **Bearish OB**: última vela alcista antes de un impulso bajista.
- Representa las órdenes institucionales que aún no han sido ejecutadas completamente.
- Cuando el precio regresa a un OB, es una zona de entrada de alta probabilidad.

**Cómo identificarlo:**
1. Busca un movimiento impulsivo (desplazamiento).
2. Identifica la última vela contraria justo antes del impulso.
3. El cuerpo de esa vela es tu Order Block.

---

## 📊 Fair Value Gap (FVG) / Imbalance

- Se produce cuando hay un **desequilibrio de liquidez** entre tres velas consecutivas.
  - **Bullish FVG**: `high[2] < low[0]` → hay un hueco entre el máximo de la vela de hace 2 y el mínimo de la actual.
  - **Bearish FVG**: `low[2] > high[0]` → hay un hueco entre el mínimo de hace 2 y el máximo de la actual.
- El mercado tiende a **rellenar los FVG** antes de continuar.
- Son zonas de retracement de alta probabilidad.

**Tipos:**
| Tipo | También llamado |
|---|---|
| Fair Value Gap (FVG) | Imbalance, SIBI/BISI |
| Consequent Encroachment (CE) | 50% del FVG |
| Balanced Price Range (BPR) | Dos FVG opuestos que se solapan |

---

## 💧 Liquidez (Liquidity)

El mercado se mueve hacia zonas donde hay **órdenes acumuladas** (stops de retail traders).

### Buy Side Liquidity (BSL)
- Se acumula **por encima** de swing highs, dobles máximos, o líneas de tendencia alcistas.
- Retail traders ponen sus stops por encima de los máximos.
- El Smart Money sube el precio para barrer esa liquidez antes de bajar.

### Sell Side Liquidity (SSL)
- Se acumula **por debajo** de swing lows, dobles mínimos, o líneas de tendencia bajistas.
- Retail traders ponen sus stops por debajo de los mínimos.
- El Smart Money baja el precio para barrer esa liquidez antes de subir.

### Equal Highs (EQH) / Equal Lows (EQL)
- Dos o más máximos/mínimos al mismo nivel.
- Son zonas de liquidez muy fuertes.
- El mercado tiende a barrerlos antes de reversión.

---

## 📏 Optimal Trade Entry (OTE)

- Zona de retracement de **61.8% – 79%** del movimiento de Fibonacci.
- Corresponde al área donde las instituciones añaden posiciones tras un desplazamiento inicial.
- Niveles clave:
  | Nivel Fib | Significado |
  |---|---|
  | 0%   | Inicio del movimiento (swing low/high) |
  | 50%  | Equilibrium — zona de interés media |
  | 61.8% | Golden ratio — inicio de la OTE |
  | 70.5% | Nivel intermedio ICT |
  | 78.6% | Límite superior de la OTE |
  | 100% | Fin del movimiento (swing opuesto) |

---

## 🕐 Kill Zones (Ventanas de Tiempo)

Las sesiones de más alto volumen e interés institucional:

| Kill Zone | Hora NY | Mercados |
|---|---|---|
| **Asian Range** | 20:00 – 00:00 | Forex |
| **London Open** | 02:00 – 05:00 | Forex, Índices EU |
| **New York AM** | 07:00 – 10:00 | Forex, Futuros, Índices |
| **Silver Bullet AM** | 10:00 – 11:00 | Forex, NQ, ES |
| **Silver Bullet PM** | 14:00 – 15:00 | Forex, NQ, ES |
| **London Close** | 10:00 – 12:00 | Forex |

---

## ⚡ Silver Bullet Setup

Setup de alta probabilidad que ocurre **exclusivamente** en las ventanas Silver Bullet.

**Pasos:**
1. Identifica el contexto del día (alcista o bajista basado en el HTF).
2. Espera a que se forme un **FVG** dentro de la ventana 10:00–11:00 o 14:00–15:00 NY.
3. Espera el retracement al FVG.
4. Entra cuando el precio cierra de vuelta en la dirección del desplazamiento.
5. Stop: más allá del FVG. TP: swing opuesto.

---

## 🔺 Power of Three (PO3 / AMD)

El ciclo de precio en 3 fases:
1. **Accumulation** — Consolidación, rango lateral. Instituciones acumulan.
2. **Manipulation** (Judas Swing) — El precio se mueve brevemente en la dirección contraria para barrer liquidez (stops de retail).
3. **Distribution** — El precio se mueve fuertemente en la dirección real del Smart Money.

Este patrón ocurre en todas las temporalidades.

---

## 🌀 Modelo de Análisis Top-Down (HTF → LTF)

Para operar con ICT siempre se analiza de mayor a menor temporalidad:

```
Weekly (W)   →  Contexto macro: tendencia principal, niveles semanales
Daily  (D)   →  Dirección del día, niveles diarios, FVG diarios
4H / 1H      →  Estructura, OBs, FVGs para planificación de entrada
15m / 5m     →  Micro-estructura, confirmación de entrada (CHoCH / FVG LTF)
1m  / 2m     →  Ejecución final (para scalpers)
```

---

## 📖 Glosario Rápido

| Término | Significado |
|---|---|
| **BOS** | Break of Structure |
| **CHoCH / MSS** | Change of Character / Market Structure Shift |
| **OB** | Order Block |
| **FVG** | Fair Value Gap |
| **SIBI** | Sell-side Imbalance, Buy-side Inefficiency (Bullish FVG) |
| **BISI** | Buy-side Imbalance, Sell-side Inefficiency (Bearish FVG) |
| **BSL** | Buy Side Liquidity |
| **SSL** | Sell Side Liquidity |
| **EQH / EQL** | Equal Highs / Equal Lows |
| **OTE** | Optimal Trade Entry (61.8–79% Fib) |
| **CE** | Consequent Encroachment (50% del FVG) |
| **PO3 / AMD** | Power of Three / Accumulation-Manipulation-Distribution |
| **HTF** | Higher Time Frame |
| **LTF** | Lower Time Frame |
| **SMC** | Smart Money Concepts |
| **PDH / PDL** | Previous Day High / Low |
| **PWH / PWL** | Previous Week High / Low |
| **PMH / PML** | Previous Month High / Low |
