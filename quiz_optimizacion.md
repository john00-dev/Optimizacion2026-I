# Quiz de Optimización — Panadería

**Universidad Nacional de Colombia**

---

## Idea clave

| Tipo | Significado | Escoger |
|:----:|:-----------:|:-------:|
| $\leq$ | "máximo permitido" | el **menor** |
| $\geq$ | "mínimo requerido" | el **mayor** |

> **"El que manda es el más estricto."**

---

## Enunciado

Una panadería produce dos tipos de pan: **pan blanco** y **pan integral**. Cada día dispone de **60 kg de harina**, **20 kg de azúcar** y **30 horas de mano de obra**. Se quiere maximizar la ganancia diaria.

| Producto | Harina (kg) | Azúcar (kg) | Mano de obra (h) | Ganancia ($/unidad) |
|----------|:-----------:|:-----------:|:----------------:|:-------------------:|
| Pan blanco ($x_1$) | 2 | 1 | 1 | 500 |
| Pan integral ($x_2$) | 3 | 0.5 | 2 | 800 |
| **Disponible** | **60** | **20** | **30** | — |

---

## a) Variables de decisión

$$
\begin{aligned}
x_1 &= \text{número de unidades de pan blanco a producir por día} \\
x_2 &= \text{número de unidades de pan integral a producir por día}
\end{aligned}
$$

---

## b) Función objetivo

Como se quiere **maximizar la ganancia diaria**:

$$
\max\; Z = 500\,x_1 + 800\,x_2
$$

---

## c) Restricciones

$$
\begin{aligned}
\text{Harina:} \quad & 2x_1 + 3x_2 \leq 60 \\
\text{Azúcar:} \quad & x_1 + 0.5\,x_2 \leq 20 \\
\text{Mano de obra:} \quad & x_1 + 2x_2 \leq 30 \\
\text{No negatividad:} \quad & x_1,\, x_2 \geq 0
\end{aligned}
$$

---

## d) Clasificación del modelo

El modelo es de **Programación Lineal (PL)** porque:

- La función objetivo es **lineal** en las variables de decisión.
- Todas las restricciones son **lineales** (desigualdades lineales).
- Las variables son **continuas** y **no negativas**.
- Es un problema de **maximización** con recursos limitados.

> En sentido estricto, $x_1$ y $x_2$ deberían ser enteros (no se venden medias unidades de pan), por lo que en la práctica podría tratarse como **Programación Lineal Entera (PLE)**. Sin embargo, dado que el enunciado pide "resolver a mano", lo trataremos como **PL continua** y verificaremos al final si la solución es entera.

---

## e) Solución a mano (método gráfico / vértices)

### 💡 Idea general

La solución óptima de un problema de programación lineal **siempre está en una esquina** (vértice) de la región factible. Entonces el plan es:

1. Encontrar todas las esquinas.
2. Evaluar $Z$ en cada esquina.
3. La esquina con $Z$ más alto gana.

Para encontrar las esquinas, las restricciones las convertimos en **igualdades** (rectas) y las cruzamos de a pares.

Nuestras 3 rectas son:

- **Harina:** $2x_1 + 3x_2 = 60$
- **Azúcar:** $x_1 + 0.5\,x_2 = 20$
- **Mano de obra:** $x_1 + 2x_2 = 30$

Y los ejes: $x_1 = 0$ y $x_2 = 0$.

---

### Paso 1 — Encontrar dónde corta cada recta a los ejes

Esto es lo más fácil: en cada recta volvemos **una variable cero** y despejamos la otra.

#### 🍞 Recta de la harina: $2x_1 + 3x_2 = 60$

- **Hago $x_2 = 0$:** $\;2x_1 = 60 \;\Rightarrow\; x_1 = 30$ → punto $(30, 0)$
- **Hago $x_1 = 0$:** $\;3x_2 = 60 \;\Rightarrow\; x_2 = 20$ → punto $(0, 20)$

#### 🍬 Recta del azúcar: $x_1 + 0.5\,x_2 = 20$

- **Hago $x_2 = 0$:** $\;x_1 = 20$ → punto $(20, 0)$
- **Hago $x_1 = 0$:** $\;0.5\,x_2 = 20 \;\Rightarrow\; x_2 = 40$ → punto $(0, 40)$

#### ⏰ Recta de mano de obra: $x_1 + 2x_2 = 30$

- **Hago $x_2 = 0$:** $\;x_1 = 30$ → punto $(30, 0)$
- **Hago $x_1 = 0$:** $\;2x_2 = 30 \;\Rightarrow\; x_2 = 15$ → punto $(0, 15)$

---

### Paso 2 — Filtrar los puntos que SÍ caben (factibles)

Un punto es **factible** solo si cumple **TODAS** las restricciones a la vez. Revisamos uno por uno:

- #### Punto $(0, 0)$ — el origen
Trivialmente cumple todo. ✅ **Es vértice.**

- #### Sobre el eje $x_1$ (cuando $x_2 = 0$): tenemos 3 candidatos $(30,0)$, $(20,0)$, $(30,0)$

¿Cuál es el verdadero borde? El más cercano al origen, porque los otros se pasan de alguna restricción.

Probemos $(30, 0)$ en **azúcar**: $30 + 0.5(0) = 30$. Pero el límite es 20. ❌ Se pasa.

Probemos $(20, 0)$ en todas:
- Harina: $2(20) = 40 \leq 60$ ✅
- Azúcar: $20 \leq 20$ ✅
- Mano de obra: $20 \leq 30$ ✅

✅ **$(20, 0)$ es vértice.**

- #### Sobre el eje $x_2$ (cuando $x_1 = 0$): tenemos 3 candidatos $(0,20)$, $(0,40)$, $(0,15)$

Probemos $(0, 20)$ en **mano de obra**: $0 + 2(20) = 40 > 30$ ❌ Se pasa.

Probemos $(0, 15)$ en todas:
- Harina: $3(15) = 45 \leq 60$ ✅
- Azúcar: $0.5(15) = 7.5 \leq 20$ ✅
- Mano de obra: $2(15) = 30 \leq 30$ ✅

✅ **$(0, 15)$ es vértice.**

---

### Paso 3 — Encontrar las esquinas donde se cruzan dos rectas (no en los ejes)

Cruzamos las rectas **de a pares** (resolviendo el sistema de 2 ecuaciones) y verificamos si el punto cumple la restricción que sobra.

#### Cruce 1: Harina × Azúcar

$$
\begin{cases}
2x_1 + 3x_2 = 60 \\
x_1 + 0.5\,x_2 = 20
\end{cases}
$$

Resolviendo el sistema, se obtiene $x_1 = 15$ y $x_2 = 10$.

¿Cumple **mano de obra**? $\;15 + 2(10) = 35 > 30$ ❌ **No es vértice.**

#### Cruce 2: Azúcar × Mano de obra ⭐

$$
\begin{cases}
x_1 + 0.5\,x_2 = 20 \\
x_1 + 2x_2 = 30
\end{cases}
$$

Resolviendo el sistema, se obtiene $x_1 = \tfrac{50}{3} \approx 16.67$ y $x_2 = \tfrac{20}{3} \approx 6.67$.

¿Cumple **harina**? $\;2(\tfrac{50}{3}) + 3(\tfrac{20}{3}) = \tfrac{160}{3} \approx 53.33 \leq 60$ ✅ **Es vértice.**

#### Cruce 3: Harina × Mano de obra

$$
\begin{cases}
2x_1 + 3x_2 = 60 \\
x_1 + 2x_2 = 30
\end{cases}
$$

Resolviendo el sistema, se obtiene $x_1 = 30$ y $x_2 = 0$.

¿Cumple **azúcar**? $\;30 > 20$ ❌ **No es vértice.**

---

### 🎯 Resumen de vértices factibles

| Vértice | Coordenadas | ¿De dónde sale? |
|:-------:|:-----------:|:----------------|
| A | $(0, 0)$ | Origen |
| B | $(20, 0)$ | Eje $x_1$ con azúcar |
| C | $(\tfrac{50}{3}, \tfrac{20}{3})$ | Cruce azúcar × mano de obra |
| E | $(0, 15)$ | Eje $x_2$ con mano de obra |

### Paso 4 — Evaluar $Z$ en cada vértice factible

| Vértice | $(x_1, x_2)$ | $Z = 500x_1 + 800x_2$ |
|:-------:|:------------:|:----------------------:|
| A | $(0, 0)$ | $0$ |
| B | $(20, 0)$ | $500(20) + 800(0) = 10{,}000$ |
| C | $(50/3,\; 20/3)$ | $500(50/3) + 800(20/3) = \tfrac{25{,}000 + 16{,}000}{3} = \tfrac{41{,}000}{3} \approx 13{,}666.67$ |
| E | $(0, 15)$ | $500(0) + 800(15) = 12{,}000$ |

### Paso 5 — Solución óptima

El máximo se alcanza en el vértice **C**:

$$
\boxed{x_1^* = \tfrac{50}{3} \approx 16.67, \quad x_2^* = \tfrac{20}{3} \approx 6.67, \quad Z^* = \tfrac{41{,}000}{3} \approx \$13{,}666.67}
$$

### Paso 6 — Verificación de las restricciones en el óptimo

- **Harina:** $2(\tfrac{50}{3}) + 3(\tfrac{20}{3}) = \tfrac{160}{3} \approx 53.33 \leq 60$ ✅ (no activa, sobran ≈ 6.67 kg)
- **Azúcar:** $\tfrac{50}{3} + 0.5(\tfrac{20}{3}) = \tfrac{50}{3} + \tfrac{10}{3} = 20 \leq 20$ ✅ (activa)
- **Mano de obra:** $\tfrac{50}{3} + 2(\tfrac{20}{3}) = \tfrac{90}{3} = 30 \leq 30$ ✅ (activa)

Las restricciones de **azúcar** y **mano de obra** son las que limitan la producción óptima.

---

## Solución entera (interpretación práctica)

Como no se pueden producir fracciones de pan, evaluamos los enteros cercanos al óptimo continuo respetando todas las restricciones:

| $(x_1, x_2)$ | Harina | Azúcar | M. obra | $Z$ |
|:------------:|:------:|:------:|:-------:|:---:|
| $(16, 7)$ | $2(16)+3(7)=53$ ✅ | $16+3.5=19.5$ ✅ | $16+14=30$ ✅ | $500(16)+800(7)=13{,}600$ |
| $(17, 6)$ | $34+18=52$ ✅ | $17+3=20$ ✅ | $17+12=29$ ✅ | $8{,}500+4{,}800=13{,}300$ |
| $(15, 7)$ | $30+21=51$ ✅ | $15+3.5=18.5$ ✅ | $15+14=29$ ✅ | $7{,}500+5{,}600=13{,}100$ |

El mejor valor entero es:

$$
\boxed{x_1 = 16,\quad x_2 = 7,\quad Z = \$13{,}600}
$$

---

## Resumen final

- **Solución óptima continua:** $x_1 = 50/3$, $x_2 = 20/3$, $Z = \$41{,}000/3 \approx \$13{,}666.67$
- **Solución óptima entera:** $x_1 = 16$ panes blancos, $x_2 = 7$ panes integrales, $Z = \$13{,}600$
- Las restricciones **activas** (recursos agotados) son **azúcar** y **mano de obra**.
- Sobra harina, lo que sugiere que comprar más harina **no aumentaría** la ganancia; el cuello de botella está en el azúcar y la mano de obra.

---
---

# Quiz 2 — Aerolínea Regional

## Enunciado

Una aerolínea regional opera **4 rutas domésticas** con **3 tipos de aeronave**. Cada aeronave tiene un **costo operativo por vuelo** (en millones de pesos) y una **capacidad de pasajeros distinta según la ruta**. La aerolínea debe garantizar transportar **al menos un número mínimo de pasajeros por ruta** cada semana y **no puede exceder las horas de vuelo disponibles** por aeronave. El objetivo es **minimizar el costo operativo total**.

| Aeronave | Ruta 1 (pas.) | Ruta 2 (pas.) | Ruta 3 (pas.) | Ruta 4 (pas.) | Horas disp. | Costo/vuelo (M$) |
|----------|:-------------:|:-------------:|:-------------:|:-------------:|:-----------:|:----------------:|
| A ($x_1$) | 80 | 60 | 90 | 50 | 120 h | 15 |
| B ($x_2$) | 50 | 120 | 70 | 80 | 100 h | 20 |
| C ($x_3$) | 110 | 80 | 50 | 60 | 90 h | 18 |
| **Mín. pasajeros** | **400** | **480** | **360** | **320** | — | — |

> Cada vuelo de la **Aeronave A dura 3 h**, la **B dura 4 h** y la **C dura 2.5 h**.

---

## a) Variables de decisión

$$
\begin{aligned}
x_1 &= \text{número de vuelos a la semana de la aeronave A} \\
x_2 &= \text{número de vuelos a la semana de la aeronave B} \\
x_3 &= \text{número de vuelos a la semana de la aeronave C}
\end{aligned}
$$

---

## b) Función objetivo

Como se quiere **minimizar el costo operativo total** (en millones de pesos):

$$
\min\; Z = 15\,x_1 + 20\,x_2 + 18\,x_3
$$

---

## c) Restricciones

$$
\begin{aligned}
\text{Ruta 1 (mín. pasajeros):} \quad & 80\,x_1 + 50\,x_2 + 110\,x_3 \geq 400 \\
\text{Ruta 2 (mín. pasajeros):} \quad & 60\,x_1 + 120\,x_2 + 80\,x_3 \geq 480 \\
\text{Ruta 3 (mín. pasajeros):} \quad & 90\,x_1 + 70\,x_2 + 50\,x_3 \geq 360 \\
\text{Ruta 4 (mín. pasajeros):} \quad & 50\,x_1 + 80\,x_2 + 60\,x_3 \geq 320 \\
\text{Horas aeronave A:} \quad & 3\,x_1 \leq 120 \\
\text{Horas aeronave B:} \quad & 4\,x_2 \leq 100 \\
\text{Horas aeronave C:} \quad & 2.5\,x_3 \leq 90 \\
\text{No negatividad:} \quad & x_1,\, x_2,\, x_3 \geq 0
\end{aligned}
$$

> 💡 Las restricciones de horas se pueden simplificar a: $x_1 \leq 40$, $x_2 \leq 25$, $x_3 \leq 36$.

---

## d) Clasificación del modelo

El modelo es de **Programación Lineal (PL)** porque:

- La función objetivo es **lineal**.
- Todas las restricciones son **lineales**.
- Las variables son **continuas** y **no negativas**.
- Es un problema de **minimización** con requisitos mínimos y recursos máximos.

> En la práctica $x_1, x_2, x_3$ deberían ser enteros (no se hacen medios vuelos), por lo que sería más correcto un modelo de **Programación Lineal Entera (PLE)**.

---

## e) Solución por vértices (método del profesor)

La idea es **ordenar todos los vértices posibles** según cuántas variables son cero. Tenemos 3 variables ($x_1, x_2, x_3$), así que los casos son:

| Caso | Variables en cero | Variables activas | Tamaño del sistema |
|:----:|:-----------------:|:-----------------:|:------------------:|
| 1 | las 3 | ninguna | trivial |
| 2 | 2 (ejes) | 1 | 1×1 |
| 3 | 1 | 2 | **2×2** |
| 4 | 0 | 3 | **3×3** |

Las ecuaciones de pasajeros (en igualdad) son:

$$
\begin{aligned}
R_1:\; & 80\,x_1 + 50\,x_2 + 110\,x_3 = 400 \\
R_2:\; & 60\,x_1 + 120\,x_2 + 80\,x_3 = 480 \\
R_3:\; & 90\,x_1 + 70\,x_2 + 50\,x_3 = 360 \\
R_4:\; & 50\,x_1 + 80\,x_2 + 60\,x_3 = 320
\end{aligned}
$$

---

### 🔹 Caso 1: $V = (0, 0, 0)$

Origen → no se transporta ningún pasajero, no cumple ningún mínimo. ❌ **No factible.**

---

### 🔹 Caso 2: solo una variable activa (sobre los ejes)

Si solo se usa una aeronave, ese $x_i$ debe ser **lo suficientemente grande** para cumplir las 4 restricciones de pasajeros. Por eso tomamos el **mayor** de los valores requeridos (recuerda: con $\geq$, manda el mayor).

#### Solo A activo ($x_2 = x_3 = 0$)

| Ruta | Cota mínima de $x_1$ |
|:----:|:--------------------:|
| $R_1$ | $400/80 = 5$ |
| $R_2$ | $480/60 = 8$ ⭐ |
| $R_3$ | $360/90 = 4$ |
| $R_4$ | $320/50 = 6.4$ |

$x_1 = 8$ → $Z = 15(8) = 120$ M\$

#### Solo B activo ($x_1 = x_3 = 0$)

| Ruta | Cota mínima de $x_2$ |
|:----:|:--------------------:|
| $R_1$ | $400/50 = 8$ ⭐ |
| $R_2$ | $480/120 = 4$ |
| $R_3$ | $360/70 \approx 5.14$ |
| $R_4$ | $320/80 = 4$ |

$x_2 = 8$ → $Z = 20(8) = 160$ M\$

#### Solo C activo ($x_1 = x_2 = 0$)

| Ruta | Cota mínima de $x_3$ |
|:----:|:--------------------:|
| $R_1$ | $400/110 \approx 3.64$ |
| $R_2$ | $480/80 = 6$ |
| $R_3$ | $360/50 = 7.2$ ⭐ |
| $R_4$ | $320/60 \approx 5.33$ |

$x_3 = 7.2$ → $Z = 18(7.2) = 129.6$ M\$

---

### 🔹 Caso 3: dos variables activas (sistemas 2×2)

Cruzamos **2 de las 4 ecuaciones de rutas** y verificamos que las otras 2 se cumplan. Si fijamos una variable en 0, el sistema queda 2×2.

#### A+B activos ($x_3 = 0$)

Sistema $R_1 \cap R_2$:

$$
\begin{cases}
80x_1 + 50x_2 = 400 \\
60x_1 + 120x_2 = 480
\end{cases}
$$

Resolviendo: $x_1 \approx 3.636,\; x_2 \approx 2.182$

¿$R_3$? $\;90(3.636) + 70(2.182) = 480 \geq 360$ ✅
¿$R_4$? $\;50(3.636) + 80(2.182) = 356.4 \geq 320$ ✅

**Costo:** $Z = 15(3.636) + 20(2.182) \approx 98.18$ M\$ ⭐

> Las otras combinaciones (R1∩R3, R1∩R4, R2∩R3, R2∩R4, R3∩R4) dan resultados **no factibles** (alguna restricción se viola o sale negativo). No las repito por brevedad.

#### A+C activos ($x_2 = 0$)

Sistema $R_2 \cap R_3$:

$$
\begin{cases}
60x_1 + 80x_3 = 480 \\
90x_1 + 50x_3 = 360
\end{cases}
$$

Resolviendo: $x_1 \approx 1.143,\; x_3 \approx 5.143$

¿$R_1$, $R_4$? Ambas se cumplen ✅

**Costo:** $Z = 15(1.143) + 18(5.143) \approx 109.71$ M\$

> Las demás combinaciones de A+C dan no factibilidad.

#### B+C activos ($x_1 = 0$)

Sistema $R_1 \cap R_3$:

$$
\begin{cases}
50x_2 + 110x_3 = 400 \\
70x_2 + 50x_3 = 360
\end{cases}
$$

Resolviendo: $x_2 \approx 3.769,\; x_3 \approx 1.923$

¿$R_2$, $R_4$? Ambas se cumplen ✅

**Costo:** $Z = 20(3.769) + 18(1.923) \approx 110.0$ M\$

> Las demás combinaciones de B+C dan no factibilidad.

---

### 🔹 Caso 4: las 3 variables activas (sistema 3×3)

Cruzamos **3 de las 4 ecuaciones de rutas** y verificamos la cuarta. $\binom{4}{3} = 4$ posibilidades.

#### Sistema $R_1 \cap R_2 \cap R_3$ ⭐

$$
\begin{cases}
80x_1 + 50x_2 + 110x_3 = 400 \\
60x_1 + 120x_2 + 80x_3 = 480 \\
90x_1 + 70x_2 + 50x_3 = 360
\end{cases}
$$

Resolviendo: $x_1 \approx 1.355,\; x_2 \approx 2.231,\; x_3 \approx 1.636$

¿$R_4$? $\;50(1.355) + 80(2.231) + 60(1.636) = 344.4 \geq 320$ ✅

**Costo:** $Z = 15(1.355) + 20(2.231) + 18(1.636) \approx 94.41$ M\$ ⭐

#### Sistema $R_1 \cap R_2 \cap R_4$

Resolviendo: $x_1 \approx -3.33$ → ❌ **No factible**

#### Sistema $R_1 \cap R_3 \cap R_4$

Resolviendo: $x_1 \approx 1.813,\; x_2 \approx 1.712,\; x_3 \approx 1.540$. ¿$R_2$? $437 < 480$ ❌

#### Sistema $R_2 \cap R_3 \cap R_4$

Resolviendo: $x_3 \approx -2.4$ → ❌ **No factible**

---

### 🎯 Resumen de todos los vértices factibles

| Caso | Vértice | $x_1$ | $x_2$ | $x_3$ | $Z$ (M\$) |
|:----:|:-------:|:-----:|:-----:|:-----:|:---------:|
| 1 | $(0,0,0)$ | 0 | 0 | 0 | ❌ no factible |
| 2 | Solo A | 8 | 0 | 0 | 120 |
| 2 | Solo B | 0 | 8 | 0 | 160 |
| 2 | Solo C | 0 | 0 | 7.2 | 129.6 |
| 3 | A+B ($R_1,R_2$) | 3.636 | 2.182 | 0 | 98.18 |
| 3 | A+C ($R_2,R_3$) | 1.143 | 0 | 5.143 | 109.71 |
| 3 | B+C ($R_1,R_3$) | 0 | 3.769 | 1.923 | 110.0 |
| 4 | A+B+C ($R_1,R_2,R_3$) | 1.355 | 2.231 | 1.636 | **94.41** ⭐ |

### 🏆 Solución óptima (continua)

$$
\boxed{x_1 \approx 1.36,\quad x_2 \approx 2.23,\quad x_3 \approx 1.64,\quad Z \approx 94.41 \text{ M\$}}
$$

Es decir: usar **las 3 aeronaves**, con las restricciones activas en las **rutas 1, 2 y 3**.

### Solución entera (práctica)

Probemos $x_1 = 2$, $x_2 = 3$, $x_3 = 2$ (redondeando hacia arriba):

- Ruta 1: $80(2) + 50(3) + 110(2) = 530 \geq 400$ ✅
- Ruta 2: $60(2) + 120(3) + 80(2) = 640 \geq 480$ ✅
- Ruta 3: $90(2) + 70(3) + 50(2) = 490 \geq 360$ ✅
- Ruta 4: $50(2) + 80(3) + 60(2) = 460 \geq 320$ ✅
- Horas: todas cumplen ✅

**Costo:** $Z = 15(2) + 20(3) + 18(2) = 126$ M\$

$$
\boxed{x_1 = 2,\quad x_2 = 3,\quad x_3 = 2,\quad Z = 126 \text{ M\$}}
$$

---

## Resumen final

- **Óptimo continuo:** $x_1 \approx 1.36$, $x_2 \approx 2.23$, $x_3 \approx 1.64$, $Z \approx 94.41$ M\$
- **Óptimo entero:** $x_1 = 2$, $x_2 = 3$, $x_3 = 2$, $Z = 126$ M\$
- **Sí conviene usar las 3 aeronaves**: cada una aporta de forma complementaria.
- Las restricciones **activas** son las de **pasajeros de las rutas 1, 2 y 3**.
- Sobran **muchísimas horas** en todas las aeronaves → la flota está sobredimensionada para esta demanda.
