# Obtener estados posibles para los prospectos

Devuelve un array de estados posibles para los prospectos

End point: https://pm.api.induxsoft.net/leads/list-lead-status.dkl

Solicitud con usuario y contraseña
```
Method: POST
Content-Type: application/json;charset=utf-8
{
  "uid":"Id de usuario (correo o teléfono)",
  "pwd":"Contraseña del usuario",
  "source":"Id de la tienda o una clave de API de una tienda"
}
```

Solicitud con id de sesión
```
Method: POST
Content-Type: application/json;charset=utf-8
{
  "ids":"Id de sesión",
  "source":"Id de la tienda o una clave de API de una tienda"
}
```

Respuesta exitosa

```
Content-Type: application/json;charset=utf-8
{
    "success": 1,
    "data": [{
        "key": 999,
        "caption": "(Por atender)",
        "final": false
    }, {
        "key": 0,
        "caption": "Recibido",
        "final": false
    }, {
        "key": 1,
        "caption": "Atendido",
        "final": true
    }, {
        "key": 2,
        "caption": "Descartado",
        "final": true
    }, {
        "key": 3,
        "caption": "Oportunidad",
        "final": false
    }, {
        "key": 4,
        "caption": "Ganado :)",
        "final": true
    }, {
        "key": 5,
        "caption": "Perdido :(",
        "final": true
    }]
}
```

* El campo 'final' indica si se considera un estado final o no, los status con clave >=999 implican combinaciones de dos o más status y otras condiciones.
