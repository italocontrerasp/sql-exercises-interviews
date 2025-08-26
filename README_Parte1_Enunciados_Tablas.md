# 📘 SQL Entrevistas – Parte 1: Enunciados y Tablas de Ejemplo

https://www.programiz.com/sql/online-compiler

## 01. Clientes sin pedidos

### 🧱 Tablas de ejemplo
```sql
-- Tabla: Clientes
CREATE TABLE Clientes (id INT, nombre TEXT);
INSERT INTO Clientes VALUES (1, 'Juan'), (2, 'Ana'), (3, 'Pedro');

-- Tabla: Pedidos
CREATE TABLE Pedidos (id INT, cliente_id INT, producto TEXT);
INSERT INTO Pedidos VALUES (1, 1, 'Teclado'), (2, 1, 'Mouse'), (3, 2, 'Monitor');
```

---

## 02. Total de pedidos por cliente

### 🧱 Tablas de ejemplo
```sql
-- Usamos la tabla Pedidos creada previamente
```

---

## 03. Segundo salario más alto por departamento

### 🧱 Tablas de ejemplo
```sql
-- Tabla: Empleados
CREATE TABLE Empleados (id INT, nombre TEXT, departamento TEXT, salario INT);
INSERT INTO Empleados VALUES 
(1, 'Carla', 'IT', 4000),
(2, 'Luis', 'IT', 3000),
(3, 'Marta', 'IT', 2500),
(4, 'Pedro', 'HR', 2800),
(5, 'Julia', 'HR', 2000);
```

---

## 04. Productos con más ventas que el promedio

### 🧱 Tablas de ejemplo
```sql
-- Tabla: Ventas
CREATE TABLE Ventas (producto_id TEXT, cantidad INT);
INSERT INTO Ventas VALUES
('A', 10), ('A', 15), ('B', 5), ('C', 20), ('C', 25);
```

---

## 05. Clientes con más de 3 pedidos

### 🧱 Tablas de ejemplo
```sql
-- Ya existe la tabla Pedidos
```

---

## 06. Última compra por cliente

### 🧱 Tablas de ejemplo
```sql
-- Tabla: Compras
CREATE TABLE Compras(id INT, cliente_id INT, fecha DATE, producto TEXT);
INSERT INTO Compras VALUES 
(1, 1, '2023-01-01', 'Laptop'),
(2, 1, '2023-01-15', 'Teclado'),
(3, 2, '2023-01-05', 'Mouse'),
(4, 2, '2023-01-20', 'Monitor');
```

---

## 07. Días sin ventas

### 🧱 Tablas de ejemplo
```sql
CREATE TABLE Calendario(fecha DATE);
INSERT INTO Calendario VALUES 
('2023-01-01'), ('2023-01-02'), ('2023-01-03');

CREATE TABLE Ventas2(id INT, fecha DATE, monto INT);
INSERT INTO Ventas2 VALUES (1, '2023-01-01', 100);
```

---

## 08. Empleados en el mismo departamento

### 🧱 Tablas de ejemplo
```sql
-- Ya existe la tabla Empleados
```

---

## 09. Separar etiquetas

### 🧱 Tablas de ejemplo
```sql
-- PostgreSQL
CREATE TABLE Post(id INT, etiquetas TEXT);
INSERT INTO Post VALUES (1, 'sql,etl,python'), (2, 'airflow,spark');
```

---

## 10. Comparar UNION vs UNION ALL

### 🧱 Tablas de ejemplo
```sql
CREATE TABLE A(id INT);
INSERT INTO A VALUES (1), (2);

CREATE TABLE B(id INT);
INSERT INTO B VALUES (2), (3);
```

---

## 11. Detectar emails duplicados

### 🧱 Tablas de ejemplo
```sql
CREATE TABLE Usuarios(id INT, email TEXT);
INSERT INTO Usuarios VALUES
(1, 'a@email.com'),
(2, 'b@email.com'),
(3, 'a@email.com'),
(4, 'c@email.com'),
(5, 'b@email.com');
```

---

## 12. Top 3 productos más vendidos

### 🧱 Tablas de ejemplo
```sql
CREATE TABLE VentasTop(producto TEXT, cantidad INT);
INSERT INTO VentasTop VALUES
('A', 100), ('B', 200), ('C', 150), ('D', 300);
```

---

## 13. Usuarios activos por día

### 🧱 Tablas de ejemplo
```sql
CREATE TABLE Eventos(usuario_id INT, evento TEXT, fecha DATE);
INSERT INTO Eventos VALUES
(1, 'login', '2023-01-01'),
(2, 'login', '2023-01-01'),
(1, 'login', '2023-01-02');
```

---

## 14. Primer y último pedido por cliente

### 🧱 Tablas de ejemplo
```sql
CREATE TABLE Pedidos2(id INT, cliente_id INT, fecha DATE);
INSERT INTO Pedidos2 VALUES
(1, 1, '2023-01-01'),
(2, 1, '2023-01-15'),
(3, 2, '2023-01-10');
```

---

## 15. Detectar sesiones separadas por más de 30 minutos

### 🧱 Tablas de ejemplo
```sql
CREATE TABLE EventosSesiones(usuario_id INT, evento TEXT, timestamp TIMESTAMP);
INSERT INTO EventosSesiones VALUES
(1, 'login', '2023-01-01 10:00:00'),
(1, 'click', '2023-01-01 10:10:00'),
(1, 'logout', '2023-01-01 11:00:00'),
(1, 'login', '2023-01-01 12:00:00');
```

---

## 16. Transformar filas a columnas (pivot)

### 🧱 Tablas de ejemplo
```sql
CREATE TABLE VentasPivot(mes TEXT, producto TEXT, total INT);
INSERT INTO VentasPivot VALUES
('Jan', 'A', 100), ('Jan', 'B', 150), ('Feb', 'A', 200), ('Feb', 'B', 300);
```

---

## 17. Venta más alta por tienda

### 🧱 Tablas de ejemplo
```sql
CREATE TABLE VentasMax(id INT, tienda TEXT, total INT);
INSERT INTO VentasMax VALUES
(1, 'A', 100), (2, 'A', 200), (3, 'B', 300), (4, 'B', 150);
```

---

## 18. Productos sin ventas

### 🧱 Tablas de ejemplo
```sql
CREATE TABLE Productos(id INT, nombre TEXT);
INSERT INTO Productos VALUES (1, 'Teclado'), (2, 'Monitor'), (3, 'Mouse');

CREATE TABLE Ventas3(id INT, producto_id INT);
INSERT INTO Ventas3 VALUES (1, 1), (2, 1), (3, 2);
```

---

## 19. Suma acumulativa de ventas

### 🧱 Tablas de ejemplo
```sql
CREATE TABLE VentasAcum(id INT, fecha DATE, total INT);
INSERT INTO VentasAcum VALUES
(1, '2023-01-01', 100),
(2, '2023-01-02', 200),
(3, '2023-01-03', 150);
```

---

## 20. Días entre compras por usuario

### 🧱 Tablas de ejemplo
```sql
CREATE TABLE ComprasDias(usuario_id INT, fecha DATE);
INSERT INTO ComprasDias VALUES
(1, '2023-01-01'),
(1, '2023-01-04'),
(1, '2023-01-10');
```

---

