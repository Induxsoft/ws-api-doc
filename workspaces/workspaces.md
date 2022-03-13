# Administración de espacios de trabajo
## Generalidades
Los espacios de trabajo son una forma de organizar y coordinar equipos de trabajo y sus derechos sobre diversos activos o servicios.

La propietariedad de un espacio de trabajo corresponde a un usuario (perfil) o a una organización (NIC).

En el caso de las organizaciones, pueden crear y administrar espacios de trabajo únicamente los usuarios vinculados al panel de control del NIC.

En todos los casos, cada espacio de trabajo puede configurar un equipo (grupo de usuarios) con permisos de administración.

## End point

https://api.induxsoft.net/workspaces/

Todos los servicios de administración se utilizan a través del mismo end-point

### Observaciones
* En las colicitudes que requieren los campos 'workspace', 'team' o 'role', puede omitirlos y en su lugar utilizar únicamente un campo denominado 'location' en la forma de una ruta: 'workspace/team/role'

## Crear objetos

### Espacio de trabajo

Solicitud
```
Method: POST
Content-Type: application/json;charset=utf-8
{
  "ids":"Identificador de sesión válida (token)",
  "operation":"create",
  "owner":"NIC de la organización, si se omite se asume al usuario como propietario (omitible)",
  "data":
    {
      "name":"Nombre del nuevo espacio de trabajo",
      ...Campos adicionales que se desee incluir ...
    }
}
```

Respuesta exitosa

```
Content-Type: application/json;charset=utf-8
{
  "success":true,
  "data":
  {
    "id":"Identificador del nuevo espacio de trabajo",
    ... Todos los datos disponibles del espacio de trabajo ...
  }
}
```

### Equipo

Solicitud
```
Method: POST
Content-Type: application/json;charset=utf-8
{
  "ids":"Identificador de sesión válida (token)",
  "operation":"create",
  "owner":"NIC de la organización, si se omite se asume al usuario como propietario (omitible)",
  "workspace":"id del espacio de trabajo al que pertencerá el equipo",
  "data":
    {
      "name":"Nombre del nuevo equipo",
      ...Campos adicionales que se desee incluir ...
    }
}
```

Respuesta exitosa

```
Content-Type: application/json;charset=utf-8
{
  "success":true,
  "data":
  {
    "id":"Identificador del nuevo equipo",
    ... Todos los datos disponibles del equipo ...
  }
}
```


### Rol

Solicitud
```
Method: POST
Content-Type: application/json;charset=utf-8
{
  "ids":"Identificador de sesión válida (token)",
  "operation":"create",
  "owner":"NIC de la organización, si se omite se asume al usuario como propietario (omitible)",
  "workspace":"id del espacio de trabajo al que pertencerá el rol",
  "team":"id del equipo al que pertenecerá el rol",
  "data":
    {
      "name":"Nombre del nuevo rol",
      ...Campos adicionales que se desee incluir ...
    }
}
```

Respuesta exitosa

```
Content-Type: application/json;charset=utf-8
{
  "success":true,
  "data":
  {
    "id":"Identificador del nuevo equipo",
    ... Todos los datos disponibles del rol ...
  }
}
```

## Obtener (leer) objetos

Solicitud
```
Method: POST
Content-Type: application/json;charset=utf-8
{
  "ids":"Identificador de sesión válida (token)",
  "operation":"read",
  "owner":"NIC de la organización, si se omite se asume al usuario como propietario (omitible)",
  "id":"Id del espacio de trabajo, equipo o rol cuyos datos requiere obtener"
}
```

Respuesta exitosa

```
Content-Type: application/json;charset=utf-8
{
  "success":true,
  "data":
  {
    "id":"Identificador del nuevo espacio de trabajo",
    ... Todos los datos disponibles del objeto solicitado ...
  }
}
```

## Actualizar datos de objetos

Solicitud
```
Method: POST
Content-Type: application/json;charset=utf-8
{
  "ids":"Identificador de sesión válida (token)",
  "operation":"update",
  "owner":"NIC de la organización, si se omite se asume al usuario como propietario (omitible)",
  "id":"Id del espacio de trabajo, equipo o rol cuyos datos requiere actualizar",
  "data":{...datos a actualizar...}
}
```

Respuesta exitosa

```
Content-Type: application/json;charset=utf-8
{
  "success":true,
  "data":
  {
    "id":"Identificador del nuevo espacio de trabajo",
    ... Todos los datos disponibles del objeto solicitado ...
  }
}
```
## Eliminar objetos

Solicitud
```
Method: POST
Content-Type: application/json;charset=utf-8
{
  "ids":"Identificador de sesión válida (token)",
  "operation":"delete",
  "owner":"NIC de la organización, si se omite se asume al usuario como propietario (omitible)",
  "id":"Id del espacio de trabajo, equipo o rol a eliminar"
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
