# Transcribir notas a un ticket

Transcribe todas las notas de la bitácora del prospecto (desde el origen de los tiempos o desde la última vez que se transcribieron) como un
registro adjunto a un ticket.

End point: https://pm.api.induxsoft.net/customers/add-to-ticket.dkl

Solicitud con usuario y contraseña
```
Method: POST
Content-Type: application/json;charset=utf-8
{
  "uid":"Id de usuario (correo o teléfono)",
  "pwd":"Contraseña del usuario",
  "source":"Id de la tienda o una clave de API de una tienda",
  "lead_sys_pk": (numérico, es la clave primaria de un prospecto),
  "ticket_id": (numérico, es el Id de un ticket existente)
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
  "ticket_id": (numérico, es el Id de un ticket existente)
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
        "note": "*** ATT ***\r\nSe ha anexado informaci\u00F3n al caso (#11383) del cliente:XXXXXXXXXXX"
    }
}
```
