# TALLER 1 — Formulación de Problemas de Optimización

**Optimización**

**Universidad Nacional de Colombia — Sede Bogotá**

Ingeniería de Sistemas & Ingeniería Industrial  

Estudiante: john jairo paez albino

---

## INSTRUCCIONES

Para cada problema se debe:

1. Definir claramente las **variables de decisión**
2. Escribir la **función objetivo** (indicar si maximiza o minimiza)
3. Escribir todas las **restricciones** (indicar el tipo: ≤, ≥ o =)

---

## PARTE A (3 puntos)

### Problema 1 — Producción de muebles

**Enunciado:** Una empresa produce sillas (S) y mesas (M). Cada silla genera $12.000 de ganancia y cada mesa $20.000. Fabricar una silla requiere 2 horas de carpintería y una mesa 5 horas. La planta dispone de máximo 40 horas de carpintería por semana. Por limitaciones de pintura, no se pueden fabricar más de 10 sillas por semana.

**Variables de decisión:**

- $S$ = número de sillas producidas por semana (unidades/semana)
- $M$ = número de mesas producidas por semana (unidades/semana)

**Función objetivo (Maximizar):**

$$\max Z = 12{,}000\,S + 20{,}000\,M$$

**Restricciones:**

| # | Restricción | Tipo | Descripción |
|---|-------------|------|-------------|
| 1 | $2S + 5M \leq 40$ | ≤ | Horas de carpintería disponibles |
| 2 | $S \leq 10$ | ≤ | Capacidad de pintura para sillas |
| 3 | $S \geq 0$ | ≥ | No negatividad |
| 4 | $M \geq 0$ | ≥ | No negatividad |

---

### Problema 2 — Distribución de procesos entre núcleos

**Enunciado:** Un sistema de cómputo debe distribuir exactamente 200 procesos entre Núcleo A y Núcleo B. El Núcleo A procesa cada tarea en 2 ms y el Núcleo B en 6 ms. El Núcleo A no puede recibir más de 150 procesos. Se quiere minimizar el tiempo total de procesamiento.

**Variables de decisión:**

- $A$ = número de procesos asignados al Núcleo A (procesos)
- $B$ = número de procesos asignados al Núcleo B (procesos)

**Función objetivo (Minimizar):**

$$\min Z = 2A + 6B$$

donde $Z$ está en milisegundos (ms).

**Restricciones:**

| # | Restricción | Tipo | Descripción |
|---|-------------|------|-------------|
| 1 | $A + B = 200$ | = | Distribuir exactamente 200 procesos |
| 2 | $A \leq 150$ | ≤ | Límite de memoria caché del Núcleo A |
| 3 | $A \geq 0$ | ≥ | No negatividad |
| 4 | $B \geq 0$ | ≥ | No negatividad |

---

### Problema 3 — Problema inventado: Asignación de servidores en la nube

**Enunciado:** Una startup tecnológica necesita desplegar sus microservicios en dos tipos de instancias en la nube: instancias estándar ($X$) e instancias de alto rendimiento ($Y$). Cada instancia estándar cuesta \$50 USD/hora y puede manejar 100 solicitudes/segundo; cada instancia de alto rendimiento cuesta \$120 USD/hora y maneja 300 solicitudes/segundo. El sistema debe atender al menos 2.000 solicitudes/segundo en hora pico. El presupuesto total disponible es de \$1.500 USD/hora. Además, por restricciones de licenciamiento del proveedor, la suma total de instancias no puede superar 20.

**Variables de decisión:**

- $X$ = número de instancias estándar desplegadas (instancias)
- $Y$ = número de instancias de alto rendimiento desplegadas (instancias)

**Función objetivo (Minimizar costo):**

$$\min Z = 50X + 120Y$$

**Restricciones:**

| # | Restricción | Tipo | Descripción |
|---|-------------|------|-------------|
| 1 | $100X + 300Y \geq 2{,}000$ | ≥ | Demanda mínima de solicitudes/segundo |
| 2 | $X + Y \leq 20$ | ≤ | Máximo de instancias por licenciamiento |
| 3 | $X \geq 0$ | ≥ | No negatividad |
| 4 | $Y \geq 0$ | ≥ | No negatividad |

---

## PARTE B

### Problema 4 — Producción de alimentos

**Enunciado:** Una fábrica produce Granola (G), Cereal (C) y Avena (A) con las siguientes características:

| Producto | Ganancia/kg | Horas máquina/kg | Materia prima/kg |
|----------|-------------|-------------------|------------------|
| Granola  | $8.000      | 1 h               | 2 kg             |
| Cereal   | $5.000      | 0.5 h             | 1 kg             |
| Avena    | $6.000      | 0.8 h             | 1.5 kg           |

Restricciones: máximo 80 horas-máquina/semana, máximo 120 kg de materia prima/semana, al menos 10 kg de avena/semana, y la producción de granola no puede superar la de cereal.

**Variables de decisión:**

- $G$ = kg de Granola producidos por semana (kg/semana)
- $C$ = kg de Cereal producidos por semana (kg/semana)
- $A$ = kg de Avena producidos por semana (kg/semana)

**Función objetivo (Maximizar):**

$$\max Z = 8{,}000\,G + 5{,}000\,C + 6{,}000\,A$$

**Restricciones:**

| # | Restricción | Tipo | Descripción |
|---|-------------|------|-------------|
| 1 | $1G + 0.5C + 0.8A \leq 80$ | ≤ | Horas-máquina disponibles |
| 2 | $2G + 1C + 1.5A \leq 120$ | ≤ | Materia prima disponible |
| 3 | $A \geq 10$ | ≥ | Demanda mínima de avena |
| 4 | $G \leq C$ (equivalente: $G - C \leq 0$) | ≤ | Granola no puede superar a cereal |
| 5 | $G \geq 0$ | ≥ | No negatividad |
| 6 | $C \geq 0$ | ≥ | No negatividad |
| 7 | $A \geq 0$ | ≥ | No negatividad |

---

### Problema 5 — Sistema de notificaciones

**Enunciado:** Una empresa debe enviar exactamente 2.000 notificaciones por campaña usando Push (P), Email (E) y SMS (S). Costos: Push = \$0.01, Email = \$0.005, SMS = \$0.09. Restricciones: máximo 500 SMS, mínimo 800 Push, y la cantidad de Emails debe ser al menos el doble de SMS.

**Variables de decisión:**

- $P$ = número de notificaciones Push enviadas (notificaciones/campaña)
- $E$ = número de notificaciones por Email enviadas (notificaciones/campaña)
- $S$ = número de notificaciones por SMS enviadas (notificaciones/campaña)

**Función objetivo (Minimizar):**

$$\min Z = 0.01P + 0.005E + 0.09S$$

**Restricciones:**

| # | Restricción | Tipo | Descripción |
|---|-------------|------|-------------|
| 1 | $P + E + S = 2{,}000$ | = | Total exacto de notificaciones |
| 2 | $S \leq 500$ | ≤ | Máximo de SMS por privacidad |
| 3 | $P \geq 800$ | ≥ | Mínimo de Push por experiencia de usuario |
| 4 | $E \geq 2S$ (equivalente: $E - 2S \geq 0$) | ≥ | Emails al menos el doble de SMS |
| 5 | $P \geq 0$ | ≥ | No negatividad |
| 6 | $E \geq 0$ | ≥ | No negatividad |
| 7 | $S \geq 0$ | ≥ | No negatividad |

---

## PARTE C

### Problema 6 — E-commerce: centro de distribución + sistema de gestión

**Enunciado:** Una empresa de e-commerce vende Electrónicos (E) y Ropa (R). Cada pedido de Electrónicos genera \$45.000 y cada pedido de Ropa \$18.000. Restricciones del centro de distribución: preparar un pedido de Electrónicos toma 30 min y uno de Ropa 10 min; 5.400 min/semana disponibles; máximo 300 pedidos de Electrónicos. Restricciones del sistema: máximo 800 transacciones/semana (pero solo el 85% disponible = 680); Ropa no puede superar el triple de Electrónicos.

**Variables de decisión:**

- $E$ = número de pedidos de Electrónicos gestionados por semana (pedidos/semana)
- $R$ = número de pedidos de Ropa gestionados por semana (pedidos/semana)

**Función objetivo (Maximizar):**

$$\max Z = 45{,}000\,E + 18{,}000\,R$$

**Restricciones:**

| # | Restricción | Tipo | Origen | Descripción |
|---|-------------|------|--------|-------------|
| 1 | $30E + 10R \leq 5{,}400$ | ≤ | Industrial | Tiempo de bodega semanal |
| 2 | $E \leq 300$ | ≤ | Industrial | Espacio de almacenamiento |
| 3 | $E + R \leq 680$ | ≤ | Sistemas | Capacidad de transacciones (85% de 800) |
| 4 | $R \leq 3E$ (equivalente: $R - 3E \leq 0$) | ≤ | Sistemas | Estabilidad del sistema |
| 5 | $E \geq 0$ | ≥ | — | No negatividad |
| 6 | $R \geq 0$ | ≥ | — | No negatividad |

---

#### Preguntas adicionales

**a) Identificación de restricciones por tipo:**

- **Restricciones de tipo Industrial (centro de distribución):**
  - Restricción 1: tiempo de bodega ($30E + 10R \leq 5{,}400$)
  - Restricción 2: espacio de almacenamiento ($E \leq 300$)

- **Restricciones de tipo Sistemas (sistema de gestión):**
  - Restricción 3: capacidad de transacciones ($E + R \leq 680$)
  - Restricción 4: estabilidad del sistema ($R \leq 3E$)

**b) ¿Es el problema lineal o no lineal?**

El problema es **lineal**. Tanto la función objetivo como todas las restricciones son combinaciones lineales de las variables de decisión $E$ y $R$. No hay productos entre variables (como $E \cdot R$), ni potencias ($E^2$), ni funciones no lineales (logaritmos, exponenciales, etc.). Todas las expresiones son de la forma $aE + bR \leq c$, que es la forma estándar de la programación lineal.

**c) ¿Variables continuas o enteras?**

Las variables **deberían ser enteras**. Cada variable representa un número de pedidos, y un pedido es una unidad discreta e indivisible: no tiene sentido gestionar 3.7 pedidos de Electrónicos ni 12.5 pedidos de Ropa. Por lo tanto, el modelo debería formularse como un problema de **programación lineal entera (ILP)**. En la práctica, dado que los valores óptimos suelen ser grandes, una relajación continua podría dar una buena aproximación, pero formalmente las variables deben ser enteras ($E, R \in \mathbb{Z}^+$).

---

*Optimización 2026 · Universidad Nacional de Colombia · Sede Bogotá*
