# Agregar entrada a la bitácora de un prospecto

End point: https://pm.api.induxsoft.net/leads/add-entry.dkl

Solicitud con usuario y contraseña
```
Method: POST
Content-Type: application/json;charset=utf-8
{
  "uid":"Id de usuario (correo o teléfono)",
  "pwd":"Contraseña del usuario",
  "source":"Id de la tienda o una clave de API de una tienda",
  "lead_sys_pk": (Numérico,) clave primaria del prospecto,
  "text":"Nota de texto para la bitácora",
  "next_contact":"(opcional,) fecha en el formato yyyy-MM-ddTHH:mm:ss del próximo contacto previsto con el prospecto"
}
```

Solicitud con id de sesión
```
Method: POST
Content-Type: application/json;charset=utf-8
{
  "ids":"Id de sesión",
  "source":"Id de la tienda o una clave de API de una tienda",
  "lead_sys_pk": (Numérico,) clave primaria del prospecto,
  "text":"Nota de texto para la bitácora",
  "next_contact":"(opcional,) fecha en el formato yyyy-MM-ddTHH:mm:ss del próximo contacto previsto con el prospecto"
}
```

## Ejemplos

### Agregar una nota de texto
Agregar una nota de texto a un prospecto con clave primaria  168781 presentando id de sesión

Solicitud
```
Method: POST
Content-Type: application/json;charset=utf-8
{
  ids":"Id de sesión",
  "source":"Id de tienda o una clave API de una tienda",
  "lead_sys_pk":168781,
  "text":"Nota de ejemplo"
}
```

Respuesta

```
Content-Type: application/json;charset=utf-8
{
    "success": 1,
    "data": {
        "sys_pk": 454800,
        "sys_dtcreated": "2022-03-16T15:36:25",
        "uname": "ADMIN",
        "note": "Nota de ejemplo"
    }
}
```

### Establecer un recordatorio de próximo contacto
Programar una llamada telefónica para el día 25 de Marzo de 2022 a las 2:00PM

Solicitud
```
Method: POST
Content-Type: application/json;charset=utf-8
{
  ids":"Id de sesión",
  "source":"Id de tienda o una clave API de una tienda",
  "lead_sys_pk":168781,
  "text":"Llamar por teléfono",
  "next_contact":"2022-03-25T14:00:00"
}
```

Respuesta

```
Content-Type: application/json;charset=utf-8
{
    "success": 1,
    "data": {
        "sys_pk": 454802,
        "sys_dtcreated": "2022-03-16T15:39:14",
        "uname": "ADMIN",
        "note": "Llamar por tel\u00E9fono"
    }
}
```

### Quitar el recordatorio

Solicitud
```
Method: POST
Content-Type: application/json;charset=utf-8
{
  ids":"Id de sesión",
  "source":"Id de tienda o una clave API de una tienda",
  "lead_sys_pk":168781,
  "text":"Ejemplo de quitar recordatorio",
  "next_contact":null
}
```

Respuesta

```
Content-Type: application/json;charset=utf-8
{
    "success": 1,
    "data": {
        "sys_pk": 454807,
        "sys_dtcreated": "2022-03-16T15:44:13",
        "uname": "ADMIN",
        "note": "Ejemplo de quitar recordatorio"
    }
}
```
