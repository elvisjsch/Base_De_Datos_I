# Ejemplo de Normalización de una Tabla SQL (1FN, 2FN, 3FN)

## Tabla Inicial (Sin Normalizar)

**Tabla: Pedidos_Clientes**

| ID_Pedido | Fecha_Pedido | ID_Cliente | Nombre_Cliente | Email_Cliente | Direccion_Cliente | ID_Producto | Nombre_Producto | Categoria_Producto | Precio_Unitario | Cantidad | Subtotal |
|-----------|--------------|------------|----------------|---------------|-------------------|-------------|-----------------|--------------------|-----------------|----------|----------|
| 1001      | 2023-05-10   | C001       | Juan Pérez     | juan@email.com| Calle 123, Ciudad | P101        | Laptop Pro      | Electrónicos       | 1200.00         | 1        | 1200.00  |
| 1001      | 2023-05-10   | C001       | Juan Pérez     | juan@email.com| Calle 123, Ciudad | P205        | Mouse Gamer     | Accesorios         | 45.00           | 2        | 90.00    |
| 1002      | 2023-05-11   | C002       | María Gómez    | maria@email.com| Avenida 456, Ciudad | P101       | Laptop Pro      | Electrónicos       | 1200.00         | 1        | 1200.00  |

**Problemas**: 
- Datos redundantes (info de cliente repetida)
- Atributos multivaluados (múltiples productos por pedido)
- Dependencias transitivas (el precio depende del producto, no del pedido)

---

## Primera Forma Normal (1FN)

**Reglas aplicadas**:
1. Eliminar grupos repetidos
2. Todos los atributos deben ser atómicos

**Tablas resultantes**:

**Pedidos**:
| ID_Pedido | Fecha_Pedido | ID_Cliente |
|-----------|--------------|------------|
| 1001      | 2023-05-10   | C001       |
| 1002      | 2023-05-11   | C002       |

**Clientes**:
| ID_Cliente | Nombre_Cliente | Email_Cliente | Direccion_Cliente |
|------------|----------------|---------------|-------------------|
| C001       | Juan Pérez     | juan@email.com| Calle 123, Ciudad |
| C002       | María Gómez    | maria@email.com| Avenida 456, Ciudad |

**Detalles_Pedido**:
| ID_Pedido | ID_Producto | Cantidad | Precio_Unitario | Subtotal |
|-----------|-------------|----------|-----------------|----------|
| 1001      | P101        | 1        | 1200.00         | 1200.00  |
| 1001      | P205        | 2        | 45.00           | 90.00    |
| 1002      | P101        | 1        | 1200.00         | 1200.00  |

**Productos**:
| ID_Producto | Nombre_Producto | Categoria_Producto | Precio_Unitario |
|-------------|-----------------|--------------------|-----------------|
| P101        | Laptop Pro      | Electrónicos       | 1200.00         |
| P205        | Mouse Gamer     | Accesorios         | 45.00           |

---

## Segunda Forma Normal (2FN)

**Reglas aplicadas**:
1. Debe estar en 1FN
2. Eliminar dependencias parciales (atributos que dependen de parte de la clave primaria)

**Tablas resultantes**:

**Detalles_Pedido** (modificada):
| ID_Pedido | ID_Producto | Cantidad |
|-----------|-------------|----------|
| 1001      | P101        | 1        |
| 1001      | P205        | 2        |
| 1002      | P101        | 1        |

**Productos** (igual que en 1FN):
| ID_Producto | Nombre_Producto | Categoria_Producto | Precio_Unitario |
|-------------|-----------------|--------------------|-----------------|
| P101        | Laptop Pro      | Electrónicos       | 1200.00         |
| P205        | Mouse Gamer     | Accesorios         | 45.00           |

---

## Tercera Forma Normal (3FN)

**Reglas aplicadas**:
1. Debe estar en 2FN
2. Eliminar dependencias transitivas (atributos que dependen de otros que no son clave)

**Tablas resultantes**:

**Categorias** (nueva tabla):
| ID_Categoria | Nombre_Categoria |
|--------------|------------------|
| CAT1         | Electrónicos     |
| CAT2         | Accesorios       |

**Productos** (modificada):
| ID_Producto | Nombre_Producto | ID_Categoria | Precio_Unitario |
|-------------|-----------------|--------------|-----------------|
| P101        | Laptop Pro      | CAT1         | 1200.00         |
| P205        | Mouse Gamer     | CAT2         | 45.00           |

**Clientes** (podría dividirse si la dirección fuera compleja):
| ID_Cliente | Nombre_Cliente | Email_Cliente | Direccion_Cliente |
|------------|----------------|---------------|-------------------|
| C001       | Juan Pérez     | juan@email.com| Calle 123, Ciudad |
| C002       | María Gómez    | maria@email.com| Avenida 456, Ciudad |

---
