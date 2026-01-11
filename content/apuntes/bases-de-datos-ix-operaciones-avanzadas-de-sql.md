---
Date: 2025-08-08
Time: 02:22
tags:
- enciclopedia
- aprenderBD
slug: bases-de-datos-ix-operaciones-avanzadas-de-sql
title: Bases de Datos IX - Operaciones Avanzadas de SQL
---

---

## I. Operaciones avanzadas

### 1.1 Procedimientos almacenados avanzados

Se pueden declarar variables que almacenen resultados de consultas y permitan realizar operaciones. Así mismo se pueden generar cambios en base a cierta lógica o notificar.

**Proceso**

1. Se crea el PA y se le da un nombre.
2. Se colocan los atributos de las tablas relevantes para el proceso.
3. Se declaran las variables que vamos a usar (No existen en las tablas).
4. Se realiza la selección para invocar los datos necesarios. Asignar esto a una variable.
5. Se realiza la lógica requerida con las variables declaradas.
6. Se ejecuta.

**Ejemplos**

Procedimiento para verificar el precio de los productos, si es mayor a 2000 aplicar descuento del 12 %, en caso contrario 2% y también recibir como parámetro la cantidad y regresar el monto total a pagar con descuento

```
CREATE PROCEDURE SP_TotalConDescuento
(
    @producto_id INT,
    @cantidad INT
)
AS
BEGIN

	DECLARE @precio DECIMAL(10,2);
	DECLARE @descuento DECIMAL(10,2);
	DECLARE @total DECIMAL(10,2);
	
	SELECT @precio = precio
	FROM Productos
	WHERE id_producto = @producto_id;
	
	IF @precio > 2000
		SET @descuento = 0.88; 
	ELSE
		SET @descuento = 0.98;  
		SET @total = (@precio * @descuento) * @cantidad;
		PRINT 'El total a pagar con descuento es: ' + CAST(@total AS VARCHAR(20));
END

EXECUTE SP_TotalConDescuento 1, 5;
```

- Validar la existencia de las paletas y aquellas con cantidad mayor a 100 descuento del 3%. Se busca por id.

```
CREATE PROCEDURE SP_DescuentoPaletas
(
    @id_paleta INT
)
AS
BEGIN

	DECLARE @cantidad INT;
	DECLARE @precio DECIMAL(10,2);
	DECLARE @descuento DECIMAL(10,2) = 0.97;
	DECLARE @total DECIMAL(10,2);

	SELECT @cantidad = cantidad, @precio = precio
	FROM Paletas
	WHERE id_paleta = @id_paleta;

	IF @cantidad > 100
		BEGIN
			SET @total = (@precio * @descuento);

			UPDATE Paletas
			SET precio = @total
			WHERE id_paleta = @id_paleta;

			PRINT 'Se ha aplicado un descuento al precio original del 3%: ' + CAST(@total AS VARCHAR(20));
		END
	ELSE
		BEGIN
			PRINT 'El precio actual se mantiene: ' + CAST(@precio AS VARCHAR(20));
		END

END

EXECUTE SP_DescuentoPaletas 1;
```

- **Actualización** del precio de los que son menores a 50 pesos y actualizarlo con la suma de 20 pesos más. Afecta a todos los datos.

```
CREATE PROCEDURE SP_AumentarPrecioPaletas
AS
BEGIN

	DECLARE @precio DECIMAL(10,2);
	DECLARE @totalDescuento DECIMAL(10,2);
	
	SELECT @precio = precio
	FROM Paletas;

	IF @precio &lt; 50
		BEGIN
			SET @totalDescuento = (@precio + 50);

			UPDATE Paletas
			SET precio = @totalDescuento;

			PRINT 'Precios actualizados: ' + CAST(@precio AS VARCHAR(20)) + ' -&gt; ' + CAST(@totalDescuento AS VARCHAR(20)) ;
		END
	ELSE
		BEGIN
			PRINT 'Los precios actuales se mantienen: ' + CAST(@precio AS VARCHAR(20));
		END
END

EXEC SP_AumentarPrecioPaletas;
```

---

## / Más Información

- [Bases de Datos I - Conceptos Básicos](/apuntes/bases-de-datos-i-conceptos-basicos/)
- [Bases de Datos II - Diagramas y Documentación](/apuntes/bases-de-datos-ii-diagramas-y-documentacion/)
- [Bases de Datos III - Reglas de Normalización](/apuntes/bases-de-datos-iii-reglas-de-normalizacion/)
- [Bases de Datos IV - Álgebra Relacional](/apuntes/bases-de-datos-iv-algebra-relacional/)
- [Bases de Datos V - Microsoft SQL](/apuntes/bases-de-datos-v-microsoft-sql/)
- [Bases de Datos VI - Estructura Básica de SQL](/apuntes/bases-de-datos-vi-estructura-basica-de-sql/)
- [Bases de Datos VII - Consultas de Datos](/apuntes/bases-de-datos-vii-consultas-de-datos/)
- [Bases de Datos VIII - Automatización y Seguridad](/apuntes/bases-de-datos-viii-automatizacion-y-seguridad/)
- [Bases de Datos IX - Operaciones Avanzadas de SQL](/apuntes/bases-de-datos-ix-operaciones-avanzadas-de-sql/)

---