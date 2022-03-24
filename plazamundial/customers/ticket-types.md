# Obtener tipos de tickets

Devuelve un array con información de los tipos de tickets disponibles.


End point: https://pm.api.induxsoft.net/customers/ticket-types.dkl

Solicitud con usuario y contraseña
```
Method: POST
Content-Type: application/json;charset=utf-8
{
  "uid":"Id de usuario (correo o teléfono)",
  "pwd":"Contraseña del usuario",
  "source":"Id de la tienda o una clave de API de una tienda",
}
```

Solicitud con Id de sesión
```
Method: POST
Content-Type: application/json;charset=utf-8
{
  "ids":"Id de sesión (token)",
  "source":"Id de la tienda o una clave de API de una tienda",
}
```

Respuesta
Solicitud con usuario y contraseña
```
Content-Type: application/json;charset=utf-8
{
    "success": 1,
    "data": [{
        "ticket_type_id": (numérico, id del tipo de ticket),
        "ticket_type": "Descripción o nombre del tipo de ticket"
    }, 
    {...},
    ...
    ]
}
```
