# Agregar o actualizar prospecto

Agrega un nuevo prospecto o actualiza uno existente con base en su clave primaria (sys_pk).

End point: https://pm.api.induxsoft.net/leads/post-lead.dkl

Solicitud con usuario y contraseña
```
Method: POST
Content-Type: application/json;charset=utf-8
{
  "uid":"Id de usuario (correo o teléfono)",
  "pwd":"Contraseña del usuario",
  "source":"Id de la tienda o una clave de API de una tienda",
  ... datos del prospecto ...
}
```

Solicitud con id de sesión
```
Method: POST
Content-Type: application/json;charset=utf-8
{
  "ids":"Id de sesión",
  "source":"Id de la tienda o una clave de API de una tienda",
  ... datos del prospecto ...
}
```

Los datos (campos) del prospecto aceptados son los siguientes, ninguno es requerido, 
pero debe indicarse al menos uno para que se realice una actualización y son necesarios para agregar un prospecto al menos 'name', 'subject' y 'email' o 'phone':

* sys_pk. Numérico, si no se indica la plataforma agregará un nuevo prospecto.
* recived. Cadena de fecha y hora en formato yyyy-MM-ddThh:mm:ss que corresponde a le fecha y hora de recepción del prospecto
* next_contact. Cadena de fecha y hora en formato yyyy-MM-ddThh:mm:ss que corresponde a le fecha y hora del próximo contacto programado
* agent_id. Cadena con el Id del perfil del agente (colaborador) al que está asignado el prospecto
* lead_status. Numérico con la clave del estado en el que está el prospecto.
* subject. Cadena con el asunto o título del prospecto
* remarks. Cadena con los comentarios o mensaje del prospecto
* color. Numérico que indica el color asignado al prospecto (0-Blanco, 1-Rojo, 2-Verde, 3-Azul, 4-Morado y 5-Amarillo)
* name. Cadena con el nombre del prospecto
* email. Cadena con el correo electrónico del prospecto
* phone. Cadena con el número telefónico del prospecto
* organization. Cadena con el nombre de la empresa u organización del prospecto
* position. Cadena con el nombre del puesto del prospecto en la organización

Ejemplo para agregar un prospecto

Solicitud con id de sesión
```
Method: POST
Content-Type: application/json;charset=utf-8
{
  "ids":"Id de sesión",
  "source":"Id de la tienda o una clave de API de una tienda",
  "name":"Juan López",
  "email":"correodejuan@servidordejuan.com",
  "phone":"5555555555",
  "subject":"prueba",
  "remarks":"Algún mensaje de prueba",
  "organization":"Empresa de juan",
  "position":"Puesto de juan en su empresa"
}
```

Respuesta

```
Content-Type: application/json;charset=utf-8
{
    "success": 1,
    "data": {
        "sys_pk": 168726,
        "sys_dtcreated": "2022-03-16T13:20:05",
        "sys_timestamp": "2022-03-16T13:20:05",
        "sys_guid": "9f0d74762562407da30b73ce2148832b",
        "recived": "2022-03-16T13:20:05",
        "next_contact": "",
        "last_contact": "",
        "last_attempt": "",
        "agent_id": "",
        "leadstatus": 0,
        "subject": "prueba",
        "color": 0,
        "name": "Juan L\u00F3pez",
        "email": "correodejuan@servidordejuan.com",
        "phone": "5555555555",
        "organization": "Empresa de juan",
        "remarks": "Alg\u00FAn mensaje de prueba",
        "position": "Puesto de juan en su empresa",
        "agent_name": "",
        "leadstatus_text": "Recibido",
        "log": [{
            "sys_pk": 454601,
            "sys_dtcreated": "2022-03-16T13:20:05",
            "uname": "ADMIN",
            "note": "Nuevo prospecto"
        }]
    }
}
```
