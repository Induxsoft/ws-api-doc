# Crear un nuevo ticket de cliente

Crea un nuevo ticket (caso) de un cliente

End point: https://pm.api.induxsoft.net/customers/new-ticket.dkl

Solicitud con usuario y contraseña
```
Method: POST
Content-Type: application/json;charset=utf-8
{
  "uid":"Id de usuario (correo o teléfono)",
  "pwd":"Contraseña del usuario",
  "source":"Id de la tienda o una clave de API de una tienda",
  "lead_sys_pk": (numérico, es la clave primaria de un prospecto),
  "customer_id": "El código de un cliente",
  "ticket_type_id":(numérico, clave -id- del tipo de ticket a crear),
  "subject":"Título o asunto del ticket",
  "remarks":"Comentarios o notas del ticket"
  
}
```

Solicitud con id de sesión
```
Method: POST
Content-Type: application/json;charset=utf-8
{
  "ids":"Id de sesión válida (token)",
  "source":"Id de la tienda o una clave de API de una tienda",
  "lead_sys_pk": (numérico, es la clave primaria de un prospecto),
  "customer_id": "El código de un cliente",
  "ticket_type_id":(numérico, clave -id- del tipo de ticket a crear),
  "subject":"Título o asunto del ticket",
  "remarks":"Comentarios o notas del ticket"
}
```

Respuesta
```
Content-Type: application/json;charset=utf-8
{
    "success": 1,
    "data": {
        "sys_pk": 457363 (clave primaria de la entrada en la bitácora del prospecto),
        "ticket_id":11381 (Id del nuevo caso),
        "sys_dtcreated": "2022-03-24T15:12:32",
        "uname": "Nombre del isuario que creó el ticket",
        "note": "*** ATT ***\r\nSe ha creado un nuevo caso(#11381) para el cliente: XXXXXXXXXXXXXXXXX"
    }
}
```
