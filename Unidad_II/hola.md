# Ejemplo de Normalización de una Tabla SQL (1FN, 2FN, 3FN)

Voy a mostrarte un ejemplo completo de una tabla que evoluciona a través de las tres formas normales principales, usando el caso de un sistema de pedidos de una tienda en línea.

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

**Cambios**:
- En Detalles_Pedido, Precio_Unitario y Subtotal dependen solo de ID_Producto, no de la combinación ID_Pedido+ID_Producto
- Movemos Precio_Unitario a la tabla Productos (ya hecho en 1FN)
- Subtotal es calculado (Cantidad * Precio_Unitario) y puede eliminarse

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

**Cambios**:
- En Productos, Categoria_Producto podría tener su propia tabla si tuviera más atributos
- En Clientes, la dirección podría normalizarse si fuera compuesta

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

## Estructura Final Normalizada (1FN + 2FN + 3FN)

1. **Pedidos** (`ID_Pedido`, Fecha_Pedido, `ID_Cliente`)
2. **Clientes** (`ID_Cliente`, Nombre_Cliente, Email_Cliente, Direccion_Cliente)
3. **Detalles_Pedido** (`ID_Pedido`, `ID_Producto`, Cantidad)
4. **Productos** (`ID_Producto`, Nombre_Producto, `ID_Categoria`, Precio_Unitario)
5. **Categorias** (`ID_Categoria`, Nombre_Categoria)

**Ventajas**:
- Eliminación de redundancias
- Mejor integridad de datos
- Facilidad de mantenimiento
- Consultas más eficientes para casos específicos

Este ejemplo muestra cómo una tabla inicial con problemas de diseño puede transformarse progresivamente en una estructura normalizada que cumple con las tres formas normales principales.