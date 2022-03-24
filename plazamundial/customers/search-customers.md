# Buscar clientes

Devuelve un array con el código (customer_id) y nombre (customer_name) de los clientes que cumplen con el criterio de filtro indicado

End point: https://pm.api.induxsoft.net/customers/search-customers.dkl

Solicitud con usuario y contraseña
```
Method: POST
Content-Type: application/json;charset=utf-8
{
  "uid":"Id de usuario (correo o teléfono)",
  "pwd":"Contraseña del usuario",
  "source":"Id de la tienda o una clave de API de una tienda",
  "text":"Criterio de filtro (parte del código, nombre o rfc del cliente)"
}
```

Solicitud con Id de sesión
```
Method: POST
Content-Type: application/json;charset=utf-8
{
  "ids":"Id de sesión (token)",
  "source":"Id de la tienda o una clave de API de una tienda",
  "text":"Criterio de filtro (parte del código, nombre o rfc del cliente)"
}
```

Respuesta
Solicitud con usuario y contraseña
```
Content-Type: application/json;charset=utf-8
{
    "success": 1,
    "data": [{
        "customer_id": "codigo1",
        "customer_name": "Nombre del cliente 1"
    }, {
        "customer_id": "codigoN",
        "customer_name": "Nombre del cliente N"
    }]
}
```
