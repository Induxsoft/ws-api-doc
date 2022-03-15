# Obtener lista de prospectos

Devuelve la lista de prospectos que coinciden con el criterio de filtro indicado.

End point: https://pm.api.induxsoft.net/leads/list-leads.dkl

Solicitud con usuario y contraseña
```
Method: POST
Content-Type: application/json;charset=utf-8
{
  "uid":"Id de usuario (correo o teléfono)",
  "pwd":"Contraseña del usuario",
  "source":"Id de la tienda o una clave de API de una tienda",
  "agent_filter":"Id del agente propietario del prospecto",
  "status_filter": (Numérico omitible, clave de estado del prospecto),
  "color_filter": (Numérico omitible, clave de color)
}
```

Solicitud con id de sesión
```
Method: POST
Content-Type: application/json;charset=utf-8
{
  "ids":"Id de sesión",
  "source":"Id de la tienda o una clave de API de una tienda",
  "agent_filter":"Id del agente propietario del prospecto",
  "status_filter": (Numérico omitible, clave de estado del prospecto),
  "color_filter": (Numérico omitible, clave de color)
}
```

Consideraciones:

* En el campo 'agent_filter' debe indicar el Id de un agente o alguno de los siguientes valores predeterminados 'unassigned' (prospectos sin asignar) o 'all' (todos los prospectos de todos los agentes, asignados o no)
* En el campo 'color_filter' use alguno de los siguientes códigos de color: 0-Blanco, 1-Rojo, 2-Verde, 3-Azul, 4-Morado y 5-Amarillo

Respuesta exitosa

```
Content-Type: application/json;charset=utf-8
{
    "success": 1,
    "message": "Ninguna operaci\u00F3n realizada",
    "data": [
            {
                "sys_pk": 168373,
                "sys_dtcreated": "2022-03-15T15:25:57",
                "sys_timestamp": "2022-03-15T15:25:57",
                "sys_guid": "37731452b9254a5b9ccdfda5fe4627db",
                "recived": "2022-03-15T15:25:57",
                "next_contact": "",
                "last_contact": "",
                "last_attempt": "",
                "agent_id": "",
                "leadstatus": 0,
                "subject": "Asunto o título asignado al prospecto",
                "color": 0,
                "name": "Nombre del prospecto",
                "email": "Correo electrónico del prospecto",
                "phone": "Teléfono del prospecto",
                "organization": "Empresa u organización",
                "remarks": "Comentarios o mensaje enviado",
                "position": null,
                "agent_name": "Sin asignar",
                "leadstatus_text": "Recibido",
                "log": [
                    {
                    "sys_pk": 453857,
                    "sys_dtcreated": "2022-03-15T14:49:16",
                    "uname": "Nombre del usuario que puso la nota",
                    "note": "Texto de la nota"
                      },...]
            }, ...
    ]
}
```
