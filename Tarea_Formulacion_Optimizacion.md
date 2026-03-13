# Tarea — Formulación de Problemas de Optimización

**Optimización — Logística Integrada**

**Universidad Nacional de Colombia — Sede Bogotá**

Ingeniería de Sistemas & Ingeniería Industrial

Estudiante: john jairo paez albino



## Problema 1 — Industrial (Panadería)

**Enunciado:** Una panadería produce panes (P) y tortas (T). La ganancia es de \$2 por pan y \$6 por torta. El horno requiere 1 hora para pan y 3 horas para torta. Están disponibles 18 horas por día. La demanda mínima es de al menos 2 tortas por día. Se busca maximizar la ganancia.

### Variables de decisión

- $P$ = número de panes producidos por día (unidades/día)
- $T$ = número de tortas producidas por día (unidades/día)

### Función objetivo (Maximizar)

$$\max\ Z = 2P + 6T$$

### Restricciones

| # | Restricción | Tipo | Descripción |
|---|-------------|------|-------------|
| 1 | $1P + 3T \leq 18$ | ≤ | Horas de horno disponibles por día (máximo 18 h) |
| 2 | $T \geq 2$ | ≥ | Demanda mínima de tortas por día ("al menos 2") |
| 3 | $P \geq 0$ | ≥ | No negatividad |
| 4 | $T \geq 0$ | ≥ | No negatividad |
 
### Solución
 
La torta da \$6 pero usa 3 horas → \$2/hora. El pan da \$2 y usa 1 hora → \$2/hora. Ambos rinden igual por hora, así que conviene producir las 2 tortas obligatorias y llenar el resto con panes (que no tienen mínimo obligatorio y rinden lo mismo).
 
Con $T = 2$: horas usadas = $3(2) = 6$, quedan $18 - 6 = 12$ horas → $P = 12$.
 
**Solución óptima:** $P = 12$, $T = 2$
 
$$Z = 2(12) + 6(2) = 24 + 12 = \$36$$
 
---

## Problema 2 — Sistemas (Balanceador de carga)

**Enunciado:** Un balanceador distribuye peticiones entre 3 microservicios: M1, M2 y M3. El total requerido es exactamente 500 peticiones por minuto. Las capacidades máximas son: M1 ≤ 200, M2 ≤ 250, M3 ≤ 150. Los costos por petición son: M1 = \$0.020, M2 = \$0.015, M3 = \$0.030. Se busca minimizar el costo total.

### Variables de decisión

- $M_1$ = número de peticiones por minuto asignadas al microservicio 1 (peticiones/min)
- $M_2$ = número de peticiones por minuto asignadas al microservicio 2 (peticiones/min)
- $M_3$ = número de peticiones por minuto asignadas al microservicio 3 (peticiones/min)

### Función objetivo (Minimizar)

$$\min\ Z = 0.020\,M_1 + 0.015\,M_2 + 0.030\,M_3$$

### Restricciones

| # | Restricción | Tipo | Descripción |
|---|-------------|------|-------------|
| 1 | $M_1 + M_2 + M_3 = 500$ | = | Total exacto de peticiones requeridas por minuto |
| 2 | $M_1 \leq 200$ | ≤ | Capacidad máxima del microservicio 1 |
| 3 | $M_2 \leq 250$ | ≤ | Capacidad máxima del microservicio 2 |
| 4 | $M_3 \leq 150$ | ≤ | Capacidad máxima del microservicio 3 |
| 5 | $M_1 \geq 0$ | ≥ | No negatividad |
| 6 | $M_2 \geq 0$ | ≥ | No negatividad |
| 7 | $M_3 \geq 0$ | ≥ | No negatividad |
 
### Solución
 
Para minimizar costo, priorizamos el microservicio más barato primero: M2 (\$0.015) → M1 (\$0.020) → M3 (\$0.030).
 
Llenamos M2 al máximo: $M_2 = 250$. Faltan $500 - 250 = 250$. Llenamos M1 al máximo: $M_1 = 200$. Faltan $250 - 200 = 50$. El resto va a M3: $M_3 = 50$.
 
**Solución óptima:** $M_1 = 200$, $M_2 = 250$, $M_3 = 50$
 
$$Z = 0.020(200) + 0.015(250) + 0.030(50) = 4 + 3.75 + 1.50 = \$9.25$$
 
---

## Problema 3 — Libre: Almacenamiento en la nube

**Enunciado:** Una empresa debe almacenar exactamente 100 TB de datos entre dos servicios: disco SSD ($S$) a \$10/TB y disco HDD ($H$) a \$4/TB. El SSD no puede superar 60 TB. Se quiere minimizar el costo.

### Variables de decisión

- $S$ = TB almacenados en SSD (TB)
- $H$ = TB almacenados en HDD (TB)

### Función objetivo (Minimizar)

$$\min\ Z = 10S + 4H$$

### Restricciones

| # | Restricción | Tipo | Descripción |
|---|-------------|------|-------------|
| 1 | $S + H = 100$ | = | Almacenar exactamente 100 TB |
| 2 | $S \leq 60$ | ≤ | Capacidad máxima de SSD |
| 3 | $S \geq 0$ | ≥ | No negatividad |
| 4 | $H \geq 0$ | ≥ | No negatividad |
 
### Solución
 
HDD es más barato (\$4/TB vs \$10/TB), así que metemos todo en HDD.
 
$S = 0$, $H = 100$ (cumple $S \leq 60$ y $S + H = 100$).
 
**Solución óptima:** $S = 0$, $H = 100$
 
$$Z = 10(0) + 4(100) = \$400$$
 
---

*Optimización 2026 · Universidad Nacional de Colombia · Sede Bogotá*
