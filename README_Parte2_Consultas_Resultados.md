# 📘 SQL Entrevistas – Parte 2: Consultas SQL y Resultados Esperados

## 01. Clientes sin pedidos

### 🧠 Consulta SQL
```sql
-- Clientes que no han hecho pedidos
SELECT c.id, c.nombre
FROM Clientes c
LEFT JOIN Pedidos p ON c.id = p.cliente_id
WHERE p.id IS NULL;
```

---

## 02. Total de pedidos por cliente

### 🧠 Consulta SQL
```sql
-- Número total de pedidos por cliente
SELECT cliente_id, COUNT(*) AS total_pedidos
FROM Pedidos
GROUP BY cliente_id;
```

---

## 03. Segundo salario más alto por departamento

### 🧠 Consulta SQL
```sql
-- Segundo salario más alto por departamento
SELECT *
FROM (
    SELECT *,
           DENSE_RANK() OVER (PARTITION BY departamento ORDER BY salario DESC) AS rnk
    FROM Empleados
) t
WHERE rnk = 2;
```

---

## 04. Productos con más ventas que el promedio

### 🧠 Consulta SQL
```sql
-- Productos cuya suma de ventas es mayor al promedio
SELECT producto_id, SUM(cantidad) AS total
FROM Ventas
GROUP BY producto_id
HAVING SUM(cantidad) > (
    SELECT AVG(total_por_producto)
    FROM (
        SELECT SUM(cantidad) AS total_por_producto
        FROM Ventas
        GROUP BY producto_id
    ) sub
);
```

---

## 05. Clientes con más de 3 pedidos

### 🧠 Consulta SQL
```sql
WITH pedidos_por_cliente AS (
    SELECT cliente_id, COUNT(*) AS total
    FROM Pedidos
    GROUP BY cliente_id
)
SELECT cliente_id
FROM pedidos_por_cliente
WHERE total > 3;
```

---

## 06. Última compra por cliente

### 🧠 Consulta SQL
```sql
SELECT *
FROM (
    SELECT *, ROW_NUMBER() OVER (PARTITION BY cliente_id ORDER BY fecha DESC) AS rn
    FROM Compras
) t
WHERE rn = 1;
```

---

## 07. Días sin ventas

### 🧠 Consulta SQL
```sql
SELECT c.fecha
FROM Calendario c
LEFT JOIN Ventas2 v ON c.fecha = v.fecha
WHERE v.id IS NULL;
```

---

## 08. Empleados en el mismo departamento

### 🧠 Consulta SQL
```sql
SELECT e1.nombre AS empleado1, e2.nombre AS empleado2, e1.departamento
FROM Empleados e1
JOIN Empleados e2 ON e1.departamento = e2.departamento
WHERE e1.id < e2.id;
```

---

## 09. Separar etiquetas

### 🧠 Consulta SQL
```sql
SELECT id, UNNEST(string_to_array(etiquetas, ',')) AS etiqueta
FROM Post;
```

---

## 10. Comparar UNION vs UNION ALL

### 🧠 Consulta SQL
```sql
-- UNION
SELECT id FROM A
UNION
SELECT id FROM B;

-- UNION ALL
SELECT id FROM A
UNION ALL
SELECT id FROM B;
```

---

## 11. Detectar emails duplicados

### 🧠 Consulta SQL
```sql
SELECT email, COUNT(*) AS veces
FROM Usuarios
GROUP BY email
HAVING COUNT(*) > 1;
```

---

## 12. Top 3 productos más vendidos

### 🧠 Consulta SQL
```sql
SELECT producto, cantidad
FROM VentasTop
ORDER BY cantidad DESC
LIMIT 3;
```

---

## 13. Usuarios activos por día

### 🧠 Consulta SQL
```sql
SELECT fecha, COUNT(DISTINCT usuario_id) AS usuarios_activos
FROM Eventos
GROUP BY fecha
ORDER BY fecha;
```

---

## 14. Primer y último pedido por cliente

### 🧠 Consulta SQL
```sql
SELECT cliente_id,
       MIN(fecha) AS primer_pedido,
       MAX(fecha) AS ultimo_pedido
FROM Pedidos2
GROUP BY cliente_id;
```

---

## 15. Detectar sesiones separadas por más de 30 minutos

### 🧠 Consulta SQL
```sql
SELECT usuario_id, timestamp,
  CASE 
    WHEN timestamp - LAG(timestamp) OVER (PARTITION BY usuario_id ORDER BY timestamp) > INTERVAL '30 minutes'
    THEN 1 ELSE 0 
  END AS nueva_sesion
FROM EventosSesiones;
```

---

## 16. Transformar filas a columnas (pivot)

### 🧠 Consulta SQL
```sql
SELECT producto,
  SUM(CASE WHEN mes = 'Jan' THEN total ELSE 0 END) AS enero,
  SUM(CASE WHEN mes = 'Feb' THEN total ELSE 0 END) AS febrero
FROM VentasPivot
GROUP BY producto;
```

---

## 17. Venta más alta por tienda

### 🧠 Consulta SQL
```sql
SELECT *
FROM (
  SELECT *, RANK() OVER (PARTITION BY tienda ORDER BY total DESC) AS rnk
  FROM VentasMax
) t
WHERE rnk = 1;
```

---

## 18. Productos sin ventas

### 🧠 Consulta SQL
```sql
SELECT p.id, p.nombre
FROM Productos p
LEFT JOIN Ventas3 v ON p.id = v.producto_id
WHERE v.id IS NULL;
```

---

## 19. Suma acumulativa de ventas

### 🧠 Consulta SQL
```sql
SELECT fecha, total,
       SUM(total) OVER (ORDER BY fecha) AS total_acumulado
FROM VentasAcum;
```

---

## 20. Días entre compras por usuario

### 🧠 Consulta SQL
```sql
SELECT usuario_id, fecha,
       fecha - LAG(fecha) OVER (PARTITION BY usuario_id ORDER BY fecha) AS dias_entre_compras
FROM ComprasDias;
```

---

