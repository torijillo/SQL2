1. Vista general del sistema

Este sistema modela el proceso completo de una planta:

👉 Pedido → Orden de Producción → Ejecución → Consumo de materiales

Es decir:

un cliente hace un pedido
el sistema lo transforma en una orden
se asigna a una línea
se ejecuta usando materiales (stock)
2. Bloque de planificación (arriba del modelo)
Gestión y Plan Operativo
Gestion
representa el año o periodo (ej: 2026)
PlanOperativo
pertenece a una gestión
organiza toda la operación

👉 Explicación:

Todo el sistema trabaja dentro de un plan operativo, que a su vez pertenece a una gestión.

3. Pedidos (entrada del sistema)
Cliente → Pedido → Pedido_Detalle
Cliente
quien solicita el pedido
Pedido
cabecera del pedido
tiene fecha, estado
Pedido_Detalle
contiene:
material requerido
cantidad

👉 Explicación:

Un pedido puede tener uno o varios materiales con cantidades específicas.

4. Materiales y Stock
Material + Stock + Stock_Movimiento
Material
catálogo de insumos
Stock
cantidad disponible por material y plan
Stock_Movimiento
historial de movimientos

👉 Explicación:

El sistema controla cuántos materiales hay disponibles y registra sus movimientos.

5. Generación de órdenes (núcleo del sistema)
Pedido → OrdenProduccion
OrdenProduccion
se genera desde un pedido
tiene:
línea asignada
cantidad total
estado

👉 Explicación clave:

Una orden de producción es la transformación de un pedido en trabajo real dentro de la planta.

6. Detalle de producción
OrdenProduccion_Detalle
materiales que usa la orden
estado por material

👉 Explicación:

Cada orden descompone el pedido en materiales específicos que se procesan individualmente.

7. Línea de producción
LineaProduccion
representa la máquina o área donde se produce

👉 Explicación:

Cada orden se asigna a una línea específica para su ejecución.

8. Flujo completo

Puedes decir esto textual:

El flujo del sistema inicia con la creación de un pedido por parte de un cliente.
Luego, mediante un procedimiento almacenado, el pedido se transforma en una orden de producción, validando que exista stock suficiente.
La orden se asigna a una línea de producción y se ejecuta, avanzando por distintos estados hasta completarse.
Durante este proceso, se consumen materiales del stock y se registran los movimientos correspondientes.

9. Validaciones importantes

👉 El sistema controla:

✔️ no generar orden si ya existe
✔️ no generar orden sin detalle
✔️ no generar orden sin stock
✔️ descontar stock automáticamente
✔️ cambiar estados de producción
10. Parte clave de la consigna

👉 Mención:

Se implementó una consulta con subconsultas que permite identificar pedidos que no pueden cumplirse por falta de materiales disponibles, lo cual cumple directamente con uno de los requisitos principales del sistema.

11. Estados
Pedido: REGISTRADO
Orden: GENERADA → EN_PRODUCCION → FINALIZADA
Detalle: PENDIENTE → EN_PROCESO → COMPLETADO
