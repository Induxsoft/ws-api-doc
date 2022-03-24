# Buscar tickets abiertos

Devuelve un array con información de los tickets abiertos de un cliente.


End point: https://pm.api.induxsoft.net/customers/search-tickets.dkl

Solicitud con usuario y contraseña
```
Method: POST
Content-Type: application/json;charset=utf-8
{
  "uid":"Id de usuario (correo o teléfono)",
  "pwd":"Contraseña del usuario",
  "source":"Id de la tienda o una clave de API de una tienda",
  "customer_id":"Código del cliente"
}
```

Solicitud con Id de sesión
```
Method: POST
Content-Type: application/json;charset=utf-8
{
  "ids":"Id de sesión (token)",
  "source":"Id de la tienda o una clave de API de una tienda",
  "customer_id":"Código del cliente"
}
```

Respuesta
Solicitud con usuario y contraseña
```
Content-Type: application/json;charset=utf-8
{
    "success": 1,
    "data": [{
    "success": 1,
    "data": [{
        "ticket_type_id": 26,
        "ticket_type": "Quejas",
        "ticket_id": 11383,
        "ticket_creation": "2022-03-24T16:48:08",
        "ticket_subject": "Ticket de ejemplo3",
        "ticket_remarks": "Comentarios del ticket3"
    }, {
        "ticket_type_id": 26,
        "ticket_type": "Quejas",
        "ticket_id": 11382,
        "ticket_creation": "2022-03-24T16:47:16",
        "ticket_subject": "Ticket de ejemplo2",
        "ticket_remarks": "Comentarios del ticket2"
    }, ...]
}
```
