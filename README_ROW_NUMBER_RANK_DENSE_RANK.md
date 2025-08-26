# 📘 ROW_NUMBER vs RANK vs DENSE_RANK 

# Enunciados


Este documento contiene la explicación de las funciones de ventana `ROW_NUMBER()`, `RANK()` y `DENSE_RANK()` en SQL con ejemplos claros.

---

# Tablas

## 🧩 Escenario: Salarios de empleados por departamento

### 📋 Tabla `Empleados`

| id | nombre | departamento | salario |
|----|--------|--------------|---------|
| 1  | Ana    | IT           | 5000    |
| 2  | Luis   | IT           | 4000    |
| 3  | Marta  | IT           | 4000    |
| 4  | Carla  | IT           | 3000    |
| 5  | Pepe   | HR           | 4000    |
| 6  | Juan   | HR           | 4000    |
| 7  | Sofía  | HR           | 3000    |

---

## 🔍 Comparación rápida

| Función        | Empates comparten ranking | Deja huecos | Numeración continua |
|----------------|---------------------------|-------------|----------------------|
| `ROW_NUMBER()` | ❌ No                     | ❌ No        | ✅ Sí                |
| `RANK()`       | ✅ Sí                     | ✅ Sí        | ❌ No                |
| `DENSE_RANK()` | ✅ Sí                     | ❌ No        | ✅ Sí                |

---

✅ Usa `ROW_NUMBER()` para numerar sin considerar empates.  
✅ Usa `RANK()` si quieres respetar empates dejando huecos.  
✅ Usa `DENSE_RANK()` si quieres empates sin huecos.



# Consultas y Resultados

Este documento contiene las consultas SQL con sus salidas esperadas para las funciones `ROW_NUMBER()`, `RANK()` y `DENSE_RANK()`.

---

## 1️⃣ ROW_NUMBER()

```sql
SELECT *,
       ROW_NUMBER() OVER (PARTITION BY departamento ORDER BY salario DESC) AS rn
FROM Empleados;
```

📤 **Salida esperada:**

| nombre | departamento | salario | rn |
|--------|--------------|---------|----|
| Ana    | IT           | 5000    | 1  |
| Luis   | IT           | 4000    | 2  |
| Marta  | IT           | 4000    | 3  |
| Carla  | IT           | 3000    | 4  |
| Pepe   | HR           | 4000    | 1  |
| Juan   | HR           | 4000    | 2  |
| Sofía  | HR           | 3000    | 3  |

---

## 2️⃣ RANK()

```sql
SELECT *,
       RANK() OVER (PARTITION BY departamento ORDER BY salario DESC) AS rk
FROM Empleados;
```

📤 **Salida esperada:**

| nombre | departamento | salario | rk |
|--------|--------------|---------|----|
| Ana    | IT           | 5000    | 1  |
| Luis   | IT           | 4000    | 2  |
| Marta  | IT           | 4000    | 2  |
| Carla  | IT           | 3000    | 4  |
| Pepe   | HR           | 4000    | 1  |
| Juan   | HR           | 4000    | 1  |
| Sofía  | HR           | 3000    | 3  |

---

## 3️⃣ DENSE_RANK()

```sql
SELECT *,
       DENSE_RANK() OVER (PARTITION BY departamento ORDER BY salario DESC) AS dr
FROM Empleados;
```

📤 **Salida esperada:**

| nombre | departamento | salario | dr |
|--------|--------------|---------|----|
| Ana    | IT           | 5000    | 1  |
| Luis   | IT           | 4000    | 2  |
| Marta  | IT           | 4000    | 2  |
| Carla  | IT           | 3000    | 3  |
| Pepe   | HR           | 4000    | 1  |
| Juan   | HR           | 4000    | 1  |
| Sofía  | HR           | 3000    | 2  |

