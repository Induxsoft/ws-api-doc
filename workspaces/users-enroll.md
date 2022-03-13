# Suscripción de usuarios

## Consideraciones
* Los usuarios (perfiles de Induxsoft) pueden relacionarse a espacios de trabajo, equipos y roles.
* Si el usuario no tiene un perfil al momento de ser "invitado" a un espacio, equipo o rol; se le enviará automáticamente un correo electrónico solicitándosele que se registre (cree un perfil) en induxsoft.net 
* Si el usuario ya tiene un perfil (registrado en induxsoft.net), pero no pertenece al espacio de trabajo o algún equipo, se le enviará un correo electrónico invitándole a unirse al espacio de trabajo (confirmación o aceptación)
* Si el usuario (ya tiene un perfil) y ya pertenece al espacio de trabajo (a algún equipo o rol), se suscribirá al equipo o rol que se indique sin invitación (es decir que no requiere que el usuario confirme o acepte explícitamente), solo será notificado del evento

## Inscripción

Solicitud
```
Method: POST
Content-Type: application/json;charset=utf-8
{
  "ids":"Identificador de sesión válida (token)",
  "operation":"register",
  "owner":"NIC de la organización, si se omite se asume al usuario como propietario (omitible)",
  "to":"Id del equipo de trabajo, equipo o rol al que se inscribirá al usuario",
  "user":"Correo electrónico, teléfono o id del usuario a inscribir"
}
```

Respuesta exitosa

```
Content-Type: application/json;charset=utf-8
{
  "success":true,
  "data":
  {
       ... Datos informativos de la operación ...
  }
}
```

## Des-inscripción

Solicitud
```
Method: POST
Content-Type: application/json;charset=utf-8
{
  "ids":"Identificador de sesión válida (token)",
  "operation":"unregister",
  "owner":"NIC de la organización, si se omite se asume al usuario como propietario (omitible)",
  "from":"Id del equipo de trabajo, equipo o rol al que está inscrito el usuario",
  "user":"Correo electrónico, teléfono o id del usuario a desinscribir"
}
```

Respuesta exitosa

```
Content-Type: application/json;charset=utf-8
{
  "success":true,
  "data": null
}
```
