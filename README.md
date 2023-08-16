- nota: me encuentro subiendo la documentación del proyecto.
# Análisis de Tienda en Línea - Proyecto Power BI

Este proyecto utiliza Power BI para analizar una pequeña base de datos de una tienda en línea. El objetivo del proyecto es realizar un 
análisis detallado de las ventas y el rendimiento de la tienda, utilizando visualizaciones interactivas y paneles informativos.
![Sales report.PNG](images%2FSales%20report.PNG)

## Pasos del desarrollo del proyecto

### Conexión a la Base de Datos

1. Utilicé la función de conexión de Power BI para establecer conexión con la base de datos PostgreSQL.
2. Seleccioné las tablas relevantes (`country`, `customer`, `order`, etc.) para el análisis.
Base de datos de muestra utilizada
![diagram data base.png](images%2Fdiagram%20data%20base.png)

### Transformación de Datos

- Agregar la columna full_name a la tabla `customer` con la siguiente fórmula: `full_name = customer[first_name] & " " & customer[last_name]`
- Creación de la tabla `calendar`, esto permite la relación de la columna fecha de la tabla `order` con la tabla `calendar` y poder manejar de forma más sencilla la manipulación de datos. 
Se consigue la tabla `calendar` con la siguiente fórmula: calendar = `CALENDAR(MIN('order'[order_date]), MAX('order'[order_date]))`
- Creación de query para mostrar la fecha de actualización del reporte, al estar conectado a una base de datos se debe mostrar la fecha de actualización de los datos (Tener cuidado con el timezone de tu motor BBDD). 
Para esto se crea una tabla `Last Refresh Data` para saber más de esto puede consultar este link: https://learn.microsoft.com/en-us/azure/devops/report/powerbi/add-last-refresh-time?view=azure-devops&tabs=private

Resultado del modelo
![modelo-powerbi.PNG](images%2Fmodelo-powerbi.PNG)

### Creación de Visualizaciones

- Creación de segmento de meses y años(utilizando la tabla `calendar`) para filtrar los datos.
- Gráficos de torta para mostrar los tipos de órdenes (online, presencial, móvil).
- Implementación un gráfico lineal que muestra las ventas por mes y año para identificar tendencias.
- Creación una tabla resumen por país para analizar los indicadores de ventas.
