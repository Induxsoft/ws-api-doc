# Actualiza o elimina varios prospectos

End point: https://pm.api.induxsoft.net/leads/update-many.dkl

Solicitud con usuario y contraseña
```
Method: POST
Content-Type: application/json;charset=utf-8
{
  "uid":"Id de usuario (correo o teléfono)",
  "pwd":"Contraseña del usuario",
  "source":"Id de la tienda o una clave de API de una tienda",
  "action":"update/delete",
  "leads":[sys_pk1, sys_pk2,...] (Claves primarias numéricas de los prospectos a eliminar o actualizar),
  "notes":"Información de bitácora por la operación"
  ... campos a actualizar ...
}
```

Solicitud con id de sesión
```
Method: POST
Content-Type: application/json;charset=utf-8
{
  "ids":"Id de sesión",
  "source":"Id de la tienda o una clave de API de una tienda",
  "action":"update/delete",
  "leads":[{"sys_pk": pk1}, {"sys_pk": pk2},...] (Claves primarias numéricas de los prospectos a eliminar o actualizar),
  "notes":"Información de bitácora por la operación"
  ... campos a actualizar ...
}
```

## Actualizar
Los campos que pueden actualizarse son:

* lead_owner - Cadena con el Id de perfil del agente (colaborador) al que está asignado el prospecto
* lead_status - Numérico, con la clave del estado en el que estarán los prospectos
* lead_color - Numérico con el color asignado a los prospectos (0-Blanco, 1-Rojo, 2-Verde, 3-Azul, 4-Morado y 5-Amarillo)

Ningún campo es requerido, pero debe indicarse al menos uno para que se realice la actualización

Ejemplo 

Solicitud con id de sesión que pone en color rojo a los prospectos con las claves primarias 168729, 168728, 168726 y 168725:
```
Method: POST
Content-Type: application/json;charset=utf-8
{
  "ids":"Id de sesión",
  "source":"Id de la tienda o una clave de API de una tienda",
  "action":"update",
  "leads":[{"sys_pk":168729},{"sys_pk":168728},{"sys_pk": 168726},{"sys_pk": 168725}],
  "lead_color":1
}
```

Respuesta
```
Content-Type: application/json;charset=utf-8
{
    "success": 1,
    "data": [{
        "sys_pk": 168729
    }, {
        "sys_pk": 168728
    }, {
        "sys_pk": 168726
    }, {
        "sys_pk": 168725
    }]
}
```


## Eliminar

No deben indicarse campos adicionales, esta operación realizará el borrado "lógico" (marca como eliminado el prospecto pero aun permanece en la base de datos).

Ejemplo

Elimina los prospectos con las claves: 168729, 168728, 168726 y 168725

```
Method: POST
Content-Type: application/json;charset=utf-8
{
  "ids":"Id de sesión",
  "source":"Id de la tienda o una clave de API de una tienda",
  "action":"delete",
  "leads":[{"sys_pk":168729},{"sys_pk":168728},{"sys_pk": 168726},{"sys_pk": 168725}]
}
```

Respuesta (claves eliminadas)
```
Content-Type: application/json;charset=utf-8
{
    "success": 1,
    "data": [{
        "sys_pk": 168729
    }, {
        "sys_pk": 168728
    }, {
        "sys_pk": 168726
    }, {
        "sys_pk": 168725
    }]
}
```
