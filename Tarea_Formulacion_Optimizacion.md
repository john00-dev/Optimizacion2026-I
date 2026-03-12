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

---

*Optimización 2026 · Universidad Nacional de Colombia · Sede Bogotá*
