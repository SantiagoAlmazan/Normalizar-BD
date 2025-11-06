# Normalizar-BD

# Normalización de Datos en Excel (hasta 3FN)
**Autor:** Santiago Isaías Almazán Chávez  
**Materia:** Administración de Bases de Datos  
**Semestre:** 7°  
**Fecha:** Noviembre 2025  

---

Introducción
Este proyecto se realizó a partir de un archivo Excel proporcionado por el profesor, el cual contenía información combinada de clientes, pedidos, productos y direcciones.  
El objetivo fue aplicar las **tres primeras formas normales (1FN, 2FN y 3FN)** para mejorar la estructura y eliminar redundancias o dependencias incorrectas.

El trabajo se hizo paso a paso, analizando los datos y generando nuevas tablas más limpias, preparadas para un sistema de gestión de base de datos.

---

Paso 1: Análisis inicial del archivo Excel
Se revisaron las columnas para identificar:
- Datos repetidos (por ejemplo, un mismo cliente aparecía varias veces).
- Celdas con más de un dato (por ejemplo, “Teléfono 1 / Teléfono 2”).
- Columnas con dependencias funcionales, es decir, cuando un dato depende de otro que no es clave.

---

Primera Forma Normal (1FN)
**Objetivo:** que cada campo contenga un solo valor atómico y no existan grupos repetitivos.  

**Acciones realizadas:**
- Se eliminaron celdas con varios datos combinados.  
- Se separaron columnas como “Teléfono” o “Dirección”.  
- Se creó una primera tabla plana llamada `prelim_1fn_table.csv`.

**Resultado:** cada fila representa una sola combinación de cliente, pedido y producto.

---

Segunda Forma Normal (2FN)
**Objetivo:** eliminar dependencias parciales (atributos que dependen solo de una parte de la clave).  

**Acciones realizadas:**
- Se identificaron columnas que solo dependían del cliente (por ejemplo, Razón Social, Dirección, Teléfono).  
- Se separaron en tablas diferentes:
  - `Clientes`
  - `Pedidos`
  - `Productos`
  - `Detalle de pedidos`

**Resultado:** las tablas quedaron más ordenadas y sin información repetida por cada pedido.

---

Tercera Forma Normal (3FN)
**Objetivo:** eliminar dependencias transitivas (atributos que dependen de otros atributos que no son clave).  

**Acciones realizadas:**
- Se detectaron relaciones como “Código Postal → Colonia → Ciudad”, que eran dependencias indirectas.
- Se crearon tablas auxiliares para romper esas dependencias cuando fue necesario.
- Se generaron relaciones entre las tablas usando claves primarias y foráneas.

**Resultado:** el modelo final cumple con 3FN, donde cada dato depende únicamente de su clave principal.

---

 Tablas finales
- **orders_3fn.csv:** información general del pedido (cliente, fecha, total, etc.).  
- **order_items_3fn.csv:** detalle de los productos en cada pedido.  
- **products_3fn.csv:** catálogo de productos únicos.  
- **decision_log.md:** reporte con las decisiones y justificaciones de cada cambio.  

---

Diagrama Relacional
El diagrama se generó en formato **DBML** y puede visualizarse fácilmente en  
Para verlo:
1. Entra a dbdiagram.io  
2. Da clic en **“Create a new diagram”**  
3. Copia el contenido del archivo `diagram/final_diagram_3fn.dbml`  
4. Se mostrará el esquema con las relaciones entre tablas.

---

Conclusión
Durante este proyecto aprendí a identificar dependencias funcionales, parciales y transitivas dentro de una base de datos.  
También comprendí cómo dividir una tabla compleja en varias entidades relacionadas, respetando las **formas normales**.  
Aunque el análisis fue automatizado con ayuda de herramientas, revisé manualmente los resultados para entender el porqué de cada decisión.

Este proceso me ayudó a visualizar cómo un archivo Excel desorganizado puede transformarse en una base de datos limpia, eficiente y lista para ser implementada en SQL.

---


---

### 💡 Nota final
El análisis se realizó como ejercicio académico. Las estructuras pueden adaptarse según el contexto real o las reglas de negocio del sistema.

---

## 🧰 Herramientas utilizadas
- **Excel / Pandas (Python)** — para limpiar y analizar datos  
- **dbdiagram.io** — para visualizar el modelo entidad-relación  
- **GitHub** — para documentar y entregar el trabajo
