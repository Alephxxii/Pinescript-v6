# PineScript v6 — Notas y Cambios Relevantes

> Referencia rápida de los cambios más importantes de **PineScript versión 6** con respecto a v5, y las características clave para programar indicadores y estrategias ICT.

---

## 🆕 Novedades de PineScript v6

### 1. Declaración de versión
```pine
//@version=6
```
Todos los scripts deben comenzar con esta línea.

---

### 2. Sistema de tipos mejorado

PineScript v6 introduce tipado más estricto y explícito:

```pine
// v5 — funcionaba sin tipo explícito
myVar = 0.0

// v6 — se puede usar tipo explícito (recomendado)
float myVar = 0.0
int   count = 0
bool  flag  = false
```

**Tipos primitivos:** `int`, `float`, `bool`, `string`, `color`
**Tipos especiales:** `line`, `label`, `box`, `table`, `array<T>`, `matrix<T>`, `map<K,V>`

---

### 3. Tipos definidos por el usuario (UDT)

En v6 se pueden crear tipos personalizados (structs):

```pine
type SwingPoint
    float price
    int   barIndex
    bool  isHigh

// Crear instancia
sp = SwingPoint.new(price = high, barIndex = bar_index, isHigh = true)
log.info("Swing at price: {0}", sp.price)
```

---

### 4. Métodos de usuario

```pine
type MyLevel
    float price
    color clr

method draw(MyLevel self) =>
    line.new(bar_index - 10, self.price, bar_index, self.price, color = self.clr)

// Uso
lvl = MyLevel.new(price = close, clr = color.blue)
lvl.draw()
```

---

### 5. `switch` expression

Más legible que múltiples `if/else`:

```pine
bias = switch
    close > ta.ema(close, 200) => "Bullish"
    close < ta.ema(close, 200) => "Bearish"
    => "Neutral"
```

---

### 6. Matrices (`matrix`)

```pine
// Crear matriz de 3x3 con valor 0.0
m = matrix.new<float>(3, 3, 0.0)

// Asignar valor
matrix.set(m, 0, 0, close)

// Obtener valor
val = matrix.get(m, 0, 0)
```

---

### 7. Mapas (`map`)

Nueva estructura `map<K, V>`:

```pine
var map<string, float> levels = map.new<string, float>()
map.put(levels, "OB_High", high[1])
float obHigh = map.get(levels, "OB_High")
```

---

### 8. Logging mejorado

```pine
// Salida en la consola de Pine (solo en modo debug)
log.info("Close: {0}, EMA: {1}", close, ta.ema(close, 20))
log.warning("No hay datos de volumen")
log.error("Error en el cálculo")
```

---

### 9. `request.security` — mejoras

```pine
// Obtener datos de una TF superior
[htfHigh, htfLow] = request.security(syminfo.tickerid, "D",
     [high, low], lookahead = barmerge.lookahead_off)
```

---

### 10. `polyline` — nuevo tipo

Permite dibujar líneas con múltiples puntos:

```pine
var polyline pl = na
points = array.from(
     chart.point.from_index(bar_index - 2, low[2]),
     chart.point.from_index(bar_index - 1, low[1]),
     chart.point.from_index(bar_index,     low))
pl := polyline.new(points, curved = false, closed = false, line_color = color.blue)
```

---

## 🔧 Funciones de uso frecuente en scripts ICT

### Detección de pivotes
```pine
pivotLen = 10
ph = ta.pivothigh(high, pivotLen, pivotLen)  // swing high
pl = ta.pivotlow(low,  pivotLen, pivotLen)   // swing low
```

### ATR para filtros de impulso
```pine
atr = ta.atr(14)
isImpulse = math.abs(close - open) > atr * 1.5
```

### Sesiones por horario
```pine
// En hora de Nueva York
inNYAM = not na(time(timeframe.period, "0930-1200", "America/New_York"))
```

### Fibonacci manual
```pine
// OTE range
range_  = swingHigh - swingLow
fib618  = swingHigh - range_ * 0.618
fib786  = swingHigh - range_ * 0.786
```

### Cajas (Boxes) para FVG / OB
```pine
b = box.new(left       = bar_index[2],
            top        = high[2],
            right      = bar_index + 100,
            bottom     = low,
            bgcolor    = color.new(color.green, 80),
            border_color = color.green,
            extend     = extend.right)
```

### Líneas para niveles de liquidez
```pine
l = line.new(x1    = bar_index - pivotLen,
             y1    = ph,
             x2    = bar_index + 50,
             y2    = ph,
             color = color.red,
             style = line.style_dotted,
             extend = extend.right)
```

---

## ⚠️ Cambios de compatibilidad v5 → v6

| Característica | v5 | v6 |
|---|---|---|
| Versión | `//@version=5` | `//@version=6` |
| Tipos de usuario | No disponible | `type MyType` |
| Métodos de usuario | No disponible | `method myMethod(...)` |
| `switch` | Limitado | Completo como expresión |
| `map<K,V>` | No disponible | Disponible |
| `polyline` | No disponible | Disponible |
| `chart.point` | No disponible | Disponible |
| `log.*` | No disponible | Disponible |
| Arrays | Disponible | Mejorado |
| Matrices | Básico | Mejorado |

---

## 📐 Plantilla Base — Indicador ICT v6

```pine
//@version=6
indicator("Mi Indicador ICT", shorttitle="ICT", overlay=true, max_boxes_count=500, max_lines_count=500)

// ── Inputs ──────────────────────────────────────────────────────────────
pivotLen = input.int(10, "Pivot Length", minval=2)

// ── Tipos personalizados ─────────────────────────────────────────────────
type Level
    float price
    int   barIdx
    bool  isBull

// ── Estado ──────────────────────────────────────────────────────────────
var Level lastSwingHigh = na
var Level lastSwingLow  = na

// ── Lógica ──────────────────────────────────────────────────────────────
ph = ta.pivothigh(high, pivotLen, pivotLen)
pl = ta.pivotlow(low,  pivotLen, pivotLen)

if not na(ph)
    lastSwingHigh := Level.new(price=ph, barIdx=bar_index-pivotLen, isBull=false)

if not na(pl)
    lastSwingLow := Level.new(price=pl, barIdx=bar_index-pivotLen, isBull=true)

// ── Plots ────────────────────────────────────────────────────────────────
plotshape(not na(ph), "SH", shape.circle, location.abovebar, color.red,   offset=-pivotLen, size=size.tiny)
plotshape(not na(pl), "SL", shape.circle, location.belowbar, color.green, offset=-pivotLen, size=size.tiny)
```

---

## 📐 Plantilla Base — Estrategia ICT v6

```pine
//@version=6
strategy("Mi Estrategia ICT", shorttitle="ICT Strat",
     overlay           = true,
     initial_capital   = 10000,
     default_qty_type  = strategy.percent_of_equity,
     default_qty_value = 5,
     commission_type   = strategy.commission.percent,
     commission_value  = 0.01)

// ── Inputs ──────────────────────────────────────────────────────────────
rrRatio = input.float(2.0, "R:R", minval=0.5, step=0.5)

// ── Lógica de entrada ────────────────────────────────────────────────────
longCondition  = <tu condición>
shortCondition = <tu condición>

// ── Ejecución ────────────────────────────────────────────────────────────
if longCondition and strategy.position_size == 0
    slPrice = <stop loss>
    tpPrice = close + (close - slPrice) * rrRatio
    strategy.entry("Long", strategy.long)
    strategy.exit("Long Exit", "Long", stop=slPrice, limit=tpPrice)

if shortCondition and strategy.position_size == 0
    slPrice = <stop loss>
    tpPrice = close - (slPrice - close) * rrRatio
    strategy.entry("Short", strategy.short)
    strategy.exit("Short Exit", "Short", stop=slPrice, limit=tpPrice)
```
