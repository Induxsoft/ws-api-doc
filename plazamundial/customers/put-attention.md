# Transcribir notas como atención

Transcribe todas las notas de la bitácora del prospecto (desde el origen de los tiempos o desde la última vez que se transcribieron) como un
registro de Atención de un cliente registrado.

End point: https://pm.api.induxsoft.net/customers/put-attention.dkl

Solicitud con usuario y contraseña
```
Method: POST
Content-Type: application/json;charset=utf-8
{
  "uid":"Id de usuario (correo o teléfono)",
  "pwd":"Contraseña del usuario",
  "source":"Id de la tienda o una clave de API de una tienda",
  "lead_sys_pk": (numérico, es la clave primaria de un prospecto),
  "customer_id": "El código de un cliente"
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
  "customer_id": "El código de un cliente"
}
```

Respuesta
```
Content-Type: application/json;charset=utf-8
{
    "success": 1,
    "data": {
        "sys_pk": 457360 (id de la entrada en la bitácora del prospecto),
        "sys_dtcreated": "2022-03-24T14:51:34",
        "uname": "Nombre del usuario que creó el registro",
        "note": "*** ATT ***\r\nSe ha creado un registro de atenci\u00F3n al cliente: xxxxxxxx"
    }
}
```
