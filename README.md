
# Prueba para soporte tecnico Luuna

## SQL Básico

Existen 3 tablas de mysql con la siguiente información:

-**1. Order**: es una tabla con la información básica de la orden. La orden con id 567.

| id  | order_number  | order_total  | user_email  | user_id  | created_at |
|---|---|---|---|---|---|
|  ... | ... | ... | ... | ...  | ...  |
|  567 | 19857758784 | 29000 | alvaro.burgos | 5  | 2019-06-10 13:45:00  |
|  ... | ... | ... | ... | ...  | ...  |

-**2. OrderItem**: Contiene información básica de los items asociados a esa orden. La orden con id 567 contiene 3 items el 56 y el 57.

| id  | order_id  | sku  | item_total  | discount  | created_at |
|---|---|---|---|---|---|
|  ... | ... | ... | ... | ...  | ...  |
|  56 | 567 | LU1001 | 20000 | 0  | 2019-06-10 13:45:00  |
|  57 | 567 | LU1002 | 4500 | 0  | 2019-06-10 13:45:00  |
|  58 | 567 | LU1002 | 4500 | 0  | 2019-06-10 13:45:00  |
|  ... | ... | ... | ... | ...  | ...  |

-**3. MachineItem**: Mantiene el historial y los estados actuales en los que se encuentran los items. La columna `is_active` si es 1 detona que es un estado actual o 0 si es un estado en el que estuvo en el pasado.

I.e: El item `56` estuvo en el estado `shipping_pending` y en este momento se encuntra en el estado `shipping_approved`. El item 57 y 58 todavia estan en `shipping_pending`.

| id  | order_id  | item_id  | is_active  | status  | created_at |
|---|---|---|---|---|---|
|  23 | 567 | 56 | 0 | shipping_pending  | 2019-06-10 13:45:00  |
|  24 | 567 | 57 | 1 | shipping_pending  | 2019-06-10 13:45:00  |
|  24 | 567 | 58 | 1 | shipping_pending  | 2019-06-10 13:45:00  |
|  25 | 567 | 56 | 1 | shipping_approved | 2019-06-10 15:45:00  |

### Contesta a lo siguiente:

1. Utilizando una sola query: Alguién quiere saber cuales son los `sku` de la orden con `order_number` = `19857758784` que estan en el `status` actual de `shipping_pending`.
2. Utilizando 2 queries: Alguién quiere pasar los items que estan en shipping_pending de la order_number `order_number` = `19857758784` del status `shipping_pending` a el status `shipping_approved`. Para ello en la tabla **MachineItem** debes de actualizar las lineas con status shipping_pending a is_active = 0 y agregar nuevas lineas con el status shipping_approved con la columna is_active = 1.


